# AGENTS.md - AI Learned Today

This is a knowledge base repository for documenting AI coding agents, tools, and related topics.

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
   cd ~/src/datopian/ailearnedtoday
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
ailearnedtoday/
├── ref/            # Full reference entries
├── logs/           # Daily logs (1-2 sentence summaries)
├── posts/          # Long-form articles
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
