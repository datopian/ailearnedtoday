---
created: 2026-07-26
author: Addy Osmani
tags: [loop-engineering, coding-agents, agent-harness, automations, skills, sub-agents, worktrees, context-engineering, claude-code, codex]
---

# Loop Engineering

Addy Osmani's essay on the emerging practice of designing systems that prompt your coding agents on a loop, rather than prompting them yourself turn-by-turn.

![Loop Engineering by Addy Osmani](https://screenshotit.app/https://addyosmani.com/blog/loop-engineering/)

## Links

- **Article**: https://addyosmani.com/blog/loop-engineering/
- **Author**: [Addy Osmani](https://addyosmani.com/)
- **Date**: 2026 (per Addy Osmani blog)
- **Related posts**: [Agent Harness Engineering](https://addyosmani.com/blog/agent-harness-engineering/), [Factory Model](https://addyosmani.com/blog/factory-model/), [Long-running agents](https://addyosmani.com/blog/long-running-agents/), [Agent Skills](https://addyosmani.com/blog/agent-skills/)

## Overview

"Loop engineering is replacing yourself as the person who prompts the agent. You design the system that does it instead." Addy Osmani argues this may be the future of working with coding agents — but it's early, he's skeptical, and you must be careful about token costs.

The idea originates from practitioners like Peter Steinberger ("You shouldn't be prompting coding agents anymore. You should be designing loops that prompt your agents.") and Boris Cherny, head of Claude Code at Anthropic ("I don't prompt Claude anymore. I have loops running that prompt Claude... My job is to write loops").

Loop engineering sits "one floor above" the agent harness: the harness is the environment a single agent runs inside, but a loop runs on a timer, spawns helpers, and feeds itself.

## The Five Pieces (plus memory)

A loop needs five primitives plus one place to remember state:

1. **Automations** — go off on a schedule and do discovery/triage by themselves.
2. **Worktrees** — so parallel agents don't step on each other.
3. **Skills** — codify project knowledge the agent would otherwise guess.
4. **Plugins/connectors** — plug the agent into the tools you already use.
5. **Sub-agents** — one has the idea, a different one checks it.

Plus **memory**: a markdown file or Linear board living outside the conversation, holding what's done and what's next. "The agent forgets, the repo doesn't."

Both Codex and Claude Code now ship all five primitives:

| Primitive | Job in the loop | Codex app | Claude Code |
| --- | --- | --- | --- |
| **Automations** | discovery + triage on a schedule | Automations tab, `/goal` for run-until-done | Scheduled tasks/cron, `/loop`, `/goal`, hooks, GitHub Actions |
| **Worktrees** | isolate parallel features | Built-in worktree per thread | `git worktree`, `--worktree`, `isolation: worktree` |
| **Skills** | codify project knowledge | Agent Skills (`SKILL.md`) | Agent Skills (`SKILL.md`) |
| **Plugins/connectors** | connect your tools | Connectors (MCP) + plugins | MCP servers + plugins |
| **Sub-agents** | ideate and verify | Subagents as TOML in `.codex/agents/` | Task subagents in `.claude/agents/` |
| **State** | track what's done | Markdown or Linear via connector | Markdown (`AGENTS.md`) or Linear via MCP |

## Heartbeat: Automations and `/goal`

- `/loop` re-runs on a cadence.
- `/goal` keeps going until a verifiable condition you wrote is true; after every turn a separate small model checks whether you're done, so the code-writing agent isn't grading itself. e.g. "all tests in test/auth pass and lint is clean."

## What a Loop Still Doesn't Do for You

Loop engineering changes the work but doesn't delete you from it. Three problems get sharper, not easier:

- **Verification is still on you** — a loop running unattended also makes mistakes unattended. "Done" is a claim, not a proof.
- **Comprehension debt** — the faster the loop ships code you didn't write, the bigger the gap between what exists and what you understand, unless you read what it made.
- **Cognitive surrender** — when the loop runs itself it's tempting to stop having an opinion. Designing the loop is the cure when done with judgement, the accelerant when done to avoid thinking.

## Key Takeaway

"Build the loop. But build it like someone who intends to stay the engineer, not just the person who presses go." Two people can build the exact same loop and get opposite results — the loop doesn't know the difference. You do. That's what makes loop design harder than prompt engineering: the leverage point moved, it didn't disappear.

## Related

- [[moc-loop-engineering]] - Map of Content for loop engineering
- [[brittany-ellich-loop-engineering]] - Brittany Ellich's 108-PRs-in-8-days case study building on this essay
- [[skill-vs-agents-vs-claude-md]]
- [[boris-cherny-claude-code-tips]]
- [[trq212-claude-5-context-engineering]]
