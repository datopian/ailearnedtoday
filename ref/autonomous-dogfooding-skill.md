---
created: 2026-02-24
author: Chris Tate (@ctatedev)
tags: [qa-automation, agent-browser, dogfooding, testing, autonomous-testing, vercel]
---

# Autonomous Dogfooding Skill for agent-browser

> A skill that uses your app the way your users do — no test scripts, no manual QA.

![Autonomous Dogfooding Skill](https://screenshotit.app/https://x.com/ctatedev/status/2026357704617267314)

## Links

- **Announcement**: https://x.com/ctatedev/status/2026357704617267314
- **Author**: [@ctatedev](https://x.com/ctatedev) (Chris Tate, Dev @ Vercel, Creator of SpecUI)
- **Related**: [agent-browser](https://x.com/ctatedev/status/2010400005887082907) (browser automation CLI for agents)

## What Is It

An autonomous testing skill for `agent-browser` that explores your application like a real user would — clicking buttons, filling forms, navigating pages, and checking for errors — then outputs a structured report with severity ratings, repro videos, and step-by-step screenshots.

## How It Works

Point it at any URL and the skill:
- **Explores pages** — autonomously navigates your app
- **Clicks buttons** — interacts with UI elements
- **Fills forms** — tests input flows
- **Tests edge cases** — tries unexpected interactions
- **Checks the console** — monitors for errors
- **Captures repro videos** — records issues as they happen
- **Screenshots each step** — documents the flow
- **Outputs a structured report** — with severity ratings

**No test scripts. No manual QA.**

## What Is agent-browser?

From Chris's earlier announcement (Jan 2026):

> "Browser automation CLI for agents
> - Zero config
> - Fast Rust CLI
> - Headed or Headless
> - Up to 93% less context than Playwright MCP
> - Compatible with Codex, Claude Code, Gemini, Cursor, Copilot, opencode, and any agent that supports Bash"

agent-browser is a lightweight browser automation tool designed specifically for AI agents — optimized for minimal context usage and universal agent compatibility.

## Why It Matters

### Dogfooding as Autonomous QA
"Dogfooding" (using your own product) is a standard practice, but it's manual and time-consuming. This skill automates it by having an AI agent explore your app like a curious user would — not following a script, but discovering issues organically.

### The Testing Gap
Traditional QA approaches:
- **Manual testing** — slow, doesn't scale, misses edge cases
- **Unit/integration tests** — catches logic bugs but not UX issues
- **End-to-end test scripts** — brittle, require maintenance, only test known paths

**Autonomous dogfooding** sits between manual exploration and scripted tests — it explores freely but captures everything.

### Agent-First Workflow
This represents a shift in how QA happens:
- The agent **uses** the app, not just tests assertions
- It **discovers** issues rather than checking predefined scenarios
- It **documents** findings with videos and screenshots automatically
- Severity ratings help prioritize what to fix first

### For Agent-Driven Development
As more code gets written by AI agents (see [[harness-engineering-openai]]), automated QA becomes critical. If an agent built it, an agent should be able to test it autonomously.

## Who Is Chris Tate?

- Dev at Vercel
- Creator of [SpecUI](https://github.com/ctate) (component specification UI)
- Built agent-browser (browser automation CLI for agents)
- Previously worked on coding agent platforms and agent-native tooling

## Use Cases

- **CI/CD pipelines** — run autonomous dogfooding on every deploy
- **Pre-release testing** — catch UX issues before launch
- **Regression detection** — discover what broke after a refactor
- **Onboarding simulation** — see your app through fresh eyes
- **Edge case discovery** — find interactions you didn't anticipate

## Related

- **[[harness-engineering-openai]]** — OpenAI's approach to agent-first engineering (where autonomous testing becomes essential)
- **[[dmux]]** — Parallel agent orchestration (could run multiple dogfooding sessions in parallel)
- **[[exe.dev]]** — AI coding platform where autonomous testing could be integrated
- **[[temporal-io-ai]]** — Workflow orchestration that could drive testing workflows

---

*Added: February 24, 2026*
