---
created: 2026-08-31
author: Rufus Pollock
tags: [agent-skills, changelog, ai-native, claude-code, codex, convention, workflow, session-checkpoint, life-itself]
star_count: 1
star_timestamp: 2026-08-31T15:55:35Z
---

# Changelog Convention

> Canonical changelog convention for AI-native repos.

![life-itself/changelog on GitHub](https://screenshotit.app/https://github.com/life-itself/changelog)

## Links

- **GitHub**: https://github.com/life-itself/changelog
- **The snippet**: https://raw.githubusercontent.com/life-itself/changelog/main/add-to-agents.md
- **Full spec**: https://raw.githubusercontent.com/life-itself/changelog/main/CONVENTION.md
- **Author**: Rufus Pollock (Life Itself)
- **Stars**: 1 (as of 2026-08-31)

## Why it exists

There is no good changelog skill out there yet — this is the attempt to fill that gap. The problem it targets: working fast across many repos with AI in the loop, finished work never gets written up. An agent that just shipped something has nothing prompting it to record what happened, and if it does try, it stalls on "where does this go?" and either blocks or picks a destination arbitrarily.

The fix is a convention, not a tool: one short block of markdown pasted verbatim into a repo's `AGENTS.md`, plus a longer spec fetched only when an entry is actually being drafted.

## How it works

**Install** — paste into a repo's coding agent:

```
Go to https://raw.githubusercontent.com/life-itself/changelog/main/add-to-agents.md
and add its content to this repo's AGENTS.md (create AGENTS.md if it doesn't exist).
```

The whole file at that URL is exactly what gets added — nothing to extract or paraphrase. It is the raw file URL, so it is one plain-markdown fetch that works from a local session, a cloud session, or Codex with no checkout or auth. To update a repo later, re-sync: fetch the file again and whole-block-replace the existing `## Changelog` section (no diffing, so the same snippet works for every future change).

**The entry format** — a `changelog/` folder at the repo root, one file per entry:

```
changelog/YYYY-MM-DD-slug.md
changelog/images/YYYY-MM-DD-slug.png
```

```markdown
---
date: 2026-08-15
title: Short title
promote: false
---

One or two sentences, written for a reader, not a commit-message dump.
See it live: [the feature](https://example.com/the-feature).
```

- Date is in the filename *and* frontmatter — filename gives free chronological sort in `ls` / GitHub's browser without opening files; frontmatter `date` is what a generator (Flowershow) sorts on; the slug disambiguates same-day entries (three in a day is not rare).
- `title` is plain text, **never a link** — it is reserved for a future listing page to link *to* the entry.
- `promote: false` by default; set `true` at drafting time when the entry is a strong social/newsletter candidate, so that judgment (made with full session context) survives to the weekly review.

**The trigger** — at session-checkpoint time (end of a work session / handoff), the same moment a `NEXT.md` update happens. AI drafts from what happened in the session; a human skims and edits before commit. Committing to the project's own repo is the automatic, no-decision floor; anything beyond that (site, social, newsletter) is always a manual promote.

## The three tiers (calibrating detail)

The failure mode in practice is not logging something trivial — the skip threshold catches that — it is **logging something real at the wrong weight**. Match the entry to what a reader outside the session would care about, not to how much work it took:

| Tier | When | Format |
|------|------|--------|
| **Skip** | typo fixes, dead ends, pure research, config fiddling with no visible outcome | no entry |
| **Small but real** | internal cleanup, rename, reorg, small fixes with no user-visible change | one plain sentence, no title, no bullets, no screenshot — several small things in one session still collapse to one sentence |
| **Real feature / fix / content** | something a user or reader would notice | title, one or two reader-facing sentences, link to the live feature, screenshot if something visual shipped (check — don't just skip it) |
| **Something bigger** | a genuine milestone with real depth (linear.app-style writeup) | multiple paragraphs / bullets, more than one link if it covers more than one thing, images where relevant — most sessions never clear this bar |

Do not let the entry mirror the session's internal structure. If you are drafting bullets that name specific files or "moved X into Y", stop — that is `git log` material, not changelog material.

## Structure of the repo

- **`add-to-agents.md`** — the short snippet, verbatim content for a repo's `AGENTS.md`. States what an entry is and when to write one; only points to `CONVENTION.md` for the first entry or when the format is unclear, so a session never fetches the full spec just to decide whether to bother.
- **`CONVENTION.md`** — the full per-entry spec: folder/frontmatter, images, linking to the live feature, the skip/weight judgment calls. What a project-repo agent reads.
- **`PUBLISHING.md`** — the separate, less frequent concern of aggregating entries across projects: weekly roll-up + manual promote to social/newsletter/site. Read by a planning repo's `changelog-rollup` skill, not by a project-repo session — kept out of `CONVENTION.md` on purpose.
- **`MOTIVATION.md`** — the full situation / complication / question / hypothesis behind the convention (SCQH), self-contained.
- **`NEXT.md`** — current checkpoint and backlog.

Progressive disclosure by design: a project-repo agent drafting one entry never loads roll-up or promote instructions into context.

## Why not a packaged skill or a website

The actual consumer is an AI agent fetching a plain-text file, not a human browsing a site. The raw GitHub URL is already public and needed zero setup. It is a convention pasted into `AGENTS.md` rather than an auto-loaded skill, so it does not cost context on every session — one line in `AGENTS.md` points to it, and the full spec is pulled only when an entry is actually being written.

## History

Started as a proposed central image-archive repo (one repo per org, subfolder per project). Reconsidered — that solved a repo-bloat problem that had not shown up yet, at the cost of a cross-repo hop for every entry. Visual entries were folded back into each project's own repo, and this repo was repurposed to hold the convention doc itself. v2 (2026-08-23) added the "something bigger" tier, the link-to-live-feature section, stronger screenshot judgment, and the `changelog/`-folder shape (was a single growing `changelog.md`).

## Related

- [[moc-best-ai-skills]] — curated best-of AI coding-agent skills.
- [[loop-engineering-preconditions]] — "durable ledger" as a loop precondition; a changelog is one.
- [[minimal-agents-file]] — what belongs in `AGENTS.md`.

## By

Rufus Pollock (Life Itself)
