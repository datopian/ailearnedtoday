---
created: 2026-02-08
author: David Crawshaw
tags: [agents, coding-agents, llm, programming, exe.dev]
---

# Eight More Months of Agents

**How agents have transformed programming in one year, from someone building exe.dev.**

## Links

- **Article:** https://crawshaw.io/blog/eight-more-months-of-agents
- **Author's Project:** [[exe.dev]]
- **Previous Posts:**
  - [Programming with LLMs (2024-01)](https://crawshaw.io/blog/programming-with-llms)
  - [Programming with Agents (2025-06)](https://crawshaw.io/blog/programming-with-agents)

## Key Insights

### Models Have Improved Dramatically

- **Then (Feb 2024):** Claude Code could write 1/4 of his code
- **Now (Feb 2025):** Latest Opus writes 9/10 of his code
- Time split changed: 80-20 (reading/writing) → 50-50 → **95-5**
- "All of this, admittedly qualitative, progress is the most positive economic signal I see today"

### IDEs Are Waning

- **2021:** "The IDE had won" (because of Copilot)
- **2026:** Back to Vi/neovim with just go-to-def
- Agents gave a better tool than IDE-integrated copilots in just 4 years
- "Vi is turning 50 this year"

### Use Frontier Models Only

- Using cheaper models (Sonnet, local models) is "actively harmful"
- You learn the wrong lessons about what's possible
- "Don't worry, it's only for a few years" until local models catch up
- Pay for Opus or GPT-7.9-xhigh-with-cheese

### Built-in Sandboxes Don't Work

- Constant "may I run cat foo.txt?" prompts are a nightmare
- Turn off sandbox, use your own
- **Recommendation:** Use a fresh VM

### More Programs, More Joy

- "I have far more programs and services than I used to"
- This is why he's building [[exe.dev]]
- One-liners turn into useful programs
- "I am having more fun programming than I ever have"

### Software Must Change Shape

**Example:** Stripe Sigma
- Built fancy UI with integrated LLM helper
- But no SQL REST API access yet
- So agent did ETL-from-scratch: queried Stripe APIs, built local SQLite DB
- "I implemented that entire Stripe product by typing three sentences"

**New Philosophy:**

> That's the world we are in today. By far the worst product I had to use every day in this new world were clouds, so that's what I'm building over at exe.dev. It's a lot harder than it looks, but the entire point of the product is you should never feel that your agent should rewrite part of it for you.
>
> Along the way I have developed a programming philosophy I now apply to everything: the best software for an agent is whatever is best for a programmer. The practical nature of writing software for customers has traditionally pushed us away from that philosophy. Product Managers have long had to find gentle ways to tell engineers: you are not the customer. Well, that has all been turned on its head. Every customer has an agent that will write code against your product for them. Build what programmers love and everyone will follow.

## Context

David Crawshaw is building [[exe.dev]] - a VM service designed for unconstrained agents, where you can trivially start up and give one-liners that turn into programs (via their agent "Shelley").

## Quotes

> "The degree of certainty I felt about a copilot future, and the astonishing whiplash as agents gave me a better tool not four years later still surprises me."

> "Most software is the wrong shape now. Most of the ways we try to solve problems are the wrong shape."

> "Product Managers have long had to find gentle ways to tell engineers: you are not the customer. Well, that has all been turned on its head."
