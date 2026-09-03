---
created: 2026-08-27
author: ara-mkr (akhil)
tags: [claude-code, ai-agents, design-systems, ui-components, css, tailwind, design-styles, coding-agents]
---

# Claude Artisan — 224 Design Styles for Claude Code

> A Claude Code skill that turns "make this brutalist" into a finished, production UI — zero guesswork.

![Claude Artisan GitHub repo](https://screenshotit.app/https://github.com/ara-mkr/claude-artisan)

**Repo:** [github.com/ara-mkr/claude-artisan](https://github.com/ara-mkr/claude-artisan)
**Stars:** 74 | **Forks:** 4 | **License:** MIT
**Created:** July 2026 | **Last updated:** Aug 25, 2026 (v1.2.0: +25 styles)

---

## What it is

`claude-artisan` is a Claude Code skill (Anthropic-format skills, works with any coding agent that can read them) that generates production-ready UI components in 224 distinct design styles — from Bauhaus to Brutalism, Art Deco to Cyberpunk. One prompt, any aesthetic.

The skill is called `design-language` and lives in the `design-language/` subdirectory. Point it at a codebase, say a style name or just a vibe, and it ships real tokens, real components, real accessibility fixes — not a mood board.

Example prompts:

- `"make my landing page glassmorphic"` → resolved instantly, named style
- `"2000s nostalgia, chrome and bubbles"` → resolved via decision tree → Y2K Futurism
- `"premium and futuristic, not childish"` → vibe → shortlist → disambiguated
- `"a spec I can paste into Cursor for this"` → tokens handed off explicitly, no ambiguity

---

## By the numbers

| | |
|---|---|
| **Styles cataloged** | 224 (researched, not invented) |
| **Deep implementation specs** | 224 — every style, full implementation-grade |
| **Style families** | 9 |
| **Starter theme files** | 448 (224 CSS + 224 Tailwind fragments) |
| **Component examples** | 224 fully-styled HTML references — one per style |

All 9 families (224 styles total):

| Family | Count | Covers |
|---|---|---|
| Niche subculture & kitsch | 43 | dark academia, cottagecore, webcore, cyberprep |
| Retrofuturism & speculative genres | 32 | cyberpunk, solarpunk, steampunk, dieselpunk, atompunk |
| Texture / material / rendering | 30 | chrome, holographic, halftone, risograph, isometric, voxel, pixel art, glitch |
| Historical graphic movements | 30 | Bauhaus, Swiss, De Stijl, Constructivism, Art Deco, Memphis, Pop Art, Dada |
| Flat, material & platform systems | 23 | Material 3, Fluent 2, Liquid Glass, Carbon, Ant Design, Polaris, USWDS |
| Minimal / maximal / organic | 17 | minimalism, maximalism, bento grid, biomorphic, Scandinavian |
| Morphism / tactile-dimensional | 9 | skeuomorphism, neumorphism, claymorphism, glassmorphism hybrids |
| Brutalist & anti-design | 8 | brutalist web, neubrutalism, anti-design, Swiss Punk |
| Glass & transparency | 7 | glassmorphism, liquid glass, acrylic, aero glass, frosted variants |

---

## How it works

1. **Identify the target style.** Named style → resolve slug/alias. Vibe/era/mood → `references/style-selection-decision-tree.md`, which forces a decade pin for anything "retro" (Y2K vs. Frutiger Aero vs. vaporwave are all "2000s" and easy to conflate).
2. **Pull the spec.** Every style has a full deep-spec file.
3. **Apply consistently, token-first.** Walk every primitive — button, input, card, nav, modal, table, tooltip, badge, toggle, loading/empty state — and repeat the signature move everywhere.
4. **Fix accessibility for that specific style.** Every flagship spec lists the exact contrast/scrim/motion-reduction corrections that style needs.
5. **Run the drift check before calling it done.**

```bash
python3 scripts/consistency_audit.py ./src --style glassmorphism
# exit 0 = clean · exit 1 = drift found
```

---

## The three scripts

All stdlib-only Python, no dependencies.

- **`generate_tokens.py`** — style → paste-ready tokens (CSS + Tailwind fragment)
- **`contrast_check.py`** — real WCAG AA/AAA luminance math (verified against known boundaries: black/white = 21.00:1, `#767676` on white = 4.54:1 AA pass, `#777` = 4.48:1 AA fail)
- **`consistency_audit.py`** — the "half-applied style" detector — flags hex/rgb colors, radius, shadow, and font-family literals that don't trace back to the applied style's token set

---

## Design ground rules

- **Research, don't invent.** Every cataloged style has a verified era, origin, and at least one real reference implementation.
- **No placeholders.** Every token is one that would genuinely ship.
- **Depth everywhere.** All 224 styles get the full implementation-grade treatment.
- **Single source of truth.** The JSON catalog (`scripts/style_catalog.json`) and every prose file agree by construction — prose is generated from the catalog, not hand-synced.
- **Known deviations:** six starter themes (glassmorphism, neubrutalism, claymorphism, neumorphism, brutalism, cyberpunk) are hand-tuned and deliberately left untouched by the generic generator — they beat the auto-generated output.

---

## Install

```bash
# Point Claude Code at the source directory directly:
design-language/
```

---

## Why it's interesting

This is a concrete example of what a well-structured Claude Code skill looks like at scale: 224 styles, each with a full implementation spec, token sets, accessibility corrections, do/don't, and confusable neighbors. The consistency audit script is a nice touch — it catches the exact drift that makes a styled UI look accidental instead of intentional. The decision tree for ambiguous vibes (e.g. "2000s nostalgia" → Y2K Futurism rather than vaporwave) is a good model for how an agent should disambiguate vague user requests.

It's a good reference for anyone building agent skills that need to produce consistent, production-quality output across a large design space.

---

**Links**

- GitHub: [https://github.com/ara-mkr/claude-artisan](https://github.com/ara-mkr/claude-artisan)
- License: MIT — [design-language/LICENSE.txt](https://github.com/ara-mkr/claude-artisan/blob/main/design-language/LICENSE.txt)
