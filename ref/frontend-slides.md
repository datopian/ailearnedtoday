---
created: 2026-03-04
author: Zara Zhang
tags: [claude-code, claude-skill, presentations, slides, web-design, html, css, animations, pptx-conversion, vibe-coding, no-dependencies]
---

# Frontend Slides - Beautiful Web Presentations with Claude

**Claude Code skill for creating stunning, animation-rich HTML presentations from scratch or by converting PowerPoint files — zero dependencies, single HTML files with inline CSS/JS.**

![Frontend Slides GitHub](https://screenshotit.app/https://github.com/zarazhangrui/frontend-slides)

## Links

- **GitHub**: https://github.com/zarazhangrui/frontend-slides
- **Announcement**: https://x.com/zarazhangrui/status/2016337615843434646
- **Author**: Zara Zhang (@zarazhangrui)
- **License**: MIT

## Demo Video

https://private-user-images.githubusercontent.com/153693696/557924257-ef57333e-f879-432a-afb9-180388982478.mp4

*Deck about the skill, made through the skill itself*

## Overview

Frontend Slides helps non-designers create beautiful web presentations without knowing CSS or JavaScript. Uses "show, don't tell" approach: generates visual previews and lets you pick what you like, instead of asking you to describe aesthetic preferences in words.

**From the author:**

> "I created a Claude Skill that make beautiful slides on the web. The world hasn't woken up to the fact that code can create much better slides than most PPT tools.
> 
> - Claude interviews you first about aesthetics, then generate a few directions to 'show not tell', and you can pick your favorite
> - Cool transitions and animations
> - Interactive hover states and cursor effects
> - Auto-fits on any screen
> - Supports converting existing PPTX files to web-based slides; preserves original images and brand assets
> 
> I asked Claude to make a slide show about this skill to showcase what it can do."

## Key Features

### 1. Zero Dependencies
- Single HTML files with inline CSS/JS
- No npm, no build tools, no frameworks
- "A single HTML file will work in 10 years. A React project from 2019? Good luck."

### 2. Visual Style Discovery
- Can't articulate design preferences? No problem
- Pick from generated visual previews
- "Show, don't tell" approach
- Claude generates 3 visual style previews to compare

### 3. PPT Conversion
- Convert existing PowerPoint files to web
- Preserves all images and content
- Extract text, images, notes from PPT
- Generate HTML presentation with all original assets

### 4. Anti-AI-Slop
- Curated distinctive styles
- Avoid generic AI aesthetics
- "Bye-bye, purple gradients on white"
- Every presentation feels custom-crafted, not template-generated

### 5. Production Quality
- Accessible
- Responsive
- Well-commented code you can customize
- "Comments are kindness. Code should explain itself to future-you."

## Installation

### For Claude Code Users

```bash
# Create the skill directory
mkdir -p ~/.claude/skills/frontend-slides/scripts

# Copy all files (or clone this repo directly)
cp SKILL.md STYLE_PRESETS.md viewport-base.css html-template.md animation-patterns.md ~/.claude/skills/frontend-slides/
cp scripts/extract-pptx.py ~/.claude/skills/frontend-slides/scripts/

# Or clone directly
git clone https://github.com/zarazhangrui/frontend-slides.git ~/.claude/skills/frontend-slides
```

Then use by typing `/frontend-slides` in Claude Code.

## Usage

### Create a New Presentation

```
/frontend-slides
> "I want to create a pitch deck for my AI startup"
```

**The skill will:**
1. Ask about your content (slides, messages, images)
2. Ask about the feeling you want (impressed? excited? calm?)
3. Generate 3 visual style previews for you to compare
4. Create the full presentation in your chosen style
5. Open it in your browser

### Convert a PowerPoint

```
/frontend-slides
> "Convert my presentation.pptx to a web slideshow"
```

**The skill will:**
1. Extract all text, images, and notes from your PPT
2. Show you the extracted content for confirmation
3. Let you pick a visual style
4. Generate an HTML presentation with all your original assets

## Included Styles (12 Curated Presets)

### Dark Themes

- **Bold Signal** — Confident, high-impact, vibrant card on dark
- **Electric Studio** — Clean, professional, split-panel
- **Creative Voltage** — Energetic, retro-modern, electric blue + neon
- **Dark Botanical** — Elegant, sophisticated, warm accents

### Light Themes

- **Notebook Tabs** — Editorial, organized, paper with colorful tabs
- **Pastel Geometry** — Friendly, approachable, vertical pills
- **Split Pastel** — Playful, modern, two-color vertical split
- **Vintage Editorial** — Witty, personality-driven, geometric shapes

### Specialty

- **Neon Cyber** — Futuristic, particle backgrounds, neon glow
- **Terminal Green** — Developer-focused, hacker aesthetic
- **Swiss Modern** — Minimal, Bauhaus-inspired, geometric
- **Paper & Ink** — Literary, drop caps, pull quotes

## Architecture: Progressive Disclosure

Main SKILL.md is a concise map (~180 lines), with supporting files loaded on-demand only when needed:

| File | Purpose | Loaded When |
|------|---------|-------------|
| SKILL.md | Core workflow and rules | Always (skill invocation) |
| STYLE_PRESETS.md | 12 curated visual presets | Phase 2 (style selection) |
| viewport-base.css | Mandatory responsive CSS | Phase 3 (generation) |
| html-template.md | HTML structure and JS features | Phase 3 (generation) |
| animation-patterns.md | CSS/JS animation reference | Phase 3 (generation) |
| scripts/extract-pptx.py | PPT content extraction | Phase 4 (conversion) |

**Design philosophy**: Follows [OpenAI's harness engineering](https://openai.com/index/harness-engineering/) principle: "give the agent a map, not a 1,000-page instruction manual."

## Philosophy

This skill was born from the belief that:

1. **You don't need to be a designer to make beautiful things.** You just need to react to what you see.

2. **Dependencies are debt.** A single HTML file will work in 10 years. A React project from 2019? Good luck.

3. **Generic is forgettable.** Every presentation should feel custom-crafted, not template-generated.

4. **Comments are kindness.** Code should explain itself to future-you (or anyone else who opens it).

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI
- For PPT conversion: Python with `python-pptx` library

## Why It Matters

**Code can create better slides than PPT tools:**
- Custom animations and transitions (not limited by PowerPoint's presets)
- Interactive hover states and cursor effects
- True responsive design (auto-fits any screen)
- No software license required
- Works on any device with a browser
- Infinite customization without learning design tools

**"Show, don't tell" approach:**
- Removes barrier of articulating design preferences
- Visual comparison more effective than verbal description
- Faster iteration (pick from 3 options vs. back-and-forth refinement)

**Zero dependencies philosophy:**
- No npm packages to maintain
- No build process to break
- No framework versions to upgrade
- Files remain functional indefinitely
- Easy to understand and modify

## Use Cases

- Pitch decks for startups
- Conference presentations
- Product demos
- Portfolio showcases
- Educational content
- Marketing presentations
- Converting old PowerPoint files to modern web format

## Workflow Example

**Traditional approach:**
1. Open PowerPoint/Keynote
2. Pick a template (all look generic)
3. Fight with layout tools
4. Export to PDF (lose animations)
5. File doesn't work on different screen size

**Frontend Slides approach:**
1. Type `/frontend-slides`
2. Describe content and feeling
3. Pick from 3 visual previews
4. Get working HTML file with animations
5. Works on any device, any screen size

## Technical Details

**Output:**
- Single HTML file
- Inline CSS and JavaScript
- No external dependencies
- Keyboard navigation support
- Responsive viewport handling
- Smooth transitions between slides

**PPT Conversion:**
- Python script extracts content using `python-pptx`
- Images preserved with original quality
- Text formatting maintained
- Notes included if present
- Brand assets transferred

## Comparison to Traditional Tools

| Feature | PowerPoint | Google Slides | Frontend Slides |
|---------|------------|---------------|-----------------|
| Custom animations | Limited presets | Limited presets | Full CSS/JS control |
| Responsive | No | Partial | Yes, auto-fits |
| Dependencies | Software license | Internet + Google account | None (HTML file) |
| Customization | Template-based | Template-based | Full code control |
| Longevity | Version-dependent | Platform-dependent | HTML = forever |
| File size | Large | Cloud-based | Small (single file) |

## Credits

Created by [@zarazhangrui](https://github.com/zarazhangrui) with Claude Code.

Inspired by the "Vibe Coding" philosophy — building beautiful things without being a traditional software engineer.

**Related concepts:**
- [[steve-yegge]] - Vibe coding philosophy
- [[harness-engineering-openai]] - "Give the agent a map, not a 1,000-page instruction manual"

## Related

- Claude Code skills
- Vibe coding
- Zero-dependency web development
- Progressive disclosure in AI skill design
- [[react-pdf-skill]] - Similar Claude Code skill approach
- [[whizz-ai-design-prompts]] - Design generation with AI

## By

Zara Zhang (@zarazhangrui)
