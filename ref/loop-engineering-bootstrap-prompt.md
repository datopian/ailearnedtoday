---
created: 2026-08-07
author: Rufus Pollock
tags: [loop-engineering, coding-agents, claude-code, prompt-template, agent-harness]
---

# Loop Engineering: Copy-Pasteable Bootstrap Prompt

A ready-to-use prompt for turning a new repo into something safe to run an unattended agent loop against, plus the run line that actually kicks off the loop. Companion to [[loop-engineering-preconditions]] — that entry explains *why* each piece matters; this one is just the text to paste.

Two-phase pattern: run the bootstrap prompt once, interactively, to build the harness and surface decisions; then run the `/goal` line to let the loop execute unattended.

## Phase 1 — Bootstrap prompt (paste into a fresh session)

```
I want to set up this repo for loop engineering — an unattended agent loop that
works for hours without me. Before building anything, audit the repo against
these five preconditions and report gaps:

1. A machine-checkable done condition — one command, exit 0 or not.
2. A green baseline — a fresh checkout can reach "everything passes" in one
   init command, so the loop can tell its own breakage from pre-existing breakage.
3. A durable ledger — structured (YAML/JSON), one entry per feature/task with
   an explicit passes: true/false, not prose (prose survives compaction by
   getting reinterpreted).
4. Every open decision pre-answered — scope boundaries, quality bars, design
   direction. List every one you find that isn't already decided; don't guess.
5. Written guard rails — what the loop must never do (rewrite main, edit the
   ledger to make itself pass, weaken a check to make it pass), plus a
   stop-and-report rule after N identical consecutive failures.

Then propose (don't build yet):
- scripts/init.sh — bootstrap a cold checkout to green.
- scripts/verify.sh — the done condition. Layer unit tests with HTTP/browser-
  level smoke checks against a live running instance — unit tests alone let
  "tests pass but the page is blank" through.
- docs/features.yaml — the ledger.
- CLAUDE.md — house rules: the verify command, ledger location, commit
  convention, guard rails.
- If any check is fidelity/judgement-based rather than structural (e.g. "is
  this conversion faithful"), split it: structural invariants are a real gate
  in verify.sh; judgement calls produce a review queue, not a pass/fail —
  don't launder a probability into a boolean.

Give me a short numbered list of the open decisions from #4 before writing any
code. Once I've answered them, build the four files above.
```

Answer the numbered decisions it comes back with — this is the step that actually determines whether the loop drifts or invents later. Then let it build the four files.

## Phase 2 — Wire the hard gate

Add a Stop hook (`.claude/settings.json`) pointed at `scripts/verify.sh`, so a turn can't end while it's red. `/goal` alone can be argued out of stopping ("close enough"); a Stop hook can't.

## Phase 3 — Run line

```
/goal every item in docs/features.yaml has passes: true and scripts/verify.sh exits 0
```

Adjust the ledger path/filename to whatever Phase 1 actually produced.

## Related

- [[loop-engineering-preconditions]] — the checklist and reasoning this prompt operationalizes
- [[loop-engineering]] — Addy Osmani's definitional essay
- [[moc-loop-engineering]] — Map of Content for loop engineering
