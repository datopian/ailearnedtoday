---
created: 2026-08-31
author: Rufus Pollock
tags: [agent-skills, ai-writing, voice-matching, claude-code, codex, cursor, writing-tools, evals]
star_count: 2
star_timestamp: 2026-08-31T15:51:24Z
---

# Sound Like Me

> An agent skill that makes AI-assisted writing sound like *you* — plus the eval harness that proves whether it actually does.

![Sound Like Me on GitHub](https://screenshotit.app/https://github.com/rufuspollock/soundlikeme)

## Links

- **GitHub**: https://github.com/rufuspollock/soundlikeme
- **Author**: Rufus Pollock
- **Stars**: 2 (as of 2026-08-31)

## Overview

Two problems hide inside "AI writing sounds like AI", and most tools conflate them:

1. **Removing AI tells.** A floor. The patterns are public and well catalogued — [[humanizer]] and others already do this well.
2. **Sounding like a specific person.** The actual work, and much less solved.

A draft with every tell removed can still sound like nobody. Over-editing then produces its own detectable style — clipped, tidy, opinion-flattened — a downgrade from the slop it replaced. `soundlikeme` does the second thing and treats the first as table stakes.

You give it three to five samples of your own writing; it builds a voice profile; `polish` rewrites drafts against that profile. It ships with an eval harness of real fixtures where blind judges pick which version sounds more like the author — the "being a noob" fixture was chosen 2-0 in both orderings.

## Install

```bash
npx skills add rufuspollock/soundlikeme/skills/soundlikeme
```

Works in Claude Code, Cursor, GitHub Copilot, and other agents supporting the agentskills.io spec.

## Related

- [[humanizer]] — Siqi Chen's tell-removal skill (the floor this builds on).
- [[voice-dna]]
- [[moc-best-ai-skills]]

## By

Rufus Pollock
