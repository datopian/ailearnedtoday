---
created: 2026-04-07
tags: [pkmpatterns, memory, long-context, mcp, local-first, knowledge-graph]
---

# MemPalace

Local-first AI memory system with palace-style structure, AAAK compression dialect, and MCP tools — highest LongMemEval score published.

![MemPalace GitHub](https://screenshotit.app/https://github.com/milla-jovovich/mempalace)

## Links

- **GitHub**: https://github.com/milla-jovovich/mempalace
- **License**: MIT
- **Benchmarks**: `benchmarks/BENCHMARKS.md`
- **Discord**: https://discord.com/invite/ycTQQCu6kn

## Overview

MemPalace is a local, open-source memory stack for AI agents. It stores **everything** (conversations, code, docs) and makes it findable through a structured "memory palace" and a custom compression dialect called **AAAK**. It is designed to work with both cloud models (via MCP) and local models, with no external APIs required.

**Headline**: "The highest-scoring AI memory system ever benchmarked. And it's free."

## Core Ideas

### 1. The Palace Structure

MemPalace adapts the ancient memory palace technique:

- **Wings** – People, projects, or topics (e.g., `wing_kai`, `wing_driftwood`)
- **Rooms** – Specific topics within a wing (e.g., `auth-migration`, `billing`)
- **Halls** – Memory types shared across wings:
  - `hall_facts` – decisions, locked choices
  - `hall_events` – sessions, milestones, debugging
  - `hall_discoveries` – breakthroughs
  - `hall_preferences` – habits, likes, opinions
  - `hall_advice` – recommendations, solutions
- **Closets** – Compressed summaries pointing to originals
- **Drawers** – Original verbatim files (convos, docs, code)
- **Tunnels** – Cross-wing links between the same room (e.g., `auth-migration` in person + project)

**Why it matters**: Structure alone boosts retrieval — tested on 22k+ real conversation memories:
- Search all closets: 60.9% R@10
- Wing filter: 73.1%
- Wing + hall: 84.8%
- Wing + room: 94.8% (**+34% improvement**)

> **The palace structure is the product.**

### 2. AAAK Compression Dialect

AAAK is a lossless shorthand dialect designed for AI agents:

- ~30x compression vs plain English
- Zero information loss
- Readable by any text model (Claude, GPT, Gemini, Llama, Mistral)
- No special decoder or fine-tuning required

Example (simplified):

English (~1000 tokens): team members, project, sprint, auth migration, decision rationale

AAAK (~120 tokens):

```text
TEAM: PRI(lead) | KAI(backend,3yr) SOR(frontend) MAY(infra) LEO(junior,new)
PROJ: DRIFTWOOD(saas.analytics) | SPRINT: auth.migration→clerk
DECISION: KAI.rec:clerk>auth0(pricing+dx) | ★★★★
```

AAAK lets an agent load **months of context in ~120 tokens** while preserving exact facts.

### 3. Local-First, API-Free

- Runs entirely on your machine
- Uses **ChromaDB** + **SQLite** for storage
- No cloud APIs required after install
- Works with cloud models via MCP or with fully local models

## Diagrammatic Summary

High-level architecture:

```text
          ┌─────────────────────────────┐
          │        Your Data           │
          │  - Project files (code)    │
          │  - Docs / notes            │
          │  - Chat transcripts        │
          └────────────┬───────────────┘
                       │  mempalace mine
                       ▼
            ┌──────────────────────┐
            │   Palace Builder     │
            │  - Detects people    │
            │  - Detects projects  │
            │  - Assigns wings     │
            └─────────┬────────────┘
                      │
        ┌─────────────┴─────────────────────────┐
        ▼                                       ▼
┌────────────────────┐                 ┌──────────────────────┐
│  Palace Structure  │                 │   AAAK Compressor    │
│  Wings / Rooms /   │                 │  Compress closets    │
│  Halls / Closets / │                 │  into AAAK text      │
│  Drawers / Tunnels │                 │                      │
└──────────┬─────────┘                 └──────────┬───────────┘
           │                                      │
           ▼                                      ▼
┌──────────────────────────────┐      ┌─────────────────────────┐
│   ChromaDB (Closets index)   │      │  Filesystem (Drawers)   │
│  - Semantic search           │      │  - Original transcripts │
│  - Wing/room filters         │      │  - Docs / code          │
└──────────┬───────────────────┘      └──────────┬──────────────┘
           │                                     │
           ▼                                     ▼
     ┌───────────────────────┐             ┌──────────────────────┐
     │  Knowledge Graph      │             │  MCP Server / CLI    │
     │  (SQLite)             │             │  - search            │
     │  - Temporal triples   │             │  - wake-up context   │
     └────────────┬──────────┘             │  - diary agents      │
                  │                        └─────────┬────────────┘
                  ▼                                  │
           ┌────────────────┐                        ▼
           │    AI Agent    │  <───────────────┬───────────────┐
           │  (Claude, GPT, │                  │               │
           │   local LLM)   │   context +      │   MCP tools   │
           └────────────────┘   search results └───────────────┘
```

## How You Use It

### Setup

```bash
pip install mempalace
mempalace init ~/projects/myapp

# Mine data
mempalace mine ~/projects/myapp          # code, docs, notes
mempalace mine ~/chats/ --mode convos    # Claude/ChatGPT/Slack exports
mempalace mine ~/chats/ --mode convos --extract general
```

### With Claude / ChatGPT / Cursor (MCP)

```bash
claude mcp add mempalace -- python -m mempalace.mcp_server
```

Then ask:

> "What did we decide about auth last month?"

Claude automatically calls `mempalace_search`, gets verbatim results, and answers. You almost never run `mempalace` commands manually.

### With Local Models

Two patterns:

1. **Wake-up context** — preload 170 tokens of critical facts:
   ```bash
   mempalace wake-up > context.txt
   # Paste into local model system prompt
   ```

2. **On-demand search** — query and inject results:
   ```bash
   mempalace search "auth decisions" > results.txt
   # Include results.txt in prompt
   ```

## Benchmarks

- **LongMemEval R@5 (raw)**: 96.6% (no API calls)
- **LongMemEval R@5 (hybrid + Haiku rerank)**: 100%
- **LoCoMo R@10**: 60.3%
- **Personal palace R@10**: 85%

Highest published LongMemEval result that requires **no API key, no cloud, no LLM** during retrieval.

## MCP Tools

MemPalace exposes **19 MCP tools**, including:

- `mempalace_status`, `mempalace_list_wings`, `mempalace_get_taxonomy`
- `mempalace_search`, `mempalace_add_drawer`, `mempalace_delete_drawer`
- Knowledge graph: `mempalace_kg_query`, `mempalace_kg_add`, `mempalace_kg_timeline`
- Agent diaries: `mempalace_diary_write`, `mempalace_diary_read`

## Related

- [[artem-grep-is-dead]]
- [[qmd]]
- [[economists-ai-adoption]]
- [[openclaw]]
- [[claude-dispatch]]
