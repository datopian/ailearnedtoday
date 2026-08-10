---
title: How do I run a fleet of coding agents?
description: Framing the shift from running one agent session to running a self-managing fleet — before researching how to actually do it.
date: 2026-08-10
---

I've got more work than one agent session can handle. But it's more than that: I want to stop running individual sessions altogether and instead work off a stack — a backlog of work that gets farmed out almost automatically, by an AI manager, to agents that then split it further into smaller tasks and hand those off in turn, down through a whole farm of agents. That's the loop-engineering piece: not me dispatching one task to one agent, but a manager layer doing the dispatching, splitting, and re-dispatching on its own.

That raises the same operational questions at every layer of that stack:

- How does a high-level piece of work get broken into parts — by me, or by an AI manager analysing it?
- How do those parts get built, then reviewed — by a human, or by another agent?
- How does the loop keep rolling once it's started, without me re-triggering each step?
- How do I see the status of everything in flight at once — a kanban board for agents?

Some of this is Claude, some is Codex, and I want a pattern that holds across both, not something wired to one tool. Claude Code has some way to view a fleet of running agents already, but I haven't used it, and it doesn't answer the manager-layer question — how work gets farmed out and split in the first place. Even scoped to just Claude Code: where does the manager's memory live, how does it write state to disk, how do I stay oriented across everything running.

So: **how do I move from running individual agent sessions to running a self-managing fleet — where a manager layer farms out, splits, and tracks work across tools — without losing sight of what's happening?**

A follow-up post will dig into what's actually out there to answer this — first pass is up: [Fleet of agents: a survey of orchestration tools (WIP)](/posts/2026-08-10-fleet-of-agents-survey).
