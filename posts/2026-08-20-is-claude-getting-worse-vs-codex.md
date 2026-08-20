---
title: Is Claude getting worse (at least compared to Codex)?
description: A trending question, a 100-hours-vs-20-hours comparison, and my own recent experience that Codex has been unusually solid.
date: 2026-08-20
---

["Is Claude getting worse?"](https://x.com/i/trending/2090084349542822355) is trending on X right now, always next to the same comparison: Codex.

I cannot fully judge "worse" — no baseline, no controlled test. But my own recent sessions line up with the mood: Codex has felt very solid lately. Fewer surprises, fewer moments where I have to stop and re-steer.

The most useful data point I found was a [Reddit comparison](https://www.reddit.com/r/ClaudeCode/comments/1sk7e2k/claude_code_100_hours_vs_codex_20_hours/): about 100 hours with Claude Code against 20 hours with Codex, same 80,000-line Python/TypeScript project, 2,800 tests. Their read: Claude is faster and more interactive, but needs more supervision — it can drift from `CLAUDE.md` and leave a migration half-finished. Codex is slower and more methodical, but treats `AGENTS.md` as a stable constraint and will pause to re-check its assumptions unprompted.

That is not "Claude got worse." It reads more like two different tradeoffs: a fast, chatty collaborator that needs a hand on the wheel, versus a slower one that holds its own guardrails better.

Two things I'd watch before drawing a firm conclusion:

- **Model vs. harness.** "Claude" conflates the model with Claude Code's agent loop, tool use, and context handling. A regression in the harness can look exactly like a regression in the model.
- **Survivorship in the discourse.** People post when something breaks, rarely when it quietly works. A trending complaint is a signal, not a measurement.

For now, my working move is boring: run both, on real tasks, and let the CLAUDE.md/AGENTS.md discipline point tell me something concrete — am I letting Claude drift, or is Claude drifting on me?
