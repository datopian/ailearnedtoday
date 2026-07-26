---
created: 2026-07-26
tags: [moc, loop-engineering, coding-agents, agent-loops, claude-code, codex, context-engineering, worktrees, skills]
---

# MOC: Loop Engineering

Map of Content for the practice of **loop engineering** — designing systems that prompt your coding agents on a loop, instead of prompting them turn-by-turn.

## Overview

Loop engineering is the discipline of building a small system that finds work, hands it out, checks it, records what's done, and decides the next thing — so the system pokes the agents rather than you doing it one turn at a time. The term was coined by Addy Osmani (June 2026), building on ideas from Boris Cherny (Claude Code) and Peter Steinberger (OpenClaw). It sits "one floor above" the agent harness: the harness is what a single agent runs inside; a loop runs on a timer, spawns helpers, and feeds itself.

### The five primitives (+ memory)

1. **Automations** — scheduled discovery/triage.
2. **Worktrees** — isolate parallel agents from each other.
3. **Skills** — codify project knowledge the agent would otherwise guess.
4. **Plugins/connectors** — plug the agent into your existing tools.
5. **Sub-agents** — one ideates, a different one verifies.
6. **Memory** — a markdown file / Linear board outside the conversation that holds what's done and what's next ("the agent forgets, the repo doesn't").

### Caveats that stay on you

- **Verification** is still yours — a loop makes mistakes unattended; "done" is a claim, not a proof.
- **Comprehension debt** — fast loops widen the gap between what exists and what you understand.
- **Cognitive surrender** — designing the loop is the cure when done with judgement, the accelerant when done to avoid thinking.

## Content in This Repository

### Essays & Overviews

- [[loop-engineering]] - Addy Osmani's definitional essay: the five primitives, the Codex-vs-Claude-Code capability table, `/loop` and `/goal`, and why loop design is harder than prompt engineering.
- [[brittany-ellich-loop-engineering]] - Brittany Ellich's real-world case study: 108 PRs in ~8 days via a protocol / loop / worker design with a markdown task-board, self-stopping `/loop`, and capped memory.

### Adjacent Practices & People

- [[boris-cherny-claude-code-tips]] - Claude Code head on writing loops that prompt Claude.
- [[trq212-claude-5-context-engineering]] - Context engineering for Claude 5; relevant to how little explicit instruction modern loops need.
- [[skill-vs-agents-vs-claude-md]] - Skills, agents, and CLAUDE.md as loop building blocks.

## Key Themes

### 1. From prompting to designing
The leverage point moved from writing the perfect prompt to designing the system that writes prompts. Same action (using agents), opposite posture (you stay the engineer).

### 2. Isolation & single-writers
Worktrees keep parallel agents from colliding; making the loop the only writer to the board/memory file prevents corruption when several workers run at once.

### 3. Self-terminating loops
A loop that can declare itself done (explicit stop condition, bare `/loop` with no interval) saves tokens and respects the human as the bottleneck.

### 4. The human moves to the ends
Effort shifts from reviewing code line-by-line to reviewing specs (what goes in the queue) and verifying outcomes (what comes out).

## External Resources

- Addy Osmani — [Loop Engineering](https://addyosmani.com/blog/loop-engineering/)
- Brittany Ellich — [108 PRs in Eight Days](https://brittany-ellich.offprint.app/a/3mrjj34puva23-108-prs-in-eight-days-accidentally-discovering-loop-engineering) · [loop-board (open source)](https://github.com/brittanyellich/loop-board)
- Peter Steinberger — "You should be designing loops that prompt your agents"
- Boris Cherny — "My job is to write loops"

---

*This MOC will grow as we document more loop-engineering practices, tools, and case studies.*
