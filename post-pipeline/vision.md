# Content Publishing System: Vision

## Goal

A personal system for rapid idea capture, refinement, and multi-platform publishing.

**Job story:** When I encounter something interesting or have a thought worth sharing, I want to capture it quickly, polish it with minimal friction, and publish it to relevant platforms — without manually logging into each one or copy-pasting between interfaces.

## The Two Parts

```
┌─────────────────────────┐         ┌─────────────────────────┐
│    PART 1: CAPTURE      │         │    PART 2: PUBLISH      │
│                         │         │                         │
│  Web clips              │         │  Markdown file          │
│  Voice memos            │         │         │               │
│  CLI quick notes        │────────▶│         ▼               │
│  Direct writing         │         │  Polished post(s)       │
│         │               │         │         │               │
│         ▼               │         │         ▼               │
│    Markdown file        │         │  Multi-platform         │
│                         │         │  distribution           │
└─────────────────────────┘         └─────────────────────────┘
```

### Part 1: Capture → Markdown

Various input methods all converge on a single format: a Markdown file in a local repository.

Possible inputs:
- Browser extension for web clipping
- Voice memo transcription
- CLI command for quick thoughts
- Direct file creation

**Status:** Out of scope for now.

### Part 2: Markdown → Published

Given a Markdown file, transform it into publishable content and distribute it across platforms.

Two sub-stages:
1. **Polish & Prepare** — Clean up prose, possibly create platform-appropriate variants (long-form, short-form, thread)
2. **Distribute** — Push to Substack, X, LinkedIn, Instagram, etc.

**Status:** Current focus. See [Post Pipeline](post-pipeline.md) for details.

## Example Use Case

"AI, Tried Today" — a learning-in-public journal about AI tools. Quick field notes captured throughout the day, polished into posts, distributed to Substack (primary) and social media (amplification).
