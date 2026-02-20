---
created: 2026-02-20
author: Justin Schroeder (@jpschroeder), Boyd (@0xboyd)
tags: [ai-agents, tmux, git-worktrees, parallel-agents, claude-code, codex, opencode, formkit]
---

# dmux — Parallel Agents with tmux and Worktrees

> Manage multiple AI coding agents in isolated git worktrees. Branch, develop, and merge — all in parallel.

![dmux.ai](https://screenshotit.app/http://dmux.ai/)

## Links

- **Website**: http://dmux.ai/
- **GitHub**: https://github.com/standardagents/dmux (formerly formkit/dmux)
- **Install**: `npm install -g dmux`
- **Docs**: https://dmux.ai (comprehensive)
- **Discord**: https://discord.gg/VGBx9dBYqy
- **Announcement**: https://x.com/jpschroeder/status/2024507517359788224

## What Is It

dmux is a dev agent multiplexer that runs multiple AI coding agents (Claude Code, Codex, OpenCode) in parallel using tmux and git worktrees. Each agent gets its own isolated working copy of your repo, so they can work simultaneously without conflicts.

> "Press `n` to create a new pane, type a prompt, pick an agent, and dmux handles the rest — worktree, branch, and agent launch."

From the team behind FormKit, Tempo, AutoAnimate, and Drag and Drop.

## What Problem Does It Solve

Running multiple AI agents on different tasks in the same repo causes conflicts — you can't easily test different approaches in parallel or compare agent outputs. dmux solves this by:

- **Isolating each agent in a git worktree** — full working copy, no conflicts
- **Orchestrating the entire lifecycle** — create worktree → launch agent → merge back → cleanup
- **Enabling A/B testing** — run two agents on the same prompt side-by-side and pick the winner

## Key Features

### Worktree Isolation
Each tmux pane gets its own git worktree and branch. Agents work in complete isolation. When done, press `m` to merge back into main.

### Multi-Agent Support
- **Claude Code** — Anthropic's agentic coding tool
- **Codex** — OpenAI's coding agent
- **OpenCode** — open-source coding agent

Automatically detects installed agents. If multiple are available, you can choose per-task.

### A/B Agent Pairs
Launch two agents on the same prompt side-by-side (e.g., "A/B: Claude Code + OpenCode"). Both get the same prompt in separate worktrees. Compare results, merge the winner, discard the other.

### AI-Powered Naming
Uses OpenRouter (gpt-4o-mini, grok-4-fast) to:
- Generate smart branch names from prompts (e.g., `fix-auth` instead of `dmux-1708542312`)
- Create conventional commit messages from diffs
- Detect agent state from terminal output

Falls back to timestamps if OpenRouter key not provided.

### Smart Merging
Two-phase merge to avoid conflicts on main:
1. Merge main → worktree (resolve conflicts in isolation)
2. Merge worktree → main (clean merge)
3. Auto-cleanup: remove worktree and branch

Auto-commits uncommitted changes before merging with AI-generated commit messages.

### Lifecycle Hooks
11 lifecycle hooks for custom automation:
- `worktree_created` — install dependencies
- `pre_merge` — run tests before merging
- `post_merge` — notify on completion
- `before_pane_create`, `pane_created`, `before_pane_close`, `pane_closed`, `before_worktree_remove`, `worktree_removed`, `run_test`, `run_dev`

AI-assisted hook authoring: press `h` and an agent walks you through creating hooks.

### Multi-Project Support
Attach multiple git repos to the same tmux session. Manage frontend + backend panes side-by-side. Automatically merges nested worktrees in the correct order (deepest first).

### Pane Status Detection
Monitors each agent to show real-time status:
- `in_progress` — actively working
- `open_prompt` — waiting for user input
- `option_dialog` — showing options

Uses lightweight LLM analysis (grok-4-fast, free) when activity stops.

### Autopilot Mode
Launch agents in fully autonomous mode:
- Claude Code: `--dangerously-skip-permissions`
- Codex: `--approval-mode full-auto`

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `n` | Create new pane (worktree + agent) |
| `t` | Create terminal pane (no agent) |
| `j` | Jump to pane |
| `m` | Open pane menu (merge, close, rename, etc.) |
| `x` | Close pane |
| `p` | Create pane in another attached project |
| `s` | Settings |
| `L` | Toggle sidebar layout mode |
| `h` | Create/modify hooks with AI |
| `q` | Quit |

## Quick Start

```bash
npm install -g dmux
cd /path/to/your/project
dmux
```

Press `n`, enter a prompt, pick an agent. dmux creates the worktree and launches the agent. Press `m` to merge when done.

## Tech Stack

Node.js · tmux · Git worktrees · OpenRouter (optional)

## Requirements

- tmux 3.0+
- Node.js 18+
- Git 2.20+
- At least one agent: Claude Code, Codex, or OpenCode
- OpenRouter API key (optional, for AI naming)

## Why It Matters

dmux represents a new primitive for agent orchestration: **parallel isolated execution with lifecycle management**. Instead of manually managing worktrees, branches, and agent coordination, dmux handles the entire flow. This is especially valuable for:

- **Agent comparison** — A/B test different agents on the same task
- **Parallel development** — run multiple tasks simultaneously without conflicts
- **Safe experimentation** — each agent is isolated; failed attempts don't affect main

The FormKit team built this as an internal tool for running "Codex and Claude Code swarms" and open-sourced it. The approach is complementary to tools like [[harness-engineering-openai]] which focus on single-agent scale, while dmux focuses on multi-agent orchestration.

## License

MIT

## Related

- **[[harness-engineering-openai]]** — OpenAI's approach to agent-first engineering (single agent at scale)
- **[[temporal-io-ai]]** — Workflow orchestration for agents (durable execution)
- **[[tmux]]** — The underlying terminal multiplexer dmux is built on
- **[[alfred-portable-openclaw]]** — Another approach to portable agent environments

---

*Added: February 20, 2026*
