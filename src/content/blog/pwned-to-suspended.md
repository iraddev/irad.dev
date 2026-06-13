---
title: 'From “PWNED” to “SUSPENDED” in 4 Easy Steps 💀'
description: "A frontier model got recalled by the US government for reading code and fixing bugs. The lesson isn't about AI safety, it's about how we gate access to defensive AI, and why passports are the dumbest filter of all."
pubDate: Jun 13 2026
heroImage: ../assets/pwned-to-suspended.png
---

### How to get a frontier model banned 😂

For months Anthropic told the world its Mythos‑class models were cyber superweapons. Project Glasswing[^1] bragged about thousands of zero‑days: a 27‑year‑old remote‑crash bug in OpenBSD ("one of the most security‑hardened operating systems"), a 16‑year‑old FFmpeg flaw that automated tooling had hit five million times without ever catching, and multiple Linux kernel exploit chains escalating from user to root. The US government heard "most capable cyber model ever built" and stopped listening after that.

So here's the speedrun:

1. **Hype it as a superweapon.** Announce thousands of autonomously‑discovered zero‑days and benchmark leaps (CyberGym 83.1% vs 66.6%, SWE‑bench Verified 93.9% vs 80.8%).
2. **Make sure the government is watching.** Mission accomplished.
3. **Let someone ask it to read a codebase and fix the flaws in it.**
4. **Get SUSPENDED.**

Today the government issued an export‑control directive[^2] suspending Fable 5 and Mythos 5 for every foreign national, inside or outside the US, including Anthropic's own employees.

The trigger? A "jailbreak." Want to know what it actually was? Asking the model to read a specific codebase and fix software flaws. That's the weapon. By Anthropic's own account, the technique surfaced a handful of minor, already‑discoverable bugs that other publicly available models find every single day, no jailbreak required.

So a model got yanked from hundreds of millions of users because it did the exact thing defenders do all day: read code, find bugs, fix them.

### This isn't an argument against AI safety

It's an argument against safety *theater*.

You cannot gatekeep your way to security when state actors are already running frontier models for offensive cyber ops. Nationality‑based bans add zero friction for them, they have the tools regardless. The only people locked out are the legitimate foreign defenders, me included, trying to keep systems standing.

The threat model is backwards. Defenders only win if they're better‑armed than attackers, and that breaks the instant access is gated on passports instead of intent.

### Three ways to gate defensive AI, in one week

Here's the thing: we just watched three different ways to gate access to defensive AI, in the same news cycle.

- **By passport** — the government's directive.[^2] The dumbest possible filter: blocks legit foreign defenders, zero friction for adversaries. Anthropic itself argued that applying this standard industry‑wide would "essentially halt all new model deployments."
- **By club membership** — Anthropic's Glasswing[^1] reserved its most capable model for ~a dozen launch partners (AWS, Microsoft, Google, Apple, and friends) plus a few dozen hand‑picked critical‑infrastructure orgs. Better than passports, still arbitrary.
- **By verified identity and intent** — OpenAI's Trusted Access for Cyber (TAC).[^3] Defenders prove who they are and get lower classifier‑based refusals for real defensive work (vulnerability triage, malware analysis, reverse engineering, detection engineering, patch validation), with stronger account security required at higher tiers. An individual researcher can self‑verify at `chatgpt.com/cyber` and get in.

Only one of these actually scales trust to the people doing the defending. It's not the passport. It's not the club.

TAC isn't perfect, identity verification has its own failure modes, and "trust us, it's authorized" is a load‑bearing assumption. But it's the only one of the three that gates on the two things that actually predict misuse: *who you are* and *what you're trying to do*.

### Bottom line

Gate on who someone is and what they're trying to do, not which border they were born inside.

A passport tells you nothing about intent. A frontier model that reads code and fixes flaws is exactly the tool defenders need, and exactly the tool attackers already have. Locking it behind nationality doesn't slow down a single adversary. It just disarms the defenders who play by the rules.

[^1]: [Anthropic — Project Glasswing](https://www.anthropic.com/glasswing)

[^2]: [Anthropic — Export control directive on Fable 5 and Mythos 5 access](https://www.anthropic.com/news/fable-mythos-access)

[^3]: [OpenAI — Scaling Trusted Access for Cyber with GPT‑5.5 and GPT‑5.5‑Cyber](https://openai.com/index/gpt-5-5-with-trusted-access-for-cyber/)
