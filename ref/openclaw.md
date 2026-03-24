---
created: 2026-03-24
author: Peter Steinberger (@steipete)
tags: [personal-ai, assistant, messaging, skills, memory, sandbox, open-source, telegram, whatsapp, imessage]
---

# OpenClaw

Open-source personal AI assistant that runs on your computer and integrates with messaging apps.

![OpenClaw](https://screenshotit.app/https://openclaw.ai)

## Links

- **Website**: https://openclaw.ai
- **GitHub**: https://github.com/openclaw/openclaw (333.4k ⭐)
- **Docs**: https://docs.openclaw.ai
- **Discord**: https://discord.com/invite/clawd
- **Skills Hub**: https://clawhub.com
- **Creator**: [@steipete](https://twitter.com/steipete)

## Overview

OpenClaw is "the AI that actually does things" — a 24/7 personal AI assistant that clears your inbox, sends emails, manages your calendar, checks you in for flights, and more. All from WhatsApp, Telegram, iMessage, Discord, Signal, or any chat app you already use.

Built as an open-source, self-hosted platform with persistent memory, skills system, and the ability to control your computer and services.

## Key Features

- **Messaging Integration**: WhatsApp, Telegram, iMessage, Discord, Signal, Slack, Google Chat
- **Persistent Memory**: Context persists 24/7, memory files track conversations and decisions
- **Skills System**: Extensible via SKILL.md files — community building and sharing skills
- **Persona Onboarding**: Configure identity, tone, preferences in AGENTS.md, SOUL.md, USER.md
- **Heartbeats**: Proactive background tasks, cron jobs, reminders
- **Sandbox**: Secure execution environment (file system, shell, browser, MCP)
- **Multi-Model**: Works with Claude, OpenAI, DeepSeek, Gemini, local models
- **Self-Hackable**: Can modify its own configuration and build new skills through conversation
- **Open Source**: MIT license, runs on your infrastructure (laptop, Pi, Mac mini, cloud)

## Use Cases

From community testimonials:
- Managing email, calendar, tasks from messaging apps
- Running coding agents (Claude Code, Codex) from phone
- Proactive reminders and daily briefings
- Automating workflows (Todoist, Linear, GitHub)
- Controlling smart home devices
- Creating websites and apps from phone
- Processing documents and data
- Building custom skills through conversation

## Architecture

- **Node.js** runtime
- **Gateway daemon** service
- **Workspace**: ~/.openclaw/workspace with AGENTS.md, SOUL.md, USER.md, memory/ folder
- **Skills**: Progressive loading — only what's needed, when needed
- **Channels**: Pluggable messaging platform integrations
- **Sub-agents**: Spawn isolated sessions for complex tasks

## Community Reception

Viral launch in January 2026 with testimonials describing it as:
- "First time I have felt like I am living in the future since ChatGPT" (@davemorin)
- "Feels like early AGI" (@tobi_bsf)
- "A megacorp like Anthropic or OpenAI could not build this" (@Dimillian)
- "Everything Siri was supposed to be. And it goes so much further" (@crossiBuilds)

## Relation to Similar Tools

- **[[deerflow]]**: ByteDance's SuperAgent harness — similar skills/sandbox architecture, but focused on research/coding tasks vs. personal assistant
- **[[alfred-portable-openclaw]]**: Portable fork by David Szabo-Stuban
- **Skills ecosystem**: Works with skills from broader agent tool community

## Related

- [[deerflow]]
- [[alfred-portable-openclaw]]
- [[telegram-topics-openclaw]]
- [[boris-cherny-claude-code-tips]]
- [[claude-code]]
- [[skill-vs-agents-vs-claude-md]]
