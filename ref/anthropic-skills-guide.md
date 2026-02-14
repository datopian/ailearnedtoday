---
created: 2026-02-14
author: Anthropic
tags: [claude-code, skills, claude, guide, workflow, mcp, documentation]
---

# The Complete Guide to Building Skills for Claude

**32-page detailed guide from Anthropic on building, testing, and distributing skills for Claude. Covers standalone workflows and MCP-enhanced integrations.**

## Links

- **PDF:** https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf
- **Blog Post:** https://claude.com/blog/complete-guide-to-building-skills-for-claude
- **Released:** January 29, 2026
- **Reddit Discussion:** https://www.reddit.com/r/ClaudeAI/comments/1r3hr40/anthropic_released_32_page_detailed_guide_on/

## What Is It?

An official 32-page comprehensive guide from Anthropic on how to build skills that give Claude reusable context for your workflows. Released following strong interest after [Skills launched in October 2025](https://claude.com/blog/skills).

**Skills** let you teach Claude your workflows once and apply them consistently across sessions.

## What Problem Does It Solve?

Since launching Skills in October 2025, Anthropic saw demand from:
- **Developers** who want Claude to follow specific workflows consistently
- **Power users** automating repeatable tasks like document creation or research
- **Teams** looking to standardize how Claude operates across their organization
- **MCP connector builders** pairing their integrations with reliable workflows

**The common thread:** People wanted more detailed guidance on building effective skills—from planning and structure to testing and distribution.

This guide fills that gap.

## What's Covered

### Core Topics

1. **Technical Requirements**
   - Skill structure and YAML frontmatter
   - How Claude decides whether to load your skill
   - Best practices for organization

2. **Patterns That Work**
   - Standalone skills (using Claude's built-in capabilities)
   - MCP-enhanced workflows
   - Patterns from early adopters across different use cases

3. **Testing & Iteration**
   - Testing approaches
   - How to iterate on skills
   - Common troubleshooting patterns

4. **Distribution**
   - How to share skills
   - Team standardization approaches

5. **MCP + Skills** (dedicated section)
   - Pairing MCP integrations with workflows
   - Enhancing MCP connectors with skill knowledge

### Performance & Monitoring

- Count tool calls
- Track total tokens consumed
- Beta user feedback approaches

### Real Examples

**sentry-code-review skill** (from Sentry):
> "Automatically analyzes and fixes detected bugs in GitHub Pull Requests using Sentry's error monitoring data via their MCP server."

## Who This Is For

- **Developers** who want Claude to follow specific workflows consistently
- **MCP connector builders** adding workflow knowledge to their integrations
- **Power users** automating repeatable tasks
- **Teams** looking to standardize how Claude works across their organization

## Time Investment

> "If you know the top 2-3 workflows you want to automate, expect about 15-30 minutes to build and test your first working skill using the skill-creator."

## Key Insights & Quotes

### The Kitchen Analogy

> "MCP provides the professional kitchen: access to tools, ingredients, and equipment.
> 
> Skills provide the recipes: step-by-step instructions on how to create something valuable.
> 
> Together, they enable users to accomplish complex tasks without needing to figure out every step themselves."

This perfectly captures the MCP + Skills relationship.

### The Problem Skills Solve

**Without skills:**
- Users connect your MCP but don't know what to do next
- Support tickets asking "how do I do X with your integration"
- Each conversation starts from scratch
- Inconsistent results because users prompt differently each time
- Users blame your connector when the real issue is workflow guidance

**With skills:**
- Pre-built workflows activate automatically when needed
- Consistent, reliable tool usage
- Best practices embedded in every interaction
- Lower learning curve for your integration

### Skills = Reusable Context

> "Instead of re-explaining your preferences, processes, and domain expertise in every conversation, skills let you teach Claude once and benefit every time."

This is about:
- Repeatability
- Standardization
- Reducing prompt engineering overhead
- Building institutional knowledge

### Progressive Disclosure (Three-Level System)

Skills use a sophisticated loading strategy:

**First level (YAML frontmatter):** Always loaded in Claude's system prompt. Just enough information for Claude to know when each skill should be used without loading all of it into context.

**Second level (SKILL.md body):** Loaded when Claude thinks the skill is relevant. Contains the full instructions and guidance.

**Third level (Linked files):** Additional files Claude can discover only as needed.

> "This progressive disclosure minimizes token usage while maintaining specialized expertise."

### Pro Tip: Iterate on a Single Task First

> "We've found that the most effective skill creators iterate on a single challenging task until Claude succeeds, then extract the winning approach into a skill. This leverages Claude's in-context learning and provides faster signal than broad testing."

Don't try to build comprehensive coverage upfront. Get one thing working really well first.

## Document Structure (32 pages)

While the exact structure isn't public, the guide covers:

1. Introduction & Use Cases
2. Technical Requirements
3. Skill Structure & Best Practices
4. Standalone Skills
5. MCP-Enhanced Skills
6. Testing & Iteration
7. Distribution & Sharing
8. Troubleshooting
9. Examples & Patterns

## Significance

This is Anthropic's **first comprehensive, official guide** on Skills. At 32 pages, it's a substantial resource that:

1. **Formalizes** the Skills system
2. **Documents** best practices from early adopters
3. **Bridges** standalone workflows and MCP integrations
4. **Standardizes** how to build reliable skills

## Related to Other Developments

### [[react-pdf-skill]]
molefrog's React-PDF skill is an example of the pattern: giving Claude domain-specific knowledge (React-PDF patterns) via a skill.

### [[github-spec-kit]]
Spec Kit uses slash commands for structured workflows. Skills are similar but:
- **Spec Kit:** Spec-driven development process
- **Claude Skills:** Reusable workflow context

Both solve: "How do we give AI agents consistent, repeatable instructions?"

### [[openspec.dev]]
OpenSpec provides spec artifacts. Skills provide workflow artifacts. Complementary approaches to managing AI agent knowledge.

## Timing & Context

**January 29, 2026** - This release comes ~4 months after Skills launched.

The timing suggests:
1. Anthropic saw significant adoption
2. Community needed more guidance
3. MCP + Skills pattern emerging as important
4. Ready to formalize best practices

## From the Reddit Discussion

Community reaction:
> "Heck you could extract the info in here and turn it into a more detailed skill-creator skill than the official one from Anthropic."

This meta-observation: Use the guide to improve the skill that creates skills. Recursive improvement.

## Philosophy: Teach Once, Use Forever

Skills embody a key principle:
> "Teach Claude your workflows once and apply them consistently."

This is about **knowledge transfer** and **institutional memory**:
- Capture expertise in reusable form
- Reduce cognitive overhead
- Enable consistency across team/time
- Build compounding knowledge base

## Practical Takeaway

**Before Skills:** Prompt engineering every time  
**With Skills:** Encode workflows once, invoke consistently

This shifts effort from **repeated instruction** to **upfront design**.

## How to Use This Guide

1. **Read** the 32-page PDF
2. **Identify** your top 2-3 workflows to automate
3. **Use skill-creator** to build your first skill (15-30 min)
4. **Test** with beta users
5. **Iterate** based on feedback
6. **Distribute** to team

## Why This Matters

As AI coding agents proliferate, the question becomes:
> "How do we give them reliable, repeatable knowledge?"

Anthropic's answer: **Skills**

This guide is Anthropic saying:
- Skills are production-ready
- Here's how to build them properly
- We're committed to this pattern

## Quote to Remember

> "MCP provides the professional kitchen: access to tools, ingredients, and equipment. Skills provide the recipes: step-by-step instructions on how to create something valuable."

The kitchen analogy perfectly captures why MCP + Skills together are more powerful than either alone.

## Related

- [[react-pdf-skill]] - Example skill for PDF generation
- [[github-spec-kit]] - Spec-driven development (similar workflow pattern)
- [[openspec.dev]] - Spec artifacts (complementary to skill artifacts)
- [[steve-yegge]] - Gas Town uses skills for agent coordination

## Download

**PDF:** https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf  
**Length:** 32 pages  
**Format:** Comprehensive guide with examples, patterns, and troubleshooting

## By

**Anthropic** - Creators of Claude and Claude Code

Released as part of their commitment to making Skills a reliable, well-documented system for workflow automation.
