# Dual-Purpose Site Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Make Way Into AI easy to enter through two clear destinations: practical AI use and broader AI understanding.

**Architecture:** Keep the existing Flowershow Markdown site and chronological posts/logs. Add two directory index pages as curated entry points, link to them from the homepage and primary navigation, and record the shared editorial direction in a short brand document. The later custom visual redesign is explicitly out of scope.

**Tech Stack:** Flowershow, Markdown/MDX, JSON site configuration.

---

### Task 1: Record the usable brand direction

**Files:**
- Create: `docs/brand/way-into-ai.md`

**Step 1: Write the brand note**

State the site promise, intended general audience, direct and practical voice, and the role of the two routes. Keep it to one screen so it guides editorial choices rather than becoming a brand manual.

**Step 2: Verify the note has all decision anchors**

Run: `rg -n "Offer|Audience|Voice|Use AI|Understand AI" docs/brand/way-into-ai.md`

Expected: one match for every named anchor.

### Task 2: Create the two editorial entry pages

**Files:**
- Create: `use/index.md`
- Create: `understand/index.md`

**Step 1: Write the Use AI page**

Use Flowershow frontmatter with a concise title and description. Explain the practical remit in plain language, then provide a deliberately short, useful set of links to existing practical guides and posts.

**Step 2: Write the Understand AI page**

Use equivalent frontmatter and structure. Define the remit as understanding what AI changes, then provide a concise selection of existing analysis and context.

**Step 3: Verify both pages offer real starting points**

Run: `rg -n "^#|^title:|\]\(/" use/index.md understand/index.md`

Expected: both pages have title metadata and multiple internal links.

### Task 3: Turn the homepage into an orientation page

**Files:**
- Modify: `README.md`

**Step 1: Replace the narrow hero copy**

Set title/description copy that communicates both acting with AI and understanding its consequences. Change the two header CTAs to `/use` and `/understand`.

**Step 2: Replace the single Quick link block**

Add a short "Two ways in" section with equally clear Use AI and Understand AI links and one-sentence descriptions. Retain latest posts, logs, and newsletter sections below it.

**Step 3: Verify the new route links**

Run: `rg -n 'href: /use|href: /understand|\]\(/use\)|\]\(/understand\)' README.md`

Expected: the homepage offers both routes in CTAs and body content.

### Task 4: Update primary navigation and check the static site files

**Files:**
- Modify: `config.json`

**Step 1: Make routes primary navigation**

Add Use AI and Understand AI as the first navigation links. Keep Posts and Logs as archive navigation; retain external links.

**Step 2: Check structural correctness**

Run: `node -e "JSON.parse(require('fs').readFileSync('config.json','utf8')); console.log('config valid')"`

Expected: `config valid`.

Run: `git diff --check`

Expected: no output and exit status 0.

**Step 3: Review the final content diff**

Run: `git diff -- index.md config.json use/index.md understand/index.md docs/brand/way-into-ai.md`

Expected: a focused IA-only diff with no visual-platform redesign.
