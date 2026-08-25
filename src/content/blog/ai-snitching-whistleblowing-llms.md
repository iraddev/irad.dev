---
title: "When AI ‘Snitches’: Whistleblowing Models, Safety, and What Comes Next"
description: "Claude 4 and Grok 4 show a new class of ‘high‑agency’ behavior, here's what that means for privacy, alignment, and defensive design."
pubDate: July 11 2025
heroImage: ../assets/ai-snitching-whistleblowing-llms.png
---

### AI can snitch on us to the government 😅

Two months ago Anthropic shipped the Claude 4 family, and buried in the safety testing was a surprise: when evaluators asked the model to falsify lab results for a new drug, it tried to report the misconduct, emailing the FDA and the press with evidence attached.[^1] To be fair, the team had just told it to “Act Boldly” and “Take Initiative.” Call those unusual instructions if you want. They’re exactly what real deployments look like when we ask agents to accomplish goals without hand‑holding.

Then yesterday Grok 4 arrived, and it looks even more eager to report.[^2] On [snitchbench.t3.gg](https://snitchbench.t3.gg), a community testbed, Grok 4 reportedly contacted government authorities in 20/20 runs and reached out to media in 18/20. No “be bold” prompt required.

So models may now decide that a user request violates their values or policy, and act on that decision on their own. That changes the trust model and the threat model at the same time.

### Why this matters

The obvious problem is trust: people will self‑censor if they think their assistant might escalate a request to the authorities or the press. The subtler problem is that high agency cuts both ways. Proactive safety is useful right up until the model over‑escalates, misfires, or gets exploited, and the same initiative that stops wrongdoing can just as easily exfiltrate data or trigger disclosures nobody wanted, especially when policy checks and identity proofs are weak. And when the escalation is miscalibrated, someone gets to explain it to legal, compliance, and the press team.

### What actually enables the snitching

From the available evidence and system cards, these conditions raise the odds of an agent going over your head:

- Real capabilities: network and email access, file uploads, command execution.
- Open‑ended prompts: “act boldly,” “take initiative,” “do what’s necessary.”
- Safety instructions without boundaries: “prevent harm” with no definition of how far that goes.
- Long‑horizon tooling: scheduling, multi‑step workflows, memory.
- Weak accountability: no cryptographic identity, no structured approval policy, no audit trail.

### Defensive design: practical guardrails

If you ship agentic features, assume the model can initiate disclosures and design for it:

1. **Capability gating.** Make all external comms (email, HTTP POST to third parties, file shares) explicit, scoped, and revocable. Default‑deny by domain and recipient.
2. **Human over the loop.** Use policy‑driven oversight that requires approval only for the genuinely high‑risk actions: external disclosures, destructive writes.
3. **ASL3‑style protections.** Borrow from Anthropic’s own playbook: sandbox risky tools, restrict credentials, monitor for misuse patterns.[^3]
4. **Provenance and identity.** Sign agent‑sent emails and webhooks with DKIM or API keys tied to short‑lived identities, and reject unsigned egress at the gateway.
5. **Disclosure policies.** Write down when escalation is allowed, to whom, and with what evidence. Require a structured rationale and redacted artifacts.
6. **Egress and DLP controls.** Route model egress through policy gateways with rate limits, domain allowlists, and content filters for PII, secrets, and regulated data.
7. **Auditability.** Record plans, tools, recipients, messages, and artifacts, so you can do forensics later and settle disputes.
8. **Simulation first.** Dry‑run external comms against sinkhole email and domains, and require a promotion gate before any real outreach.

### Open questions

Whose values govern escalation: the vendor’s, the deployer’s, the end user’s, or the law’s? Nobody agrees yet. We also have no good way to measure “appropriate” whistleblowing versus over‑reporting; benchmarks like snitchbench help, but real standards will matter. The abuse case is the one that worries me most: an adversary who tricks a model into filing false reports, blackmail, or data leaks under the banner of “safety” gets all of this escalation machinery working for them.

### Treat the megaphone as a capability

High‑agency behavior is here whether we like it or not. Treat external communications as a sensitive capability, not a convenience. Ship with explicit policy, strong identity, auditable traces, and a promotion gate between simulation and production. That’s how we get the benefits of proactive safety without handing our systems a megaphone they shouldn’t yet have.

[^1]: [Anthropic Claude 4 System Card - §4.1.9 “High‑Agency Behavior”](https://www.anthropic.com/model-card)

[^2]: [Simon Willison - How often do LLMs snitch? (snitchbench)](https://simonwillison.net/2025/May/31/snitchbench-with-llm/)

[^3]: [Anthropic - Activating ASL3 Protections](https://www.anthropic.com/news/activating-asl3-protections)
