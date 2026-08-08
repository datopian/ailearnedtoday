---
created: 2026-08-08
tags: [claude-code, automation, scheduling, cron, routines]
---

# Scheduling Claude Code Sessions

How to make a Claude Code session start later — in N hours, at a fixed time, or on a repeating schedule. Four mechanisms, two of them local, two of them cloud.

## The short answer

| Want | Use | Survives quitting Claude? | Runs local? |
|---|---|---|---|
| "Wake this session up in 5h" | `CronCreate` (one-shot) | ❌ no | ✅ yes |
| "Run every 5 min while I watch" | `/loop` | ❌ no | ✅ yes |
| "Run at 2am whether or not my laptop is on" | Cloud routine (`/schedule`) | ✅ yes | ❌ no |
| "Run on my machine at 2am, with my env/creds" | OS cron / launchd + `claude -p` | ✅ yes | ✅ yes |

## 1. `CronCreate` — schedule inside the live session

Ask Claude in-session: *"remind me in 5 hours to review the PR"*. Claude calls `CronCreate` with a pinned cron and `recurring: false`.

- Cron is 5-field, **local time**: `M H DoM Mon DoW`.
- Fires only while the REPL is idle (not mid-query).
- **Session-only.** Nothing on disk. Quit Claude → job gone.
- Recurring jobs auto-expire after 7 days.
- Scheduler adds jitter; avoid `:00`/`:30` minutes when the time is approximate.

Good for: "come back to this in a few hours" while the terminal stays open.
Bad for: anything that must survive a reboot.

## 2. `/loop` — self-paced or fixed-interval repetition

```
/loop 5m /check-deploys      # fixed interval
/loop                        # model self-paces via ScheduleWakeup (60s–3600s)
```

Same lifetime caveat: live session only. Use for polling something the harness can't notify on (CI, a deploy, a remote queue). Don't use it to poll background work Claude already tracks — that re-invokes automatically.

## 3. Cloud routines — the durable option

`/schedule` in Claude Code, or the web UI at <https://claude.ai/code/routines>.

Each routine spawns a **fully isolated cloud session** in Anthropic's infra: own sandbox, own git checkout, own tools. Your laptop can be off.

Two schedule shapes, exactly one per routine:

- `cron_expression` — 5-field, **UTC**. Minimum interval **1 hour** (`*/30 * * * *` is rejected).
- `run_once_at` — RFC3339 UTC timestamp, must be in the future. Fires once, then auto-disables.

For a one-shot in 5 hours: take now in UTC, add 5h, pass as `run_once_at`. Watch the timezone — the UI takes local time, the API takes UTC.

Key constraints:

- **No local access.** No local files, no local services, no local env vars. The prompt starts from zero context and must be self-contained.
- Repo comes from `job_config.ccr.session_context.sources[].git_repository.url`.
- External services need **MCP connectors** attached to the routine (Gmail, Drive, Calendar, etc.), managed at <https://claude.ai/customize/connectors>.
- Model defaults to `claude-sonnet-5`.
- You can create/list/update/run-now via the `RemoteTrigger` tool. **Deleting is web-UI only.**
- A fired one-shot shows `ended_reason: "run_once_fired"` ("Ran" in the UI); re-arm by updating with a new `run_once_at`.

Because the session is fresh and unattended, tell it explicitly what to produce — e.g. *open a PR*, not *fix things*.

## 4. OS scheduler + headless `claude`

When you need durability **and** the local machine (local creds, local DB, an app only running here):

```bash
# crontab -e  — 2am daily
0 2 * * * cd ~/src/datopian/ailearnedtoday && /usr/local/bin/claude -p "$(cat ~/prompts/nightly.md)" >> ~/logs/claude-nightly.log 2>&1
```

On macOS prefer **launchd** (a `~/Library/LaunchAgents/*.plist` with `StartCalendarInterval`) — cron on macOS is deprecated and doesn't run when the user isn't logged in. Either way: use absolute paths, and remember cron gets a minimal `PATH`/env, so source what you need explicitly.

## Choosing

- Machine must be involved → 4 (or 1 for short waits).
- Must run unattended overnight → 3.
- Just don't want to forget in an hour → 1.

## Related

- [[claude-dispatch]]
- [[boris-cherny-claude-code-tips]]
