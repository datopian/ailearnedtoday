# AI Learned Today - Logging Skill

This skill documents how to create log entries for the AI Learned Today repository.

## Repository Structure

```
ailearnedtoday/
├── logs/           # Daily logs with wiki links
│   └── YYYY-MM-DD.md
├── ref/            # Detailed reference entries
│   └── topic-name.md
├── links/          # Quick link collections
├── backlog/        # Items to process
└── SKILL.md        # This file
```

## Log Entry Process

### 1. Determine Entry Type

**Full reference entry:**
- Use when topic warrants detailed documentation
- Include frontmatter, links, screenshots, full context
- File location: `ref/topic-name.md`

**Simple log entry:**
- Use for quick notes, links without deep dive
- Just bullet point in daily log
- No separate ref file

### 2. Creating Reference Entries

**File naming:**
- Use descriptive, URL-friendly names
- Examples: `msgvault.md`, `inference-sh.md`, `pi.dev.md`
- Hyphens for multi-word names

**Frontmatter (required):**
```yaml
---
created: YYYY-MM-DD
author: Author Name (if applicable)
tags: [tag1, tag2, tag3]
---
```

**Content structure:**
1. **Title (H1)** - Project/tool name
2. **Tagline/Description** - One-sentence summary
3. **Screenshot** (if web-based) - Using `screenshotit.app/URL`
4. **Links section** - Website, GitHub, docs, announcement
5. **Overview** - What it is, what it does
6. **Key Features** - Main capabilities
7. **Why It Exists / Why Interesting** - Context, motivation
8. **Technical Details** - Stack, architecture, specs
9. **Related** - Links to related topics, blog posts

**Screenshots:**
- Use screenshotit.app for web URLs
- Format: `![Description](https://screenshotit.app/https://example.com/)`
- Service auto-caches, provides stable URLs

### 3. Daily Log Entries

**File location:** `logs/YYYY-MM-DD.md`

**Format:**
```markdown
# YYYY-MM-DD

## [[ref-file-name]] - Short Title

Brief one-sentence description with key details. Can span multiple sentences if needed to capture essence.
```

**Wiki links:**
- Use Obsidian-style: `[[filename]]` (without `.md`)
- Links resolve to ref/ entries
- Keep description concise but informative

### 4. Update Memory

After creating entries, update `~/.openclaw/workspace/memory/YYYY-MM-DD.md`:

```markdown
## AI Learned Today Updates

- Created ref/topic.md with frontmatter, links, details
- Updated logs/YYYY-MM-DD.md with [[topic]] wiki link
- Topic: brief description
- Key links: URLs
```

### 5. Git Workflow

**Add files:**
```bash
cd ~/src/ailearnedtoday
git add logs/YYYY-MM-DD.md ref/new-entry.md
```

**Commit message format:**
```
Add [topic] reference and YYYY-MM-DD log

- Created ref/topic.md: detailed reference for [description]
- Added logs/YYYY-MM-DD.md: daily log with [[topic]] wiki link
- [Key details about the entry]
- [Any notable features/context]
```

**Push:**
```bash
cd ~/src/ailearnedtoday
git push
```
- GitHub PAT configured in remote URL
- Can push automatically after commit

## Examples

### Full Reference Entry (msgvault)

**Created files:**
- `ref/msgvault.md` - Full reference
- Updated `logs/2026-02-04.md` - Added wiki link

**Features:**
- Frontmatter with created date, author, tags
- Links to GitHub, announcement tweet
- Overview, key features, why interesting
- Technical details, context

**Log entry:**
```markdown
## [[msgvault]] - Local-first Email Archive

Wes McKinney (pandas/Arrow creator) built msgvault: local-first email archive 
powered by DuckDB with MCP server for AI agent integration. Handles 20 years 
of Gmail (2M emails, 150K attachments) in a single Go binary.
```

### Full Reference with Screenshot (inference.sh)

**Created files:**
- `ref/inference-sh.md`
- Updated `logs/2026-02-04.md`

**Special:**
- Included screenshot via `screenshotit.app`
- Hyphenated filename for domain name

**Screenshot:**
```markdown
![inference.sh homepage](https://screenshotit.app/https://inference.sh/)
```

### Domain/URL in Filename (pi.dev)

**Filename:** `pi.dev.md`
- Preserves dot for domain names
- User explicitly requested this format

## Guidelines

**Conciseness:**
- Log entries: 1-2 sentences capturing essence
- Reference entries: comprehensive but organized
- Use headers to break up long content

**Links:**
- Always include primary website
- GitHub if open source
- Announcement tweet/blog post if relevant
- Related documentation

**Tags:**
- Be specific and useful for search
- Include: technology stack, category, key features
- Examples: `[ai-agents, platform, durable-execution]`

**Screenshots:**
- Only for web-based tools/platforms
- Use screenshotit.app for automatic caching
- Place early in reference (after title/links)

## Tools

**screenshotit.app:**
- URL-based screenshot service
- Format: `screenshotit.app/https://example.com/`
- Modifiers: `@full`, `@mobile`, `@refresh`
- See: https://github.com/flowershow/screenshotit

**Obsidian wiki links:**
- `[[filename]]` - links to ref/filename.md
- No need for path or extension
- Works in Obsidian and compatible Markdown renderers

## Workflow Checklist

- [ ] Decide: full reference or simple log entry?
- [ ] If reference: create `ref/topic-name.md` with frontmatter
- [ ] If reference: include links, overview, features
- [ ] If web tool: add screenshot via screenshotit.app
- [ ] Update `logs/YYYY-MM-DD.md` with wiki link entry
- [ ] Update `~/.openclaw/workspace/memory/YYYY-MM-DD.md`
- [ ] Git add both files
- [ ] Git commit with descriptive message
- [ ] Git push (automatic with configured PAT)

## Notes

- Filename format can vary (hyphens, dots) based on topic
- User may specify preferred filename format
- Always use Obsidian wiki link syntax in logs
- Screenshots are optional but recommended for web tools
- Maintain consistent frontmatter format
