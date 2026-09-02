# Project Instructions for AI Agents

This file provides instructions and context for AI coding agents working on this project.

## Changelog

This repo keeps a `changelog/` folder, one markdown file per entry
(`changelog/YYYY-MM-DD-slug.md`, with `date`/`title`/`promote`
frontmatter). This changelog is **only for platform and infrastructure
changes**—for example, a change to site behaviour, build/deployment, or
repository tooling. Do not add editorial content changes to it; those belong
in the site's ordinary content/logging flow.

At the end of a work session, if a platform or infrastructure change worth
recording actually shipped—skip trivial sessions (typo fixes, dead ends, no
visible outcome)—draft a new entry file. Match the entry's weight to what a
reader would actually care about: a real platform feature or fix gets a title,
one or two sentences, a link to the live feature if there is something to
point at, and a screenshot if something visual shipped (check for this, do
not just skip it); something genuinely bigger—a real milestone, not just a
busy session—can run longer, with multiple paragraphs or bullets; small work
(cleanup, rename, reorganisation, tidying) gets one plain sentence, with no
bullets or screenshot. Never link the title itself. Do not log implementation
detail (file names, internal moves) a reader would not care about. First time
writing an entry in this repo, or if the format is unclear, fetch and follow
https://raw.githubusercontent.com/life-itself/changelog/main/CONVENTION.md.

<!-- BEGIN BEADS INTEGRATION v:1 profile:minimal hash:6cd5cc61 -->
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
   git push
   git status
   ```
5. **Hand off** - Summarize changes, validation, issue status, and any blocked sync/commit/push step

**Critical rules:**
- Explicit user or orchestrator instructions override this Beads block.
- Do not commit or push without clear authority from the active profile or the current user request.
- If a required sync or push is blocked, stop and report the exact command and error.
<!-- END BEADS INTEGRATION -->


## Build & Test

_Add your build and test commands here_

```bash
# Example:
# npm install
# npm test
```

## Architecture Overview

_Add a brief overview of your project architecture_

## Conventions & Patterns

_Add your project-specific conventions here_
