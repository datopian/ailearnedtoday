---
created: 2026-02-09
author: GitHub (Den Delimarsky, John Lam)
tags: [specs, planning, coding-agents, spec-driven-development, github, open-source]
---

# Spec Kit - GitHub's Spec-Driven Development Toolkit

**Build high-quality software faster. Focus on product scenarios and predictable outcomes instead of vibe coding every piece from scratch.**

## Links

- **GitHub:** https://github.com/github/spec-kit
- **Documentation:** https://github.github.io/spec-kit/
- **Video Overview:** https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv
- **Install:** `uv tool install specify-cli --from git+https://github.com/github/spec-kit.git`

## What Is It?

Spec Kit is GitHub's open source toolkit for **Spec-Driven Development (SDD)**. It's a structured process where specifications become executable, directly generating working implementations rather than just guiding them.

**Core Philosophy:** Specifications define the "what" before the "how" through multi-step refinement rather than one-shot code generation from prompts.

## What Problem Does It Solve?

### Traditional Development Issues
- Vibe coding from scratch without clear requirements
- Lost context in one-off prompts
- Code-first approach where specs are just scaffolding
- Disconnect between what you want and what you get

### Spec-Driven Development Solution
- **Intent-driven:** Specifications define requirements before implementation
- **Rich specs:** Using guardrails and organizational principles
- **Multi-step refinement:** Systematic process from spec → plan → tasks → implementation
- **Predictable outcomes:** Clear validation and acceptance criteria

## How to Use It Quickly

### Quick Start

```bash
# Install (recommended - persistent)
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git

# Create new project
specify init <PROJECT_NAME>

# Or initialize in existing project
specify init . --ai claude
# or
specify init --here --ai claude

# Check installed tools
specify check
```

### The 6-Step Workflow

Once initialized, your AI agent gets `/speckit.*` slash commands:

**1. Establish Principles** (`/speckit.constitution`)
```
/speckit.constitution Create principles focused on code quality, 
testing standards, user experience consistency, and performance requirements
```

**2. Create Spec** (`/speckit.specify`)
```
/speckit.specify Build an application that can help me organize my photos 
in separate photo albums. Albums are grouped by date and can be re-organized 
by dragging and dropping on the main page.
```

**3. Clarify** (`/speckit.clarify` - optional but recommended)
- Structured questioning to fill gaps before planning

**4. Create Plan** (`/speckit.plan`)
```
/speckit.plan The application uses Vite with minimal number of libraries. 
Use vanilla HTML, CSS, and JavaScript. Images stored in local SQLite database.
```

**5. Break Down Tasks** (`/speckit.tasks`)
```
/speckit.tasks
```

**6. Implement** (`/speckit.implement`)
```
/speckit.implement
```

## Supported AI Agents (20+)

- ✅ **Claude Code**
- ✅ **Cursor**
- ✅ **Codex CLI**
- ✅ **GitHub Copilot**
- ✅ **Windsurf**
- ✅ **Gemini CLI**
- ✅ **opencode**
- ✅ **Qoder CLI**
- ✅ **Auggie CLI**
- ✅ **Roo Code**
- ✅ **Amp**
- ✅ **IBM Bob**
- ✅ **Jules** (by Google)
- ✅ **Kilo Code**
- ✅ **SHAI** (OVHcloud)
- ⚠️ **Amazon Q Developer CLI** (limited - no custom args for slash commands)
- ...and more

## Development Phases

### 0-to-1 Development (Greenfield)
- Start with high-level requirements
- Generate specifications
- Plan implementation steps
- Build production-ready applications

### Creative Exploration
- Explore diverse solutions
- Support multiple tech stacks & architectures
- Experiment with UX patterns

### Iterative Enhancement (Brownfield)
- Add features iteratively
- Modernize legacy systems
- Adapt processes

## Key Features

### Constitution-First
Project governing principles guide all decisions throughout development (stored in `.specify/memory/constitution.md`)

### Multi-Artifact Structure
```
.specify/
├── memory/
│   └── constitution.md
├── scripts/
│   ├── create-new-feature.sh
│   ├── setup-plan.sh
│   └── update-claude-md.sh
├── specs/
│   └── 001-feature-name/
│       ├── spec.md
│       ├── plan.md
│       ├── tasks.md
│       ├── data-model.md
│       ├── contracts/
│       └── research.md
└── templates/
    ├── spec-template.md
    ├── plan-template.md
    └── tasks-template.md
```

### Branch-per-Feature
- Git branches created per feature (e.g., `001-create-taskify`)
- Enables parallel exploration of different implementations
- PR-ready workflow with GitHub CLI integration

### Validation & Checklists
- Review & Acceptance Checklist in spec
- Structured validation before implementation
- Cross-artifact consistency analysis (`/speckit.analyze`)

## Prerequisites

- Linux/macOS/Windows
- [uv](https://docs.astral.sh/uv/) for package management
- Python 3.11+
- Git
- Supported AI coding agent

## Research Goals

GitHub is using Spec Kit to validate:

1. **Technology independence** - Works across diverse tech stacks, languages, frameworks
2. **Enterprise constraints** - Mission-critical apps with organizational requirements
3. **User-centric development** - Different cohorts, from vibe-coding to AI-native
4. **Creative & iterative processes** - Parallel exploration, upgrades, modernization

## Comparison to Other Tools

See [[moc-planning-work]] for how Spec Kit compares to [[openspec.dev]] and other planning tools.

## By

GitHub - Den Delimarsky ([@localden](https://github.com/localden)) & John Lam ([@jflam](https://github.com/jflam))

MIT License
