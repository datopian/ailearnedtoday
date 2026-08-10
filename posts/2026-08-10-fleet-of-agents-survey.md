---
title: "Fleet of agents: a survey of orchestration tools (WIP)"
description: A first pass through Gas Town, Paperclip, Claude Code's native Agent View, and the rest of the agent-orchestration field — answering the question posed in the previous post.
date: 2026-08-10
---

*This is a work in progress — first pass at the research, published as I go. Follow-up to [How do I run a fleet of coding agents?](/posts/2026-08-10-running-a-fleet-of-agents)*

## TL;DR

The field splits into roughly three tiers, matching the three questions from the framing post (break up work, review it, track it):

- **Native/built-in**: Claude Code's **Agent View** (research preview, May 2026) gives a single dashboard over your own concurrent Claude Code sessions — status, inline reply, background sessions. It's supervisory only: it doesn't break work up or hand it off, it just lets you see and answer sessions you already started. No cross-tool support (Claude only).
- **Full "company" platforms**: **Paperclip** and **Gas Town** are the two serious attempts at the whole loop — a manager layer that breaks work down, assigns it, tracks it, and enforces some governance. Paperclip models this as an org chart (roles, budgets, approvals) and is explicitly tool-agnostic (Claude Code, Codex, Cursor, anything that can take a heartbeat). Gas Town is Claude-Code-specific, built on Steve Yegge's Beads ledger, with a Mad-Max-themed role hierarchy (Mayor, Polecats, Refinery, Witness). Both are young, both are heavy — Paperclip needs a Postgres-backed server, Gas Town is notoriously idiosyncratic and burns real API budget.
- **Lighter kanban/TUI layer**: a long tail of smaller tools (Vibe Kanban, Agent Kanban, claude-squad, agent-deck, herdr, etc.) sit between the two — visual boards or terminal multiplexers over several parallel agent sessions, usually per-repo via git worktrees, without a "manager" that plans or delegates on its own.

For my actual question — a manager layer that farms out and splits work automatically, across Claude and Codex, with visibility into it all — **Paperclip is the closest fit on paper** (tool-agnostic, explicit task-breakdown hierarchy), with **Gas Town** as the more battle-tested-but-Claude-only alternative and worth watching for its ledger/handoff model even if I don't adopt it directly. Claude's own Agent View is useful but solves a smaller problem (visibility, not delegation). Next step: actually stand up Paperclip or Gas Town against a real backlog and see what breaks.

---

## Appendix: tool by tool

### Claude Code Agent View (native)

Research preview, launched 2026-05-11, ships in Claude Code itself (Pro/Max/Team/Enterprise/API, v2.1.139+).

- **What it is**: one table listing every active Claude Code session — status (working / waiting for input / done / idle), last response, timestamp. Press Space to peek at a session and reply inline without opening the full transcript; Enter opens the full transcript.
- **Backgrounding**: `/bg` pushes the current session to background; `claude --bg "<task>"` starts a new one without opening a foreground terminal.
- **What it doesn't do**: no task breakdown, no assignment, no cross-tool support. It's a viewer/responder for sessions you already spun up yourself — closer to a window manager than a manager-agent. Anthropic's own docs point people toward pairing it with external orchestration (e.g. "ClaudeFast Code Kit") for actual planning/dependency handling.
- **Take**: solves the "I can't see all my terminals" problem, not the "who decides what work happens next" problem.

### Gas Town (Steve Yegge)

Released 2026-01-01, Go-based, open source, built on Yegge's earlier **Beads** project (a version-controlled work-item ledger).

- **Roles**: Mad-Max-themed hierarchy — **Mayor** (chief-of-staff, coordinates across rigs), **Polecats** (worker agents, persistent identity + ephemeral sessions), **Witness** (watches polecat activity per rig, i.e. monitoring), **Refinery** (merge-queue processor, serializes merges so parallel agents don't collide), **Deacon** (maintenance). Designed to run 20-30 parallel agents productively, commonly over tmux.
- **Work model**: work is defined as **formulas** (reusable recipes/templates) that polecats execute; every unit of work — task, fix, merge request, an agent's own note — becomes a **bead** in the ledger. This is what gives it durable memory and handoff across sessions/crashes: the ledger is the source of truth, not any one agent's context window.
- **Status**: the Witness plus the ledger itself serve as the status view — it's queryable, auditable history rather than a live dashboard in the Paperclip/Agent-View sense.
- **Scope**: Claude-Code-specific in practice (Yegge built it for his own Claude Code-heavy workflow); a cloud version has since shipped too.
- **Known problems** (per critical writeups, e.g. Maggie Appleton's): grew reactively rather than being designed up front — "a stream of consciousness converted directly into code" — resulting in a steep, idiosyncratic learning curve (polecats/deacons/mayors/molecules/witnesses all mean different things). Speed without guardrails means it's easy to prompt your way into architectural messes faster than you can review them. Reported to burn "thousands of dollars a month" in API spend for Yegge's own usage.
- **Take**: the most thought-through model of *durable memory + handoff + merge serialization* I found, and worth studying even if the tool itself is rough. The ledger-as-source-of-truth idea (vs. dashboard-as-source-of-truth) is the interesting bit for the memory/state question from the framing post.

### Paperclip (paperclip.ing / paperclipai/paperclip)

Launched 2026-03-02 by a pseudonymous dev (@dotta), open source, crossed 30k GitHub stars in three weeks, ~76k stars and 3,520 commits as of this writing — one of the fastest-growing agent-orchestration projects released so far.

- **Model**: "if [an individual coding agent] is an employee, Paperclip is the company." Agents get roles, titles, reporting lines, and budgets inside an explicit org chart, rather than being dispatched ad hoc.
- **Work breakdown**: hierarchy of **Company → Project → Goal → Task**. Tasks carry goal ancestry (so an agent picking up a task inherits the *why*, not just the *what*), atomic checkout prevents two agents grabbing the same task, and there are first-class blocker/dependency links between tasks.
- **Governance**: approval workflows, review/approval stages, decision tracking, budget hard-stops, and the ability to pause/resume/terminate an agent, all with full audit logging.
- **Status/monitoring**: real-time dashboard (React UI) with a mobile-ready view, cost tracking by agent/project/goal, token budgets with hard stops.
- **Tool support**: explicitly adapter-agnostic — Claude Code, Codex, Cursor, raw Bash, HTTP-based agents. Their line: "if it can receive a heartbeat, it's hired."
- **Infra**: self-hosted Node.js 20+ / pnpm 9.15+ server, Postgres (embedded by default or external), local or cloud object storage. Single process is enough for small deployments.
- **Maturity/gaps**: plugins, schedules, budget controls, multi-company isolation are shipped; memory/knowledge systems, desktop apps, and bring-your-own-ticket-system integration are still in progress.
- **Take**: closest match to "AI manager that farms out and splits work, across tools, with tracking" from the framing post. Heavier to stand up than the TUI tools, but the Company/Project/Goal/Task model maps directly onto "break a design into parts, hand them off, track status."

### The lighter layer (kanban boards & TUI multiplexers)

Cataloged well by [andyrewlee/awesome-agent-orchestrators](https://github.com/andyrewlee/awesome-agent-orchestrators). Rough groups, for reference rather than deep-dived yet:

- **Kanban boards for agents**: [Vibe Kanban](https://vibekanban.com/) (now community-maintained, was sunsetting as a commercial product), [Agent Kanban](https://agent-kanban.dev/) (open-source, leader agent plans/assigns, workers claim tasks and ship PRs — for Claude Code, Codex, Gemini CLI, Copilot, Hermes).
- **Terminal multiplexers over parallel sessions**: claude-squad, agent-deck, dmux, herdr, amux, repomon — mostly "one agent per git worktree, tmux underneath, live status in a TUI." No planning/delegation layer; you still decide what each agent works on.
- **Autonomous loop runners**: ralph-claude-code, ralphex, bernstein, fractal, Dex — closer to "keep one agent looping against a task list with retries/validation" than fleet management per se, but relevant to the "how does the loop keep rolling" question.
- **Issue-tracker-triggered**: cyrus (watches Linear/GitHub/GitLab issues, spins up an isolated worktree+agent per issue), sortie, claude-code-action / codex-action (official GitHub Actions from Anthropic/OpenAI for CI-triggered runs).

Haven't stood any of these up yet — next pass should actually run Paperclip and/or Gas Town against a real piece of backlog and report what breaks.

Sources: [Gas Town — Steve Yegge](https://yegge.ai/gastown), [Welcome to Gas Town (Medium)](https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04), [Gas Town's Agent Patterns, Design Bottlenecks — Maggie Appleton](https://maggieappleton.com/gastown), [Steve Yegge's Gas Town comes to the cloud — The New Stack](https://thenewstack.io/steve-yegges-ai-agent-orchestration-project-gas-town-comes-to-the-cloud-and-brings-the-wasteland-with-it/), [paperclipai/paperclip on GitHub](https://github.com/paperclipai/paperclip), [Paperclip — the "Company OS" (Substack)](https://nervegna.substack.com/p/paperclip-the-company-os-your-agents), [Claude Code Agent View — claudefa.st](https://claudefa.st/blog/guide/agents/agent-view), [Anthropic Ships Agent View — NYU RITS](https://rits.shanghai.nyu.edu/ai/anthropic-ships-agent-view-a-multi-session-dashboard-for-claude-code/), [awesome-agent-orchestrators](https://github.com/andyrewlee/awesome-agent-orchestrators), [9 Open-Source Agent Orchestrators — Augment Code](https://www.augmentcode.com/tools/open-source-agent-orchestrators), [Vibe Kanban](https://vibekanban.com/), [Agent Kanban](https://agent-kanban.dev/)
