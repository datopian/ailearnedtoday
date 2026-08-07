---
created: 2026-08-07
author: Rufus Pollock
tags: [loop-engineering, coding-agents, claude-code, agent-harness, verification, checklist]
---

# Loop Engineering: The Five Preconditions (Applied)

A practical checklist for whether a repo is actually ready for an unattended agent loop, distilled from setting one up on a real project ([Reports That Matter](https://reportsthatmatter.org)) rather than from theory. Builds on [[loop-engineering]] (Addy Osmani's framing) but answers the harder question: *what has to be true before you press go?*

## The core insight

**A loop is only as good as its stopping condition.** An agent given a vague goal doesn't stop cleanly — it drifts, declares premature victory, or polishes the wrong thing for hours. Anthropic's own guidance on long-running harnesses names the same failure modes: declaring victory prematurely, attempting too much per session, leaving buggy undocumented code, wasting time on environment setup.

Before starting a loop, check for five things. A repo with zero of them (the normal starting state) needs the setup work below before it's safe to leave unattended.

## The five preconditions

1. **A machine-checkable done condition.** One command, exit code 0 or not. Not "does this look right" — something that runs and fails loudly.
2. **A green baseline + `init.sh`.** A fresh context must be able to reach "everything passes" in one command, so it can tell *its own* breakage from *pre-existing* breakage. Without this, every failure is ambiguous.
3. **A durable ledger.** Context gets compacted; a file does not. Use structured data (YAML/JSON with an explicit `passes: true/false` field per item), not prose — prose survives compaction by being reinterpreted, which is exactly what you don't want.
4. **Every open decision pre-answered.** Design questions, scope boundaries, quality bars — anything genuinely undecided is what makes a loop stall (waiting on you) or invent (guessing wrong, confidently). Answer them *before* the loop starts, not when it hits them.
5. **Written guard rails.** With `--dangerously-skip-permissions` (or any always-approve mode) there is no human veto mid-run, so the veto has to be written down in advance: don't rewrite `main`, don't edit the ledger to make the goal pass, don't weaken a test/check to make it pass, stop-and-report after N identical consecutive failures.

## Mechanism pairing that actually works (Claude Code 2.1.220)

- **`/goal <condition>`** — a persistent goal across many autonomous turns; an independent checker re-verifies the condition after each turn. This is the "keep going until done" primitive.
- **A Stop hook** wired to your verify script — a shell script that blocks the turn from ending unless it exits 0.
- **The combination is the point**: `/goal` alone can be talked out of stopping (an agent can rationalize "close enough"). A Stop hook is a hard gate — it can't be argued with. Use `/goal` for direction and a Stop hook for the actual guarantee.

## What the verify script should check

Unit tests aren't enough — they're what let "tests pass but the page is blank" happen. Layer in HTTP/browser-level smoke checks against a live running instance: does the health endpoint respond, does the homepage contain expected content, does a detail page return 200 with the right text, does a bad route 404. The smoke checks catch what the unit tests structurally can't see.

## Where a threshold is dishonest

Not every check should be pass/fail. When a task is fidelity-graded (e.g. "did this PDF-to-Markdown conversion preserve meaning"), split it: cheap structural invariants and lossless-content checks are real gates and belong in `verify.sh`; anything that's ultimately a judgement call (OCR-suspect scoring, "is this faithful") should produce a **report and a review queue**, not a pass/fail gate pretending to be objective. Auto-fix only what has no other reading; surface the rest rather than laundering a probability into a boolean.

## House rules worth writing into `CLAUDE.md`

- Fixes go in the pipeline/tool, not in its output — never hand-edit a generated artifact; fix the generator and re-run, so the fix compounds across every future use.
- Never weaken a check to make something pass. If it can't meet the gate, mark it as not-passing and record why.
- Don't modify tests to make them pass — fix the code (but do fix tests whose fixtures were unrealistic to begin with).

## Related

- [[loop-engineering]] — Addy Osmani's definitional essay this playbook operationalizes
- [[moc-loop-engineering]] — Map of Content for loop engineering
- [[brittany-ellich-loop-engineering]] — a different applied case study (108 PRs via board/loop/worker split)
