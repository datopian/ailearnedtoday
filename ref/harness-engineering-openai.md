---
created: 2026-02-13
author: OpenAI (Codex team)
tags: [ai-coding, agents, codex, software-engineering, agent-first, agentic-workflow, openai]
---

# Harness Engineering: Leveraging Codex in an Agent-First World

> Building and shipping a real product with 0 lines of manually-written code.

![OpenAI Harness Engineering](https://screenshotit.app/https://openai.com/index/harness-engineering/)

## Links

- **Article**: https://openai.com/index/harness-engineering/
- **Published**: ~February 2026 (OpenAI blog)
- **Codex**: https://openai.com/codex/

## Summary

OpenAI's Codex team built a real internal product — used by hundreds of internal daily users and external alpha testers — with a team of 3–7 engineers writing **zero lines of code by hand**. Every line of application logic, tests, CI configuration, documentation, observability tooling, and internal utilities was written by Codex.

The result:
- **~1 million lines of code** shipped in 5 months
- **~1,500 pull requests** opened and merged
- **3.5 PRs per engineer per day** average throughput (and growing as team scaled)
- Estimated **1/10th the time** it would have taken to write manually

The article is a detailed account of what broke, what they had to build, and the principles that emerged. The core shift: engineers no longer write code — they **design environments, specify intent, and build feedback loops** that allow agents to do reliable work.

---

## Key Lessons

### 1. AGENTS.md is a map, not a manual

> "Give Codex a map, not a 1,000-page instruction manual."

Their AGENTS.md is ~100 lines — a table of contents pointing to a structured `docs/` directory as the system of record. A giant instruction file crowds out the task; too much guidance becomes non-guidance; it rots instantly; it's hard to verify.

Repository knowledge is organized as:
- **Architecture docs** — top-level map of domains and package layering
- **Design docs** — catalogued with verification status and core beliefs
- **Quality doc** — grades each product domain, tracks gaps over time
- **Execution plans** — checked into the repo as first-class artifacts with progress and decision logs
- **A "doc-gardening" Codex agent** — scans for stale docs and opens fix-up PRs automatically

### 2. Repository is the only source of truth

> "From the agent's point of view, anything it can't access in-context while running effectively doesn't exist."

Knowledge in Slack, Google Docs, or people's heads is inaccessible to the agent. Every architectural decision, team norm, and design alignment must be in the repo as versioned artifacts. "That Slack discussion that aligned the team on an architectural pattern? If it isn't discoverable to the agent, it's illegible in the same way it would be unknown to a new hire joining three months later."

### 3. Application legibility — making the world visible to the agent

As code throughput increased, the bottleneck became **human QA capacity**. They made the app itself legible to Codex:
- **Bootable per git worktree** — Codex can launch and drive one instance per change
- **Chrome DevTools Protocol** wired into the agent runtime — DOM snapshots, screenshots, navigation
- **Local observability stack** — ephemeral per worktree; agents query logs with LogQL, metrics with PromQL

This enabled prompts like "ensure service startup completes in under 800ms" or "no span in these four critical user journeys exceeds two seconds." Agents can reproduce bugs, validate fixes, and reason about UI behavior directly.

> "We regularly see single Codex runs work on a single task for upwards of six hours (often while the humans are sleeping)."

### 4. Strict architecture enforced mechanically

> "This is the kind of architecture you usually postpone until you have hundreds of engineers. With coding agents, it's an early prerequisite."

Each business domain is divided into fixed layers with validated dependency directions — enforced by custom linters (Codex-generated) and structural tests. Error messages in custom lints inject remediation instructions into agent context.

"Taste invariants": structured logging, naming conventions, file size limits, platform reliability requirements — all mechanically enforced. In a human-first workflow, these feel pedantic. With agents, they become multipliers.

### 5. Prefer "boring" technology

> "Technologies often described as 'boring' tend to be easier for agents to model due to composability, API stability, and representation in the training set."

They sometimes had Codex reimplement subsets of library functionality rather than use opaque upstream packages — resulting in tighter integration, 100% test coverage, and exact behavior control.

### 6. Garbage collection beats cleanup sprints

> "Our team used to spend every Friday (20% of the week) cleaning up 'AI slop.' Unsurprisingly, that didn't scale."

Instead: encode "golden principles" directly into the repo and run recurring background Codex cleanup tasks that scan for deviations, update quality grades, and open targeted refactoring PRs. Most can be reviewed in under a minute.

> "Technical debt is like a high-interest loan: it's almost always better to pay it down continuously in small increments than to let it compound and tackle it in painful bursts."

### 7. Throughput changes the merge philosophy

With agent throughput far exceeding human attention, **corrections are cheap and waiting is expensive**. Minimal blocking merge gates, short-lived PRs, test flakes addressed with follow-up runs. "This would be irresponsible in a low-throughput environment. Here, it's often the right tradeoff."

---

## Key Quotes

> "Humans steer. Agents execute."

> "When something failed, the fix was almost never 'try harder.' Because the only way to make progress was to get Codex to do the work, human engineers always stepped into the task and asked: 'what capability is missing, and how do we make it both legible and enforceable for the agent?'"

> "Context is a scarce resource. A giant instruction file crowds out the task, the code, and the relevant docs—so the agent either misses key constraints or starts optimizing for the wrong ones."

> "Anything it can't access in-context while running effectively doesn't exist. Knowledge that lives in Google Docs, chat threads, or people's heads are not accessible to the system."

> "The resulting code does not always match human stylistic preferences, and that's okay. As long as the output is correct, maintainable, and legible to future agent runs, it meets the bar."

> "Building software still demands discipline, but the discipline shows up more in the scaffolding rather than the code."

---

## Full Autonomy Loop (Latest Capability)

Given a single prompt, Codex can now:
1. Validate the current state of the codebase
2. Reproduce a reported bug
3. Record a video demonstrating the failure
4. Implement a fix
5. Validate the fix by driving the application
6. Record a second video demonstrating the resolution
7. Open a pull request
8. Respond to agent and human feedback
9. Detect and remediate build failures
10. Escalate to a human only when judgment is required
11. Merge the change

---

## Why It Matters

This is one of the most detailed public accounts of running a **fully agent-generated codebase** at scale with real users. Unlike demo projects, this product ships, breaks, and gets fixed. The learnings are grounded in production reality, not theory.

The piece challenges several assumptions:
- **AGENTS.md should be long and comprehensive** → No: short map + structured docs
- **Strict architecture is for large teams** → No: it's the prerequisite for agent velocity
- **Clean-up can be batched** → No: continuous garbage collection by agents
- **Human review is required** → Increasingly pushed to agent-to-agent review

---

## Related

- **[[steve-yegge]]** — Ex-Sourcegraph, built Gas Town orchestrator; shares similar views on agent-first engineering
- **[[temporal-io-ai]]** — Orchestration infrastructure that supports durable long-running agent tasks
- **[[crawshaw-eight-more-months-agents]]** — Complementary perspective on agentic software development challenges
- **[[cognitive-debt-ai]]** — The risk Harness Engineering partially mitigates: keeping the "theory of the system" in the repo
- **[[openspec.dev]]** — Spec-writing approach compatible with the "repository as system of record" philosophy
- **[[github-spec-kit]]** — GitHub's take on specs for agent consumption (similar philosophy)
- **[[exe.dev]]** — AI coding environment where similar patterns apply

---

*Added: 2026-02-18 (originally encountered: 2026-02-13)*
