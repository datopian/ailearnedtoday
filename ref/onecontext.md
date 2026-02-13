---
created: 2026-02-11
author: Junde Wu (@JundeMorsenWu)
tags: [context, memory, coding-agents, persistence, collaboration, ai]
---

# OneContext - Agent Self-Managed Context Layer

**A persistent context layer that enables AI coding agents to retain and reuse project knowledge across sessions, devices, and collaborators.**

![OneContext Tweet](https://x.com/JundeMorsenWu/status/2020161412593774922)

## Links

- **GitHub:** https://github.com/TheAgentContextLab/OneContext
- **Announcement:** https://x.com/JundeMorsenWu/status/2020161412593774922
- **Install:** `npm i -g onecontext-ai`
- **First Release:** February 7, 2026

## What Is It?

OneContext is a **self-managed contextual layer** designed to overcome the most common issue in AI-assisted programming: **context loss**. It's a persistent environment that AI coders can easily reuse, allowing work to continue without having to re-explain requirements, decisions, or previous progress.

**The Problem:** AI coding agents suffer from session-based memory. Each new session often starts with partial or no memory of prior decisions, architecture, or progress. Developers must constantly restate requirements and re-establish project understanding.

**The Solution:** OneContext provides a durable, shareable context layer that makes project memory persistent across:
- Sessions
- Devices  
- Coding agents (Codex, Claude Code, etc.)
- Team members

## What Problem Does It Solve?

### Context Fragmentation Issues
- **Repeated explanations** of project structure and goals
- **Inconsistent outputs** from different sessions
- **Lost architectural decisions** and design choices
- **Difficult collaboration** - can't share exact AI configuration
- **Knowledge decay** in long-running projects

### Why Persistent Context Matters
Modern AI coders are efficient but depend on session-based memory. After a session ends, its context is lost until manually restored. This creates friction and delays in development.

## How It Works

### 1. Persistent Context Across Sessions
When you start an AI coding agent using OneContext, it collects relevant project details and history into a unified context layer. This layer is reused each time a new session launches within that project.

**No need to:**
- Copy/paste summaries manually
- Rephrase criteria
- Re-explain project structure

The agent already has access to the entire project understanding.

### 2. Multiple Agents, One Shared Memory
OneContext lets you run multiple AI agents in the same context. Each agent has access to the entire project memory, enabling concurrent or sequential workflows without compromising continuity.

**Use cases:**
- Switching between different AI coding agents
- Restarting tools during long development cycles
- Running parallel agents on different features

### 3. Context Sharing by Link
Share the entire project context via a hyperlink. Anyone with the link can work with the same information and see exactly what the agent knows about the project.

**This transforms context from:**
- ❌ Private session-bound artifact
- ✅ Shareable, collaborative asset

## Quick Start

```bash
# Install globally
npm i -g onecontext-ai

# Run
onecontext

# Or use short alias
oc
```

**Commands:**
```bash
# Check version
onecontext version

# Show help
onecontext --help

# Update
onecontext update

# Troubleshoot
onecontext doctor --fix-upgrade
```

## Key Features

| Feature | Description |
|---------|-------------|
| **Persistent Context Layer** | Maintains project memory across sessions and devices |
| **Multi-Agent Support** | Multiple AI agents can operate under the same context |
| **Automatic Context Management** | No manual summaries or re-prompting required |
| **Shareable Context Links** | Enables collaboration using identical project memory |
| **CLI-Based Workflow** | Fits naturally into developer tooling |
| **Agent Trajectory Recording** | Records your agents' paths and decisions |

## Supported Agents

Works with major AI coding agents:
- **Claude Code**
- **Codex**
- Other AI coding agents

## Practical Use Cases

### 1. Long-Running Software Projects
For projects lasting weeks or months, OneContext prevents knowledge decay between sessions. Pause and resume work without reconstructing context.

### 2. Switching Between Devices
Moving between machines? The persistent context ensures the AI agent is fully aware of the project's current state.

### 3. Team Collaboration
Share context links to enable team members to take on work using the same knowledge. Reduces onboarding time and confusion.

### 4. Experimentation and Prototyping
Explore different solutions with distinct agents without losing the project's core context.

### 5. Slack Integration
Anyone can talk to your agents on Slack using the shared context.

## Benefits

- **Reduced Repetition** - Eliminates need to explain project details repeatedly
- **Better Consistency** - Agents generate more consistent outputs over time
- **Saves Time** - Faster onboarding for new sessions or collaborations
- **Scalable Workflows** - Supports complex, multi-agent development patterns
- **True Continuity** - Agents behave like long-term partners, not one-shot tools

## OneContext vs Traditional Workflows

| Aspect | Traditional Workflow | With OneContext |
|--------|---------------------|-----------------|
| Session Memory | Temporary | Persistent |
| Context Reuse | Manual | Automatic |
| Collaboration | Re-explain or document | Share context directly |
| Multi-Agent Continuity | Fragmented | Unified |

## Limitations and Considerations

While OneContext solves persistence, some practical considerations remain:

- **Context quality** depends on project history quality
- **Large-scale projects** might require disciplined use to reduce noise
- **Access control** matters when sharing context links
- Storage/performance limits may vary based on usage

## Prerequisites

- **Node.js** >= 16
- **Python** 3.11+ with one of: uv, pipx, pip3, or pip

## Who Built It

Created by **Junde Wu** ([@JundeMorsenWu](https://twitter.com/JundeMorsenWu))

Junde is interested in Buddhism, AI, Medicine, Economics, and Modern Art. His academic work has been published in CVPR, ECCV, IEEE TIP, AAAI, MICCAI, MedIA.

**Personal note from the creator:**
> "I built it for myself but now I can't work without it, so it felt wrong not to share."

## Why It Matters

As AI development workflows become more complex and layered, persistent contexts like OneContext are expected to become foundational infrastructure. Tools that preserve project memory, minimize repetition, and enable seamless collaboration will play a greater role in how developers build and maintain software.

**The shift:** OneContext moves AI coding agents from "one-shot tools" to "long-term partners."

## Philosophy

> "Instead of treating every interaction as an isolated exchange, it enables agents to retain and reuse project knowledge across sessions, devices, and even collaborators."

This aligns with broader trends in AI agent development:
- [[steve-yegge]]'s Gas Town - agent factories need coordination
- [[temporal-io-ai]] - workflows need persistence
- Spec-driven development ([[github-spec-kit]], [[openspec.dev]]) - context needs structure

OneContext fills the gap between sessions, making context a first-class citizen in AI-assisted development.

## Related

- [[steve-yegge]] - Gas Town uses Beads for agent coordination (similar persistence problem)
- [[temporal-io-ai]] - Workflow orchestration with durable state
- [[github-spec-kit]] - Spec-driven development with persistent artifacts
