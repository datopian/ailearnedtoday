---
created: 2026-08-17
author: Paul Bakaus
tags: [design, claude-code, cursor, coding-agents, design-systems, frontend, ai-slop, plugin]
star_count: 64289
star_timestamp: 2026-08-31T15:51:24Z
---

# Impeccable

> The missing design vocabulary for agents.

![Impeccable — the missing design vocabulary for agents](https://screenshotit.app/https://impeccable.style/)

**Website:** [impeccable.style](https://impeccable.style/)
**GitHub:** [github.com/pbakaus/impeccable](https://github.com/pbakaus/impeccable)
**Stars:** 64k | **Forks:** 3.4k | **License:** Apache 2.0 · *(star_count 64,289 as of 2026-08-31)*

## What it is

A design language and agent skill from Paul Bakaus that strips the "slop" from AI-generated interfaces. It gives coding agents (Claude Code, Cursor, GitHub Copilot, Gemini CLI, Codex CLI, Grok Build, Antigravity, OpenCode, Pi) precise commands to steer design output and iterates visual variants live in the product.

The pitch: before/after demo after demo — generic AI beige, purple gradients, ghost cards, side-tab borders, vague headlines, too many fields — replaced with intentional design: sharp typography, clear hierarchy, deliberate color, real content.

## How it works

**Hooks inspect UI edits in real time.** Each edit gets run through slop detectors; findings come back to the agent; the agent corrects on the second pass. The same detector can fail a PR in CI.

**Per-harness builds.** Same skill, recompiled per target — builds for models with known tells carry extra slop rules banning that model's habits (Gemini build kills image-on-hover motion; Codex build refuses ghost-cards and over-rounding).

**Command vocabulary.** `/polish`, `/distill`, `/clarify` — and the more thorough mode pushes through multiple iterations.

**DESIGN.md integration.** Impeccable reads a project's `DESIGN.md` (the Google Stitch-compatible spec — YAML design tokens + markdown rationale) so the agent knows what a color is for, can validate against WCAG, and doesn't guess intent.

## Install

**Claude Code:**

```bash
/plugin marketplace add pbakaus/impeccable
```

Then open `/plugin` and install Impeccable from the list.

**npm / other harnesses:**

```bash
npx impeccable install
```

Requires Node 22.12+.

**GitHub Copilot:** Built in — enable under Settings → Experimental.

## Tools in the ecosystem

- **Chrome extension** — run the detector overlay on any page: your staging, a competitor, anything in the browser. [Install from Chrome Web Store](https://chromewebstore.google.com/detail/impeccable/bdkgmiklpdmaojlpflclinlofgjfpabf)
- **CLI for CI** — `npx impeccable detect src/` in a PR check. 59 deterministic rules. JSON output, exit codes for build gates. [View on npm](https://www.npmjs.com/package/impeccable)
- **Newsletter** — the design thinking behind new commands and anti-patterns, in long form. [Read the newsletter](https://impeccablestyle.substack.com/) · [Follow @impeccable_ai on X](https://x.com/impeccable_ai)

## Why interesting

This is the most-watched design-for-agents project right now (61k stars, 3.7k forks). It sits at the intersection of several things the repo already tracks: the slop-problem in AI-generated UI (cf. [[variant]], [[frontend-slides]]), design-system-as-context-for-agents (cf. [[design-md]]), and the emerging category of agent-native design tools (cf. [[claude-design]], [[stitch-google]], [[aura-build]]).

The hook-based detector model is the interesting technical piece — rather than asking the agent to "be less slop" (which doesn't work), it intercepts edits and enforces rules deterministically, then hands the findings back. Same idea as Vercel's agent lint rules [[vercel-product-design-agents]], but productized and broad.

## Related

- [[design-md]] — the DESIGN.md spec Impeccable reads for design tokens
- [[variant]] — AI UI design tool via endless scroll; "show, don't tell" philosophy
- [[frontend-slides]] — Claude Code skill for beautiful HTML presentations; anti-AI-slop curation
- [[claude-design]] — Anthropic Labs prototype/slides/one-pagers by talking to Claude
- [[stitch-google]] — Google Stitch, AI UI design (DESIGN.md origin)
- [[aura-build]] — Aura Build, AI design agent
- [[typevibe]] — TypeVibe, AI typography tool
- [[vercel-product-design-agents]] — Vercel's agent lint rules and design evals
- [[mockdown.design]] — ASCII wireframe editor, AI-readable plain text layouts
- [[whizz-ai-design-prompts]] — 10 Claude prompts for Apple-level design systems

## By

Paul Bakaus ([@pbakaus](https://twitter.com/pbakaus))
