---
created: 2026-06-27
author: Brian Armstrong
tags: [ai-costs, llm-routing, caching, defaults, ai-gateway, productivity]
---

# AI Spend Management Through Defaults, Routing, and Caching

Brian Armstrong argues that AI usage can scale without forcing AI spend to scale at the same rate if teams optimize defaults, routing, caching, and context discipline.

![Brian Armstrong tweet](https://screenshotit.app/https://x.com/brian_armstrong/status/2070670644577280109)

## Links

- Tweet: https://x.com/brian_armstrong/status/2070670644577280109?s=20
- Author: Brian Armstrong
- Related MOC: [[moc-ai-spend-management]]

## Important Point

The core move is to replace hard usage caps and friction with better defaults, smarter model routing, warmer caches, and leaner contexts. Armstrong says that shift nearly halved AI spend while token usage kept growing.

## Breakdown

- Better defaults: make cheaper models the default path, while still letting engineers choose a different model when needed.
- Better routing: use stronger models for planning and cheaper models for execution when frontier models are overkill.
- Better caching: treat cache misses as direct cost leaks and design for reuse.
- Lean context: start fresh when switching tasks and disconnect unused tools.
- Better visibility: expose usage and spend so teams can use more AI without hiding the cost.

## Significance

This is a practical cost-control pattern for agent-heavy teams: improve the system so usage can scale without turning AI into a constrained, high-friction utility.
