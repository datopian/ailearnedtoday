---
title: How do I run multiple threads in Claude at the same time?
description: I don't want to wait on one Claude Code thread before starting the next — here's what's actually available today for running several at once on the same project.
date: 2026-08-26
---

**TL;DR:** There's no "multiple threads, one brain" mode. What you actually get is four bolt-on tricks — background subagents, git worktrees, an experimental teammates mode, and a dashboard so you stop staring at one terminal — and you'll probably end up duct-taping two of them together, same as everyone else.

I keep hitting the same friction: I ask Claude Code something, then I have to sit there while it works before I can ask the next thing. I want to be in it, but not serialized — fire off one question, fire off another, keep going, without waiting on each to finish. Maybe that's one session that somehow runs things in parallel. Maybe it's just several sessions open on the same folder at once. I wasn't sure which of these was even real, so here's what I found.

There are four different things "run multiple threads" can mean, and they solve different parts of the waiting problem.

**1. Subagents inside one session (the one I'm already using).** From a single Claude Code session you can dispatch several independent subagents in one message — a single "long prompt" that fans out into parallel work, exactly the mechanism you were guessing at. The newer twist is **forking**: a forked subagent inherits your whole conversation context and runs in the background, so you keep chatting in the foreground while it works, and its tool noise never fills your context — you just get a notification when it's done. This is the closest thing to "ask one question, then ask another, without waiting" *within* one thread. The limit: subagents report back to you, they don't talk to each other, and they're bounded to one instruction each — not an open-ended parallel conversation.

**2. Multiple sessions, same folder.** You can just open several `claude` terminals in the same project directory. It works, but they'll happily collide if two of them touch the same files at the same time. The fix is **git worktrees** — each session gets its own checkout of the repo on its own branch, so they can edit freely without stepping on each other, and you merge back when each is done.

**3. Agent Teams (experimental).** Claude Code's native multi-agent mode: one lead session spawns teammate sessions that work off a shared task list and can message each other directly, not just report to the lead. It can run across tmux or iTerm2 split panes, so you visually get several live Claude threads on screen at once, coordinating. This is the real answer to "one project, several threads talking to each other" — but it needs the `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` flag, and Anthropic itself flags rough edges around session resumption and status lag.

**4. Agent View, for not babysitting any of them.** If you background sessions (`/bg`, or `claude --bg "task"`), Agent View gives you one table of everything running — status, last response — and you can peek and reply inline without opening the full transcript. It doesn't split or assign work itself; it's the dashboard that stops you from needing five visible terminals to know what's happening.

So: the "long prompt that parallelizes for me" instinct was right — that's subagents/forking, and it already exists. For genuinely separate lines of work on the same project, worktrees plus multiple sessions (or Agent Teams if you want them coordinating) is the current answer, with Agent View so you're not stuck watching one pane at a time.

None of this is a manager that decides *what* to parallelize for you, though — that's the bigger question I'm chasing separately in [How do I run a fleet of coding agents?](/posts/2026-08-10-running-a-fleet-of-agents)
