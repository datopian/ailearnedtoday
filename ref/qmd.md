---
created: 2026-03-03
author: Tobias Lütke
tags: [search, local-search, knowledge-management, obsidian, qmd, vector-search, bm25, hybrid-search, llm-tools, cli]
---

# QMD - Query Markup Documents

**Local search engine by Tobias Lütke (Shopify CEO) for markdown notes, docs, and knowledge bases — combines BM25 full-text search, vector semantic search, and LLM re-ranking, all running locally.**

![QMD GitHub repo](https://screenshotit.app/https://github.com/tobi/qmd)

## Links

- **GitHub**: https://github.com/tobi/qmd
- **npm**: @tobilu/qmd
- **Author**: Tobias Lütke (@tobi), CEO of Shopify
- **License**: MIT

## Overview

QMD is an on-device search engine for everything you need to remember. Index your markdown notes, meeting transcripts, documentation, and knowledge bases. Search with keywords or natural language. Ideal for agentic flows.

**Tagline**: "mini cli search engine for your docs, knowledge bases, meeting notes, whatever. Tracking current sota approaches while being all local"

**Made in Canada**

## Key Features

### Three Search Modes

1. **BM25 (qmd search)** - Fast keyword search
   - Deterministic full-text search
   - Like grep, but scores by relevance
   - How often word appears + how rare it is across documents
   - Short note mentioning "sleep" 5x scores higher than 10k-word file with one mention
   - No AI, no embeddings — just math

2. **Semantic (qmd vsearch)** - Vector search
   - Uses embeddings to find meaning
   - Search for concepts even if exact words aren't there
   - Example: "couldn't sleep, bad night" finds "bedtime discipline goal"

3. **Hybrid (qmd query)** - Best quality
   - Combines BM25 + Vector + Query Expansion + Re-ranking
   - Original query gets ×2 weight
   - LLM re-ranks top 30 candidates
   - Position-aware blending (preserves exact matches at top)

## Architecture

```
User Query
  │
  ├─► Query Expansion (fine-tuned LLM) → 2 alternative queries
  │   └─► Original Query (×2 weight)
  │
  ├─► Each query → BM25 + Vector Search in parallel
  │
  ├─► RRF Fusion (k=60)
  │   ├─► Top-rank bonus: +0.05 for #1, +0.02 for #2-3
  │   └─► Top 30 candidates
  │
  ├─► LLM Re-ranking (yes/no + logprobs)
  │
  └─► Position-Aware Blend
      ├─► Rank 1-3: 75% RRF / 25% reranker (preserve exact matches)
      ├─► Rank 4-10: 60% RRF / 40% reranker
      └─► Rank 11+: 40% RRF / 60% reranker
```

**Why position-aware blending**: Pure RRF can dilute exact matches when expanded queries don't match. Top-rank bonus preserves documents scoring #1 for original query.

## GGUF Models (Local, Auto-Downloaded)

Three models cached in `~/.cache/qmd/models/`:

| Model | Purpose | Size |
|-------|---------|------|
| embeddinggemma-300M-Q8_0 | Vector embeddings | ~300MB |
| qwen3-reranker-0.6b-q8_0 | Re-ranking | ~640MB |
| qmd-query-expansion-1.7B-q4_k_m | Query expansion (fine-tuned) | ~1.1GB |

All via node-llama-cpp, downloaded from HuggingFace on first use.

## Quick Start

```bash
# Install globally
npm install -g @tobilu/qmd
# or
bun install -g @tobilu/qmd

# Create collections
qmd collection add ~/notes --name notes
qmd collection add ~/Documents/meetings --name meetings

# Add context (key feature!)
qmd context add qmd://notes "Personal notes and ideas"
qmd context add qmd://meetings "Meeting transcripts and notes"

# Generate embeddings
qmd embed

# Search
qmd search "project timeline"      # Fast keyword search
qmd vsearch "how to deploy"        # Semantic search
qmd query "quarterly planning"     # Hybrid + reranking (best)

# Get documents
qmd get "meetings/2024-01-15.md"
qmd get "#abc123"                   # By docid from search results
qmd multi-get "journals/2025-05*.md"  # Glob pattern
```

## Key Feature: Context Tree

**Critical for LLMs**: Context adds descriptive metadata to collections and paths, helping search understand your content. Each piece of context returned when matching sub-documents are found.

```bash
qmd context add qmd://notes "Personal notes and ideas"
qmd context add qmd://notes/work "Work-related notes"
qmd context add / "Knowledge base for my projects"  # Global
```

This works as a tree. "Don't sleep on it!" — per QMD docs.

## Smart Chunking

Instead of hard token boundaries, QMD uses scoring algorithm to find natural markdown break points:

| Pattern | Score | Description |
|---------|-------|-------------|
| # Heading | 100 | H1 - major section |
| ## Heading | 90 | H2 - subsection |
| ``` | 80 | Code block boundary |
| --- / *** | 60 | Horizontal rule |
| Blank line | 20 | Paragraph boundary |
| - item | 5 | List item |

**Algorithm**:
- When approaching 900-token target, search 200-token window before cutoff
- Score each break point: `finalScore = baseScore × (1 - (distance/window)² × 0.7)`
- Cut at highest-scoring break point
- Squared distance decay: heading 200 tokens back (score ~30) still beats line break at target (score 1)

**Code fence protection**: Break points inside code blocks ignored — code stays together.

**Chunks**: ~900 tokens with 15% overlap, stored with hash (document), seq (chunk number), pos (character position).

## For AI Agents

### CLI Integration

Designed for agentic workflows:

```bash
# Structured results for LLM
qmd search "authentication" --json -n 10

# List all relevant files above threshold
qmd query "error handling" --all --files --min-score 0.4

# Retrieve full document content
qmd get "docs/api-reference.md" --full
```

### MCP Server

Exposes Model Context Protocol server for tighter integration:

**Tools**:
- `qmd_search` - Fast BM25 keyword search
- `qmd_vector_search` - Semantic vector search
- `qmd_deep_search` - Deep search with query expansion and reranking
- `qmd_get` - Retrieve document by path or docid
- `qmd_multi_get` - Retrieve multiple documents by glob/list/docids
- `qmd_status` - Index health and collection info

**Claude Code integration**:
```bash
claude marketplace add tobi/qmd
claude plugin add qmd@qmd
```

Or manual config in `~/.claude/settings.json`:
```json
{
  "mcpServers": {
    "qmd": {
      "command": "qmd",
      "args": ["mcp"]
    }
  }
}
```

### HTTP Transport

For shared, long-lived server (avoids repeated model loading):

```bash
# Foreground
qmd mcp --http  # localhost:8181

# Background daemon
qmd mcp --http --daemon  # Writes PID to ~/.cache/qmd/mcp.pid
qmd mcp stop
qmd status  # Shows "MCP: running (PID ...)" when active
```

LLM models stay loaded in VRAM across requests. Embedding/reranking contexts disposed after 5 min idle, recreated on next request (~1s penalty).

Endpoints:
- `POST /mcp` — MCP Streamable HTTP (JSON responses, stateless)
- `GET /health` — Liveness check with uptime

## Score Interpretation

| Score | Meaning |
|-------|---------|
| 0.8 - 1.0 | Highly relevant |
| 0.5 - 0.8 | Moderately relevant |
| 0.2 - 0.5 | Somewhat relevant |
| 0.0 - 0.2 | Low relevance |

## Data Storage

Index stored in: `~/.cache/qmd/index.sqlite`

**Schema**:
- `collections` — Indexed directories with name and glob patterns
- `path_contexts` — Context descriptions by virtual path (qmd://...)
- `documents` — Markdown content with metadata and docid (6-char hash)
- `documents_fts` — FTS5 full-text index
- `content_vectors` — Embedding chunks (hash, seq, pos, 900 tokens each)
- `vectors_vec` — sqlite-vec vector index (hash_seq key)
- `llm_cache` — Cached LLM responses (query expansion, rerank scores)

## Requirements

- Node.js >= 22 or Bun >= 1.0.0
- macOS: Homebrew SQLite (for extension support)
  ```bash
  brew install sqlite
  ```

## Why It Matters

**For knowledge workers**:
- Fast, local search over all notes/docs
- Semantic search finds concepts without exact keywords
- Context tree helps AI make better document selections

**For AI agents**:
- MCP integration for Claude Code, Claude Desktop
- JSON/files output formats for programmatic use
- All local — no API calls, no rate limits

**For Obsidian users**:
- Perfect complement to Obsidian vault search
- Works with sync (vault updates → re-index)
- Can power advanced AI workflows (see [[artem-grep-is-dead]])

## Output Formats

**Default** (colorized CLI):
```
docs/guide.md:42 #a1b2c3
Title: Software Craftsmanship
Context: Work documentation
Score: 93%

This section covers the **craftsmanship** of building
quality software with attention to detail.
```

**Other formats**:
- `--files` — `docid,score,filepath,context`
- `--json` — JSON with snippets
- `--csv` — CSV output
- `--md` — Markdown output (for LLM context)
- `--xml` — XML output

## Comparison: Grep vs BM25 vs Semantic

**Example search for "sleep"**:

**Grep** (200 files):
- Finds all files containing "sleep"
- Even finds `sleep()` programming command
- No relevance ranking
- Pure string matching

**BM25** (2 seconds):
- Reflection about sleep quality
- Experiment with tracking sleep fragmentation
- Sleep interrupted at 3am
- Scored by relevance

**Semantic** (instant):
- Query "couldn't sleep, bad night"
- Finds "bedtime discipline goal" set years ago
- 4 of 5 results don't contain search words at all
- Explores meaning beyond keywords

**Hybrid** (qmd query):
- Ranks sleep quality improvement at 89%
- Sleep interrupted at 3am at 51%
- Health sleep optimization at 42%
- Best ranking of all

## Use Cases

- Personal knowledge management (Obsidian vaults)
- Documentation search for development teams
- Meeting notes and transcripts archive
- Research notes and citations
- AI agent memory/context layer
- Any markdown-based knowledge base

## Technical Details

- Built with Node.js/TypeScript
- SQLite for indexing (FTS5 for full-text)
- sqlite-vec for vector storage
- node-llama-cpp for local LLM inference
- Runs entirely offline after model download

## Related

- [[artem-grep-is-dead]] - Using QMD with Claude Code and Obsidian for persistent context
- [[obsidian]] - Note-taking app commonly used with QMD
- Local-first tools
- Knowledge management
- AI agent memory systems

## By

Tobias Lütke (@tobi), CEO of Shopify
