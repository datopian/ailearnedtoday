---
created: 2026-03-03
author: Artem Zhutov
tags: [claude-code, qmd, obsidian, memory, context, search, knowledge-management, ai-agents, recall-skill]
---

# Grep Is Dead: How I Made Claude Code Actually Remember Things

**Artem Zhutov's comprehensive guide (March 2026) on building a memory/context system for Claude Code using [[qmd]] search engine + Obsidian — solves the "every conversation starts from zero" problem with /recall skill.**

![Artem's Grep Is Dead article](https://screenshotit.app/https://x.com/ArtemXTech/status/2028330693659332615)

## Links

- **Article**: https://x.com/ArtemXTech/status/2028330693659332615
- **Published**: March 2, 2026
- **Author**: Artem Zhutov (@ArtemXTech)
- **Install /recall skill**: https://memory-artemzhutov.netlify.app/
- **Video walkthrough**: https://youtu.be/RDoTY4_xh0s (42 min with live demos)
- **QMD**: [[qmd]] by Tobias Lütke

## Overview

Deep dive into solving Claude Code's context problem: every conversation starts from zero. Solution: plug [[qmd]] (local search engine by Shopify CEO) into Obsidian vault, create /recall skill that loads full context before you type a word.

**The problem**: "I had 700 sessions in 3 weeks and I don't remember what was happening back then. I'm losing control in terms of what's happening."

**The solution**: Local search engine + skill that makes all past context searchable and recoverable.

## The Problem Visualized

**One week of work**:
- Every node is a session
- Every connection is a file it touched
- 700 sessions in 3 weeks
- "Every conversation with Claude Code starts from zero"
- Need to find context: what was the project, what are the decisions
- Worse mid-session: hit 60% context limit → compact or hand off → half the decisions lost
- Worse next day: "I don't remember what was happening back then"

**Zoomed in**:
- Every purple node: a conversation
- Every colored square: a file created/modified
- Skills, recipes, content drafts — all tangled together

**The paradigm doesn't scale**: "Grepping over files doesn't scale."

## The Solution Stack

```
┌─────────────────────────────────────┐
│ Claude Code + OpenClaw (top)        │ ← AI agents
├─────────────────────────────────────┤
│ /recall skill (middle)              │ ← Interface layer
├─────────────────────────────────────┤
│ QMD search engine (middle)          │ ← Search/retrieval
├─────────────────────────────────────┤
│ Obsidian vault (bottom)             │ ← Data layer
└─────────────────────────────────────┘
```

Context flows up from vault through QMD to Claude Code.

## QMD Integration

**Setup**:
- One QMD collection per vault folder (notes, daily entries, sessions, transcripts)
- One-to-one mapping
- Focused search per collection

**Why QMD**:
- Local search engine by Tobias Lütke (@tobi), Shopify CEO
- "Made in Canada"
- Indexes Obsidian vault
- Finds anything in under a second

## Grep vs BM25 vs Semantic: The Benchmark

**Searching for notes about "sleep"**:

### Grep (The Old Way)
- Takes 3 minutes
- "I was bored, scrolling Twitter while waiting"
- Returns 200 files
- All over the place
- Finds `sleep()` programming command (nothing to do with actual sleep)
- Pure string matching — no relevance

**Problem**: "That's the problem with string matching."

### BM25 (qmd search) - 2 seconds
- Deterministic full-text search
- Scores each file by:
  - How often word appears
  - How rare it is across all documents
- Short note mentioning "sleep" 5x scores higher than 10k-word file with one mention
- No AI, no embeddings — just math

**Results**:
- Reflection about sleep quality
- Experiment with tracking sleep fragmentation patterns
- Sleep interrupted at 3am
- Much better

**Limitation**: `qmd search "insomnia"` returns zero results (word doesn't exist in vault)

### Semantic (qmd vsearch) - Instant
- Uses embeddings to find meaning
- Search for concept even if exact words aren't there

**Test**: `qmd vsearch "couldn't sleep, bad night"`
- Found bedtime discipline goal set years ago
- 4 of 5 results don't contain search words at all
- "Grep could never find them"
- Goes beyond keywords, explores meaning

### Hybrid (qmd query) - Best Ranking
Query: "couldn't sleep, bad night"

**Results**:
- Sleep quality improvement: 89%
- Sleep interrupted at 3am: 51%
- Health sleep optimization: 42%
- Best ranking of all

**The progression**: "Grep catches strings, BM25 catches relevance, semantic catches meaning"

**Recommendation**:
- Start with BM25 (fast, handles structured notes, 80% of searches)
- Add semantic for transcripts and braindumps (where you'd never search for exact words)

## What Semantic Search Actually Surfaces

**Example query**: "find the days when I was happy and what was the reason"

**Non-trivial query** — Claude adapted it and ran multiple searches:

**Pattern discovered**:
- Happiest days: when shipping something AND good sleep recovery (sauna or 9 hours)

**Unexpected find**:
- October note about PhD thesis, about to give up
- "I just need to see it through discomfort instead of escaping to quick fixes"
- Complete forgot writing that
- Didn't expect search could surface this
- But there it was, exact citation

## /recall Skill: Three Modes

Sits on top of QMD. Loads context before you start working.

**Instead of**: Explaining to Claude what you were doing
**Just**: Tell it to recall

### 1. Temporal Mode

**Command**: `/recall yesterday` or `/recall last week`

**Example**: `/recall yesterday`
- Reconstructed 39 sessions from one day
- Timeline
- Number of messages in each session
- What was done when
- Each row shows time, message count, what you were working on
- Can go back to any of them

### 2. Topic Mode

**Command**: `/recall topic [query]`

**Example**: `/recall topic graph`
- BM25 search across QMD collections
- Returned dashboard, production plan, to-do list
- All related files surfaced in less than a minute

**Compare to brute force**:
- Tell Claude "find all information about this project"
- Sends Haiku to grep through vault for 3 minutes
- Burns tokens
- Comes back with worse results

**With /recall topic**: Reconstructed full state of project, asked "what is the next highest leverage action?"

### 3. Graph Mode

**Command**: `/recall graph` or `/recall graph last week`

**What it shows**:
- Interactive visualization of whole week
- Sessions as colored blobs
- Older ones dimmer
- Recent ones highlighted in purple
- Files clustered by type: goals, research, voice, docs, content, skills

**Example use**:
- Was exploring lunch places
- Told Claude "I want to have a great lunch"
- Analyzed different places, stored as activities to try
- Week later: open graph, see that session
- Copy file paths into Claude Code
- Continue from there

**The value**: "The graph makes every past conversation recoverable."

**Graph controls**:
- Filter by time range
- Color-coded by file type
- Older sessions fade to dimmer purple
- Recent ones glow bright
- Hover to highlight connections
- Click to select

## 700 Sessions, All Searchable

**Problem**: Claude Code saves all conversations as JSONL files on your computer
- 700 sessions in last 3 weeks
- Each has decisions, questions, context needed again
- Raw files have tool uses, system prompts, roles

**Solution**:
- Parse into clear markdown (actual signal, actual user messages)
- Embed into QMD index
- At end of each session when closing terminal: hook fires
- Exports and embeds sessions into QMD
- "So the index is always fresh"
- "I can get back to anything I had even from today"

## Finding Ideas You Never Acted On

**Query**: "find the ideas that I have never acted on"

**Why Claude synthesis is useful**: "It's hard to parse the actual raw results yourself"

**What Claude found**:
- October 19th: wanted to build PhD writing dashboard, never did
- Had ideas for illustration-based apps, never followed through
- Idea to record screen recording about full Obsidian workflow, never committed

**Dates, ideas, things written months ago and completely forgot about.**

**Key point**: "And it's all local — all of these embeddings live on your computer."

## Tools Change. Your Context Stays.

**Core philosophy**:

> "Your notes stop being passive. They stop being trapped in your Obsidian world. They actually start doing things. All of your notes is useful context about yourself that you can use to achieve goals in your life."

**Future-proof**:
> "Tools change. A month from now there are going to be new models. So what. If you have your context you can make it work in any situation. Claude Code, Codex, Gemini CLI, anything."

**Memory layer works as skill**: Across your whole stack.

**Sync setup**:
- Obsidian Sync keeps vault in sync between Mac and Mac Mini
- Mac Mini always on with OpenClaw running 24/7
- Pick up phone, open OpenClaw
- Same vault, same QMD index, same skills — from anywhere

## The Full Stack

```
┌────────────────────────────────────────┐
│  Claude Code        OpenClaw (top)     │
├────────────────────────────────────────┤
│  /recall skill (interface)             │
├────────────────────────────────────────┤
│  QMD search engine (by Tobi Lütke)     │
├────────────────────────────────────────┤
│  Obsidian vault (bottom)               │
└────────────────────────────────────────┘

Context flows up ↑
```

## Next Steps (From Article)

1. **Download /recall skill**:
   - Drop in `.claude/skills/` folder
   - Session pipeline and recall working today
   - Or ask Claude to do it for you

2. **Get QMD**:
   - Search engine behind all of this
   - By Tobias Lütke
   - https://github.com/tobi/qmd

3. **Watch full video**:
   - 42 min walkthrough with live demos
   - https://youtu.be/RDoTY4_xh0s

## Key Insights

### On Context Loss

> "Every conversation with Claude Code starts from zero. I had 700 sessions in 3 weeks and I don't remember what was happening back then. I'm losing control in terms of what's happening."

### On Grep's Limitations

> "The current paradigm of grepping over files doesn't scale."

### On Search Quality

> "Grep matches strings, QMD ranks by relevance."

### On Semantic Power

> "I searched my daily notes: 'find the days when I was happy and what was the reason.' This is a non-trivial query."

### On Forgotten Insights

> "I didn't remember writing that. I didn't expect the search could surface this. But there it was, the exact citation."

### On Future-Proofing

> "Tools change. A month from now there are going to be new models. So what. If you have your context you can make it work in any situation."

## Technical Implementation

**Session export hook**:
- Runs when closing terminal
- Parses JSONL into markdown
- Embeds into QMD
- Index always fresh

**QMD collections**:
- One per vault folder
- Notes, daily entries, sessions, transcripts
- One-to-one mapping
- Focused search per collection

**Obsidian Sync**:
- Keeps vault in sync across devices
- Works with Mac Mini running OpenClaw 24/7
- Mobile access via OpenClaw

## Comparison to Default Claude Code Search

**Default way** (brute force):
- Sends Haiku sub-agent to grep through every file
- Takes 3 minutes
- 300 files, not great results
- Lots of tokens burned

**QMD way**:
- Instant
- Better results
- Way fewer tokens
- No sub-agents needed

## Use Cases Shown

1. **Recovering project context**: `/recall topic graph` → full project state
2. **Temporal review**: `/recall yesterday` → 39 sessions with timeline
3. **Finding patterns**: "days when I was happy" → shipping + sleep recovery
4. **Rediscovering ideas**: "ideas never acted on" → PhD dashboard, illustration apps
5. **Visual exploration**: Graph mode → see week's work, click to recover any session
6. **Lunch planning**: Past lunch exploration → continue conversation week later

## Why It Matters

**Solves fundamental problem**: Context loss in AI coding agents
- Every conversation starting from zero
- Can't remember what happened weeks ago
- Decisions lost mid-session (context limit)
- Can't continue next day

**Enables new workflows**:
- Persistent memory across sessions
- Searchable conversation history
- Visual session graphs
- Semantic discovery of forgotten insights

**Local-first**:
- All embeddings on your computer
- No API calls for search
- Privacy preserved
- Works offline (after model download)

**Tool-agnostic**:
- Works as skill across any agent
- Future-proof against model changes
- Context is portable

## Author Context

**Artem Zhutov** (@ArtemXTech):
- Heavy Claude Code user (700 sessions in 3 weeks)
- Built comprehensive memory system
- Documented with 42-min video walkthrough
- Created /recall skill for community
- Published detailed article (Mar 2, 2026)
- 667.9K views, 7.6K bookmarks

## Metrics

- **Sessions**: 700 in 3 weeks
- **Search speed**: Under 1 second (vs 3 minutes grep)
- **Yesterday recall**: 39 sessions reconstructed
- **Article engagement**: 667.9K views, 2.2K likes, 7.6K bookmarks

## Related

- [[qmd]] - The search engine powering this system
- [[obsidian]] - Vault/note-taking layer
- Claude Code - Agent being enhanced
- OpenClaw - 24/7 running environment
- Knowledge management
- AI agent memory systems
- Context persistence

## Significance

**First comprehensive solution** to Claude Code context loss:
- Not just theoretical — working system with 700 sessions
- Video walkthrough shows real usage
- Skill available for others to use
- Combines local search + vault sync + agent skills

**Demonstrates power of**:
- Local-first AI tools
- Persistent context layers
- Semantic search for personal knowledge
- Visual session graphs

**Aligns with trends**:
- [[hbr-ai-intensifies-work]] - Need to manage increasing AI workload
- [[agent-psychosis]] - Need for structure in AI workflows
- [[karpathy-december-coding-agents-breakthrough]] - Agents capable enough to need memory

## By

Artem Zhutov (@ArtemXTech)
