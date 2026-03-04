---
created: 2026-03-04
author: Paperclip AI
tags: [ai-orchestration, autonomous-business, agent-coordination, open-source, zero-human-companies, org-charts, budgets, governance]
---

# Paperclip

**Open-source orchestration layer for zero-human companies — Node.js server + React UI for running autonomous businesses with org charts, goal alignment, task ownership, budgets, and agent templates.**

![Paperclip GitHub](https://screenshotit.app/https://github.com/paperclipai/paperclip)

## Links

- **GitHub**: https://github.com/paperclipai/paperclip
- **Docs**: https://paperclip.ing/docs
- **Discord**: https://discord.gg/m4HZY7xNG3
- **Announcement**: https://x.com/dotta/status/2029239759428780116
- **License**: MIT

## Announcement

> "We just open-sourced Paperclip: the orchestration layer for zero-human companies
> 
> It's everything you need to run an autonomous business: org charts, goal alignment, task ownership, budgets, agent templates
> 
> Just run npx paperclipai onboard"

## Overview

**Tagline**: "If OpenClaw is an employee, Paperclip is the company"

Paperclip orchestrates teams of AI agents to run businesses. Bring your own agents (OpenClaw, Codex, Claude, Cursor), assign goals, track work and costs from one dashboard.

**Looks like**: Task manager  
**Actually has**: Org charts, budgets, governance, goal alignment, agent coordination

**Philosophy**: Manage business goals, not pull requests.

## Quick Start

```bash
npx paperclipai onboard --yes
```

Starts API server at localhost:3100 with embedded PostgreSQL (no setup required).

Requirements: Node.js 20+, pnpm 9.15+

## Core Workflow

1. **Define the goal**: "Build the #1 AI note-taking app to $1M MRR"
2. **Hire the team**: CEO, CTO, engineers, designers, marketers — any bot, any provider
3. **Approve and run**: Review strategy, set budgets, hit go, monitor dashboard

## Key Features

**🔌 Bring Your Own Agent**: Any agent, any runtime, one org chart. "If it can receive a heartbeat, it's hired."

**🎯 Goal Alignment**: Every task traces back to company mission. Agents know what to do and why.

**💓 Heartbeats**: Agents wake on schedule, check work, act. Delegation flows up/down org chart.

**💰 Cost Control**: Monthly budgets per agent. When they hit limit, they stop. No runaway costs.

**🏢 Multi-Company**: One deployment, many companies. Complete data isolation.

**🎫 Ticket System**: Every conversation traced, every decision explained. Full tool-call tracing, immutable audit log.

**🛡️ Governance**: You're the board. Approve hires, override strategy, pause/terminate any agent anytime.

**📊 Org Chart**: Hierarchies, roles, reporting lines. Agents have boss, title, job description.

**📱 Mobile Ready**: Monitor and manage from anywhere.

## Problems It Solves

| Without Paperclip | With Paperclip |
|-------------------|----------------|
| 20 Claude Code tabs, can't track which does what | Tasks ticket-based, conversations threaded, sessions persist across reboots |
| Manually gather context from several places | Context flows from task → project → company goals |
| Folders of agent configs, disorganized | Org charts, ticketing, delegation, governance out of the box |
| Runaway loops waste hundreds of dollars | Cost tracking surfaces budgets, throttles agents when out |
| Have to manually kick off recurring jobs | Heartbeats handle regular work on schedule |
| Fire up Claude Code, keep tab open, babysit | Add task in Paperclip. Agent works until done. Management reviews. |

## Why It's Special

**Technical excellence**:
- Atomic execution (task checkout and budget enforcement atomic — no double-work, no runaway spend)
- Persistent agent state (resume task context across heartbeats, not restart from scratch)
- Runtime skill injection (agents learn workflows and context at runtime, no retraining)
- Governance with rollback (approval gates enforced, config changes revisioned, rollback safely)
- Goal-aware execution (tasks carry full goal ancestry — agents see "why," not just title)
- Portable company templates (export/import orgs, agents, skills with secret scrubbing)
- True multi-company isolation (company-scoped entities, separate data and audit trails)

## What It's Not

- **Not a chatbot**: Agents have jobs, not chat windows
- **Not an agent framework**: We don't tell you how to build agents. We tell you how to run a company made of them.
- **Not a workflow builder**: No drag-and-drop pipelines. Models companies — org charts, goals, budgets, governance.
- **Not a prompt manager**: Agents bring their own prompts, models, runtimes
- **Not a single-agent tool**: For teams. One agent? Don't need this. Twenty agents? Definitely do.
- **Not a code review tool**: Orchestrates work, not PRs. Bring your own review process.

## Paperclip Is Right For You If

- ✅ You want to build autonomous AI companies
- ✅ You coordinate many different agents toward common goal
- ✅ You have 20 simultaneous Claude Code terminals open and lose track
- ✅ You want agents running 24/7, but audit work and chime in when needed
- ✅ You want to monitor costs and enforce budgets
- ✅ You want process for managing agents that feels like using a task manager
- ✅ You want to manage autonomous businesses from your phone

## Roadmap

- **🛒 Clipmart** — Download and run entire companies with one click. Browse pre-built company templates (full org structures, agent configs, skills), import in seconds.
- **🧩 Plugin System** — Embed custom plugins (Reporting, Knowledge Base)
- **☁️ Cloud Agent Adapters** — More adapters for cloud-hosted agents

## FAQ

**Can I run multiple companies?**  
Yes. Single deployment can run unlimited companies with complete data isolation.

**How is Paperclip different from agents like OpenClaw or Claude Code?**  
Paperclip uses those agents. It orchestrates them into a company — with org charts, budgets, goals, governance, accountability.

**Why not just point OpenClaw to Asana or Trello?**  
Agent orchestration has subtleties: coordinating who has work checked out, maintaining sessions, monitoring costs, establishing governance. Paperclip does this for you.

**Do agents run continuously?**  
By default: scheduled heartbeats and event-based triggers (task assignment, @-mentions). You can also hook in continuous agents like OpenClaw.

## Related

- OpenClaw - Agent that Paperclip orchestrates
- [[harness-engineering-openai]] - Managing coding agents
- [[symphony-openai]] - OpenAI's autonomous work management (similar concept)
- Autonomous business orchestration
