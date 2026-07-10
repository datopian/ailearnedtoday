---
created: 2026-07-10
author: Prajwal Tomar (@PrajwalTomar_)
tags: [hermes-agent, ai-agents, autonomous-agents, persistent-memory, ai-coding]
---

# Hermes Agent: The Autonomous AI Agent Playbook

A practical guide to setting up Hermes Agent for persistent memory, self-created skills, multi-profile workflows, and autonomous execution.

![Hermes Agent playbook](https://screenshotit.app/https://x.com/PrajwalTomar_/article/2064324584254710262)

## Links

- **Original article:** https://x.com/PrajwalTomar_/article/2064324584254710262
- **Author:** Prajwal Tomar (@PrajwalTomar_)
- **Hermes Agent:** https://github.com/NousResearch/hermes-agent

## Article

Most builders open a new Claude Code session and spend the first ten minutes re-explaining their stack.
Some are paying for three different agents (Cursor, Claude Code, Codex) and still losing every Friday afternoon to context drift.
And then there's a small group quietly running Hermes Agent on a $5 server. The agent remembers them. It writes its own skills. It steers itself overnight. They wake up to finished work.
The gap is getting wider every week.
I've spent the last few weeks going deep on Hermes Agent. Reading every doc, watching every breakdown, testing the setup, and listening to the builders running it 24/7. This article is the synthesized playbook.
At @ignytlabs we have shipped 60+ MVPs in the last 1.5 years. We test every major agent platform that drops because the wrong stack costs us calendar days on every client project. Hermes Agent is the first one we've started running alongside Claude Code. The difference is starting to show.
Here is the full breakdown of what Hermes Agent actually is, why it is suddenly everywhere right now, and the exact setup that takes 30 minutes to deploy and 6 months to fully compound.
## What Hermes Agent Actually Is
Quick context before we get into the setup.
Hermes Agent is an open-source autonomous AI agent built by Nous Research. Same lab behind the Hermes, Nomos, and Psyche model families. Launched February 2026. MIT licensed. Roughly 185K stars on GitHub at the time of writing.
This is the part most builders miss. Hermes is not "Claude Code 2.0." It's not a coding tool. It's a fundamentally different category of agent.
Here is the cleanest way to think about it. Claude Code, Cursor, Codex, and OpenClaw are session-based agents. You open them. You give them a task. You close them. Next time you open them, they start from zero. They forget your stack. They forget your conventions. They forget the call you had with the client yesterday.
Hermes is the opposite. It lives on a server. It runs 24/7. It remembers every conversation. It writes its own skill files after every task. It reaches you on Telegram. The longer you run it, the less you spend re-explaining anything.
The official Nous Research tagline says it cleanly. "Not a chatbot. Not a copilot. An agent that lives on your machine and gets smarter every day."
The five things that make it different from every other agent platform on the market.
-  Persistent memory across sessions (FTS5 full-text search and LLM summarization on every conversation you've ever had with it)
-  Autonomous skill creation (after every task, it writes what worked and what didn't into a markdown skill file)
-  Multi-profile architecture (you can run a Chief of Staff, a Head of Research, and a Head of Content as separate agents in parallel)
-  Multi-platform reach (Telegram, Discord, Slack, WhatsApp, Teams, plus 20+ other messaging platforms)
-  Server-resident execution (runs on a $5 VPS, a GPU cluster, or serverless infrastructure like Modal or Daytona that costs nearly nothing when idle)
That is the agent. Now here is why this is suddenly everywhere.
Hermes Desktop officially launched the first week of June 2026. The same week, NVIDIA announced they had post-trained Nemotron Ultra specifically for Hermes Agent. The conversation crossed a threshold.
This is the article that breaks down what you actually need to know.
## The Problem With How Most People Use AI Agents Right Now
Here's what most builders do.
They open Claude Code. They re-explain their stack for the tenth time this week. They paste their conventions. They paste the client's brief. They ship a feature. They close the tab. Next morning, the session is gone. They re-explain everything again.
In parallel, they have Cursor open in another window. They have Codex running for backend work. Maybe they have OpenClaw for a specific niche tool. Each one starts from zero. Each one needs the same context dump every morning.
This is what people mean when they say "AI tooling is exhausting."
The model isn't the problem. Opus 4.8 is excellent. GPT-5.5 is excellent. The problem is the architecture. Every session-based agent assumes you'll re-pour the context every time. None of them are built to compound across days, weeks, or months. So your knowledge stays trapped in chat history that gets summarized and lost.
Hermes is the first agent platform built around the assumption that the agent itself should be the long-running entity, not the conversation.
You set it up once. You give it your goals. You give it your stack. You give it your tone. Then you let it run. Six weeks in, you stop noticing how much faster everything moves because re-explaining context has stopped being part of your workflow.
This is the unlock. Now here is how to actually set it up.
### Step 1: Install Hermes and Set Up Your First SOUL .md
This is the first thing you set up. It's also the part most builders skip on day one and regret two weeks later.
Installation is one curl command. Works on Linux, macOS, WSL2, or native Windows.
```sh
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```
For Windows via PowerShell, there is an install.ps1 variant in the same repo. For Android via Termux, the same curl command works because the installer detects Termux automatically.
Once installed, you start with hermes. The first thing it does is auto-seed a starter SOUL .md at ~/.hermes/SOUL.md. This is the file that defines who your agent is.
SOUL .md occupies slot #1 in the system prompt. It replaces the built-in default identity entirely when you fill it in. This is not project-specific (that's what AGENTS .md is for). SOUL .md is the durable identity of the agent itself. Its tone. Its style. Its defaults. Its boundaries.
The official Nous Research docs publish a canonical example you can paste in to start with.
Four sections:
-  Personality. Who the agent is. ("You are a pragmatic senior engineer with strong taste.")
-  Style. How it should sound. ("Be direct without being cold. Push back when something is a bad idea.")
-  What to avoid. ("Sycophancy. Hype language. Overexplaining obvious things.")
-  Technical posture. ("Prefer simple systems over clever systems.")
That's the official template. Twenty lines that change every session your agent has, forever.
The single-rule safety net every builder should bake into their SOUL .md from day one is this line. "Never send money to anyone without explicit confirmation." One rule, most of the personal-use risk covered.
The wider shift is that the conversation has moved on from CLAUDE .md to SOUL .md being the leverage file. Same idea, new file, different agent.
### Step 2: Pick Your Model Tier
Hermes is provider-agnostic. You can swap models anytime with hermes model. No reinstall needed.
The community has converged on three practical tiers.
-  Default daily driver. GPT-5.5 via your existing $20/month ChatGPT subscription. This is where you start.
-  Premium reasoning. Claude Opus 4 or Sonnet 4 via API key for complex multi-step tasks. Budget a few hundred dollars per month under heavy use.
-  Long-horizon autonomy. Qwen 3.7 Max via OpenRouter. Reports of 35 hours of continuous execution with 1,000+ tool calls without context loss for long overnight runs.
If you don't want to manage three different bills, Nous Portal is a flat $20/month for OAuth-based access to multiple models in one place.
The default I'd start anyone on. GPT-5.5 for daily work. Add a Claude API key for the /goal runs. Skip everything else until you actually need it.
```sh
hermes model
```
Run this anytime to switch. The skill files and memory don't care which model you're on. They carry over.
### Step 3: Connect Telegram in 5 Minutes
This is the step that feels optional and isn't.
Hermes supports 20+ messaging platforms (Telegram, Discord, Slack, WhatsApp, Teams, plus others). Use Telegram. It's the only one actively building for agent-to-agent communication right now, and the setup is five minutes.
The full setup is literally three steps.
-  Open Telegram. Search for @BotFather. Type /newbot. Follow the prompts. Copy the bot token.
-  Paste the token into Hermes during the initial setup wizard (or later via hermes config).
-  Send your bot a first message. Who you are. What you're building. Your goals for the next three to six months.
That first message is the part that matters. It goes straight into the agent's memory. It filters every proactive task the agent generates from that point forward. Skip this and the agent is working blind.
The actual unlock that hits people the first time. You can now check on your agents from your phone. You can give them new tasks while sitting on the couch. You can review what they did overnight while making coffee. The agent doesn't care which device you're on.
You can be at dinner and check on 6 agents from your pocket. The work continues without you watching. That is the unlock.
### Step 4: Set Up Profiles for Your Org Chart
This is where the workflow stops looking like prompting and starts looking like an actual operating system.
A Hermes profile is a fully isolated agent with its own SOUL .md, its own memory, its own skill library, and its own configured model. Multiple profiles run in parallel. Each one specializes independently as it accumulates skills.
The pattern most builders are converging on is the org chart. You create profiles that mirror the team you would hire if you were funded.
```text
~/.hermes/profiles/chief-of-staff/SOUL.md
```
```text
~/.hermes/profiles/head-of-research/SOUL.md
```
```text
~/.hermes/profiles/head-of-content/SOUL.md
```
```text
~/.hermes/profiles/head-of-finance/SOUL.md
```
Each one has a different SOUL .md defining its role. The Chief of Staff agent knows your high-level priorities and runs the daily brief. The Head of Research drills deep on competitor analysis and market trends. The Head of Content drafts and schedules X posts and articles. The Head of Finance reconciles your Stripe, your subscriptions, and your runway.
One morning brief sent to your Telegram triggers all four agents running in parallel. By the time you've finished coffee, the Chief of Staff has surfaced what needs your attention, the Head of Research has dropped a competitor update, the Head of Content has three drafts waiting for review, and the Head of Finance has flagged anything weird in the books.
The next layer up is splitting work across specialists. One profile masters planning. One masters execution. Each builds its own skill library and they only get better the longer they run.
Beyond that. Open specialists handle messy unbounded work. Closed specialists run repeatable pipelines. Different profiles for different jobs. None of them step on each other.
### Step 5: Use /goal for Autonomous Overnight Runs
This is the command that turns Hermes from a reactive chatbot into a background worker.
-  /goal [description] starts autonomous execution
-  /goal status checks what's currently running
-  /goal pause pauses without losing context
-  /goal resume continues after pause
-  /goal clear ends the current goal
-  /subgoal [text] adds conditions mid-execution
You set an objective. Hermes breaks it into tasks. It executes them. It continues until the goal is done. You don't sit there watching. You walk away.
The default max_turns is 5 to 10. That's too low for serious work. Raise it based on the type of work you're doing.
-  hermes config set goals.max_turns 20 for research, reports, and content drafts
-  hermes config set goals.max_turns 50 for code refactoring and multi-step builds
Every turn costs tokens, so don't crank it past what the work actually needs.
The use case that converts most builders into believers is the overnight run. You give Hermes a complex task before bed. Something like "research the top 5 design tools shipping multi-agent design in 2026, summarize their differentiators, and draft a comparison post." You set max_turns to 30. You go to sleep. You wake up to a finished draft waiting for review.
The work that would have eaten your morning is done before you finish your first coffee. That hour back compounds.
### Step 6: Open the Dashboard and Use the Kanban Board
```sh
hermes dashboard
```
Opens in your browser at localhost:9119.
One sharp move when you first open the dashboard. Click Skills first, not Models. A well-used Hermes agent accumulates well over a hundred skills specific to your workflows, all stored as readable markdown files on your machine.
These are the procedural memories the agent has written for itself. Every time it completes a task that takes 5 or more tool calls, it writes a skill file describing the procedure, the known pitfalls, and the verification steps. The next time a similar task appears, it loads the relevant skill instead of figuring everything out from scratch.
Browser automation and computer use are off by default for safety reasons. Both can be enabled per profile from the dashboard.
The Kanban board is the part most builders use daily. The daemon (v0.16+) checks for new tasks every 60 seconds continuously.
The workflow is dead simple. Drop your morning to-do list into the Triage column. Hermes reads each item, splits it into subtasks, assigns them to sub-agents, and runs them in parallel. By lunchtime most of them have moved to Done or are waiting on a specific approval from you.
This is the moment Hermes stops feeling like a tool you use and starts feeling like a team you manage. You orchestrate. The agents execute. The bottleneck shifts from "how fast can I prompt" to "how clearly can I plan."
## The Skill That Writes Itself: One Real Example
One more visual worth taking because it makes the autonomous-skill-creation claim concrete.
Every skill Hermes writes itself lives as a markdown file under ~/.hermes/skills/ (or inside a specific profile's skills folder). They are readable. They are versionable. You can commit them. You can share them.
This is what makes the "self-improving" claim non-marketing. The agent literally writes new procedures into its own toolkit. You don't engineer these by hand. They accumulate while you work.
An example of what one of these skill files looks like. Five sections:
-  When to use. The trigger condition the agent watches for.
-  Procedure. The numbered steps the agent will execute next time.
-  Pitfalls. The known traps and edge cases. (Example: "Pricing pages frequently A/B test based on geo.")
-  Verification. How the agent confirms its own work before marking the task done.
-  Auto-improvement notes. What changed in the procedure based on the last few runs.
## When to Use Hermes vs Claude Code
This is the question every builder asks first. The cleanest answer is below.
### Use Claude Code when:
-  You are deep in a focused coding session on a complex application
-  You need persistent context inside a single repo (CLAUDE .md is doing the job)
-  The task is one well-scoped feature you can ship in a session
-  You need the absolute best coding model with full plan mode and verification loops
### Use Hermes when:
-  The task is research, documents, scheduling, or business analysis
-  You need an agent that runs autonomously for hours or overnight
-  You want the same agent reachable from your phone via Telegram
-  You're building a long-running workflow that should compound over weeks (content, finance, research)
-  You need multiple specialized agents running in parallel with separate memory
The honest answer for most builders. Run both.
That's the split we're moving toward at IgnytLabs. Claude Code stays in the coding loop. Hermes handles everything around it. Operations. Research. Drafts. Reviews. Reconciliations. The two stop competing for context. They split the work cleanly.
The article isn't telling you to drop your current setup. It's telling you you're missing the second half of the stack.
## What to Watch Out For
Four honest flags before you run this.
Skills compound over months, not days. Don't expect magic on day one. Hermes gets noticeably more useful at the 30-day mark and meaningfully more useful at the 6-month mark as the skill library accumulates. The first week feels like setup tax. Push through it.
Computer use and browser automation are off by default for real reasons. Both can be enabled per profile from the dashboard. Don't enable them globally on day one. Enable them per profile only when that profile actually needs them. Otherwise you're handing every agent in your stack full browser access to whatever's logged in.
The default max_turns is too low for serious autonomous work. Raise it to 20-50 depending on the work type. But also know that every turn costs tokens. Don't crank it to 100 unless you actually need 100 turns of work. The model bill stacks up fast on long autonomous runs.
Production deployments need Bitwarden + iron-proxy egress firewall before you trust the agent with real credentials. Hermes ships both integrations. hermes secrets bitwarden setup and hermes egress install get you started. For personal use, the single-rule "Never send money to anyone without explicit confirmation" in your SOUL .md covers most of what you actually need.
## What This Actually Means
Here's the honest take.
The agent paradigm just split into two categories.
Session-based agents. Claude Code. Cursor. Codex. OpenClaw. Open a tab. Do focused work. Close it. Best in class for coding inside a known repo.
Persistent agents. Hermes is the first and currently the only one shipping the full stack. Lives on a server. Remembers everything. Writes its own skills. Runs autonomously. Reaches you on Telegram. Best in class for everything around the coding work.
Most builders are still using only the first category and wondering why they spend so much of their day re-pouring the same context into different tools.
The builders who set up both this year are going to look unfairly ahead next year. Not because they're working harder. Because they stopped paying the context tax that everyone else is still paying every morning.
Hermes Desktop just launched. NVIDIA is post-training models specifically for it. Nous Research is shipping new features every week. The infrastructure is finally here. The setup takes 30 minutes. The compounding is permanent.
2026 is going to be UNFAIR for builders who set this up early. Bookmark the playbook. Run it this week.
## TLDR
-  Hermes Agent is the first AI agent built around persistent memory and autonomous skill creation. Built by Nous Research. Launched February 2026. MIT licensed. 185K stars on GitHub.
-  It's not Claude Code 2.0. Claude Code wins focused coding sessions. Hermes wins everything else (research, documents, scheduling, business analysis, autonomous overnight runs). Run both.
-  Step 1: Install with one curl command. Set up SOUL .md (the agent identity file at slot #1 of the system prompt). Use the official Nous Research template as your starter.
-  Step 2: Pick your model tier. GPT-5.5 for daily. Claude Opus for /goal runs. Qwen 3.7 Max for long autonomous work.
-  Step 3: Connect Telegram in 5 minutes via BotFather. This is the unlock that lets you steer your agents from your phone.
-  Step 4: Set up profiles like an org chart. Chief of Staff, Head of Research, Head of Content. Each gets its own SOUL .md, memory, and skill library.
-  Step 5: Use /goal for autonomous overnight runs. Raise max_turns to 20-50 for serious work.
-  Step 6: Open the dashboard at localhost:9119. Use the Kanban board for triage. Watch your skill library grow.
-  Hermes Desktop just launched. NVIDIA post-trained Nemotron Ultra for it. The momentum is real. The setup takes 30 minutes. The compounding is permanent.
LFG.
