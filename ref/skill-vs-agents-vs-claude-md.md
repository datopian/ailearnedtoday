---
created: 2026-02-24
author: Various (comparison/synthesis)
tags: [skills, agents-md, claude-md, conventions, documentation, ai-agents]
---

# What's the Difference Between SKILL.md, AGENTS.md, and .claud Files?

> Three different conventions for instructing AI agents, each with a distinct purpose and scope.

![agents.md website](https://screenshotit.app/https://agents.md/)

## Links

- **AGENTS.md spec**: https://agents.md/
- **AGENTS.md GitHub**: https://github.com/agentsmd/agents.md
- **Anthropic Skills Guide**: [[anthropic-skills-guide]] (covers SKILL.md)
- **Claude Code docs**: https://docs.anthropic.com/en/docs/claude-code
- **Codex AGENTS.md guide**: https://developers.openai.com/codex/guides/agents-md/

## Quick Answer

- **AGENTS.md** — General-purpose instructions for any AI coding agent working on your project (universal convention)
- **SKILL.md** — Reusable workflow knowledge for Claude Code (Anthropic-specific format)
- **.claud files** — Individual skill definitions for Claude Code (YAML frontmatter + markdown)

**In short**: AGENTS.md is project-level guidance for agents, SKILL.md is workflow knowledge for Claude, and .claud files are individual Claude skills.

---

## The Full Story

### AGENTS.md — Universal Project Instructions

**What it is**: A standardized convention for providing context and instructions to AI coding agents working on your codebase.

**Format**: Markdown file at the root of your repository (or home directory)

**Scope**: Project-level or global

**Purpose**: 
- "Think of AGENTS.md as a README for agents"
- Provides context agents need that isn't in READMEs (which are written for humans)
- Eliminates repetitive prompt instructions

**Example content**:
```markdown
# AGENTS.md

## Dev environment tips
- Use `pnpm dlx turbo run where <project_name>` to jump to a package
- Run `pnpm install --filter <project_name>` to add the package to your workspace

## Project structure
- `/packages/ui` — React component library
- `/apps/web` — Next.js application

## Code conventions
- Use named exports, not default exports
- Prefer `async/await` over promises
```

**Who uses it**:
- Codex (OpenAI) — reads `AGENTS.override.md` or `AGENTS.md` in `~/.codex` or project root
- Factory AI CLI
- Builder.io
- Any agent that follows the convention

**Key insight**: Universal format, not tied to a specific agent or platform.

**Reference**: https://agents.md/

---

### SKILL.md — Claude Code Workflow Knowledge

**What it is**: A file format used by Claude Code (Anthropic) to define reusable workflows and knowledge.

**Format**: Markdown file with optional YAML frontmatter

**Scope**: Workflow-specific (can be standalone or part of a skill package)

**Purpose**:
- Teach Claude a specific workflow once, apply it consistently across sessions
- Provide domain knowledge or procedural guidance
- Often paired with MCP (Model Context Protocol) integrations

**Example content**:
```yaml
---
name: Code Review Assistant
description: Reviews code for security issues and best practices
mcp_servers:
  - sentry
---

# Code Review Workflow

When reviewing code:
1. Check for security vulnerabilities
2. Verify error handling patterns
3. Look for performance issues
4. Suggest improvements with examples
```

**Who uses it**:
- Claude Code (Anthropic's coding agent)
- Part of Claude's skills system (launched October 2025)

**Distribution**:
- Can be shared as standalone `.claud` files
- Can be published to skill repositories
- Teams can standardize workflows using shared skills

**Reference**: [[anthropic-skills-guide]] — Anthropic's 32-page guide on building skills

---

### .claud Files — Individual Claude Skills

**What it is**: Individual skill definition files for Claude Code, containing YAML frontmatter and markdown content.

**Format**: `.claud` file extension (e.g., `code-review.claud`)

**Scope**: Single skill

**Purpose**:
- Packageable, shareable skill definitions
- Each file is a discrete unit of workflow knowledge
- Can be distributed, installed, and loaded by Claude Code

**Example**:
```yaml
---
name: Sentry Code Review
description: Analyzes and fixes bugs in GitHub PRs using Sentry error data
mcp_servers:
  - sentry
  - github
version: 1.0
---

# Sentry Code Review Skill

Automatically analyzes detected bugs in GitHub Pull Requests using Sentry's 
error monitoring data via their MCP server.

## Workflow
1. Load Sentry error context
2. Analyze PR for related issues
3. Suggest fixes with code examples
```

**Who uses it**:
- Claude Code (Anthropic)

**Key difference from SKILL.md**: 
- `.claud` files are individual skill packages
- `SKILL.md` is often the main documentation within a skill directory
- A skill repo might contain multiple `.claud` files or a `SKILL.md` that defines the workflow

---

## When to Use Each

### Use AGENTS.md when:
- Providing project-level context for **any** AI coding agent
- Documenting conventions, shortcuts, or workflows that aren't in the README
- You want a universal format that works across Codex, Claude Code, Cursor, etc.
- Guidance applies to the entire codebase

**Example use case**: Monorepo with complex tooling — AGENTS.md explains how to run tests, navigate packages, and where configs live.

---

### Use SKILL.md when:
- Building a reusable workflow for Claude Code specifically
- Teaching Claude a repeatable process (code review, testing, documentation generation)
- Pairing workflow knowledge with MCP integrations (e.g., Sentry + GitHub)
- You want Claude to consistently follow a specific approach

**Example use case**: A testing workflow that always checks for edge cases, writes tests in a specific style, and uses your team's test utilities.

---

### Use .claud files when:
- Packaging an individual skill for distribution
- Creating a shareable, installable workflow for Claude Code
- Building a library of discrete skills users can pick and choose from
- Publishing to a skill repository or marketplace

**Example use case**: A "React Component Generator" skill that can be installed and used across multiple projects.

---

## How They Work Together

### In a Project Repository

```
your-project/
├── AGENTS.md              # Universal agent instructions
├── skills/
│   ├── code-review.claud  # Claude-specific skill
│   ├── testing.claud      # Another skill
│   └── SKILL.md           # Workflow documentation
└── README.md              # Human-facing docs
```

- **AGENTS.md** — tells agents how to work with this project
- **skills/*.claud** — Claude skills for specific workflows
- **skills/SKILL.md** — documents the skills and their workflows

### In a Claude Code Skill Package

```
sentry-code-review-skill/
├── SKILL.md               # Main workflow documentation
├── mcp-config.json        # MCP server configuration
├── examples/              # Example usage
└── README.md              # Human-facing description
```

The `SKILL.md` contains the workflow instructions Claude follows. The skill itself might be distributed as a `.claud` file or as a directory with `SKILL.md` at the root.

### In Your Workspace (~/.openclaw or ~/.codex)

```
~/.openclaw/workspace/
├── AGENTS.md              # Global agent instructions
└── skills/
    ├── code-review.claud
    └── documentation.claud
```

Global AGENTS.md provides workspace-level guidance. Individual skills provide workflow-specific knowledge.

---

## Key Differences at a Glance

| Feature | AGENTS.md | SKILL.md | .claud files |
|---------|-----------|----------|--------------|
| **Format** | Markdown | Markdown (+ optional YAML) | YAML frontmatter + markdown |
| **Scope** | Project/global | Workflow-specific | Single skill |
| **Purpose** | General agent guidance | Workflow knowledge | Packaged skill |
| **Used by** | Multiple agents (Codex, Claude, Cursor) | Claude Code | Claude Code |
| **Convention** | Universal (agents.md spec) | Anthropic-specific | Anthropic-specific |
| **Location** | Project root or `~/.agent-home` | Skill directory or project | Skill packages |
| **Shareability** | Copy to other projects | Share as skill repo | Distribute as file |

---

## Real-World Examples

### AGENTS.md Example (from agents.md spec)

```markdown
# AGENTS.md

## Dev environment tips
- Use `pnpm dlx turbo run where <project_name>` to jump to a package 
  instead of scanning with `ls`.
- Run `pnpm install --filter <project_name>` to add the package to 
  your workspace so Vite, ESLint, and TypeScript can see it.

## Testing
- Run `pnpm test` from the project root to test all packages
- Use `pnpm test --filter <package>` to test a specific package
```

**What this does**: Tells agents how to navigate a monorepo and run tests efficiently.

---

### SKILL.md Example (from AI Learned Today repo)

```markdown
# AI Learned Today - Logging Skill

This skill documents how to create log entries for the AI Learned Today repository.

## Repository Structure

ailearnedtoday/
├── logs/           # Daily logs
├── ref/            # Reference entries
└── SKILL.md        # This file

## When Adding Entries

1. Create ref entry with frontmatter
2. Add screenshot using screenshotit.app
3. Add 1-2 sentence log entry
4. Commit and push
```

**What this does**: Teaches Claude the workflow for adding entries to this knowledge base.

---

### .claud File Example (Sentry Code Review)

```yaml
---
name: Sentry Code Review
description: Analyzes bugs in GitHub PRs using Sentry error data
mcp_servers:
  - sentry
  - github
version: 1.0
author: Sentry
---

# Sentry Code Review Skill

Automatically analyzes and fixes detected bugs in GitHub Pull Requests 
using Sentry's error monitoring data via their MCP server.

## Workflow

1. Load Sentry error context for the PR
2. Analyze code for related issues
3. Suggest fixes with code examples
4. Comment on the PR with findings
```

**What this does**: Defines a complete, shareable skill for Claude Code that combines Sentry and GitHub via MCP.

---

## Which Format Should You Use?

### For general project guidance → AGENTS.md
If you want **any** AI agent to understand your project structure, tooling, and conventions, use AGENTS.md. It's universal and widely adopted.

### For Claude-specific workflows → SKILL.md or .claud
If you're building reusable workflows for Claude Code, use SKILL.md (for documentation) and .claud files (for distribution).

### For both
Many projects use **AGENTS.md for general context** and **SKILL.md for Claude-specific workflows**. They complement each other:
- AGENTS.md: "Here's how to work with this codebase"
- SKILL.md: "Here's the specific workflow for code reviews"

---

## Related

- **[[anthropic-skills-guide]]** — Anthropic's complete guide to building Claude skills
- **[[react-pdf-skill]]** — Example of a Claude Code skill
- **[[larry-tiktok-skill]]** — Another skill example (OpenClaw/ClawHub)
- **agents.md spec** — https://agents.md/
- **OpenClaw skills** — Similar concept for OpenClaw agents

---

*Added: February 24, 2026*
