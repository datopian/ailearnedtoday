---
created: 2026-06-27
author: John Phamous
tags: [vercel, agents, product-design, design-systems, evals, linting]
---

# Teaching agents product design at Vercel

Vercel’s approach to teaching agents product-design judgment through skills, lint rules, agent code reviews, evals, and a human-led update loop.

![Teaching agents product design at Vercel](https://screenshotit.app/https://vercel.com/blog/teaching-agents-product-design-at-vercel)

## Links

- **Article**: https://vercel.com/blog/teaching-agents-product-design-at-vercel
- **Vercel Agent**: https://vercel.com/agent

## Overview

The post lays out how Vercel turns repeated product-design decisions into something agents can actually use. Instead of treating design quality as an intangible taste problem, the team encodes the recurring decisions as skills, lint rules, review checks, and evals.

The central idea is practical: keep human ownership on standards, let agents consume those standards where code is written and reviewed, and move anything unreliable back into guidance rather than forcing brittle automation.

## Key Ideas

- **Agent skills**: packaging product-design guidance so agents can find and reuse it.
- **Lint rules**: checks for decisions that can be enforced reliably in code.
- **Vercel Agent reviews**: using an agent in the review loop to catch product-design regressions.
- **Evals and ownership**: measuring whether the workflow holds up, while humans approve changes to the standards.

## Why It Matters

This is a concrete example of product taste being operationalized for agentic workflows. It fits the broader pattern of moving from informal guidance to encoded standards, but without pretending every design decision can be reduced to a rule.

