---
created: 2026-03-24
author: ByteDance
tags: [ai-agents, research, coding, super-agent, sandbox, skills, memory, subagents, open-source]
---

# DeerFlow

Open-source SuperAgent harness by ByteDance for deep research, coding, and creation.

![DeerFlow](https://screenshotit.app/https://deerflow.tech)

## Links

- **Website**: https://deerflow.tech
- **GitHub**: https://github.com/bytedance/deer-flow (41.1k ⭐)
- **License**: MIT
- **Sandbox**: https://github.com/agent-infra/sandbox

## Overview

DeerFlow is an open-source SuperAgent harness that researches, codes, and creates. With sandboxes, memories, tools, skills, and subagents, it handles tasks ranging from minutes to hours. Originally a deep research agent, it has evolved into a full-stack Super Agent.

## Key Features (DeerFlow 2.0)

- **Context Engineering**: Long/short-term memory for better understanding
- **Long Task Running**: Planning and sub-tasking — plans ahead, reasons through complexity, executes sequentially or in parallel
- **Extensible**: Skills and tools system — plug, play, or swap built-in tools
- **Persistent**: Sandbox with file system — read, write, run like a real computer
- **Flexible**: Multi-model support (Doubao, DeepSeek, OpenAI, Gemini, etc.)
- **Free**: MIT License, self-hosted, full control

## Agent Skills

Skills are loaded progressively — only what's needed, when it's needed. Built-in library includes:
- Deep search (biotech, computer science, physics)
- Frontend design
- Deploy (with scripts)

## Agent Runtime Environment

Docker-based secure sandbox that can execute commands, manage files, and run long tasks. Recommends [All-in-One Sandbox](https://github.com/agent-infra/sandbox) combining Browser, Shell, File, MCP, and VSCode Server in a single container.

Features: Isolated, Safe, Persistent, Mountable FS, Long-running

## Relation to OpenClaw

DeerFlow and [[openclaw]] share architectural similarities:
- Both use Skills mechanism for extensibility
- Both feature sandboxes, memory systems, and tool integration
- Both are MIT-licensed, self-hosted agent frameworks
- **Focus difference**: DeerFlow emphasizes research and coding tasks; OpenClaw is a personal assistant platform that integrates with messaging apps
- **Deployment**: DeerFlow runs task-oriented sessions; OpenClaw runs 24/7 as persistent assistant

## Related

- [[openclaw]]
- [[paperclip]]
- [[symphony-openai]]
- [[boris-cherny-claude-code-tips]]
