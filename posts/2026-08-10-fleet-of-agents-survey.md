---
title: "Fleet of agents: a survey of orchestration tools (WIP)"
description: Optio, Paperclip, Gas Town, or Claude's own Agent Teams — which one actually manages a fleet of agents instead of just watching them? A field survey with a verdict.
date: 2026-08-10
updated: 2026-08-16
---

*This is a work in progress — first pass at the research, published as I go. Follow-up to [How do I run a fleet of coding agents?](/posts/2026-08-10-running-a-fleet-of-agents)*

![Vibe Kanban board for orchestrating AI coding agents](https://screenshotit.app/https://vibekanban.com/)

## TL;DR

| Option | What it coordinates | Automation depth | Best read on it |
| --- | --- | --- | --- |
| **Claude Code Agent Teams** | A lead plus collaborating Claude Code sessions | Shared tasks, dependencies and direct agent messaging; experimental | The strongest native multi-agent option, but Claude-only and local-session scoped |
| **Claude Code Agent View** | Your already-running Claude Code sessions | Visibility and inline replies only | A session dashboard, not an orchestrator |
| **Optio** | Tickets, isolated K8s agent runs, PRs and CI/review feedback | Runs the ticket-to-merged-PR loop, including automatic retries | The clearest fit for unattended, multi-repo delivery—if you accept Kubernetes |
| **Paperclip** | Agents in a Company → Project → Goal → Task hierarchy | Delegation, governance, budgets and tracking | Best match for an explicit, tool-agnostic manager layer |
| **Gas Town** | Claude Code workers and a durable Beads ledger | Persistent workers, handoffs and merge serialization | Most developed ledger/handoff model; also the most idiosyncratic |
| **GSD Core** | The workflow inside a coding-agent project | Structured discuss → plan → execute → verify → ship loop | Useful context/process discipline, but not a fleet control plane |

The field splits into roughly three tiers, matching the three questions from the framing post (break up work, review it, track it):

- **Native/built-in**: Claude Code now has both **Agent Teams** and **Agent View**. Agent Teams is the meaningful orchestration feature: a lead coordinates independent Claude sessions using a shared task list, dependencies and a mailbox. It is still experimental, local-state based, and Claude-only. Agent View is the smaller companion: a dashboard over sessions you already started, with status and inline replies.
- **Full lifecycle platforms**: **Optio**, **Paperclip**, and **Gas Town** are serious attempts at a manager layer that breaks work down, assigns it, tracks it, and enforces some governance. Optio is oriented around a ticket moving through an isolated agent run to a merged PR, with CI and review feedback fed back into the agent. Paperclip models work as an org chart (roles, budgets, approvals) and is explicitly tool-agnostic (Claude Code, Codex, Cursor, anything that can take a heartbeat). Gas Town is Claude-Code-specific, built on Steve Yegge's Beads ledger, with a Mad-Max-themed role hierarchy (Mayor, Polecats, Refinery, Witness). All are young and substantial systems: Optio assumes Kubernetes for its production path, Paperclip needs a Postgres-backed server, and Gas Town is notoriously idiosyncratic and burns real API budget.
- **Lighter kanban/TUI layer**: a long tail of smaller tools (Vibe Kanban, Agent Kanban, claude-squad, agent-deck, herdr, etc.) sit between the two — visual boards or terminal multiplexers over several parallel agent sessions, usually per-repo via git worktrees, without a "manager" that plans or delegates on its own.

For my actual question — a manager layer that farms out and splits work automatically, across Claude and Codex, with visibility into it all — **Paperclip and Optio are now the closest fits on paper**. Paperclip is the more general management model; Optio is the more concrete ticket-to-PR loop and explicitly supports both Claude Code and Codex. Gas Town remains the battle-tested-but-Claude-only alternative worth studying for its ledger/handoff model. Claude Agent Teams is a promising native option for one bounded piece of parallel work, but not yet a cross-repo fleet manager. Next step: stand up Paperclip or Optio against a real backlog and see what breaks.

---

## Appendix: tool by tool

### Claude Code Agent Teams (native, experimental)

[Agent Teams](https://code.claude.com/docs/en/agent-teams) is Claude Code's native multi-agent mode. One Claude Code session is the lead; it creates independent teammate sessions, assigns or lets them claim work from a shared task list, and the teammates can message one another directly. Tasks can have dependencies, and the team can run in one terminal or in tmux/iTerm2 split panes.

- **What it solves**: real collaboration within a single bounded piece of work—parallel research, competing debugging hypotheses, separate modules, or frontend/backend/test ownership. Unlike ordinary subagents, teammates retain independent contexts and can coordinate directly instead of reporting only to the caller.
- **What it does not solve**: it is not an always-on ticket/PR control plane. Team state lives locally under `~/.claude`; one lead can manage one team; teammates cannot create nested teams; and there is no Codex or cross-repository routing.
- **Status and cost**: it requires Claude Code v2.1.32+ and the `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` flag. Anthropic warns of limitations around session resumption, task-status lag, and shutdown; every teammate is a full Claude instance, so token use rises quickly.
- **Take**: much more than Agent View, and perhaps the easiest thing to try before installing a platform. Its useful boundary is *teamwork inside a run*, rather than fleet management across a backlog.

### Claude Code Agent View (native)

Research preview, launched 2026-05-11, ships in Claude Code itself (Pro/Max/Team/Enterprise/API, v2.1.139+).

- **What it is**: one table listing every active Claude Code session — status (working / waiting for input / done / idle), last response, timestamp. Press Space to peek at a session and reply inline without opening the full transcript; Enter opens the full transcript.
- **Backgrounding**: `/bg` pushes the current session to background; `claude --bg "<task>"` starts a new one without opening a foreground terminal.
- **What it doesn't do**: no task breakdown, no assignment, no cross-tool support. It's a viewer/responder for sessions you already spun up yourself — closer to a window manager than a manager-agent. Anthropic's own docs point people toward pairing it with external orchestration (e.g. "ClaudeFast Code Kit") for actual planning/dependency handling.
- **Take**: solves the "I can't see all my terminals" problem, not the "who decides what work happens next" problem.

### Optio (jonwiggins/optio)

Open-source, self-hosted orchestration for taking a ticket through to a merged pull request. It had **1,034 GitHub stars on 2026-08-16**. Its [Show HN announcement](https://news.ycombinator.com/item?id=47520220) is a useful articulation of the problem: too many concurrent Claude Code/Codex sessions, worktrees, and repositories leave the human as the bottleneck.

- **Intake and execution**: tasks can be entered manually or pulled from GitHub Issues, Linear, Jira, or Notion. Optio provisions an isolated environment per run and starts Claude Code, Codex, GitHub Copilot, Gemini, or OpenCode against a repository/worktree with per-repo prompts and models.
- **The feedback loop**: it polls PR status every 30 seconds, then feeds CI failures, merge conflicts, and reviewer change requests back into the appropriate agent. When the checks and review state are good, it squash-merges and closes the linked issue. That is the crucial difference from a board that merely launches sessions.
- **Beyond repo tasks**: reusable parameterized jobs can run on schedules, webhooks, or manually without a checkout; persistent named agents have inboxes and can wake from messages, webhooks, cron ticks, or ticket events.
- **Infrastructure**: Fastify API, Next.js UI, BullMQ, Drizzle/Postgres, and a Helm chart. Its reconciler is deliberately Kubernetes-shaped: periodic reconciliation and compare-and-swap execution aim to recover from missed events rather than leaving a run stuck.
- **Take**: closest fit where the desired unit is an issue/ticket and the desired outcome is a reviewed, merged PR—not simply a productive set of terminals. The trade-off is operational weight: it is designed around isolated pods and a cluster, so it is likely overkill for a single laptop workflow.

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

### GSD: original project and successor

[GSD — Get Shit Done](https://github.com/gsd-build/get-shit-done) is the older, highly adopted context-engineering/spec-driven workflow for Claude Code (**64,689 GitHub stars on 2026-08-16**). The repository is now archived and points to [Open GSD Core](https://github.com/open-gsd/gsd-core), which has its own [reference entry](/ref/gsd-core).

GSD Core keeps the central agent lean by making work explicit in a discuss → plan → execute → verify → ship loop, often using fresh-context subagents. It supports several coding-agent runtimes, including Claude Code and Codex. That makes it complementary to fleet orchestration: it improves the quality and continuity of work *inside* a project/run, but does not itself maintain a multi-repository ticket queue, watch PRs, or operate a merge loop.

Sources: [Gas Town — Steve Yegge](https://yegge.ai/gastown), [Welcome to Gas Town (Medium)](https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04), [Gas Town's Agent Patterns, Design Bottlenecks — Maggie Appleton](https://maggieappleton.com/gastown), [Steve Yegge's Gas Town comes to the cloud — The New Stack](https://thenewstack.io/steve-yegges-ai-agent-orchestration-project-gas-town-comes-to-the-cloud-and-brings-the-wasteland-with-it/), [paperclipai/paperclip on GitHub](https://github.com/paperclipai/paperclip), [Paperclip — the "Company OS" (Substack)](https://nervegna.substack.com/p/paperclip-the-company-os-your-agents), [Claude Code Agent Teams documentation](https://code.claude.com/docs/en/agent-teams), [Claude Code Agent View — claudefa.st](https://claudefa.st/blog/guide/agents/agent-view), [Anthropic Ships Agent View — NYU RITS](https://rits.shanghai.nyu.edu/ai/anthropic-ships-agent-view-a-multi-session-dashboard-for-claude-code/), [Optio on GitHub](https://github.com/jonwiggins/optio), [Optio Show HN](https://news.ycombinator.com/item?id=47520220), [GSD — Get Shit Done](https://github.com/gsd-build/get-shit-done), [Open GSD Core](https://github.com/open-gsd/gsd-core), [awesome-agent-orchestrators](https://github.com/andyrewlee/awesome-agent-orchestrators), [9 Open-Source Agent Orchestrators — Augment Code](https://www.augmentcode.com/tools/open-source-agent-orchestrators), [Vibe Kanban](https://vibekanban.com/), [Agent Kanban](https://agent-kanban.dev/)
