---
created: 2026-04-25
author: chopratejas
tags: [context-optimization, compression, agents, tool-outputs, logs, rag, memory, local-first]
---

# Headroom

Context optimization layer for LLM apps: compresses what agents read (tool outputs, logs, RAG, file reads) while preserving accuracy.

![Headroom docs](https://screenshotit.app/https://headroom-docs.vercel.app/docs)

## Links

- **GitHub**: https://github.com/chopratejas/headroom (1.5k ⭐, Apache-2.0)
- **Docs**: https://headroom-docs.vercel.app/docs

## Overview

Headroom strips boilerplate and keeps signal — **losslessly and locally** — before context reaches the model. It targets high-volume agent inputs like JSON tool outputs, build/test logs, search results, diffs, and source code.

## How it fits (one line)

Agent/App → (tool outputs, logs, DB reads, RAG chunks, files) → **Headroom** → LLM provider.

## Notable features

- **Wrap existing coding agents**: `headroom wrap claude|codex|cursor|aider|copilot`
- **Proxy mode**: run as a local proxy for zero-code integration
- **Content-aware compressors**: JSON, code (AST-aware), logs, text, diffs, search results, images
- **CCR (reversible / lossless compression)**: compress aggressively but allow retrieval of originals
- **Local-first**: no data egress; millisecond compression latency
- **Cross-agent memory + learning**: mines failed sessions and can write corrections to CLAUDE.md / AGENTS.md / GEMINI.md

## Numbers (as marketed)

- ~87% token reduction on example log debugging (10,144 → 1,260) with identical answer.

## Related

- [[openclaw]]
- [[cloudflare-dynamic-workers]]
- [[deerflow]]
- [[mempalace]]
