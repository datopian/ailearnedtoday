---
created: 2026-08-20
author: Shannon Holmberg (@shannholmberg)
tags: [claude-code, skills, skill-library, company-brain, agent-skills, team-workflow, auto-pull, git]
---

# Company Skills Library — Building and Maintaining a Team-Wide Agent Skills Repository

> A shared repository where everyone writes down their whole team's complete workflow — and everyone gets the update. The key insight: downloading skills through a UI every time there's an update kills workflow; instead, set up auto-scan or hook agents to always pull the latest version.

![Company Skills Library — X thread by Shannon Holmberg](https://screenshotit.app/https://x.com/shannholmberg/status/2092137771846844642)

## What the pattern is

Shannon Holmberg (@shannholmberg) posted a thread on X laying out how to create and maintain a company-wide skills library. The core idea: instead of treating skills as something each person downloads individually from a UI (which leads to version drift and nobody knowing about improvements), treat a GitHub repo as the source of truth ("the Brain") and auto-pull the latest versions into every agent session.

## The workflow

**Bad path:**
- Each person downloads skills through a UI every time
- Versions drift per person
- Nobody knows about improvements
- Skills rot

**Good path:**

```
BRAIN → AUTO-PULL → USE + LOG → PATCH → BRAIN
```

1. **BRAIN** — a GitHub repo as the single source of truth for all team skills
2. **AUTO-PULL** — at session start, the agent pulls the latest version of the company-brain skills
3. **USE + LOG** — agents work on the real task, logging what worked and what failed
4. **PATCH** — when someone improves a skill (observed mistake → noticed → patched), they push to the company-brain
5. **BRAIN** — everybody gets the improvement on the next agent interaction

## The improvement loop

The thread describes a tight feedback loop:

- **Observe** — someone makes a mistake
- **Notice** — pull the skill, edit it
- **Patch** — push to company-brain

And the cultural layer:

- **Git / agent-friendly** — use tools that work well with this pattern
- **Use other people's skills** — don't rebuild what exists
- **Share what you learn** — feed the loop
- **Robot agents** — automate the scanning and pulling

## Why it matters

This is the team/organizational version of what individual developers are already doing with Claude Code skills (`.claude/skills/`), OpenClaw skills, and similar. The Anthropic guide [[anthropic-skills-guide]] covers how to build skills; this thread covers how to **operate them at team scale** — the governance, distribution, and improvement mechanics that make a skills library actually useful rather than a folder that 10% of the company knows how to use.

The insight echoes what [[loop-engineering]] argues: design loops (automations, worktrees, skills, connectors, sub-agents + memory) rather than prompting agents turn-by-turn. A skills library with an auto-pull + patch loop is a designed loop.

## Related

- [[anthropic-skills-guide]] — the 32-page Anthropic guide on building, testing, and distributing Claude skills
- [[skills-managers]] — skills managers and marketplaces
- [[openskills]] — open skills collections
- [[loop-engineering]] — designing loops for agents rather than prompting turn-by-turn
- [[autonomous-dogfooding-skill]] — autonomous testing skill as an example of a skill that runs itself

## Source

Shannon Holmberg (@shannholmberg) — X thread on company-wide skills libraries, August 2026.
