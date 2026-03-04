---
created: 2026-03-04
author: OpenAI
tags: [ai-coding, agents, codex, autonomous, project-management, harness-engineering, experimental]
---

# Symphony

**OpenAI's experimental tool that turns project work into isolated, autonomous implementation runs — monitor Linear board, spawn agents for tasks, manage work instead of supervising coding agents.**

![Symphony GitHub](https://screenshotit.app/https://github.com/openai/symphony)

## Links

- **GitHub**: https://github.com/openai/symphony
- **Spec**: https://github.com/openai/symphony/blob/main/SPEC.md
- **Reference implementation**: Elixir-based
- **Related**: [[harness-engineering-openai]] - Prerequisite approach

## Overview

Symphony monitors work boards (e.g., Linear) and spawns autonomous agents to handle tasks. Agents complete work and provide proof: CI status, PR review feedback, complexity analysis, walkthrough videos. When accepted, agents land the PR safely.

**Key shift**: Engineers manage work at higher level, not supervise coding agents.

**Status**: Low-key engineering preview for trusted environments. ⚠️ Experimental.

## Requirements

Works best in codebases that have adopted [[harness-engineering-openai]] practices. Symphony is the next step: moving from managing coding agents to managing work itself.

## Setup Options

1. **Make your own**: Tell your coding agent to implement from [SPEC.md](https://github.com/openai/symphony/blob/main/SPEC.md)
2. **Use reference implementation**: Elixir-based (see [elixir/README.md](https://github.com/openai/symphony/blob/main/elixir/README.md))

## Demo

Video shows Symphony monitoring Linear board, spawning agents for tasks, agents providing proof of work, and landing PRs safely.
