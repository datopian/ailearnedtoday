---
created: 2026-02-25
author: Greg Isenberg (@gregisenberg)
tags: [obsidian, claude-code, markdown, personal-knowledge-management, pkm, second-brain, ai-workflows, markdownmanifesto]
---

# Obsidian + Claude Code: Building a 24/7 Personal Operating System

> "Markdown files are the oxygen of LLMs. The more you write, the more context your agents have."

![Greg Isenberg Obsidian Tweet](https://screenshotit.app/https://x.com/gregisenberg/status/2026036464287412412)

## Links

- **Tweet**: https://x.com/gregisenberg/status/2026036464287412412
- **Author**: [@gregisenberg](https://x.com/gregisenberg) (GREG ISENBERG)
- **Referenced**: [@internetvin](https://x.com/internetvin) — inspiration for the workflow
- **Podcast**: [@startupideaspod](https://x.com/startupideaspod)
- **Date**: February 23, 2026
- **Engagement**: 552K views, 5.9K likes, 12K bookmarks

## Summary

Greg Isenberg outlines a workflow for using Obsidian (markdown-based note-taking) + Claude Code to build a "24/7 personal operating system" that turns your notes into leverage for AI agents. The key insight: by writing everything in interconnected markdown files, you create a knowledge vault that agents can read, understand, and act on — eliminating the need to re-explain context every session.

> "Vin uses AI like a thinking partner wired into his life's work. 99.99% of people won't do this because it requires reflection + setup. But once the vault exists, the agent stops being generic. It starts thinking in your voice."

## The 10-Step Workflow

### 1. Write Everything in Markdown
Daily notes, projects, beliefs, people, meetings — all in plain markdown files in Obsidian.

### 2. Link Notes Together
Use wiki-links (`[[note-name]]`) to mirror how your brain actually thinks. Build a graph of interconnected ideas.

### 3. Install Obsidian CLI
Enable Claude Code to read your entire vault + the relationships between notes. The agent gains access to your full knowledge graph.

### 4. Use Reference Files, Not Re-Explanations
Stop reexplaining projects every session. Point Claude to reference files in your vault.

### 5. Build Custom Slash Commands
- `/context` → Load your full life + work state
- `/trace` → See how an idea evolved over months
- `/connect` → Bridge two domains you've been circling
- `/ideas` → Generate startup ideas from your vault
- `/graduate` → Promote daily thoughts into real assets

### 6. Rule: Human Writes, Agent Reads
**Human writes the vault. Agents read it, suggest, execute.**

This boundary keeps you as the source of truth while letting agents act on your behalf.

### 7. Let Claude Surface Patterns
The agent can identify patterns you've been "unconsciously circling for years" by analyzing the vault.

### 8. Delegate From Inside Notes
> "One sentence in Obsidian → agent handles the rest."

Example: Write "Draft investor update for Q1" in your daily note → agent reads project context, financials, recent wins from vault → generates the update.

### 9. Treat Writing as Leverage
The more you write, the more context your agents have. Your notes become a force multiplier.

### 10. Markdown Files Are the Oxygen of LLMs
Plain text, structured, interconnected, and portable. LLMs consume markdown better than any other format.

---

## Why This Matters

### The Personal Knowledge Graph as Agent Context
Most people use AI in stateless sessions — each conversation starts from zero. This workflow inverts that:
- **Your vault is the state**
- **The agent reads it before acting**
- **Context persists across all sessions**

This is the difference between "ChatGPT" and "an AI assistant that knows everything about you."

### Writing as Infrastructure
In this model, writing isn't just documentation — it's the substrate AI agents operate on. Every note you write becomes:
- Reference material for future sessions
- Training context for understanding your voice/style
- Source material for pattern recognition

### The "Reflection + Setup" Barrier
> "99.99% of people won't do this because it requires reflection + setup."

Most people want instant gratification from AI tools. This approach requires:
- Discipline to write consistently
- Time to link notes and build the graph
- Willingness to structure knowledge

But once built, the agent "starts thinking in your voice."

### Markdown as the Standard
Greg's emphasis on markdown aligns with the broader "Markdown Manifesto" movement — plain text files are:
- Portable (not locked in proprietary formats)
- Future-proof (readable for decades)
- Version-controllable (git-friendly)
- AI-friendly (LLMs trained on markdown)

---

## How This Connects to Existing Patterns

### AGENTS.md Convention
This workflow is conceptually similar to [[skill-vs-agents-vs-claude-md]] — using markdown files to provide persistent context to agents. Obsidian becomes a personal-scale version of project-level AGENTS.md files.

### Second Brain / PKM Movement
Obsidian is a leading tool in the "Personal Knowledge Management" (PKM) space, building on ideas from:
- Zettelkasten (Niklas Luhmann's note-taking system)
- "Building a Second Brain" (Tiago Forte)
- Evergreen notes (Andy Matuschak)

The AI integration transforms PKM from "information retrieval" to "augmented execution."

### Claude Code Skills
This workflow essentially treats your Obsidian vault as a personal skill — persistent context that Claude Code loads to understand your projects, preferences, and patterns.

### The Design Repo Pattern
Similar to [[design-repo-pattern]] (draft post on keeping design inspiration separate from code), this approach advocates for a structured, version-controlled knowledge base that AI can query.

---

## Practical Implementation

### Tools Mentioned
- **Obsidian** — markdown-based note-taking with graph visualization
- **Obsidian CLI** — command-line interface for programmatic access
- **Claude Code** — AI coding agent that can read vault via CLI
- **Custom slash commands** — scripted workflows triggered by shortcuts

### Example Workflow
1. Morning: Write daily note in Obsidian
2. Link to relevant projects, people, ideas using `[[wiki-links]]`
3. Add a task: "Prepare pitch deck for Series A"
4. Claude Code reads:
   - `/context` → loads company info, financials, team
   - `/trace pitch-strategy` → sees how pitch evolved over months
   - `/connect fundraising` + `product-market-fit` → bridges domains
5. Claude generates draft deck based on vault context
6. Human reviews, edits, publishes

---

## Quotes

> "how to use obsidian + claude code to build a 24/7 personal operating system and build your startup"

> "stop reexplaining projects every session. use reference files instead."

> "human writes the vault. agents read it, suggest, execute."

> "let claude surface patterns you've been unconsciously circling for years."

> "markdown files are the oxygen of llms."

> "once the vault exists, the agent stops being generic. it starts thinking in your voice."

> "99.99% of people won't do this because it requires reflection + setup."

---

## Limitations & Considerations

### Privacy
Giving an agent access to your entire vault (daily notes, beliefs, meetings) raises questions about what gets sent to API endpoints. Need to ensure sensitive info isn't leaked.

### Maintenance Overhead
Requires consistent discipline:
- Writing daily notes
- Linking notes properly
- Organizing vault structure
- Updating reference files

If the vault gets stale, context degrades.

### Tool Lock-In (or Not?)
Obsidian stores notes as markdown files in a local folder — no lock-in. But the custom slash commands and CLI integrations are Obsidian-specific. Migrating to another tool means rebuilding those workflows.

### Context Window Limits
Even with a well-organized vault, there's a limit to how much an agent can load into context. Need strategies for:
- Selective loading (only relevant notes)
- Summarization (compress vault into key points)
- Incremental updates (agent remembers recent sessions)

---

## Related

- **[[skill-vs-agents-vs-claude-md]]** — markdown files as agent instructions (project-level vs personal-level)
- **[[anthropic-skills-guide]]** — official guide to building Claude skills (vault as a skill)
- **[[design-repo-pattern]]** — similar idea of structured, version-controlled knowledge base
- **[[harness-engineering-openai]]** — agents.md pattern at scale (repo-as-context)
- **Markdown Manifesto** — plain text > proprietary formats
- **Obsidian** — https://obsidian.md/
- **Personal Knowledge Management (PKM)** — Zettelkasten, Second Brain, Evergreen Notes

---

*Added: February 25, 2026*
