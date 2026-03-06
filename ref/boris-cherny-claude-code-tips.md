---
created: 2026-03-06
author: Boris Cherny
tags: [claude-code, tips, best-practices, productivity, parallel-workflows, git-worktrees, planning, skills, subagents]
original_date: 2026-02-01
---

# Boris Cherny's Claude Code Tips

**Thread of tips for using Claude Code from Boris Cherny (creator of Claude Code), sourced from the Claude Code team — February 1st, 2026.**

![Boris Cherny thread](https://screenshotit.app/https://x.com/bcherny/status/2017742741636321619)

## Links

- **Thread**: https://x.com/bcherny/status/2017742741636321619
- **Posted**: February 1, 2026
- **Engagement**: 8.9M views, 103K bookmarks, 50K likes

## Opening

> "I'm Boris and I created Claude Code. I wanted to quickly share a few tips for using Claude Code, sourced directly from the Claude Code team. The way the team uses Claude is different than how I use it. Remember: there is no one right way to use Claude Code -- everyones' setup is different. You should experiment to see what works for you!"

## The Tips

### 1. Do More in Parallel

**The single biggest productivity unlock**: Spin up 3–5 git worktrees at once, each running its own Claude session in parallel.

**How the team does it**:
- Most of the Claude Code team prefers worktrees (reason @amorriscode built native support into Claude Desktop app)
- Boris personally uses multiple git checkouts
- Some name their worktrees and set up shell aliases (`za`, `zb`, `zc`) to hop between them in one keystroke
- Others have a dedicated "analysis" worktree only for reading logs and running BigQuery

**Reference**: https://code.claude.com/docs/en/common-workflows#run-parallel-claude-code-sessions-with-git-worktrees

### 2. Start Every Complex Task in Plan Mode

**Pour your energy into the plan** so Claude can 1-shot the implementation.

**Strategies from the team**:
- One person has one Claude write the plan, then spins up a second Claude to review it as a staff engineer
- When something goes sideways, switch back to plan mode and re-plan. Don't keep pushing.
- Explicitly tell Claude to enter plan mode for verification steps, not just for the build

### 3. Invest in Your CLAUDE.md

**After every correction**: "Update your CLAUDE.md so you don't make that mistake again."

**Key insights**:
- Claude is eerily good at writing rules for itself
- Ruthlessly edit your CLAUDE.md over time
- Keep iterating until Claude's mistake rate measurably drops

**Advanced strategy**: One engineer tells Claude to maintain a notes directory for every task/project, updated after every PR. They then point CLAUDE.md at it.

### 4. Create Your Own Skills and Commit Them to Git

Reuse across every project.

**Tips from the team**:
- If you do something more than once a day, turn it into a skill or command
- Build a `/techdebt` slash command and run it at end of every session to find and kill duplicated code
- Set up a slash command that syncs 7 days of Slack, GDrive, Asana, and GitHub into one context dump
- Build analytics-engineer-style agents that write dbt models, review code, and test changes in dev

**Reference**: https://code.claude.com (skills documentation)

### 5. Claude Fixes Most Bugs by Itself

**How the team does it**:

- **Enable the Slack MCP**: Paste a Slack bug thread into Claude and just say "fix." Zero context switching required.
- **CI failures**: Just say "Go fix the failing CI tests." Don't micromanage how.
- **Distributed systems**: Point Claude at docker logs to troubleshoot — it's surprisingly capable at this.

### 6. Level Up Your Prompting

**a. Challenge Claude**

Say "Grill me on these changes and don't make a PR until I pass your test." Make Claude be your reviewer.

Or, say "Prove to me this works" and have Claude diff behavior between main and your feature branch

**b. After a mediocre fix, say:**

"Knowing everything you know now, scrap this and implement the elegant solution"

**c. Write detailed specs and reduce ambiguity before handing work off**

The more specific you are, the better the output

**d. Route permission requests to Opus 4.5 via a hook**

Let it scan for attacks and auto-approve the safe ones (see https://code.claude.com/docs/en/hooks#permissionrequest)

### 7. Terminal & Environment Setup

**Terminal**: The team loves Ghostty!
- Synchronized rendering
- 24-bit color
- Proper unicode support

**Claude-juggling**:
- Use `/statusline` to customize your status bar to always show context usage and current git branch
- Color-code and name your terminal tabs
- Some use tmux — one tab per task/worktree

**Voice dictation**: You speak 3x faster than you type, and your prompts get way more detailed as a result. (Hit fn x2 on macOS)

**Reference**: https://code.claude.com/docs/en/terminal-config

### 8. Use Subagents

**a.** Append "use subagents" to any request where you want Claude to throw more compute at the problem

**b.** Offload individual tasks to subagents to keep your main agent's context window clean and focused

### 9. Use Claude for Data & Analytics

Ask Claude Code to use the "bq" CLI to pull and analyze metrics on the fly. We have a BigQuery skill checked into the codebase, and everyone on the team uses it for anlytics queries directly in Claude Code.

Personally, I haven't written a line of SQL in 6+ months.

This works for any database that has a CLI, MCP, or API.

### 10. Learning with Claude

A few tips from the team to use Claude Code for learning:

**a.** Enable the "Explanatory" or "Learning" output style in /config to have Claude explain the *why* behind its changes

**b.** Have Claude generate a visual HTML presentation explaining unfamiliar code. It makes surprisingly good slides!

**c.** Ask Claude to draw ASCII diagrams of new protocols and codebases to help you understand them

**d.** Build a spaced-repetition learning skill: you explain your understanding, Claude asks follow-ups to fill gaps, stores the result

## Key Principles

From the 10 tips, several principles emerge:

1. **Parallelism is power** - The #1 productivity unlock
2. **Planning beats iteration** - Invest in the plan, get 1-shot implementations
3. **Self-improvement through CLAUDE.md** - Let Claude write rules for itself
4. **Automation through skills** - If you do it twice, make it a skill
5. **High-level direction** - "Go fix the failing CI tests" not step-by-step
6. **Challenge and verification** - Make Claude prove it works
7. **Voice > typing** - 3x faster, more detailed prompts
8. **Subagents for scale** - Offload and keep main context clean
9. **Data & analytics** - Haven't written SQL in 6+ months (use CLI/MCP/API)
10. **Learning modes** - Explanatory output style, HTML presentations, ASCII diagrams, spaced-repetition

## Context

- **Author**: Boris Cherny, creator of Claude Code
- **Source**: Claude Code team's actual practices
- **Emphasis**: "No one right way" — experiment to find what works for you
- **Engagement**: Massive (8.9M views, 103K bookmarks) — clearly resonated with community

## Related

- [[karpathy-december-coding-agents-breakthrough]] - The capabilities enabling these workflows
- [[artem-grep-is-dead]] - Memory/context management for Claude Code
- [[agent-psychosis]] - The importance of structure and discipline
- Claude Code documentation
- Git worktrees workflows
