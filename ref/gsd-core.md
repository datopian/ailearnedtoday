---
created: 2026-06-28
author: Open GSD
tags: [ai-coding, agents, context-engineering, spec-driven-development, cli, open-source]
---

# GSD Core

Git. Ship. Done.

![GSD Core](https://screenshotit.app/https://github.com/open-gsd/gsd-core)

## Links

- **GitHub**: https://github.com/open-gsd/gsd-core
- **NPM**: https://www.npmjs.com/package/@opengsd/gsd-core
- **Docs**: https://github.com/open-gsd/gsd-core/tree/main/docs
- **Discord**: https://discord.gg/mYgfVNfA2r

## Overview

GSD Core is a lightweight context-engineering and spec-driven development system for AI coding agents. It is designed to keep the main session lean by pushing research, planning, execution, and verification into fresh-context subagents.

The core idea is a repeatable five-step loop: discuss, plan, execute, verify, and ship. That makes it closer to a disciplined project workflow than a generic prompt pack, with artifacts and phase boundaries intended to reduce context rot on larger tasks.

## Key Features

- **Multi-runtime support**: Claude Code, OpenCode, Gemini CLI, Kimi CLI, Kilo, Codex, Copilot, Cursor, Windsurf, and others
- **Fresh-context execution**: heavy work runs in subagents with clean context windows
- **Phase loop**: discuss, plan, execute, verify, ship
- **Installer-first setup**: `npx @opengsd/gsd-core@latest`
- **Project bootstrap**: `/gsd-new-project` to start a new workflow
- **Documentation-driven**: tutorials, how-tos, reference docs, and architecture notes

## Use Cases

- Orchestrating multi-step coding tasks without letting the main chat get bloated
- Running spec-driven feature work with explicit planning and verification
- Standardizing how teams use different coding agents across runtimes
- Keeping durable project context through structured artifacts instead of ad hoc prompts

## Why It Matters

GSD Core targets a common failure mode in agentic coding: once a project grows, context fills up, quality drops, and the agent starts to drift. Its answer is to treat the agent workflow itself as a process that can be structured, repeated, and verified.

That makes it interesting both as a tooling layer and as an example of the broader shift from prompt engineering toward context engineering.
