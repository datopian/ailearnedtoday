---
title: How do I run a fleet of coding agents?
description: I've got more work than one agent session can handle, and I want a manager layer that farms it out and tracks it cross models
date: 2026-08-10
---

![Claude Code Agent View, a dashboard for multiple concurrent agent sessions](https://screenshotit.app/https://claudefa.st/blog/guide/agents/agent-view)

I want to stop running individual agent sessions altogether. Instead: work off a stack — a backlog that gets farmed out almost automatically, by an AI manager, to agents that split it further into smaller tasks and hand those off in turn, down through a whole farm of agents.

That's the loop-engineering piece: not me dispatching one task to one agent, but a manager layer doing the dispatching, splitting, and re-dispatching on its own. But it's bigger than loop engineering alone — loop engineering usually means one task looping. I want this running across multiple projects and areas at once, not just one loop on one task.

That raises the same operational questions at every layer of that stack:

- How does a high-level piece of work get broken into parts — by me, or by an AI manager analysing it?
- How do those parts get built, then reviewed — by a human, or by another agent?
- How does the loop keep rolling once it's started, without me re-triggering each step?
- How do I see the status of everything in flight at once — a kanban board for agents?

I also don't want to be locked into one model for everything. Different tasks warrant different models — cheap, fast models for simple or high-volume work, the expensive frontier models only where they're actually needed — so the fleet needs to route tasks to whichever LLM fits, not default everything to the priciest option. Claude Code has some way to view a fleet of running agents already, but I haven't used it, and it doesn't answer the manager-layer question — how work gets farmed out, split, and routed to the right model in the first place. Even scoped to just Claude Code: where does the manager's memory live, how does it write state to disk, how do I stay oriented across everything running.

So: **how do I move from running individual agent sessions to running a self-managing fleet — where a manager layer farms out, splits, routes work to the right model for the job, and tracks it — without losing sight of what's happening?**

A follow-up post will dig into what's actually out there to answer this — first pass is up: [Fleet of agents: a survey of orchestration tools (WIP)](/posts/2026-08-10-fleet-of-agents-survey).
