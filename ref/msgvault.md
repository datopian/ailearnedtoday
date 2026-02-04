---
created: 2026-02-04
author: Wes McKinney
tags: [email, local-first, duckdb, go, mcp, search]
---

# msgvault

**Archive a lifetime of email and chat. Offline search, analytics, and AI query over your full message history. Powered by DuckDB.**

## Links

- **GitHub:** https://github.com/wesm/msgvault
- **Announcement:** https://x.com/wesmckinn/status/2018303622145065455
- **Author:** [Wes McKinney](https://wesmckinney.com) (@wesmckinn)

## Overview

Local-first email and chat archive system built by Wes McKinney (creator of pandas, Apache Arrow).

**Key Features:**
- Archive Gmail, chat messages locally
- Lightning-fast search powered by DuckDB
- Terminal UI for browsing
- MCP (Model Context Protocol) server for AI agent integration
- Single Go binary (easy deployment)
- Open source (MIT License)

**Tech Stack:**
- **Language:** Go
- **Database:** DuckDB (analytical queries)
- **Interface:** Terminal UI
- **AI Integration:** MCP server

**Scale:**
- Handles 2M+ emails
- 150K+ attachments
- 20 years of Gmail history

## Why Interesting

1. **Local-first philosophy** - Own your data, no vendor lock-in
2. **DuckDB for email** - Analytical database enables complex queries on structured email data
3. **MCP integration** - AI agents can query email archives directly
4. **Built by data infrastructure expert** - Wes McKinney has deep experience with pandas, Arrow
5. **Single binary** - No complex setup, just download and run

## Context

**Posted:** February 2, 2026  
**Engagement:** 705 stars (as of Feb 4), 4.3K likes, 350K+ views

**Quote from announcement:**
> "I've used Gmail for 20 years. Almost 2M emails, 150K attachments. Rather than let Google hold my data hostage, I built msgvault: local-first email archive with a terminal UI and MCP server, powered by DuckDB. Open source, single Go binary."

## Related

- DuckDB: https://duckdb.org
- Model Context Protocol (MCP): https://modelcontextprotocol.io
- Apache Arrow: https://arrow.apache.org
