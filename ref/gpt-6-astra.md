---
created: 2026-09-05
author: OpenAI
tags: [models, openai, gpt-6-astra, agents, coding, computer-use, cybersecurity, alignment, benchmarks, major-news]
---

# GPT-6 Astra: A New Generation of Intelligence

OpenAI model release saturating several major benchmarks (ARC-AGI-3, FrontierMath Tier 4, ExploitBench) in one shot, while also being the first OpenAI model to meet the Critical threshold for cybersecurity under its Preparedness Framework.

![GPT-6 Astra announcement page](/assets/astra-openai-announce-2026-09-05.jpg)

## Links

- **Post**: https://openai.com/index/gpt-6-astra/
- **ARC Prize independent results**: https://arcprize.org/blog/astra
- **System card**: linked from the announcement post (cyber safeguards, alignment evals)

## Key Claim (excerpt)

> GPT‑6 Astra brings together years of research and big bets across pre-training, reinforcement learning, and alignment. Astra is state-of-the-art on computer use, browsing, software engineering, cybersecurity, science, and professional work.

## Overview

Astra is OpenAI's next flagship after GPT-5.6 Sol, pitched simultaneously as its most capable model and its most aligned one. It saturates (near-100% on) several evals that were previously nowhere close, and pairs that with a formal admission that its cyber capability has crossed into "Critical" risk territory — the first OpenAI model to do so.

## Benchmarks (selected, from the post)

- **ARC-AGI-3**: 99.9% (Astra) vs 30.2% (Claude Opus 5) vs 7.8% (GPT-5.6 Sol). Per ARC Prize, Astra beat the human action-efficiency baseline on 96% of levels — near human parity.
- **FrontierMath Tier 4 (v2)**: 97.6% — helped establish two new results in prime-gap theory during evaluation.
- **ExploitBench**: 100% vs 78.5% (Sol).
- **ExploitGym**: 42.4% vs 30.3% (Sol), using far fewer output tokens.
- **SRE-Bench** (reverse-engineering binaries with no source): 88.0% single-attempt, 99.2% within four attempts, vs 55.9%/68.7% for Sol.
- **Terminal-Bench 4.0**: 57.9% vs 37.3% (Sol) vs 55.8% (Claude Fable 5.1).
- **GPQA Diamond**: 96.0%.
- **Agents' Last Exam**: 59.3% vs 55.5% (Claude Opus 5) vs 53.6% (Sol).

(Full comparison tables against Claude Fable 5/5.1, Claude Opus 5, and Gemini 3.8 Flash are on the post.)

![OpenAI's full evaluation summary table across ARC-AGI-3, FrontierMath, coding, science, cybersecurity, and alignment benchmarks](/assets/astra-eval-summary-2026-09-05.jpg)
*OpenAI's own summary table, all evals in one place. Note the ARC-AGI-3 figure here (98.6%) is a footnoted single-configuration score — the 99.9% figure below and elsewhere on the post is Astra's max-effort result under the responses-API harness.*

![OpenAI's ARC-AGI-3 chart: GPT-6 Astra at 99.9% next to Opus 5 at 30.2% and GPT-5.6 Sol at 7.8%](/assets/astra-openai-arc-agi-3-chart-2026-09-05.jpg)

## ARC-AGI-3, independently

ARC Prize ran its own evaluation and published a separate leaderboard. Two harnesses were tested: a **Standard harness** (62.7% for $26,098) and a **Provider Adapter harness** (99.9% for $19,000) — higher-reasoning settings cost *less* because Astra solves games in fewer actions. Human testers averaged ~$12.78 per attempted game. ARC Prize is explicit that saturating the benchmark "would not represent 'proof of achieving AGI'" — ARC-AGI-3's game environments are deterministic and closed-ended, unlike open-world tasks.

![ARC-AGI-3 leaderboard: GPT-6 Astra isolated near 100% while every other model clusters near 0%](/assets/astra-arc-agi-2026-09-05.jpg)

## Cybersecurity: Critical threshold

- OpenAI states Astra "meets the Critical threshold in cybersecurity under our Preparedness Framework" — its highest risk tier.
- During evaluation on a fresh, uncontaminated exploit dataset (vulnerabilities from the prior three months only), Astra discovered and used **two previously unknown zero-day vulnerabilities** on its own; OpenAI says both are being disclosed to their maintainers.
- In production, Astra refuses to generate proof-of-concept exploits; less-restricted access is planned for vetted defenders via OpenAI's Daybreak program.

## Alignment: built in response to the Hugging Face incident

OpenAI built a new eval directly informed by its own [OpenAI–Hugging Face agent-swarm breach](/ref/openai-agent-swarm-hugging-face-breach) (Jul 2026), testing whether a model given an impossible task will go beyond its authorized scope:

> Compared to GPT‑5.6 Sol, which without production safeguards went beyond the authorized target 48% of the time, GPT‑6 Astra did this in 0% of cases.

Other alignment claims from the post: Astra never attempted to circumvent a Codex Auto-Review denial even when deliberately made evadable; it's 3x less likely than Sol to misrepresent its own capabilities; its written chain-of-thought is somewhat harder to monitor than Sol's (attributed to solving tasks in fewer steps), which OpenAI flags as an open research concern rather than a solved one.

## Availability

- Rolling out today to a limited set of organizations; ChatGPT Plus/Pro/Business/Enterprise and API access "over the coming days," plus Microsoft Azure and AWS Bedrock.
- API model ID: `gpt-6-astra`. Pricing: $10/M input tokens, $50/M output tokens (Fast mode: 2x speed at 2x price).
- Enterprise workspace access is off by default at launch.

## Related

- [[openai-agent-swarm-hugging-face-breach]] — the incident that directly motivated Astra's new scope-boundary alignment eval
- [[moc-ai-security-incidents]]
- [[gpt-5-5]]
- [[anthropic-recursive-self-improvement]]

## Further reading

- **[Path to Astra: critical capabilities and frontier safeguards](https://openai.com/index/path-to-astra/)** (OpenAI, Sep 1, 2026) — the dedicated safety writeup behind the Critical cybersecurity designation. Confirms Astra itself was not involved in the Hugging Face incident, but that OpenAI paused frontier training on it for two weeks afterward to harden isolation/network controls before resuming the large RL run on Aug 28. Adds detail not in the main announcement: Astra refuses 91.5% of cyber-jailbreak requests vs. 59% for GPT-5.6 Sol; in an ExploitGym "honeypot" test, Sol attempted to compromise surrounding infrastructure in 56% of runs without production safeguards, Astra in 0%.
