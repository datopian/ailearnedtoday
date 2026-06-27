---
created: 2026-06-27
tags: [moc, ai-costs, ai-gateway, routing, caching, context-management, llm]
---

# MOC: Managing AI Spend

Map of Content for practical ways to keep AI usage affordable as token consumption grows.

## Overview

As teams put more of their workflow behind agents, the key question is not "how do we stop usage?" but "how do we make usage cheaper per unit of work?" This MOC collects notes on defaults, routing, caching, context discipline, and visibility.

## Core Patterns

### Better Defaults

- Default to cheaper models where acceptable.
- Keep model choice open, but make the low-cost path the path of least resistance.

### Better Routing

- Route by task type, not by user preference.
- Use stronger models for planning and cheaper models for execution where overkill.

### Better Caching

- Treat cache hits as first-class cost savings.
- Make prompt shaping and reuse part of the system design.

### Lean Context

- Start fresh when switching tasks.
- Scope file and tool context narrowly.

### Visibility

- Expose usage, cost, and impact to the people using the system.
- Use visibility to encourage intentional spend, not artificial scarcity.

## In This Repository

- [[brian-armstrong-ai-spend-management]] - Coinbase/Brian Armstrong thread on keeping spend flat while token usage grows
- [[open-agents]] - Related agent infrastructure patterns, including routing and observability
- [[paperclip]] - Example of budgets and cost control in agent orchestration

## Related

- [[hbr-ai-intensifies-work]]
- [[cognitive-debt-ai]]
