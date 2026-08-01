# Can I schedule Claude Code for when my usage resets?

I had a practical question: if I have exhausted my Claude Code allowance and the next usage window starts in three hours, can I queue useful work now and have Claude begin when the allowance returns?

![Claude Code scheduled tasks](https://screenshotit.app/https://code.claude.com/docs/en/scheduled-tasks)

Yes. Claude Code now has two native options: a cloud Routine created from the terminal, or a local scheduled task in Claude Desktop. The choice is mostly about where the code lives when the task begins.

## Option 1: schedule a cloud session from the terminal

First, check the actual reset time rather than guessing:

```text
/usage
```

Then create a one-off [cloud Routine](https://code.claude.com/docs/en/web-scheduled-tasks), ideally a few minutes after the displayed reset:

```text
/schedule today at 3:05pm, continue implementing the authentication flow in
github.com/me/my-project. Run the tests and open a pull request, but do not
deploy or merge anything.
```

Claude asks for missing details and confirms the absolute run time. Anthropic then starts a fresh Claude Code cloud session, even if my laptop is asleep.

The important word is *fresh*. A cloud Routine clones the repository from GitHub, starting from its default branch unless told otherwise. It cannot see uncommitted changes or pick up the exact local conversation. I therefore need to commit and push anything it depends on, and make the prompt self-contained.

Cloud Routines run without permission prompts, so boundaries such as “do not deploy,” “do not merge,” and “stay on this branch” should be explicit.

One-off `/schedule` support is still rolling out. If it is unavailable—or I have already hit the limit—I can create the same Routine at [claude.ai/code/routines](https://claude.ai/code/routines).

## Option 2: schedule against my local working tree

If the task needs uncommitted files, local tools, or the exact checkout on my Mac, the better route is a [Claude Desktop local scheduled task](https://code.claude.com/docs/en/desktop-scheduled-tasks).

In Claude Desktop:

1. Open **Code**, start a **Local** session, and select the project folder.
2. Ask Claude: “Create a one-time local scheduled task for 3:05pm. Continue implementing the authentication flow, run the tests, and leave the changes for review. Do not push or deploy.”
3. Open **Routines** in the sidebar and inspect the new task: folder, instructions, model, permission mode, and scheduled time.
4. Click **Run now** once if I want to discover permission prompts in advance. For tools the task genuinely needs, I can choose “always allow” so the scheduled run does not stall waiting for me.
5. Leave Claude Desktop open and keep the computer awake. On macOS, **Settings → Desktop app → General → Keep computer awake** prevents idle sleep, although closing the laptop lid still puts it to sleep.

I can also begin with **Routines → New routine → Local** and fill in the details there. For a one-off time rather than a recurring preset, asking Claude in a Desktop session is simplest.

By default the task sees the selected folder, including uncommitted changes. I would leave the optional worktree isolation off when the point is to continue unfinished local work.

If the Mac sleeps through the scheduled time, Desktop may start one catch-up run after it wakes, but it will not run on time.

## Which one should I use?

| | Cloud Routine | Desktop local task |
|---|---|---|
| Laptop may be off | Yes | No |
| Sees uncommitted local changes | No | Yes |
| Starts from | Fresh repository clone | Selected local folder |
| Permissions | Runs autonomously | Configurable; may wait for approval |

My rule of thumb: use a cloud Routine when the relevant work is committed and pushed; use a Desktop local task when Claude needs the current working tree.

Scheduling does not bypass Claude's limits. The future run still consumes normal subscription usage and will be rejected if no allowance is available. The trick is to read the reset time from `/usage`, schedule a few minutes after it, and let the next window start with useful work.
