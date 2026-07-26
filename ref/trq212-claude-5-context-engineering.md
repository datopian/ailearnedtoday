---
created: 2026-07-26
author: Thariq (@trq212)
tags: [context-engineering, claude-code, claude-5, system-prompt, skills, claude-md, agents, anthropic]
---

# Thariq: New Rules of Context Engineering for Claude 5

Thariq (@trq212) shares Anthropic's lessons from cutting ~80% of Claude Code's system prompt for the newest models — and what it means for writing system prompts, skills, and CLAUDE.md files.

![Thariq tweet on context engineering for Claude 5](https://screenshotit.app/https://x.com/trq212/status/2080710971228918066)

## Links

- **Tweet**: https://x.com/trq212/status/2080710971228918066
- **Date**: July 24, 2026
- **Author**: [@trq212](https://x.com/trq212)
- **Blog post**: https://www.claude.com/blog/the-new-rules-of-context-engineering-for-claude-5-generation-models

## Overview

Thariq highlights Anthropic's Claude blog post "The new rules of context engineering for Claude 5 generation models." The headline finding: the team removed over 80% of Claude Code's system prompt for newer models like Claude Opus 5 and Claude Fable 5 with no measurable loss on coding evaluations. The post argues that much of the old guardrail-style context engineering has become counterproductive as model judgement has improved.

## Key Lessons

**Unhobbling Claude** — Claude Code was overconstrained by the system prompt, CLAUDE.md files, and skills. Internal transcripts showed conflicting messages (e.g. "leave documentation as appropriate" vs. "DO NOT add comments") that made the model spend extra effort resolving overlaps. Many old constraints can simply be deleted and replaced with surrounding context and judgement.

**Myths that became anti-patterns:**

- **Then: Give Claude rules → Now: Let Claude use judgement.** Older models needed strong guardrails (e.g. "default to writing no comments"). Newer models can match the surrounding code's comment density and idiom without explicit rules.
- **Then: Give Claude examples → Now: Design interfaces.** Examples constrain exploration to a fixed space; instead, design expressive tools/scripts/parameters. (Example: the Todo tool's status enum hints at usage.)
- **Then: Put it all upfront → Now: Use progressive disclosure.** Load context on demand rather than front-loading everything.

**Tooling** — Anthropic packaged these best practices into `claude doctor` (`/doctor` command in Claude Code) to rightsize your skills and CLAUDE.md files.

## Related

- [[skill-vs-agents-vs-claude-md]]
- [[boris-cherny-claude-code-tips]]
- [[claude-code]]
