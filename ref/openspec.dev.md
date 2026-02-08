---
created: 2026-02-08
tags: [specs, planning, coding-agents, requirements, open-source]
---

# OpenSpec - A Lightweight Spec-Driven Framework

**Universal planning layer for AI coding agents. Review intent, not just code.**

![OpenSpec Screenshot](https://screenshotit.app/https://openspec.dev)

## Links

- **Website:** https://openspec.dev
- **GitHub:** https://github.com/Fission-AI/OpenSpec/ (23k stars)
- **Discord:** https://discord.gg/YctCnvvshC
- **Install:** `npm install -g @fission-ai/openspec@latest`

## What Is It?

OpenSpec is a lightweight, spec-driven framework that acts as a planning layer for AI coding agents. It's:
- **Universal** - works across 20+ coding tools
- **Open Source** - no API keys required
- **No MCP** - direct integration

## What Problem Does It Solve?

### 1. Review Intent, Not Just Code
Each OpenSpec change produces a **spec delta** that captures the change in requirements. This makes it easy for:
- **Developers** to understand how they're modifying the system
- **Reviewers** to understand changes without digging through code
- **Teams** to gain high-level understanding quickly

### 2. Universal Planning Format
Specs live in your codebase and work with any agent:
- Claude Code
- Cursor
- Codex
- GitHub Copilot
- 16+ more tools

### 3. Better Than Prompts
Specs provide persistent, reviewable requirements instead of one-off prompts that get lost.

## How to Use It Quickly

```bash
# Install globally
npm install -g @fission-ai/openspec@latest

# Initialize in your project
openspec init

# Start planning
openspec plan
```

Specs live in your codebase (e.g., `openspec/specs/auth-session/spec.md`) and generate diffs like:

```diff
### Requirement: Session expiration
- The system SHALL expire sessions after a configured duration.
+ The system SHALL support configurable session expiration periods.

#### Scenario: Default session timeout
- GIVEN a user has authenticated
- - WHEN 24 hours pass without activity
+ - WHEN 24 hours pass without "Remember me"
- THEN invalidate the session token

+ #### Scenario: Extended session with remember me
+ - GIVEN user checks "Remember me" at login
+ - WHEN 30 days have passed
+ - THEN invalidate the session token
+ - AND clear the persistent cookie
```

## Key Features

- **Native Support** for 20+ coding agents
- **Spec Deltas** - see requirement changes, not just code changes
- **Version Controlled** - specs live in your repo
- **Team Ready** - workspaces coming soon for multi-repo planning

## Coming Soon: Workspaces

OpenSpec is building team features for:
- Large codebases
- Multi-repo planning
- Custom integrations
- Better collaboration

## By

Fission AI
