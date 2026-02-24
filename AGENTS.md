# AGENTS.md - AI Learned Today Repository Guide

This document explains how to add entries to the AI Learned Today knowledge base.

## Repository Structure

```
ailearnedtoday/
├── logs/           # Daily logs with wiki links (1-2 sentence summaries)
│   └── YYYY-MM-DD.md
├── ref/            # Detailed reference entries (full documentation)
│   └── topic-name.md
├── posts/          # Long-form articles and drafts
│   └── YYYY-MM-DD-title.md
├── links/          # Quick link collections
├── backlog/        # Items to process
├── SKILL.md        # Skill documentation (deprecated in favor of this file)
└── AGENTS.md       # This file
```

## Quick Reference

### Adding a New Entry

1. **Decide**: Full reference entry or simple log?
2. **Create ref file** (if full entry): `ref/topic-name.md` with frontmatter and screenshot
3. **Add log entry**: Update `logs/YYYY-MM-DD.md` with 1-2 sentence summary
4. **Update memory**: Add note to `~/.openclaw/workspace/memory/YYYY-MM-DD.md`
5. **Commit and push**: `git add ref/ logs/ && git commit -m "Add: [Topic]" && git push`

## Reference Entries (ref/)

### When to Create a Reference Entry

Use a full reference entry when:
- The topic warrants detailed documentation
- There are multiple key points, quotes, or insights
- You want to include screenshots, links, and context
- It's something you'll reference in the future

### File Naming

- Use descriptive, URL-friendly names
- Lowercase with hyphens for multi-word names
- Examples: `msgvault.md`, `dmux.md`, `anthropic-distillation-attacks.md`
- For domains/products, you can preserve dots: `pi.dev.md`, `mockdown.design.md`

### Frontmatter (Required)

Every ref file MUST start with:

```yaml
---
created: YYYY-MM-DD  # Date entry was added to repo (required)
author: Author Name  # Creator/publisher (optional)
tags: [tag1, tag2, tag3]  # Searchable tags
---
```

**Important**: 
- `created` is the date you added the entry to the repo, NOT the original publication date
- Use today's date in `YYYY-MM-DD` format
- Tags should be specific and useful for search (tech stack, category, key features)

### Content Structure

1. **Title (H1)** — Project/tool/topic name
2. **Tagline** — One-sentence summary (use blockquote: `>`)
3. **Screenshot (REQUIRED for web content)** — Using `screenshotit.app`
4. **Links** — Website, GitHub, docs, announcement
5. **Summary** — What it is, what it does
6. **Key Features/Insights** — Main points
7. **Quotes** (if applicable) — Important excerpts
8. **Why It Matters** — Context, significance
9. **Technical Details** (if relevant) — Stack, architecture
10. **Related** — Wiki links to related entries

### Screenshots (CRITICAL)

**For any web-based content, ALWAYS include a screenshot at the top:**

```markdown
# Title

> Tagline

![Description](https://screenshotit.app/https://example.com/url)

## Links
...
```

**Screenshot rules:**
- Format: `![Description](https://screenshotit.app/{url})`
- Example: `![dmux.ai](https://screenshotit.app/https://dmux.ai/)`
- **Place immediately after the tagline, before the Links section**
- This gives visual context before reading details
- Service auto-caches and provides stable URLs
- Works with any public URL (tweets, articles, tools)

### Example Reference Entry

```markdown
---
created: 2026-02-24
author: Chris Tate
tags: [qa-automation, agent-browser, testing]
---

# Autonomous Dogfooding Skill

> A skill that uses your app the way your users do — no test scripts, no manual QA.

![Autonomous Dogfooding](https://screenshotit.app/https://x.com/ctatedev/status/2026357704617267314)

## Links

- **Announcement**: https://x.com/ctatedev/status/2026357704617267314
- **Author**: [@ctatedev](https://x.com/ctatedev)

## Summary

An autonomous testing skill for agent-browser that explores your application...

## Key Features

- Explores pages autonomously
- Clicks buttons and fills forms
- Captures repro videos
- Outputs structured report

## Why It Matters

Represents a shift from scripted testing to autonomous exploration...

## Related

- [[harness-engineering-openai]]
- [[dmux]]
```

## Log Entries (logs/)

### Format

```markdown
# YYYY-MM-DD

## [[ref-file-name]] - Short Title

Brief 1-2 sentence summary capturing the essence. Maximum two sentences.
```

### Rules

- **1-2 sentences maximum** — be concise
- Use wiki links: `[[filename]]` (no `.md` extension)
- Capture the key insight or value proposition
- Include relevant names, numbers, key features

### Example Log Entries

**Good (concise):**
```markdown
## [[dmux]] - Parallel Agents with tmux and Worktrees

Dev agent multiplexer by FormKit team that runs multiple AI coding agents 
(Claude Code, Codex, OpenCode) in parallel using tmux and git worktrees — 
each agent gets its own isolated working copy.
```

**Bad (too long):**
```markdown
## [[dmux]] - Parallel Agents with tmux and Worktrees

Dev agent multiplexer by Justin Schroeder (@jpschroeder) and Boyd (@0xboyd) 
from FormKit team. Runs multiple AI coding agents (Claude Code, Codex, OpenCode) 
in parallel using tmux and git worktrees. Each agent gets its own isolated 
working copy — no conflicts. Press `n` to create pane, type prompt, pick agent; 
dmux creates worktree, launches agent. Press `m` to merge back when done. 
Key features: A/B agent pairs (run two agents on same prompt side-by-side, 
pick winner), AI-powered branch names and commit messages via OpenRouter...
```

## Posts (posts/)

For longer-form content, drafts, or essays:

- File naming: `YYYY-MM-DD-title.md`
- Include `Status: Draft` at the top if not final
- Reference from logs with a brief note
- Can be more exploratory and less structured than ref entries

## Git Workflow

### Before Adding

Always pull latest:
```bash
cd ~/src/datopian/ailearnedtoday
git pull --rebase
```

### Adding Files

```bash
git add ref/topic-name.md logs/YYYY-MM-DD.md
```

### Commit Message

```
Add: [Topic Name] - Brief description

For multiple items in one commit:
Add: Topic A, Topic B + update SKILL.md
```

### Push

```bash
git push
```

## Memory Updates

After creating entries, update your session memory:

```markdown
# YYYY-MM-DD

## ailearnedtoday Knowledge Base

### Added: Topic Name
- Created ref entry for...
- Key points: ...
- Cross-referenced: [[related-topic]]
- Commit: abc1234
- Files: ref/topic.md + logs/YYYY-MM-DD.md
```

## Common Patterns

### Adding a Tweet/Article

1. Fetch content with `web_fetch` or `browser`
2. Create `ref/topic-name.md`:
   - Frontmatter with today's date
   - Screenshot using `https://screenshotit.app/{tweet-url}`
   - Links section (tweet, author profile)
   - Summary and key quotes
3. Add 1-2 sentence entry to today's log
4. Commit and push

### Adding a GitHub Project

1. Fetch README with `web_fetch`
2. Create `ref/project-name.md`:
   - Frontmatter
   - Screenshot of GitHub repo page
   - Links (GitHub, docs, related)
   - Summary, key features, why it matters
3. Add log entry
4. Commit and push

### Adding Multiple Items

You can add multiple entries in a single commit:
- Create multiple ref files
- Update single log file with all entries
- Commit message: `Add: Topic A, Topic B, Topic C`

## Screenshot Guidelines

### When to Use Screenshots

- **Always** for web-based tools, products, or services
- **Always** for tweets/announcements
- **Always** for articles or blog posts
- Optional for GitHub projects (but recommended)
- Not needed for pure text/concept entries

### How to Use screenshotit.app

The service is simple:

```
https://screenshotit.app/{url-to-screenshot}
```

Examples:
- Tweet: `https://screenshotit.app/https://x.com/user/status/123456`
- Website: `https://screenshotit.app/https://dmux.ai/`
- Article: `https://screenshotit.app/https://anthropic.com/news/article-name`
- GitHub: `https://screenshotit.app/https://github.com/user/repo`

**Markdown format:**
```markdown
![Description](https://screenshotit.app/https://example.com/)
```

**Placement:**
Right after the title and tagline, before everything else.

### Advanced Screenshot Options

screenshotit.app supports modifiers:
- `@full` — full page capture
- `@mobile` — mobile viewport
- `@refresh` — force new screenshot

Example: `https://screenshotit.app/https://example.com/@full`

## Tags

Use specific, searchable tags:

**Technology/Stack:**
- `[ai-agents, claude, openai]`
- `[react, typescript, rust]`
- `[tmux, git-worktrees]`

**Category:**
- `[qa-automation, testing]`
- `[design-tools, wireframing]`
- `[orchestration, workflow]`

**Domain:**
- `[national-security, export-controls]`
- `[ai-safety, model-distillation]`
- `[developer-tools, cli]`

Aim for 3-7 tags per entry.

## Quality Standards

### Reference Entries

- **Comprehensive over brief** — ref files should be 3-10KB
- Include key quotes if they add value
- Cross-reference related topics with wiki links
- Explain "why it matters" in context
- Use headers to organize long content

### Log Entries

- **Concise over comprehensive** — 1-2 sentences max
- Capture the essence and key differentiator
- Include relevant metrics or notable facts
- Make it scannable

### Screenshots

- **Always include for web content**
- Place at the top for visual context
- Use descriptive alt text

## Troubleshooting

### "Forgot to add screenshot"

Edit the ref file and add:
```markdown
![Topic Name](https://screenshotit.app/https://url-here/)
```
Right after the tagline, then commit the update.

### "Log entry too long"

Edit `logs/YYYY-MM-DD.md` and trim to 1-2 sentences. Focus on the key insight.

### "Wrong created date"

Edit the frontmatter in `ref/topic.md` and set `created` to today's date in `YYYY-MM-DD` format.

### "Need to update AGENTS.md or SKILL.md"

You can update these files as you learn patterns. Commit changes with:
```
Update: AGENTS.md - clarify screenshot placement
```

## Related Documentation

- `SKILL.md` — Original skill documentation (being deprecated)
- `PLAN.md` — Project planning and roadmap
- `README.md` — Repository overview

---

**Last updated**: 2026-02-24

*This is the living guide for contributing to AI Learned Today. Update it as patterns emerge.*
