---
title: Give AI work a next action
description: A simple checkpoint pattern for resuming AI work across sessions and repos.
created: 2026-08-08
date: 2026-08-08
---

AI coding work rarely happens in one sitting anymore. A project may span a long-running tmux session, several agents, a GitHub repository, and a personal planning system. The hard part is often not doing the work. It is knowing what to do when you come back.

I kept running into the same failure mode: I would stop because it was late, the context was getting too large, or I had run out of tokens. Sometimes the work was complete for that session; sometimes it was only half-done. Later I would have to search a terminal, an old conversation, a repository, or GitHub to reconstruct where things stood. Work was not necessarily lost, but it became expensive to resume—and some of it simply disappeared from attention.

The useful distinction is three separate jobs.

## A/B/C: decide, record, surface

**A — Identify the next action.** At the end of a session, determine what should happen next. It may be a concrete action, a review step, or “needs planning” if the next move is not yet clear.

**B — Record it locally.** Put that next action and its context in one standard, findable place near the work. The record should survive the conversation that produced it.

**C — Surface it centrally.** Periodically pull those local signals into a central planning view so that the question “what can I resume?” does not require visiting every repository by hand.

These should not be collapsed into one system. The project repository is the natural home for the local next action. The planning repository is a view across projects. GitHub is a shared collaboration system when shared tracking is needed.

## The default convention: `NEXT.md`

If a project has a canonical local repository, put its current checkpoint in the repository root as `NEXT.md`:

```md
## Current checkpoint

- **Project:** Without Hot Air
- **State:** ready
- **Next:** Open the book plan, do #3, then Phase 1’s audit.
- **Context:** Stop at Phase 2 and bring back the options.
- **Updated:** 2026-08-08
```

This is intentionally not a backlog. It is the current checkpoint: the smallest useful marker for resuming the work. A repository can have several projects, but each workstream should have one current checkpoint rather than an accumulating list of old handoffs.

If there is no external repository, put the equivalent checkpoint in the relevant project or initiative file in the central planning repo. The rule chooses the location automatically; the person stopping work should not have to decide between four competing systems.

GitHub is optional. If the work already has a shared issue, `NEXT.md` can point to it. Create a new issue only when the work needs shared visibility, discussion, or team tracking. A personal session handoff is not, by itself, a reason to create an issue.

## The stopping workflow

The desired interaction is short:

> Checkpoint this.

The AI should then summarize what changed, propose the next action, identify the relevant context, and update `NEXT.md`. If the next action is genuinely unclear, it should record `needs-planning` rather than inventing a fake task.

That checkpoint supports both kinds of stopping:

- A long-running session is still active or uncertain; checkpointing makes its current state explicit.
- A session has reached a natural boundary; checkpointing prepares a clean restart in a later session.

Starting the next session should begin by reading `NEXT.md`, not by searching the old conversation. When the work moves forward, the checkpoint is replaced with the new one. The file remains small and current.

## Make the convention discoverable

The repository’s `AGENTS.md` can carry a short instruction like this:

```md
## Session checkpoints

When stopping work:

1. Summarize what changed.
2. Identify the next action, or mark `needs-planning`.
3. Update the repository root `NEXT.md` with the current checkpoint.
4. Link a GitHub issue only when shared tracking is useful.
```

This is deliberately a pointer, not a full workflow manual. A reusable `session-checkpoint` skill can teach the AI how to perform the checkpoint consistently: inspect the current work, draft a concise checkpoint, ask for correction only when needed, and write the file. The skill belongs in a shared planning/tooling location; the short `AGENTS.md` rule makes it discoverable wherever work happens.

## The central planning view

The central planner should primarily pull rather than depend on every session pushing an update. Given the planning portfolio’s links to local workspaces and GitHub repositories, a planning review can inspect:

- root `NEXT.md` files;
- explicitly linked GitHub issues;
- a small set of other agreed status signals.

It can then show a reviewable board of current checkpoints, stale signals, and items marked `needs-planning`. The central view should be generated or refreshed from those sources; it should not become a second detailed backlog. A push from the checkpoint skill may still be convenient, but the pull path is the safety net.

## Alternatives considered

| Option | Strength | Main failure |
|---|---|---|
| Central planning project file | Easy to see centrally; already exists | External AI sessions must write back here; creates push friction and duplication |
| GitHub issue | Excellent shared/team history | Too heavy for personal checkpoints; often no issue is needed |
| Dedicated handoff file in each repo | Clear and structured | New file convention; central pull has to discover many filenames |
| `NEXT.md` in each repo | Extremely discoverable to humans and AIs; easy to pull; works offline; fits existing conventions | Some repos may already use `NEXT.md` differently; needs a tiny standard format |

The practical choice is `NEXT.md` by default, with a fallback to `planning/NEXT.md` where a repository already uses the root filename for something incompatible.

The point is not to build another task manager. It is to make the next action survive the session that created it, remain visible where the work happens, and become discoverable from a central planning review.
