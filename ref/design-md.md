---
created: 2026-04-23
author: Google Labs
tags: [designapps, design-systems, spec, agents, designmd]
---

# DESIGN.md (spec)

Open specification for describing a visual identity to coding agents via design tokens + rationale.

![design.md GitHub repo](https://screenshotit.app/https://github.com/google-labs-code/design.md)

## Links

- **Repo**: https://github.com/google-labs-code/design.md
- **Spec**: https://github.com/google-labs-code/design.md/blob/main/docs/spec.md
- **Announcement**: https://x.com/stitchbygoogle/status/2046624729403142320

## Announcement (verbatim)

> Today, we’re open-sourcing the draft specification for DESIGN.md, so it can be used across any tool or platform. We’re also adding new capabilities. DESIGN.md lets you easily export and import your design rules from project to project. Instead of guessing intent, agents know exactly what a color is for and can even validate their choices against WCAG accessibility rules. Watch David East break down this shared visual language in action👇. New capabilities and links in 🧵

## Overview

DESIGN.md is a format specification for a single file that combines:

- **YAML front matter**: machine-readable design tokens (colors, typography, spacing, components, etc.)
- **Markdown prose**: human-readable rationale and guidance for how to apply the system

Goal: give agents a **persistent, structured understanding** of a design system so they can produce consistent UI and avoid guessing intent.

## Tooling

The repo includes CLI tooling to:

- **Lint** a DESIGN.md (including WCAG contrast checks)  
  `npx @google/design.md lint DESIGN.md`

- **Diff** two DESIGN.md files for token/prose regressions  
  `npx @google/design.md diff DESIGN.md DESIGN-v2.md`

## Related

- [[aura-build]]
- [[stitch-google]]
- [[claude-design]]
- [[variant]]
- [[design-pkm-tags]]
