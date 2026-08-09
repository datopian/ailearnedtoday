---
created: 2026-06-05
author: Anthropic
tags: [ai-progress, recursive-self-improvement, coding, productivity, mythos, anthropic-internal]
---

# Recursive Self-Improvement (Anthropic Institute)

> Anthropic's AI is now meaningfully accelerating Anthropic's own AI development — a first empirical signal of recursive self-improvement in practice.

![Code contributed per person, by quarter](/assets/anthropic-recursive-self-improvement-code-per-person.png)

![Anthropic Recursive Self-Improvement](https://screenshotit.app/https://www.anthropic.com/institute/recursive-self-improvement)

## Links

- **Article**: https://www.anthropic.com/institute/recursive-self-improvement
- **Publisher**: Anthropic Institute
- **Date**: June 2026

## Summary

Anthropic tracked code contributed per engineer per quarter from Q2 2021 through Q2 2026 (partial). The chart shows output was flat at ~1× the pre-2025 average through end of 2024, then accelerated sharply:

| Period | Multiplier vs pre-2025 avg |
|--------|---------------------------|
| Q1 2025 | 1.2× |
| Q2 2025 | 1.5× |
| Q3 2025 | 1.9× |
| Q4 2025 | 2.5× |
| Q1 2026 | 5.8× |
| Q2 2026 (partial) | 8.0× |

Inflection points correlate with Claude Code release, Claude Sonnet 4.5, Claude Opus 4.5, and Claude Mythos Preview (internal access).

Key framing: this is **recursive self-improvement** — AI helping build better AI, measured not theoretically but in actual merged code per engineer.

## Excerpts

### From 3x to 52x speed up in improving AI models

![Excerpt: Claude gone from super helpful to superhuman in under a year](/assets/anthropic-recursive-self-improvement-excerpt-claude-superhuman.png)

> **Claude is good at running experiments to hit a goal that someone else has set.** Every time Anthropic releases a model, we run the same test: we give Claude some code that trains a small AI model, and ask it to make that code run as fast as possible while still passing the same correctness checks. [...] In May 2025, Claude Opus 4 averaged a ~3x speedup over the starting code. By April 2026, Claude Mythos Preview was achieving ~52x. For calibration, a skilled human researcher would need four to eight hours to reach 4x. In this part of the research workflow—optimizing steps within a clearly defined experiment—Claude has gone from super helpful to superhuman in under a year.

### We need to slowdown and that requires solving a collective action problem

Want a slowdown

> If it were possible to effectively slow the development of this technology to give ourselves more time to deal with its immense implications, we think that would likely be a good thing. ... We believe it would be good for the world to have the option to slow or temporarily pause frontier AI development to enable societal structures and alignment research to keep up with the advance of the technology.

But face a collective action problem

> But if a slowdown simply lets the least cautious actors catch up technologically, it could leave everyone less safe. Without a global coordination mechanism, companies and governments will have to make difficult decisions about safety while under competitive and geopolitical pressures.

Particularly bad as multi-country and multi-actor on short timescales with clear geopolitical tensions and hard to monitor

> A meaningful slowdown or pause would require multiple well-resourced labs at or near the frontier, in multiple countries, agreeing to stop under the same conditions. It would also require that each can verify that the others have actually stopped. Due to the unique characteristics of AI systems, the detectability (a lower standard than verifiability) element of this arms control problem is much more challenging than with other technologies

But not impossible

> None of this is necessarily impossible in principle

But they are pessimistic

> None of this is necessarily impossible in principle—the world has built verification regimes for other complex technologies (e.g., the Intermediate-Range Nuclear Forces Treaty)—but those regimes took decades to build both the infrastructure and the trust. We don’t have that long. A unilateral pause by one lab, by contrast, is achievable immediately, but accomplishes much less: it would change who the front-runner is, but it would not create the wider deliberative process that is currently missing.

Full excerpt

> #### What should we do?
>
> **If it were possible to effectively slow the development of this technology to give ourselves more time to deal with its immense implications, we think that would likely be a good thing.** But if a slowdown simply lets the least cautious actors catch up technologically, it could leave everyone less safe. Without a global coordination mechanism, companies and governments will have to make difficult decisions about safety while under competitive and geopolitical pressures.
>
> We believe it would be good for the world to have the option to slow or temporarily pause frontier AI development to enable societal structures and alignment research to keep up with the advance of the technology. The Anthropic Institute will conduct research—in collaboration with many others—and take actions to help build the systems that a credible slowdown or pause would require. These systems would enable frontier AI developers to verify that others globally have actually stopped or slowed, and that a bad actor could not use the auspices of a coordinated slowdown to jump ahead in secret. If such systems existed, we expect that we would slow down or temporarily pause, if other developers at or near the frontier also did so in a verifiable manner.
>
> A meaningful slowdown or pause would require multiple well-resourced labs at or near the frontier, in multiple countries, agreeing to stop under the same conditions. It would also require that each can verify that the others have actually stopped. Due to the unique characteristics of AI systems, the detectability (a lower standard than verifiability) element of this arms control problem is much more challenging than with other technologies. Training runs are far easier to conceal than missile silos, their inputs are general-purpose, and the incentive to defect quietly is enormous, because whoever continues while others pause could inherit the lead. A credible pause also has to specify what triggers it, what lifts it, and who adjudicates.
>
> None of this is necessarily impossible in principle—the world has built verification regimes for other complex technologies (e.g., the Intermediate-Range Nuclear Forces Treaty)—but those regimes took decades to build both the infrastructure and the trust. We don’t have that long. A unilateral pause by one lab, by contrast, is achievable immediately, but accomplishes much less: it would change who the front-runner is, but it would not create the wider deliberative process that is currently missing.

## Significance

- First published internal data showing the feedback loop closing: AI tools → faster AI development → better AI tools
- 8× productivity multiplier in partial Q2 2026 is a striking number even accounting for partial-quarter effects
- Dashed release markers make the causal story explicit: each major model release correlates with a step up

## Related

- [[anthropic-glasswing]]
- [[openai-unit-distance-problem]]
