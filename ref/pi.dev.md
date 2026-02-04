---
created: 2026-02-04
author: Mario Zechner
tags: [coding-agent, terminal, ai, extensible, open-source]
---

# pi - Coding Agent

**There are many coding agents, but this one is mine.**

## Links

- **Website:** https://pi.dev/
- **GitHub:** https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent
- **npm:** https://www.npmjs.com/package/@mariozechner/pi-coding-agent
- **Discord:** https://discord.com/invite/3cU7Bz4UPx
- **Announcement:** https://x.com/badlogicgames/status/2018808723687546998

## Overview

Pi is a minimal terminal coding harness. A coding agent designed for customization and control, not dictating workflows.

**Tagline:** "There are many coding agents, but this one is mine."

**Install:**
```bash
npm install -g @mariozechner/pi-coding-agent
```

## Why pi?

**Philosophy:** Adapt pi to your workflows, not the other way around. 

Pi is aggressively extensible so it doesn't have to dictate your workflow. Features that other tools bake in can be built with extensions, skills, or installed from third-party pi packages.

**What it ships with:**
- Powerful defaults
- Minimal core
- 15+ providers, hundreds of models
- Tree-structured sessions
- Four modes: interactive, print/JSON, RPC, SDK

**What it deliberately doesn't ship with:**
- No MCP (build CLI tools with READMEs or add via extension)
- No sub-agents (build your own or install package)
- No permission popups (use containers or build custom flow)
- No plan mode (write to files or build via extension)
- No built-in to-dos (use TODO.md or build extension)
- No background bash (use tmux for observability)

## Key Features

**Extensibility:**
- TypeScript extensions with access to tools, commands, keyboard shortcuts, events, full TUI
- Skills: capability packages with instructions and tools, loaded on-demand
- Prompt templates: reusable prompts as Markdown files
- Themes: customize appearance
- Pi packages: bundle and share via npm or git

**Providers & Models:**
- 15+ providers: Anthropic, OpenAI, Google, Azure, Bedrock, Mistral, Groq, Cerebras, xAI, Hugging Face, Kimi For Coding, MiniMax, OpenRouter, Ollama, more
- Switch models mid-session with `/model` or `Ctrl+L`
- Cycle favorites with `Ctrl+P`
- Add custom providers via `models.json` or extensions

**Sessions:**
- Tree-structured history (navigate with `/tree`)
- All branches in single file
- Filter by message type, bookmark entries
- Export to HTML or share via GitHub gist

**Context Engineering:**
- Minimal system prompt + full extensibility = real context engineering
- `AGENTS.md` - project instructions from multiple locations
- `SYSTEM.md` - replace or append to system prompt per-project
- **Compaction:** auto-summarizes older messages, fully customizable
- **Skills:** progressive disclosure without busting prompt cache
- **Dynamic context:** extensions inject messages, filter history, implement RAG

**Queuing:**
- Submit messages while agent works
- `Enter` = steering message (interrupts remaining tools)
- `Alt+Enter` = follow-up (waits until finish)

**Extensions (50+ examples):**
- Sub-agents, plan mode, permission gates, path protection
- SSH execution, sandboxing, MCP integration
- Custom editors, status bars, overlays
- Yes, [Doom runs](https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent/examples/extensions/doom-overlay/)

**Packages:**
- Install from npm or git: `pi install npm:@foo/pi-tools`
- Pin versions, update all, list, configure
- Test without installing: `pi -e git:github.com/user/repo`
- Share with `pi-package` keyword

## Four Modes

1. **Interactive:** Full TUI experience
2. **Print/JSON:** `pi -p "query"` for scripts, `--mode json` for event streams
3. **RPC:** JSON protocol over stdin/stdout for non-Node integrations
4. **SDK:** Embed pi in your apps (see [clawdbot](https://github.com/clawdbot/clawdbot))

## Keyboard Shortcuts

- `esc` - interrupt
- `ctrl+c` - clear (twice to exit)
- `ctrl+k` - delete line
- `shift+tab` - cycle thinking
- `ctrl+p` - cycle models
- `ctrl+o` - expand tools
- `ctrl+t` - toggle thinking
- `/` - commands
- `!` - run bash
- Drop files to attach

## New Home Announcement

**Date:** February 3, 2026  
**By:** Mario Zechner (@badlogicgames)

"People of pi. I have good news. pi has finally found its home on pi.dev, thanks to the gracious domain donation by the wonderful people at @ssh_exe_dev. Check out their niffty VM offerings at exe.dev"

Domain donated by exe.dev (https://exe.dev)

**Engagement:** 468 likes, 32 reposts, 13.6K views

## Community

- **Issues:** [GitHub](https://github.com/badlogic/pi-mono/issues)
- **Discord:** [Community server](https://discord.com/invite/nKXTsAcmbT)
- **Docs:** [README](https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent#readme) and [docs/](https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent/docs)

## Technical Details

- MIT License
- By Mario Zechner & contributors
- Terminal-based, minimal design
- Full programmatic access via SDK/RPC
- Real-world integration example: clawdbot

## Related

- [Blog post: Why pi?](https://mariozechner.at/posts/2025-11-30-pi-coding-agent/)
- [Why you don't need MCP](https://mariozechner.at/posts/2025-11-02-what-if-you-dont-need-mcp/)
