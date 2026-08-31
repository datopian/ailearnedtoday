# AGENTS.md - Way Into AI

This is a practical guide and knowledge base for documenting AI coding agents, tools, and related topics.

## When Adding Entries

**Before doing any work**, read `SKILL.md` to understand the repository structure and patterns.

## Quick Workflow

1. **Read SKILL.md** — first time working in this repo
2. **Decide**: Full reference entry or simple log?
3. **Create ref entry** (if applicable):
   - Frontmatter with `created: YYYY-MM-DD` (today's date)
   - Screenshot at top using `screenshotit.app` for any web content
   - Follow structure in SKILL.md
4. **Add log entry**: 1-2 sentences in `logs/YYYY-MM-DD.md`
5. **Pull, commit, push**:
   ```bash
   cd ~/src/datopian/wayintoai
   git pull --rebase
   git add ref/ logs/
   git commit -m "Add: [Topic]"
   git push
   ```

## Critical Rules

### Screenshots
**ALWAYS include a screenshot at the top of ref entries for web content**:
```markdown
![Topic](https://screenshotit.app/https://example.com/url)
```
Place immediately after title/tagline, before Links section.

### Log Entries
**Maximum 1-2 sentences**. Concise over comprehensive.

### Log Entry H1 Titles
Every log file must have an H1 title in the format: `# yyyy-mm-dd {Short Title}`
- The date comes from the filename
- The title should be a brief, meaningful summary (3-8 words)
- This ensures entries are recognizable when listed on the website

Every log file must also have `date: YYYY-MM-DD` in its frontmatter so Flowershow can sort the log listing newest-first. The date must match the filename.

### Blog Posts

Every blog post in `posts/` (excluding `posts/index.md`) must begin with:

```yaml
---
title: A concise post title
description: A one-sentence summary used in listings and social metadata.
date: YYYY-MM-DD
---
```

- The date must match the date prefix in the filename.
- Do not repeat the title as an H1 in the body. Flowershow renders the frontmatter `title` as the page title.
- Start the body with the opening paragraph, tagline, or screenshot as appropriate.
- Keep `title`, `description`, and `date` accurate because the homepage and `posts/index.md` use them to render and sort post listings.

### Frontmatter
Every ref entry needs:
```yaml
---
created: YYYY-MM-DD  # Date added to repo (required)
author: Author Name
tags: [tag1, tag2, tag3]
---
```

## Repository Structure

```
wayintoai/
├── ref/            # Full reference entries
├── logs/           # Daily logs (1-2 sentence summaries)
│   └── index.md    # Flowershow log listing
├── posts/          # Long-form articles with title/description/date frontmatter
│   └── index.md    # Flowershow post listing
├── SKILL.md        # Comprehensive guide (READ THIS)
└── AGENTS.md       # This file
```

## See SKILL.md for Details

- File naming conventions
- Content structure
- Screenshot placement and examples
- Frontmatter requirements
- Git workflow
- Common patterns
- Quality standards
- Troubleshooting

---

**Don't work from memory. Read SKILL.md when adding entries.**

<!-- BEGIN BEADS INTEGRATION v:1 profile:minimal hash:970c3bf2 -->
## Beads Issue Tracker

This project uses **bd (beads)** for issue tracking. Run `bd prime` to see full workflow context and commands.

### Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --claim  # Claim work
bd close <id>         # Complete work
```

### Rules

- Use `bd` for ALL task tracking — do NOT use TodoWrite, TaskCreate, or markdown TODO lists
- Run `bd prime` for detailed command reference and session close protocol
- Use `bd remember` for persistent knowledge — do NOT use MEMORY.md files

**Architecture in one line:** issues live in a local Dolt DB; sync uses `refs/dolt/data` on your git remote; `.beads/issues.jsonl` is a passive export. See https://github.com/gastownhall/beads/blob/main/docs/SYNC_CONCEPTS.md for details and anti-patterns.

## Agent Context Profiles

The managed Beads block is task-tracking guidance, not permission to override repository, user, or orchestrator instructions.

- **Conservative (default)**: Use `bd` for task tracking. Do not run git commits, git pushes, or Dolt remote sync unless explicitly asked. At handoff, report changed files, validation, and suggested next commands.
- **Minimal**: Keep tool instruction files as pointers to `bd prime`; use the same conservative git policy unless active instructions say otherwise.
- **Team-maintainer**: Only when the repository explicitly opts in, agents may close beads, run quality gates, commit, and push as part of session close. A current "do not commit" or "do not push" instruction still wins.

## Session Completion

This protocol applies when ending a Beads implementation workflow. It is subordinate to explicit user, repository, and orchestrator instructions.

1. **File issues for remaining work** - Create beads for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **Handle git/sync by active profile**:
   ```bash
   # Conservative/minimal/default: report status and proposed commands; wait for approval.
   git status

   # Team-maintainer opt-in only, unless current instructions forbid it:
   git pull --rebase
   bd dolt push
   git push
   git status
   ```
5. **Hand off** - Summarize changes, validation, issue status, and any blocked sync/commit/push step

**Critical rules:**
- Explicit user or orchestrator instructions override this Beads block.
- Do not commit or push without clear authority from the active profile or the current user request.
- If a required sync or push is blocked, stop and report the exact command and error.
<!-- END BEADS INTEGRATION -->

<!-- BEGIN BEADS CODEX SETUP: generated by bd setup codex -->
## Beads Issue Tracker

Use Beads (`bd`) for durable task tracking in repositories that include it. Use the `beads` skill at `.agents/skills/beads/SKILL.md` (project install) or `~/.agents/skills/beads/SKILL.md` (global install) for Beads workflow guidance, then use the `bd` CLI for issue operations.

### Quick Reference

```bash
bd ready                # Find available work
bd show <id>            # View issue details
bd update <id> --claim  # Claim work
bd close <id>           # Complete work
bd prime                # Refresh Beads context
```

### Rules

- Use `bd` for all task tracking; do not create markdown TODO lists.
- Run `bd prime` when Beads context is missing or stale. Codex 0.129.0+ can load Beads context automatically through native hooks; use `/hooks` to inspect or toggle them.
- Keep persistent project memory in Beads via `bd remember`; do not create ad hoc memory files.

**Architecture in one line:** issues live in a local Dolt DB; sync uses `refs/dolt/data` on your git remote; `.beads/issues.jsonl` is a passive export. See https://github.com/gastownhall/beads/blob/main/docs/SYNC_CONCEPTS.md for details and anti-patterns.
<!-- END BEADS CODEX SETUP -->
