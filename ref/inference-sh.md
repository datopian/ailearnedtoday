---
created: 2026-02-04
tags: [ai-agents, platform, runtime, infrastructure, durable-execution, observability]
---

# inference.sh

**The agent runtime for production AI agents.**

![inference.sh homepage](https://screenshotit.app/https://inference.sh/)

## Links

- **Website:** https://inference.sh/
- **Docs:** https://inference.sh/docs
- **GitHub:** https://github.com/inference-sh
- **Discord:** https://discord.gg/RM77SWSbyT

## Overview

inference.sh is a production runtime platform for AI agents. Instead of building infrastructure (queues, retries, state persistence, auth), you focus on what your agent does.

**Tagline:** "run reliable agents in production without reinventing the platform."

## Key Features

**Runtime Layer:**
- **Durable execution** - Event-driven, state persists across invocations
- **Tool orchestration** - 150+ apps as tools via one API
- **Observability** - Real-time streaming and logs for every action
- **Pay-per-execution** - No idle costs

**Agent Primitives:**
- **Deep-agents** - Agents spawn sub-agents as tools
- **Human-in-the-loop** - Approval workflows
- **Widgets** - Dynamic UI generation (HTML/CSS inline)
- **Webhooks** - Async API callbacks
- **Client tools** - Execute on user's system
- **Memory** - Built-in key-value store per conversation
- **Planning** - Multi-step plans, resume after interruption
- **Structured output** - Typed results

**Infrastructure:**
- **App library** - 150+ pre-built tools
- **OAuth integrations** - Real oauth with token refresh, encrypted storage
- **x402 payments** - Agentic payments protocol for agents
- **Self-hosted option** - Deploy in your VPC or on-prem
- **Multiple models** - OpenAI, Anthropic, Google, Meta, Mistral, DeepSeek, 500+ more

## Why It Exists

Common developer pain points:
- "The agent framework is not the moat. The specialized tools are."
- "6 hours debugging with zero error logs."
- "Agent works in 2-minute quanta, long tasks need pipeline thinking."
- "Users thought it crashed. If they see internal monologue, they wait."
- "Spent 10 hours deploying on EC2... $13/mo per agent. Serverless: 10 cents."

## Philosophy

**"Trust is not a feature. It is a design constraint."**

Automation should never be a black box. Systems should fail gracefully, not catastrophically.

## Usage Levels

1. **No code** - Build in UI, use in UI with chat interface
2. **Low code** - Design in UI, call with code, embed anywhere
3. **Full API** - Create, manage, run agents via SDK

**SDK:**
```bash
pip install inferencesh
npm i @inferencesh/sdk
```

## Pricing & Scale

- Pay-per-execution model
- Free tier available
- Self-hosted enterprise option
- **x402 stats:** $24M+ volume processed, 75M+ transactions

## Technical Details

- Built on Cloudflare's edge infrastructure
- Durable execution with graph-backed decision chains
- Chat history persistence across sessions
- Event-driven architecture
- Automatic retries and error handling

## Company

- Backed by EWOR
- Enterprise support available
- Self-hosted deployments supported
- Active community on Discord

## Coming Soon

- **Chat deployment** - Agents live in Slack, Discord, Telegram, WhatsApp
- **Event triggers** - Fire agents on messages, file uploads, reactions
- **Scheduled runs** - Cron-style execution for background tasks
