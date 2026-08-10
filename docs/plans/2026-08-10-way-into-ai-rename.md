# Way Into AI Rename Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Make Way Into AI the canonical public and repository identity while retaining the existing navigation logo.

**Architecture:** Flowershow reads navigation and social metadata from `config.json`, and renders the homepage from `README.md`. Update those sources plus active contributor documentation; do not rewrite historical reference material.

**Tech Stack:** JSON configuration, Markdown/MDX, Git.

---

### Task 1: Update public site configuration

**Files:**
- Modify: `config.json`

**Step 1: Change canonical brand settings**

Set the social-image URL to `https://screenshotit.app/wayintoai.com@social`, retain `assets/ailearnedtoday-logo.webp`, set the navigation title to `Way Into AI`, and point GitHub at `https://github.com/datopian/wayintoai`.

**Step 2: Validate JSON**

Run: `jq empty config.json`

Expected: exits successfully with no output.

**Step 3: Commit**

```bash
git add config.json
git commit -m "Rename: update Way Into AI site configuration"
```

### Task 2: Refresh homepage positioning

**Files:**
- Modify: `README.md`

**Step 1: Replace old title and diary framing**

Use `# Way Into AI`, followed by `From curious to capable.` and concise copy that presents the site as practical guides, field notes, and tools for building AI capability.

**Step 2: Change canonical web link and newsletter framing**

Replace the old site URL with `https://wayintoai.com`; retain the current Substack URL/embed and introduce it as the Way Into AI newsletter.

**Step 3: Verify visible text**

Run: `rg -n -i 'AI, Learned Today|ailearnedtoday\.com' README.md`

Expected: no matches.

### Task 3: Update active repository documentation

**Files:**
- Modify: `AGENTS.md`
- Modify: `SKILL.md`

**Step 1: Rename active project references and local command paths**

Replace the former project name and `ailearnedtoday` command-path examples with Way Into AI and `wayintoai`.

**Step 2: Preserve historical source examples**

Do not change references under `ref/` or dated logs, which document their original context.

**Step 3: Verify active docs**

Run: `rg -n -i 'AI Learned Today|ailearnedtoday' AGENTS.md SKILL.md`

Expected: no matches.

### Task 4: Verify and commit the rename

**Files:**
- Verify: `config.json`
- Verify: `README.md`
- Verify: `AGENTS.md`
- Verify: `SKILL.md`

**Step 1: Run content checks**

Run: `jq empty config.json && rg -n -i 'AI, Learned Today|ailearnedtoday\.com|github.com/datopian/ailearnedtoday' config.json README.md AGENTS.md SKILL.md`

Expected: JSON validation succeeds; the search returns no stale public identity references.

**Step 2: Review the patch**

Run: `git diff --check && git diff -- config.json README.md AGENTS.md SKILL.md`

Expected: no whitespace errors; only the intended brand and copy changes appear.

**Step 3: Commit**

```bash
git add config.json README.md AGENTS.md SKILL.md docs/plans/2026-08-10-way-into-ai-rename.md
git commit -m "Rename: make Way Into AI the canonical identity"
```
