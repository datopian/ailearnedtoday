---
created: 2026-02-09
tags: [moc, planning, specs, coding-agents, requirements]
---

# MOC: Planning Work with AI Agents

**Map of Content for tools and approaches to planning software development with AI coding agents.**

## Overview

As AI coding agents become more capable, the question shifts from "can they write code?" to "how do we tell them what to build?" This MOC tracks tools, frameworks, and philosophies for planning and specifying work before (and during) implementation.

## The Spectrum

### 1. Vibe Coding
- No planning, just prompts
- One-shot code generation
- Fast exploration, poor predictability
- Context gets lost between sessions

### 2. Detailed Prompts
- Rich, specific instructions
- Better than vibe coding, but still ephemeral
- No artifact to review, version, or reference

### 3. Spec-Driven Development
- **Specifications as artifacts** that persist and guide implementation
- Multi-step refinement
- Reviewable intent, not just code
- Version controlled alongside implementation

## Tools & Frameworks

### [[openspec.dev]]
**Universal, lightweight planning layer**

- **What:** Spec deltas for reviewing intent changes
- **Approach:** Specs live in your repo, work with any agent (20+ tools)
- **Philosophy:** Review intent, not just code
- **Install:** `npm install -g @fission-ai/openspec@latest`
- **Stars:** 23k GitHub stars
- **Best for:** Developers who want lightweight, universal format without heavy process

**Key Features:**
- Native support for 20+ coding agents
- Spec diffs show requirement changes
- No API keys, no MCP
- Open source

### [[github-spec-kit]]
**GitHub's structured SDD toolkit**

- **What:** Full Spec-Driven Development workflow with slash commands
- **Approach:** Constitution → Spec → Plan → Tasks → Implement
- **Philosophy:** Intent-driven, multi-step refinement, rich specifications
- **Install:** `uv tool install specify-cli --from git+https://github.com/github/spec-kit.git`
- **Best for:** Teams/enterprises wanting structured, validated process with governance

**Key Features:**
- 6-step workflow with `/speckit.*` commands
- Constitution-first (project principles guide everything)
- Branch-per-feature with PR workflow
- Multi-artifact structure (spec, plan, tasks, research, contracts)
- Validation & checklists
- Supports 20+ AI agents

**Workflow:**
1. `/speckit.constitution` - Establish principles
2. `/speckit.specify` - Define what to build
3. `/speckit.clarify` - Fill gaps (optional)
4. `/speckit.plan` - Tech stack & implementation
5. `/speckit.tasks` - Break down into actionable tasks
6. `/speckit.implement` - Execute

## Key Concepts

### Spec Deltas
Both OpenSpec and Spec Kit focus on **diff-able specifications**. When requirements change, you can see:
```diff
- The system SHALL expire sessions after a configured duration.
+ The system SHALL support configurable session expiration periods.
```

This makes it easy to:
- Review intent changes (not just code changes)
- Understand system modifications at high level
- Track requirement evolution over time

### Constitution / Principles
Spec Kit emphasizes establishing **project governing principles** first:
- Code quality standards
- Testing requirements
- UX consistency
- Performance requirements
- How principles guide technical decisions

These act as a foundation that guides all subsequent spec, planning, and implementation.

### Multi-Step Refinement
Both tools reject one-shot "prompt → code" in favor of:
1. **Requirements** (what & why)
2. **Planning** (how & with what)
3. **Tasks** (breakdown & ordering)
4. **Implementation** (execution)

This separation allows:
- Reviewing intent before committing to tech stack
- Validating completeness before coding
- Iterative refinement at each stage

## Comparison

| Feature | OpenSpec | Spec Kit |
|---------|----------|----------|
| **Philosophy** | Lightweight, universal | Structured, comprehensive |
| **Process** | Flexible | 6-step workflow |
| **Governance** | Minimal | Constitution-first |
| **Artifacts** | Specs + deltas | Spec, plan, tasks, research, contracts |
| **Validation** | Implicit | Explicit (checklists, analysis) |
| **Best for** | Solo devs, quick adoption | Teams, enterprises, complex projects |
| **Installation** | npm | uv (Python) |
| **Branch strategy** | Your choice | Branch-per-feature built-in |

## Philosophies

### From [[crawshaw-eight-more-months-agents]]

> "The best software for an agent is whatever is best for a programmer. Every customer has an agent that will write code against your product for them. Build what programmers love and everyone will follow."

David Crawshaw's insight: agents change the shape of good software. Products need APIs/interfaces that agents can use, not just fancy UIs with weak APIs.

### Spec-Driven Development Core Tenets

1. **Intent-driven** - Define "what" before "how"
2. **Specifications become executable** - Not just documentation, but source of implementation
3. **Multi-step refinement** - Not one-shot generation
4. **Rich specifications** - With guardrails, principles, validation

## When to Use What

**Use vibe coding when:**
- Quick spike/prototype
- Exploring unknown territory
- Learning a new technology
- Timeline < 1 hour

**Use detailed prompts when:**
- Well-defined task
- Solo project
- Simple scope
- No need for review

**Use OpenSpec when:**
- You want spec artifacts
- Working across multiple agents
- Need lightweight process
- Want reviewable intent

**Use Spec Kit when:**
- Team/enterprise development
- Complex, multi-phase projects
- Need governance & validation
- Want structured workflow with checklists
- Building mission-critical applications

## Related

- [[pi.dev]] - Coding agent that can work with these specs
- [[exe.dev]] - VM service for unconstrained agent work
- [[inference-sh]] - Agent runtime platform

## Resources

- [Spec Kit Full Methodology](https://github.com/github/spec-kit/blob/main/spec-driven.md)
- [OpenSpec Docs](https://openspec.dev)

---

**Meta:** This is a living document. As new planning tools emerge, add them here with comparisons.
