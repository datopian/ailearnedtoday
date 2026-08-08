---
created: 2026-08-08
tags: [claude-code, automation, scheduling, cron, routines]
---

# Scheduling a Claude Code Session for Later

Two ways to have Claude pick work up at a future time. They differ on one axis that decides everything: **does the session keep its context, and does it survive quitting?**

| | Path A — Cloud routine | Path B — In-session wake-up |
|---|---|---|
| Where it runs | Anthropic cloud sandbox | Your terminal |
| Survives quitting Claude / reboot | ✅ yes | ❌ no |
| Has conversation context | ❌ none — starts cold | ✅ full |
| Local files / env / creds | ❌ no | ✅ yes |
| Prep needed | 10–20 min spec | ~1 min |
| Output | must be a commit/PR or it's lost | in your scrollback |

Rule of thumb: **unattended overnight → A. Continuing tonight's work with the laptop awake → B.**

---

## Path B — wake up the current session (step by step)

Requires: the terminal stays open, the machine stays awake, Claude not quit.

### 1. Start a session on a machine you can leave running

```bash
cd ~/src/datopian/ailearnedtoday
claude
```

### 2. Do the work as normal

Don't schedule first. Build up the context you want the future turn to inherit.

### 3. Set the wake-up — at any point, not just the start

Mid-session is fine, and usually better: the later you set it, the more context is banked for the wake-up. Just ask in plain language:

> remind me in 5 hours to pick this back up and finish the X entry

or pin an absolute time:

> at 2:30am, re-run the tests and summarise what's still failing

Claude calls `CronCreate` with `recurring: false` and a cron pinned to that minute/hour/day/month. The cron is **5-field local time** (`M H DoM Mon DoW`) — no UTC conversion.

### 4. Make the wake-up prompt self-contained *enough*

The session context is intact, but you'll be asleep. Say what "done" looks like so the turn doesn't stall waiting on you:

> in 5h: run the full test suite, fix any failures in `post-pipeline/`, commit on a branch `fix/pipeline-nightly` and open a PR. Don't ask me anything — if blocked, write what blocked you into the PR description.

### 5. Leave it alone

The job **only fires while the REPL is idle** — not mid-query. If Claude is still churning at fire time, it fires right after. Keep the terminal focused-or-not, doesn't matter; just don't quit and don't let the machine sleep.

```bash
# macOS: keep it awake for 6 hours
caffeinate -i -t 21600
```

### 6. Check / cancel

- "list my scheduled jobs" → `CronList`
- "cancel that job" → `CronDelete` with the job ID

### Gotchas

- **Session-only.** Nothing is written to disk. Quit Claude, close the terminal, or reboot → job gone, silently.
- Recurring jobs (if you make one) auto-expire after 7 days.
- The scheduler adds jitter: recurring fires up to 10% of the period late (max 15 min); one-shots landing on `:00`/`:30` fire up to 90s early. Ask for an odd minute when the exact time doesn't matter.

---

## Path A — cloud routine (durable, no local access)

Set up with `/schedule` in Claude Code, or the web UI at <https://claude.ai/code/routines>.

Each routine spawns a **fully isolated cloud session**: own sandbox, own git checkout, own tools. Your laptop can be off.

### Steps

1. Run `/schedule` → choose **create**.
2. Pick the schedule shape — exactly one of:
   - `run_once_at` — RFC3339 **UTC** timestamp, must be in the future. Fires once, then auto-disables.
   - `cron_expression` — 5-field **UTC**. Minimum interval **1 hour** (`*/30 * * * *` is rejected).
   Local → UTC conversion is on you (or Claude, but confirm it).
3. Confirm the repo (`job_config.ccr.session_context.sources[].git_repository.url`).
4. Attach any MCP connectors the task needs (Gmail, Drive, Calendar…). Manage them at <https://claude.ai/customize/connectors>.
5. Write the prompt — see spec checklist below.
6. Confirm and create. You get a routine ID: `https://claude.ai/code/routines/{ID}`.

### The spec you must write in advance

The cloud agent starts **cold**. It gets exactly two things: the repo contents, and your prompt. Everything this conversation knows has to be re-supplied.

1. **Entry point** — which file to read first (`AGENTS.md`, `SKILL.md`, a `NEXT.md`)
2. **The task** — concrete and bounded, not "advance the work"
3. **Done condition** — what artifact proves success
4. **Output mode** — explicit: branch name, open a PR
5. **Don't-touch list** — what it must not rewrite

Cheapest trick: keep the spec **in the repo** (a `NEXT.md` checkpoint), so the prompt shrinks to "read `NEXT.md`, do the top item, open a PR" — and it's reusable for every future run.

### Gotchas

- No local files, no local services, no local env vars.
- Output that isn't committed dies with the sandbox.
- Model defaults to `claude-sonnet-5`.
- Create / list / update / run-now via the `RemoteTrigger` tool; **deleting is web-UI only**.
- A fired one-shot shows `ended_reason: "run_once_fired"` ("Ran" in the UI). Re-arm by updating with a new `run_once_at`.

---

## Also worth knowing

- **`/loop`** — repeat a prompt on an interval (`/loop 5m /check-deploys`) or let the model self-pace (`/loop`). Same session-only lifetime as Path B. For polling things the harness can't notify on (CI, deploys, remote queues).
- **OS cron / launchd + `claude -p`** — durable *and* local, when you need machine creds or a local service. On macOS prefer launchd (`~/Library/LaunchAgents/*.plist`, `StartCalendarInterval`); cron there is deprecated and won't run when logged out. Use absolute paths — cron gets a minimal env.

## Related

- [[ai-work-next-action-checkpoints]]
- [[claude-dispatch]]
