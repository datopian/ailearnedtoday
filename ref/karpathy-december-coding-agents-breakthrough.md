---
created: 2026-02-26
tags: [ai, coding-agents, breakthrough, december-2024, agentic-engineering, orchestration]
---

# Karpathy: December Coding Agents Breakthrough

Andrej Karpathy's February 2026 thread documenting the fundamental shift in AI coding agent capabilities that occurred in December 2024/early 2025.

![Andrej Karpathy tweet on December coding agents breakthrough](https://screenshotit.app/https://x.com/karpathy/status/2026731645169185220)

## Links

- **Tweet**: https://x.com/karpathy/status/2026731645169185220
- **Date**: February 22, 2026
- **Author**: [[andrej-karpathy]]

## Overview

Karpathy identifies December 2024 as an inflection point where coding agents transitioned from "basically didn't work" to "basically work" - not gradual progress but a sharp discontinuity. The core change: significantly higher quality, long-term coherence, and tenacity enabling agents to power through large, complex tasks autonomously.

## Key Example: Home Video Dashboard

Weekend project demonstrating the new capabilities:

**Task given (in English):**
> "Here is the local IP and username/password of my DGX Spark. Log in, set up ssh keys, set up vLLM, download and bench Qwen3-VL, set up a server endpoint to inference videos, a basic web ui dashboard, test everything, set it up with systemd, record memory notes for yourself and write up a markdown report for me"

**Result:** 
- Agent completed autonomously in ~30 minutes
- Ran into multiple issues, researched solutions online, resolved them
- Wrote code, tested, debugged, set up services
- Returned with complete report
- Zero manual intervention required

**Historical context:** This would have been a full weekend project just 3 months prior.

## The Paradigm Shift

### Old: Direct Code Authoring
- Typing computer code into an editor
- The default since computers were invented
- That era is over

### New: Agentic Management
- Spinning up AI agents
- Giving them tasks in natural language
- Managing and reviewing parallel work streams
- Ascending layers of abstraction

## Agentic Engineering

**The emerging skill:** Setting up long-running orchestrator "Claws" with:
- Right tools
- Memory systems
- Instructions
- Managing multiple parallel Code instances

**Leverage:** "Top tier 'agentic engineering' feels very high right now"

## Constraints & Limitations

### What it needs:
- High-level direction
- Judgment and taste
- Oversight and iteration
- Hints and ideas

### Where it works best:
- Well-specified tasks
- Verifiable/testable functionality

### The key skill:
Building intuition to decompose tasks appropriately - hand off parts that work, help around the edges.

## Implications

**Core assessment:** "This is nowhere near 'business as usual' time in software"

The shift represents a fundamental transformation in the practice of programming, moving from direct code authorship to agentic orchestration and management.

## Context

Karpathy is uniquely positioned to assess this shift:
- Former Director of AI at Tesla (Autopilot)
- Founding member of OpenAI
- Created CS231n (Stanford's foundational deep learning course)
- Built [[nanoGPT]] and other educational AI tools

His assessment carries weight both from technical depth and practical experience building production AI systems.

## Related

- [[moc-andrej-karpathy]] - Overview of Karpathy's work and insights
- [[crawshaw-eight-more-months-agents]] - Crawshaw's parallel analysis of agent evolution
- [[temporal-io-ai]] - Workflow orchestration for agentic systems
- [[steve-yegge]] - Yegge's Gas Town orchestrator (v4)

## Commentary

This thread crystalizes a widely-felt but hard-to-articulate shift. The specific December timing aligns with:
- Claude 3.5 Sonnet improvements (October 2024+)
- GPT-4 Turbo refinements
- Emergence of specialized agent frameworks

The "30-minute weekend project" example is particularly striking - not because it's flashy, but because it's mundane infrastructure work requiring:
- Multiple technology stacks (SSH, vLLM, systemd)
- Remote system administration
- Debugging and problem-solving
- Documentation

The fact that this just works now, reliably enough to "kick off and forget," represents a practical threshold crossing.

## Timestamp

Posted: February 22, 2026 (roughly 2 months after the December breakthrough he describes)
