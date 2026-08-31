---
created: 2026-08-31
author: Siqi Chen (@blader)
tags: [agent-skills, ai-writing, humanizer, claude-code, codex, cursor, writing-tools, prompt-engineering]
star_count: 39219
star_timestamp: 2026-08-31T15:51:24Z
---

# Humanizer

> Agent skill that removes signs of AI-generated writing from text.

![Humanizer on GitHub](https://screenshotit.app/https://github.com/blader/humanizer)

## Links

- **GitHub**: https://github.com/blader/humanizer
- **skills.sh**: https://skills.sh/blader/humanizer
- **Author**: Siqi Chen (@blader)
- **License**: MIT
- **Stars**: 39,219 · **Forks**: 3,428 (as of 2026-08-31)

## Overview

Humanizer rewrites AI-sounding text so it reads like a person wrote it, without changing what it says. It is just Markdown, so it runs in any agent that supports skills — Claude Code, Codex, Cursor.

The method is grounded in an external source rather than the author's taste: it works from the 35 patterns in Wikipedia's ["Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), maintained by WikiProject AI Cleanup. Humanizer makes a first rewrite pass without treating the original structure as fixed, then checks the draft against those 35 patterns and against the original claims, and rewrites again wherever it still sounds artificial.

It does not invent facts. Any name, number, date, quote, or citation must come from the source or the writer — if a needed detail is missing, it asks rather than filling in. Point it at a file and it changes only the prose, leaving code, data, frontmatter, and link targets alone. When you paste text it shows its work: the first rewrite plus a short critique of what still sounds off, then the final version.

## The 35 patterns (grouped)

- **Content** (1–6): inflated importance, name-dropping, shallow `-ing` analysis, sales language, vague sources, formulaic "despite challenges" outlook.
- **Language & grammar** (7–13): overused AI words, avoiding "is/are", "not X but Y", forced rule of three, false "from X to Y" ranges, drifting names / repeated sentence openings, needless passive voice.
- **Style** (14–19, 26–35): em/en dashes, over-bolding, bold mini-headings in lists, title case, emojis, curly quotes, hyphen-pair pile-ups, fake "at its core" truths, "let's dive in" announcements, headings echoed by their first line, forced punchline fragments, formulaic sayings, "honestly?" openings, answering objections nobody raised, rejecting fake alternatives.
- **Chatbot** (20–22): leftover "I hope this helps!", knowledge-limit disclaimers, "Great question!" over-agreeableness.
- **Filler & hedging** (23–25): "in order to" / "due to the fact that", stacked qualifiers, "the future looks bright" endings.

## Voice matching

Paste 2–3 paragraphs of your own writing alongside the text to humanize and Humanizer follows that sample's rhythm, word choice, punctuation, and deliberate quirks instead of its default neutral style. For personal writing it keeps the writer's style; technical and reference prose stays plain.

## Install

```bash
# Skills CLI (any supported agent)
npx skills add blader/humanizer --global

# Claude Code plugin (2.1.142+)
/plugin marketplace add blader/humanizer
/plugin install humanizer@humanizer
```

Then `/humanizer` and paste text, or "humanize the prose in docs/launch-post.md".

## Why interesting

- **Externally anchored.** The rule set is a public, community-maintained Wikipedia page, not one person's ear. Easy to audit, argue with, and extend.
- **Two-pass with a check step.** Draft, critique against the patterns and the original claims, rewrite. Shows its work.
- **Fact-safe by construction.** Refuses to invent the details a de-slopped rewrite tends to smuggle in.
- **De-slopping is a floor, not the finish.** Removing tells can still leave prose that sounds like nobody. Rufus Pollock's [[soundlikeme]] takes the next step — matching a specific person's voice, with an eval harness that tests whether it worked — and treats tell-removal as table stakes.

## Related

- [[soundlikeme]] — Rufus Pollock's skill for sounding like *you* (not just un-AI), with a blind-judged eval harness.
- [[voice-dna]]
- [[llms-erase-linguistic-diversity]]
- [[moc-best-ai-skills]] — curated best-of AI coding-agent skills.

## By

Siqi Chen (@blader)
