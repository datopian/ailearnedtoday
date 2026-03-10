---
created: 2026-03-10
original_date: 2026-03-09
author: Simon Willison
tags: [coding-agents, skills, technology-choices, llm, claude-code]
---

# Perhaps not Boring Technology after all

Simon Willison's analysis of how coding agents handle new/unfamiliar technology.

![Screenshot](https://screenshotit.app/simonwillison.net/2026/Mar/9/not-so-boring/)

## Links

- **Post**: https://simonwillison.net/2026/Mar/9/not-so-boring/
- **Date**: March 9, 2026

## Overview

Contrary to expectations, LLMs and coding agents don't push developers toward "boring technology" (widely-used, well-documented tools). Despite concerns that they would reinforce mainstream tech choices, modern coding agents work effectively with new, private, or niche tools by:

1. Consuming documentation via long context windows
2. Learning from existing codebase patterns
3. Iterating and testing their own output to fill gaps

Willison reports excellent results using brand-new tools (showboat, rodney, chartroom) by simply prompting agents to read their help documentation first.

## Key Insight on Skills

> The [Skills](https://simonwillison.net/tags/skills/) mechanism that is being rapidly embraced by most coding agent tools is super-relevant here. We are already seeing projects release official skills to help agents use them—here are examples from [Remotion](https://github.com/remotion-dev/skills), [Supabase](https://github.com/supabase/agent-skills), [Vercel](https://github.com/vercel-labs/agent-skills), and [Prisma](https://github.com/prisma/skills).

Projects are now releasing official Skills to help agents use their tools, accelerating the adoption of new technology rather than ossifying around old choices.

## Technology Bias Study

Willison references [What Claude Code Actually Chooses](https://amplifying.ai/research/claude-code-picks) by Edwin Ong and Alex Vikati, which tested Claude Code 2,000+ times and found:

- Strong bias toward build-over-buy
- "Near monopoly" preferences: GitHub Actions, Stripe, shadcn/ui in their categories
- **Note**: This addresses what agents *recommend*, not whether they can *work with* different choices

## Context

The "[Choose Boring Technology](https://boringtechnology.club)" principle suggests using proven, well-understood tools over cutting-edge ones. Willison initially expected coding agents would amplify this (favoring tools in training data), but experience shows they adapt well to any technology choice.

## Related

- [[boris-cherny-claude-code-tips]]
- [[claude-code]]
- [[react-pdf-skill]]
- [[frontend-slides]]
- [[autonomous-dogfooding-skill]]
