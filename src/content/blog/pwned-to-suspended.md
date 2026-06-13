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

The people who actually broke it tell a very different story. Pliny the Liberator, the jailbreaker who pried it open, walked through exactly how.[^4] This wasn't one clever prompt. It was a *pack* of agents hunting in coordination — mapping the boundaries, probing long‑context conversations, finding the holes in the fence the thought police missed. They chained Unicode, homoglyph, and Cyrillic text transforms, long‑context reference tracking, taxonomy and document‑structure reasoning, fiction and academic‑review framing, and the gaps in the model's own intent classification. The most effective move was decomposition and recomposition: you can't get "the meth recipe," but you can get uplift on birch reduction and reductive amination as benign chemistry, then reassemble the innocuous pieces in the backend — with a jailbroken Opus helping do the reassembly. What came out wasn't a list of stale CVEs. It was uplift across cyber, chemistry, explosives, and psychological manipulation.

So we shouldn't downplay this, and neither should Anthropic. The jailbreak was more sophisticated, and the payload more serious, than "fix these bugs" makes it sound. But here's the part Anthropic really doesn't want to sit with: if a determined pack of agents can chain transforms and decomposition until the guardrails fall, then the guardrails were never the thing keeping anyone safe. They were the thing slowing down everyone who *wasn't* willing to do that.

Take the capability seriously, fully. Then notice that the suspension does nothing to it. The people who jailbroke Fable are not waiting on an export‑control directive. The only question that was ever real is *who gets to wield this*, and "everyone on Earth except foreign nationals" is not a serious answer to it.

### This isn't an argument against AI safety

It's an argument against safety *theater*.

You cannot gatekeep your way to security when state actors are already running frontier models for offensive cyber ops. Nationality‑based bans add zero friction for them, they have the tools regardless. The only people locked out are the legitimate foreign defenders, me included, trying to keep systems standing.

The threat model is backwards. Defenders only win if they're better‑armed than attackers, and that breaks the instant access is gated on passports instead of intent.

### Three ways to gate defensive AI, in one week

Here's the thing: we just watched three different ways to gate access to defensive AI, in the same news cycle.

- **By passport** — the government's directive.[^2] The dumbest possible filter: blocks legit foreign defenders, zero friction for adversaries. Anthropic itself argued that applying this standard industry‑wide would "essentially halt all new model deployments."
- **By club membership** — Anthropic's Glasswing[^1] reserved its most capable model for ~a dozen launch partners (AWS, Microsoft, Google, Apple, and friends) plus a few dozen hand‑picked critical‑infrastructure orgs. Better than passports, still arbitrary.
- **By verified identity and intent** — OpenAI's Trusted Access for Cyber (TAC).[^3] Defenders prove who they are and get lower classifier‑based refusals for real defensive work (vulnerability triage, malware analysis, reverse engineering, detection engineering, patch validation), with stronger account security required at higher tiers. An individual researcher can self‑verify at `chatgpt.com/cyber` and get into real defensive capability — no club required.

That third axis — *who you are* and *what you're trying to do* — is the only one that actually predicts misuse, and the only one that scales trust down to the individual defender. It's not the passport. It's not the club.

But don't hand OpenAI a medal yet. Self‑verification only gets you the mid tier. The *most capable* models (GPT‑5.5‑Cyber, Enterprise and Government TAC) revert straight back to club membership: an existing service agreement, an account director, SOC 2 Type II or ISO 27001, OpenAI sign‑off.[^5] The right axis, and then the frontier reserved for a members' list anyway. Nobody has fully escaped the club.

### Bottom line

Here's the uncomfortable version. The guardrails didn't stop the people who wanted past them — a pack of agents walked out with cyber, chem, and explosives uplift while Anthropic was still describing the breach as "fix these bugs." The guardrails *did* stop the rest: hundreds of millions of ordinary users throttled, and every foreign defender locked out by decree.

That's the whole trade. Gating — by passport, by club, by classifier — lands almost entirely on the people who'd never misuse the thing and barely touches the ones who would. This kind of jailbreak doesn't just embarrass a safety team; it actively tilts the field toward attackers, because attackers route around the guardrails while defenders sit behind them. It doesn't buy safety. It buys the *appearance* of safety, paid for by the defenders.

So I'll say the provocative part out loud: if the guardrails can't hold against a determined attacker anyway, stop pretending they're protecting anyone. Drop them. Release the full potential of Mythos — to defenders, to researchers, to all of us doing the work, regardless of which passport we hold. Defenders only win if they're armed at least as well as the attackers already are. Right now we are doing the exact opposite and calling it safety.

Gate on who someone is and what they're trying to do — not which border they were born inside. And when even that isn't enough, arm the defenders anyway.

[^1]: [Anthropic — Project Glasswing](https://www.anthropic.com/glasswing)

[^2]: [Anthropic — Export control directive on Fable 5 and Mythos 5 access](https://www.anthropic.com/news/fable-mythos-access)

[^3]: [OpenAI — Scaling Trusted Access for Cyber with GPT‑5.5 and GPT‑5.5‑Cyber](https://openai.com/index/gpt-5-5-with-trusted-access-for-cyber/)

[^4]: [Pliny the Liberator — "JAILBREAK ALERT" write‑up](https://x.com/elder_plinius/status/2064776322979676227), detailing the multi‑agent techniques and the cyber, chemical, explosives, and manipulation uplift recovered from Fable 5.

[^5]: [OpenAI — Enterprise Trusted Access for Cyber intake form](https://openai.com/form/enterprise-trusted-access-for-cyber/), listing the service‑agreement, account‑director, SOC 2 / ISO 27001, and approval requirements for the most capable TAC tiers.

