---
created: 2026-07-26
author: Brittany Ellich
tags: [loop-engineering, coding-agents, claude-code, worktrees, agent-loop, productivity, prs, offprint]
---

# Brittany Ellich: 108 PRs in Eight Days (Accidentally Discovering Loop Engineering)

Brittany Ellich's hands-on account of running an agent-driven loop over her task board — 108 PRs in ~8 days vs. her previous 5-10/week — and the three-layer design she settled on.

![Brittany Ellich: 108 PRs in Eight Days](https://screenshotit.app/https://brittany-ellich.offprint.app/a/3mrjj34puva23-108-prs-in-eight-days-accidentally-discovering-loop-engineering)

## Links

- **Article**: https://brittany-ellich.offprint.app/a/3mrjj34puva23-108-prs-in-eight-days-accidentally-discovering-loop-engineering
- **Author**: [Brittany Ellich](https://brittany-ellich.offprint.app/)
- **Date**: 2026
- **Open-source setup**: https://github.com/brittanyellich/loop-board
- **Builds on**: [[loop-engineering]] (Addy Osmani)

## Overview

Brittany Ellich ran an agent against her task board for about a week: it picks up a task, writes code in an isolated worktree, opens a PR, gets CI green, responds to review feedback, and parks the result for her to test — then sleeps and repeats. The result: 108 tasks processed in ~8 days, up from a previous average of 5-10 PRs per week. She later learned this practice had a name — loop engineering, coined by [[loop-engineering|Addy Osmani]].

She stresses the team context matters: a small, high-trust 2-3 person team that talks daily, with no mandatory second-human review gate. She didn't remove human review — she moved it from line-by-line in a PR to the testing-and-outcome level. She also dropped continuous deployment in favor of CI + a preview/stage environment, releasing batches (~2 production changes/day) to shrink the regression surface.

## Three Layers to Loop Engineering

The system has a **protocol**, a **loop**, and a **worker**:

- **Protocol** — a markdown file of rules: what each status means, what happens in what order on each pass, what gets merged. Lives next to the board (not in the repo) so editing rules and editing the board are the same act.
- **Loop** — reads the board, runs `gh`, updates task frontmatter, dispatches work. Writes no code and never touches the repo working tree. It's the only writer to the board and memory file (avoids collisions from concurrent agents).
- **Worker** — writes code in its own isolated worktree and reports back with a small structured block. Never touches the board, never talks to her directly.

## Key Design Decisions

- **Board = a folder of markdown task files** (one note per task), queried via Obsidian Bases. A single markdown table caused collisions between her edits and the board's self-updates; per-task files fix it structurally.
- **Main checkout stays hers** — every task runs in a subagent with worktree isolation branched from the repo's default branch, so local half-finished state never leaks into a task.
- **The loop must be able to stop** — bare Claude Code `/loop` (no interval) is self-paced and can end itself when the board can't move without her. Explicit stop condition: nothing in progress, nothing waiting on CI, nothing merge-ready, and every remaining task waiting on her or finished.
- **Memory with a hard cap** — a memory file of codebase facts, repeated preferences, recurring defects, each with a confirmation count and date. Once a bug hits a confirmation threshold, fixing it becomes its own task. The hard cap forces tradeoffs to keep context small.

## The Bottleneck Moved

Her board ends up with zero queued tasks and several waiting on her to test — the human shifted from reviewing code to reviewing **specs and issue definitions** (both ends of the pipeline became spec work). She's iterating on automating task creation (a skill to explore issues and queue them) and the testing/verification stage.

## Related

- [[moc-loop-engineering]] - Map of Content for loop engineering
- [[loop-engineering]]
- [[boris-cherny-claude-code-tips]]
