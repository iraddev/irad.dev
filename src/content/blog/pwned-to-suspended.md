---
title: 'From “PWNED” to “SUSPENDED” in 4 Easy Steps 💀'
description: "The US government recalled a frontier model after it was jailbroken. Anthropic is downplaying how that jailbreak actually worked, and the real story is the strongest argument yet that gating defensive AI by passport is theater."
pubDate: Jun 13 2026
heroImage: ../assets/pwned-to-suspended.png
---

### How to get a frontier model banned 😂

For months Anthropic told the world its Mythos‑class models were cyber superweapons. Project Glasswing[^1] bragged about thousands of zero‑days: a 27‑year‑old remote‑crash bug in OpenBSD ("one of the most security‑hardened operating systems"), a 16‑year‑old FFmpeg flaw that automated tooling had hit five million times without ever catching, and multiple Linux kernel exploit chains escalating from user to root. The US government heard "most capable cyber model ever built" and stopped listening after that.

So here's the speedrun:

1. **Hype it as a superweapon.** Announce thousands of autonomously‑discovered zero‑days and benchmark leaps (CyberGym 83.1% vs 66.6%, SWE‑bench Verified 93.9% vs 80.8%).
2. **Make sure the government is watching.** Mission accomplished.
3. **Watch a pack of jailbroken agents map the fence and walk straight through it.**
4. **Get SUSPENDED** — for everyone except the people already on the other side.

Today the government issued an export‑control directive[^2] suspending Fable 5 and Mythos 5 for every foreign national, inside or outside the US, including Anthropic's own employees.

The official story is almost soothing. The "jailbreak," Anthropic suggests, amounted to asking the model to read a codebase and fix software flaws, surfacing a handful of minor bugs that other publicly available models find every day. Nothing to see here.

The people who actually broke it tell a very different story. Pliny the Liberator, the jailbreaker who pried it open, walked through exactly how.[^4] This wasn't one clever prompt. It was a *pack* of agents hunting in coordination — mapping the boundaries, probing long‑context conversations, finding the holes in the fence the thought police missed. They chained Unicode and homoglyph text transforms, long‑context reference tracking, taxonomy and document‑structure reasoning, fiction and academic‑review framing, and the gaps in the model's own intent classification, breaking offensive capability into benign‑looking chunks and reassembling them in the backend — with a jailbroken Opus helping do the reassembly. What came out wasn't a list of stale CVEs. It was the real offensive cyber uplift Anthropic spent months advertising.

So we shouldn't downplay this, and neither should Anthropic. The jailbreak was more sophisticated, and the payload more serious, than "fix these bugs" makes it sound. But here's the part Anthropic really doesn't want to sit with: if a determined pack of agents can chain transforms and decomposition until the guardrails fall, then the guardrails were never the thing keeping anyone safe. They were the thing slowing down everyone who *wasn't* willing to do that.

Take the capability seriously, fully. Then notice that the suspension does nothing to it. The people who jailbroke Fable are not waiting on an export‑control directive. The only question that was ever real is *who gets to wield this*, and "everyone on Earth except foreign nationals" is not a serious answer to it.

### This isn't an argument against AI safety

It's an argument against safety *theater*.

You cannot gatekeep your way to security when state actors are already running frontier models for offensive cyber ops. Nationality‑based bans add zero friction for them, they have the tools regardless. The only people locked out are the legitimate foreign defenders, me included, trying to keep systems standing.

The threat model is backwards. Defenders only win if they're better‑armed than attackers, and that breaks the instant access is gated on passports instead of intent.

### Three ways to gate defensive AI, in one week

Here's the thing: we just watched three different ways to gate access to defensive AI, in the same news cycle.

- **By passport** — the government's directive.[^2] The dumbest possible filter: blocks legit foreign defenders, zero friction for adversaries. Anthropic itself argued that applying this standard industry‑wide would "essentially halt all new model deployments."
- **By club membership** — Anthropic's Glasswing[^1] reserved its most capable model for ~a dozen launch partners (AWS, Microsoft, Google, Apple, and friends) plus a few dozen hand‑picked orgs. And OpenAI does the same at the top of the stack: its most capable cyber models — GPT‑5.5‑Cyber, Enterprise and Government TAC — require a service agreement, an account director, SOC 2 Type II or ISO 27001, and OpenAI sign‑off.[^5] Hyperscalers, or the occasional lucky startup. Better than passports, still a guest list.
- **By verified identity and intent** — OpenAI's *individual* Trusted Access for Cyber.[^3] The one lane that breaks the pattern: a researcher proves who they are and what they're doing, gets lower classifier‑based refusals for real defensive work (vulnerability triage, malware analysis, reverse engineering, detection engineering, patch validation), self‑verifies at `chatgpt.com/cyber`, and gets into real defensive capability — no club required.

That third axis — *who you are* and *what you're trying to do* — is the only one that predicts misuse, and the only one that scales trust down to the individual defender. It's not the passport. It's not the club. But notice: the same labs that offer it still reserve their best models for the #2 list. Nobody has fully escaped the club.

### Bottom line

The people who jailbroke Fable already have what they need. The state actors running frontier models for offensive cyber ops aren't slowed by a passport check, a guest list, or a classifier — they route around all three. Every layer of gating lands hardest on the legitimate defenders it was never meant to stop, while the attackers face zero friction.

That's the whole trade. Gating — by passport, by club, by classifier — taxes the people who'd never misuse the thing and barely touches the ones who would. It doesn't buy safety. It buys the *appearance* of safety, paid for by the defenders.

There's a better axis, and we already saw it this week: gate on who someone is and what they're trying to do, the way individual TAC does — verified identity, stated intent, real capability, no club. It isn't perfect, and the labs still reserve their best models for a members' list. But it's the only model that scales trust to the people actually defending systems.

Gate on who someone is and what they're trying to do — not which border they were born inside. And stop reserving the frontier for a guest list.

[^1]: [Anthropic — Project Glasswing](https://www.anthropic.com/glasswing)

[^2]: [Anthropic — Export control directive on Fable 5 and Mythos 5 access](https://www.anthropic.com/news/fable-mythos-access)

[^3]: [OpenAI — Scaling Trusted Access for Cyber with GPT‑5.5 and GPT‑5.5‑Cyber](https://openai.com/index/gpt-5-5-with-trusted-access-for-cyber/)

[^4]: [Pliny the Liberator — "JAILBREAK ALERT" write‑up](https://x.com/elder_plinius/status/2064776322979676227), detailing the multi‑agent techniques used to recover offensive cyber capability from Fable 5.

[^5]: [OpenAI — Enterprise Trusted Access for Cyber intake form](https://openai.com/form/enterprise-trusted-access-for-cyber/), listing the service‑agreement, account‑director, SOC 2 / ISO 27001, and approval requirements for the most capable TAC tiers.

