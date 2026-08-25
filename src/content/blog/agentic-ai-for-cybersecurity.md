---
title: "Agentic AI in Cybersecurity: Moving Toward Fully Autonomous Pentesting"
description: "Hot take: fully autonomous pentesting isn't a moonshot but an engineering discipline. the real question is how can we make HITL the exception?"
pubDate: Aug 16 2025
heroImage: ../assets/agentic-ai-for-cybersecurity.png
---

### Hot take

I don't think human-in-the-loop (HITL) agentic AI[^1] is where this ends up. Inside a clearly defined scope, with real policies and guardrails doing the work, pentesting should run fully autonomously.

To be clear: full autonomy without guardrails is unsafe. What I'm arguing for is full autonomy inside strict policy, rich telemetry, and fast rollback, with HITL used by exception for destructive or regulated actions.

> There are two fundamental strategies to build an AI startup: you either bet the technology is going to get massively better or you bet the technology is about as good as it's going to be... In the first world, you will be really happy when the models improve, and in the second world you will be really sad. - [Sam Altman](https://www.youtube.com/watch?v=zoviibYmqmI)

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 12px; box-shadow: var(--box-shadow);">
  <iframe
    src="https://www.youtube.com/embed/zoviibYmqmI"
    title="Agentic AI for Cybersecurity"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;"
  ></iframe>
</div>

I'm taking the first bet: design for full autonomy within clear bounds, and let agents run pentest workflows end to end without pausing for approvals once the policy, telemetry, and rollback guarantees are in place.

### Why autonomy by default (and common misconceptions)

Automated recon can surface thousands of findings. If a person has to approve every step, chains stall and validating the real risk slows to a crawl ([Rapid7](https://www.rapid7.com/fundamentals/human-in-the-loop/)). Exploit chains run at machine speed, so approval queues add latency and hurt end-to-end completion rates ([AthenaCore](https://www.athenacore.com/post/human-in-the-loop-is-not-enough-designing-meaningful-human-oversight-for-high-risk-ai)). Operator judgment also varies and the skills are scarce, which is another reason gating by default doesn't scale ([SAFE Security](https://safe.security/resources/blog/what-is-agentic-ai-in-cybersecurity/)). And a flood of probes waiting on review produces triage fatigue and automation bias, which is the opposite of the oversight you wanted ([CybersecurityTribe](https://www.cybersecuritytribe.com/articles/an-introduction-agentic-ai-in-cybersecurity/)). Oversight that actually scales looks like attack graph traces (goals, steps, artifacts, outcomes), tool policies, and replayable logs, not a queue of black-box approvals ([NVIDIA Blog](https://blogs.nvidia.com/blog/agentic-ai-cybersecurity/)).

A few things people get wrong when I make this argument. You don't need AGI for it: narrow, policy-bounded autonomy can fully run recurring work like recon triage, exploit validation, canary-only lateral movement, evidence capture, and reporting at machine speed. Agents also aren't roaming freely. A well-designed system runs with least-privilege, short-lived capabilities tied to intent and scope, inside geofences and rate limits, and every step is replayable.

Edge cases are a policy problem, not an argument against autonomy: default-deny on uncertainty, stage in sandboxes and canaries first, escalate only on crisp triggers. Dropping step approvals doesn't mean dropping responsibility either. You swap them for policy-as-code and audit trails, keep exception approvals for destructive writes and policy violations, and get accountability from pre-authorization plus full telemetry. "Fully autonomous" also isn't a switch you flip on day one. You get there through progressive hardening: start safe, track reliability (chain completion, unsafe-action rate, time-to-detect, time-to-revert), then expand.

A concrete example: an agent triages web recon findings, validates an SSRF in a sandbox, moves laterally only within canary accounts (isolated, monitored decoys) using short-lived credentials, captures evidence, and leaves a replayable trace. It escalates only for destructive writes or when a policy-based risk score trips a threshold.

### Oversight model and caveats

Default to autonomy for low- and medium-risk actions in scoped, reversible environments. Keep continuous oversight and a fast-acting kill switch. Pull in HITL for destructive or irreversible operations and for explicit regulatory triggers. Always operate within legal authorizations and rules of engagement. This lines up with guidance from [NIST AI RMF 1.0](https://www.nist.gov/itl/ai-risk-management-framework) and [ENISA](https://www.enisa.europa.eu/publications/cybersecurity-of-ai-and-standardisation).

Three oversight modes worth naming, because people use HITL to mean all of them:

- Human-in-the-loop (HITL): a human approves actions before execution. High friction, and the right call for destructive or irreversible writes.
- Human-on-the-loop (HOTL): a human supervises a running system and can intervene mid-flight. Good for elevated-risk phases.
- Human-over-the-loop (HoTL)[^2]: humans set policy and thresholds, watch telemetry, and intervene by exception. This is the right default for reversible, well-scoped operations.

### Implementation playbook: guardrails and steps

The guardrails that keep this safe:

- Engagement policies that encode scope, rules of engagement, allowed hours, and no-touch assets. Agents request capabilities; policies decide, log, and constrain.
- Scoped credentials: short-lived, least-privilege tokens bound to intent, resources, and rate limits.
- Staged execution through dry runs, simulations, and canary resources before anything high-impact, with promotion only on passing checks.
- Attack validation that checks no-harm constraints, correct asset and tenant scope, reversibility, and policy alignment, and denies on ambiguity.
- Attack graph observability: log goals, plans, actions, evidence, and outcomes for replay and forensics.
- Continuous evaluation of exploit success, false positives, unsafe-action and policy-violation rates, time-to-detect, and time-to-revert, with a halt on regressions.
- Safety and rollback via payload sandboxes, allowlists, canary tokens, rate limits, and a global kill switch.
- Targeted human override, escalating on destructive writes, exfil outside canaries, policy exceptions, or a policy-based risk score crossing a threshold.

The rollout order I'd use:

1. Pick low-risk candidates: recon triage, evidence capture, sandboxed exploit validation, canary-scope lateral movement.
2. Start read-only or simulated: dry runs in sandboxes and canary tenants, no external writes.
3. Enforce policy-bound scopes: rules of engagement, rate limits, geofences, and no-touch lists.
4. Issue scoped, short-lived credentials tied to intent, resources, and rate limits.
5. Stage and promote: require success in sim and canary before production-adjacent scopes.
6. Instrument observability: attack graph traces, artifact logs, and per-tool safety metrics.
7. Gate destructive writes behind exception-based approval on explicit triggers, and wire a global kill switch.
8. Close the loop: feed lessons into policies, tests, and SLOs, and expand only when reliability stays green.

### Evidence: systems and frameworks

Research from 2024 and 2025 that's worth reading:

- RapidPen, an LLM-orchestrated autonomous pentest framework, reports end-to-end exploit chains in controlled targets with explicit scoping and replayable logs ([arXiv](https://arxiv.org/abs/2502.16730)).
- VulnBot uses multi-agent collaboration across recon, scanning, and exploitation, guided by a penetration task graph and policy-bounded tool use ([arXiv](https://arxiv.org/abs/2501.13411)).
- ARACNE is a service-focused autonomous agent (SSH, for example) with constrained action spaces and guardrails against out-of-scope actions ([arXiv](https://arxiv.org/abs/2502.18528)).
- AutoPentest is a black-box LLM agent applying chain-of-thought and tool orchestration with safety staging and evaluation harnesses ([arXiv](https://arxiv.org/abs/2505.10321)).

On the regulatory side, [NIST AI RMF 1.0](https://www.nist.gov/itl/ai-risk-management-framework) emphasizes transparency, traceability, documentation, measurable risk controls, continuous monitoring, and incident response across its Govern, Map, Measure, and Manage functions. [ENISA](https://www.enisa.europa.eu/publications/cybersecurity-of-ai-and-standardisation) recommends secure-by-design engineering, rigorous logging, data governance, evaluation, and alignment with emerging standards. The [EU AI Act](https://digital-strategy.ec.europa.eu/en/policies/eu-ai-act) requires human oversight, robust logging, technical documentation, and risk management proportional to system risk, which fits policy- and telemetry-driven autonomy for high-impact operations better than step gating does.

Read the systems work and the frameworks together and you get the same guardrails either way: strict scoping, staged execution starting read-only or simulated, short-lived least-privilege credentials, policy-based gating, and comprehensive audit trails.

### Challenges we're solving (and how)

Autonomy doesn't make the risk disappear, it moves where you handle it. Here's what's worked in practice.

Agents are under adversarial pressure from prompt and tool injection, data-exfil attempts, and model evasion. We handle it with tool allowlists, strong input sanitization, payload sandboxes, canary tokens, out-of-band DLP and egress monitors, and deny-by-default on ambiguity.

Automation bias and triage fatigue are real: teams over-trust automated results or stop noticing anomalies. Our answer is policy-based risk thresholds, exception-only approvals for destructive writes, periodic trace reviews, and keeping "review SLOs" separate from "execution SLOs."

Rules of engagement miss edge cases and degrade over time, so policies live as code with versioning, pre-deployment policy test suites, and drift detection wired to a kill switch.

Without telemetry, autonomy just adds uncertainty. That means full-fidelity attack graph traces, per-tool safety metrics (unsafe-action rate, policy-violation rate), anomaly detection, and one-click system-wide rollback and kill.

The last one is culture. Not every org is ready to drop step approvals on day one, and that's fine. Start read-only or simulated, publish weekly reliability and safety metrics, and expand autonomy only while the SLOs stay green.

[^1]: By “agentic AI,” I mean systems that can plan and act via tools under explicit policies and telemetry. By “HITL,” I mean step‑gated approvals for each action rather than supervising by exception.

[^2]: “Human‑over‑the‑loop” (HoTL) refers to policy‑ and telemetry‑driven oversight where humans supervise outcomes and intervene by exception rather than approving each step in advance.
