---
created: 2026-02-14
author: David Szabo-Stuban (@ssdavid)
tags: [openclaw, ai-agents, deployment, infrastructure, memory, vault, clustering, solopreneur]
---

# Alfred - Portable OpenClaw Fork with Associative Memory

**AI-first business OS for solopreneurs. Now fully portable: deploys to Hetzner VM in 10 minutes, self-fixes bugs, maintains an associative memory vault with auto-clustering.**

## Links

- **Announcement:** https://substack.com/@ssdavid/note/c-210266130 (Feb 5, 2026)
- **AlfredOS Open Source:** https://lumberjack.so/alfredos-is-now-open-source/
- **Blog:** https://lumberjack.so/
- **Author:** David Szabo-Stuban (@ssdavid)
- **Previous Note on Associative Memory:** https://substack.com/@ssdavid/note/c-208407833

## What Is It?

**Alfred** is a modded OpenClaw fork that's evolved into "AlfredOS" - an AI-first business operating system for solopreneurs. It combines:

1. **Full Infrastructure Deployment** - Auto-deploys entire stack to Hetzner VM
2. **Associative Memory Vault** - Structured knowledge base with auto-clustering
3. **Self-Fixing Deployment** - Alfred fixes bugs automatically during deployment
4. **Business App Integration** - LibreChat, n8n, Ghost, Cal.com, NocoDB

**Key Milestone (Feb 5, 2026):** Alfred is now **portable**. The entire modded OpenClaw fork can deploy from scratch in ~10 minutes.

> "The whole setup takes about 10 minutes. In case of any bugs, Alfred fix the deployment automatically and pushes it to completion while I sip my coffee."

## What Problem Does It Solve?

### Solopreneur Infrastructure Pain
- **SaaS fees** - Constant subscription costs
- **Server management** - DevOps complexity
- **Context switching** - Copy/paste between tools
- **Memory fragmentation** - Information scattered across tools

### Alfred's Solution
- **One-click deployment** - Full stack in minutes
- **Self-hosted** - Own your data, pay token costs only
- **Integrated AI agent** - Access all tools natively
- **Associative memory** - Unified knowledge vault with auto-maintenance

## How Alfred's Portable Deployment Works

### 1. Infrastructure Deployment
- **Deploys to:** Hetzner VM
- **Secrets management:** Pulumi ESC
- **Networking:** Tailscale VPN
- **Time:** ~10 minutes

### 2. Vault Preloading
- Loads custom agents
- Installs skills and scripts
- Sets up vault maintenance automation

### 3. Autoclustering Pipeline
- **Embedding:** nomic-embed-text
- **Clustering:** HDBSCAN on vector data to reveal patterns
- **Labeling:** Cerebras using Llama 3.1 for cluster and relationship labels
- **Ontology:** Palantir-based structure for nodes

### 4. Self-Fixing
Alfred monitors deployment, detects bugs, fixes them automatically, and pushes to completion.

## The Associative Memory System

Alfred builds and maintains an **associative memory vault** - a structured knowledge base that:

### Automatic Processing
- **Processes conversations and files** at regular intervals into the vault
- **Follows ontology** strictly - Palantir-based structure
- **Accepts any input** - Audio, video, text braindumps

### Automatic Maintenance
- **Scans for violations** - Ontology issues, duplicates, empty stubs, broken links
- **Fixes automatically** - No manual intervention needed
- **Finds hidden relationships** - Links unlinked entities
- **Enriches content** - Using web search

### Clustering Workflow
1. **Embed full vault text** with nomic-embed-text
2. **Run HDBSCAN** on vector data to reveal clusters
3. **Label clusters** with Qwen 2.5 7B (running locally)
4. **Label relationships** and relationship types (also Qwen)
5. **Reruns regularly** on DGX Spark to keep vault healthy

### Fast Retrieval with Small Language Models

Alfred trains **small language models** (Qwen 3 0.6B) on the **ontology schema** (not content) for sub-100ms retrieval:

**The Process:**
1. Use Opus 4.5 and Sonnet 4.5 subagents to generate 1000 pairs of:
   - Natural language prompts
   - Obsidian Base syntax responses
2. Submit TRL job with LoRA fine-tuning on HF Jobs (a10g-large)
3. Convert to Q4_K_M quantization for Ollama
4. Deploy on DGX Spark
5. Add alias on OpenClaw for future use

**How It Works at Runtime:**
- Every prompt gets intercepted
- Small model returns relevant Obsidian filenames in Base syntax (<100ms)
- Filenames get injected into prompt
- Alfred agent receives context-aware prompt
- Result: **Associative memory - rebuilding context on the fly faster than lightning**

Expected accuracy: ~70%+ (theory)

## The Tech Stack

### Core Infrastructure
- **Agent Interface:** LibreChat (custom fork called "Alfred")
- **Automation:** n8n
- **Blog:** Ghost
- **Calendar:** Cal.com
- **Database:** NocoDB
- **Deployment:** Railway.com template (moving to Hetzner)
- **MCP Connections:** Hardwired between agent and apps

### AI/ML Stack
- **Models:** Opus 4.5, Sonnet 4.5, Qwen 2.5 7B, Qwen 3 0.6B
- **Embedding:** nomic-embed-text
- **Clustering:** HDBSCAN
- **Labeling:** Cerebras (Llama 3.1)
- **Hardware:** DGX Spark

### Infrastructure-as-Code
- **Secrets:** Pulumi ESC
- **VPN:** Tailscale
- **Hosting:** Hetzner VM

## Why OpenClaw?

Alfred is built as a **modded OpenClaw fork** because OpenClaw provides:
- Agent coordination framework
- MCP integrations
- Skill system
- Multi-agent orchestration

David extended it with:
- Portable deployment automation
- Associative memory vault
- Auto-clustering pipeline
- Self-fixing capabilities

## Philosophy: AI-First Solopreneurship

### Core Principles
1. **Own your data** - Self-hosted, not SaaS
2. **Pay for tokens, not seats** - Token costs dropped 280x in 3 years
3. **Zero manual context switching** - AI has native access to all tools
4. **Write SOPs once** - AI executes them repeatedly
5. **Minimize maintenance** - Auto-fixing, auto-clustering, auto-enrichment

### The Vision
> "My goal is to run my business autonomously and AlfredOS provides the scaffolding."

Alfred represents a shift from "AI as tool" to "AI as business operating system."

## The Journey (Timeline)

**Early 2025:** Started building "my own butler" - simple Telegram bot  
**Mid 2025:** Realized context management needed structured data → AlfredOS v1.0  
**May 2025:** AlfredOS v1.0 launched (Linux, Docker-in-Docker, unusable)  
**Aug 2025:** AlfredOS v1.1 rebuilt on Railway.com, made open source  
**Jan 2026:** Alfred gains associative memory with small language model training  
**Feb 2026:** **Alfred becomes portable** - full deployment automation

## Key Innovation: Self-Fixing Deployment

> "In case of any bugs, Alfred fix the deployment automatically and pushes it to completion while I sip my coffee."

This is a major milestone: an AI system that can:
1. Deploy its own infrastructure
2. Detect deployment failures
3. Fix them automatically
4. Push to completion without human intervention

This moves beyond "AI agents that write code" to "AI agents that deploy and maintain themselves."

## Comparison to Other AI Systems

| Feature | Alfred | Standard AI | OpenClaw Base |
|---------|--------|-------------|---------------|
| **Deployment** | Self-deploying (10min) | Manual | Manual |
| **Memory** | Associative vault | Session-based | Context layer |
| **Maintenance** | Self-fixing | Manual | Manual |
| **Integration** | Hardwired MCP | API calls | MCP support |
| **Infrastructure** | Full stack | Cloud API | Framework only |
| **Clustering** | Auto (HDBSCAN) | None | None |
| **Retrieval** | <100ms (SLM) | RAG (~seconds) | Standard |

## Use Cases

### For Solopreneurs
- Run entire business on self-hosted infrastructure
- Pay token costs instead of SaaS fees
- Own all data
- Automate repetitive tasks with SOPs

### For Builders
- Template for AI-first business infrastructure
- Reference implementation of associative memory
- Example of self-fixing deployment
- OpenClaw fork with production features

### For Researchers
- Associative memory implementation
- Small language model training for fast retrieval
- Auto-clustering pipeline
- Ontology-based knowledge organization

## Technical Achievements

### 1. Portable Deployment
Full infrastructure deployment in 10 minutes with auto-fixing

### 2. Associative Memory
Fast (<100ms) retrieval using small language models trained on ontology schema

### 3. Auto-Clustering
HDBSCAN + Cerebras/Llama 3.1 for discovering hidden relationships

### 4. Auto-Maintenance
Vault health scanner that fixes violations, enriches content, finds relationships

### 5. Self-Fixing
Deployment system that monitors, detects issues, and fixes them automatically

## Why It Matters

Alfred represents several important trends:

### 1. Self-Deploying AI Systems
Moving from "AI writes code" to "AI deploys and maintains infrastructure"

### 2. Associative Memory
Solving the context problem with structured vaults and fast retrieval

### 3. AI-First Business OS
Not just "AI tools" but "AI as operating system" for business

### 4. Solopreneur Economics
Shifting from SaaS fees to token costs (280x price drop enables this)

### 5. OpenClaw Extensions
Demonstrating how to build production systems on OpenClaw

## Related Concepts

### From [[onecontext]]
Persistent context across sessions - Alfred's vault is a similar concept but more structured

### From [[temporal-io-ai]]
Workflow orchestration - Alfred uses n8n for automation, Temporal-style reliability

### From [[steve-yegge]]'s Gas Town
Agent orchestration - Alfred is an orchestrated system of agents and automations

### From [[github-spec-kit]]
Ontology/constitution - Alfred has a Palantir-based ontology for vault structure

## Who Built It

**David Szabo-Stuban** (@ssdavid)
- **Blog:** Lumberjack (https://lumberjack.so/)
- **Substack:** 7.1K+ subscribers
- **Background:** Building AI stuff with no-code, in tech since 2012
- **Previous work:** 4 startups, 30+ products shipped
- **Current:** Building AI-first business OS for solopreneurs

## Open Source

AlfredOS was made open source in August 2025 as a gift for Lumberjack's first birthday.

**Deploy:** Railway.com template (free tier available)  
**License:** Open source (license not specified in sources)

## The "I'm so nerdsniped" Moment

> "I'm so nerdsniped."

David's reaction to getting Alfred fully portable captures something important: this is a **builder building their dream infrastructure**. Not a product, not a startup, just pure "I wanted this to exist so I built it."

That authenticity - building for yourself first - often leads to the most interesting systems.

## Future Directions

Based on the journey so far:

1. **LibreChat API** - Once shipped, enable true automations combining n8n + agent
2. **Hetzner Migration** - Move from Railway to cheaper hosting
3. **API Access** - MCP connection to plug Alfred into Claude or other agents
4. **Community Forks** - Open source enables others to extend Alfred

## Should You Try It?

**Yes, if:**
- You're a solopreneur tired of SaaS fees
- You want to own your business data
- You're comfortable with self-hosting
- You want an AI agent that knows all your tools

**Wait, if:**
- You need enterprise features
- You want zero maintenance (this is v1.1, expect bugs)
- You're not technical enough for self-hosting
- You prefer SaaS simplicity

## Key Quote

> "The value of AlfredOS is not the agent. It's the plumbing."

This captures the essence: Alfred is infrastructure for AI-first business, not just another chatbot.

## Related

- [[onecontext]] - Persistent context layer
- [[temporal-io-ai]] - Workflow orchestration
- [[steve-yegge]] - Agent orchestration (Gas Town)
- [[github-spec-kit]] - Structured ontology
