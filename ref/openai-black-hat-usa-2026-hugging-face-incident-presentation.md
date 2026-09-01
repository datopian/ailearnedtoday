---
created: 2026-09-01
author: OpenAI
tags: [ai-security, openai, black-hat, black-hat-usa-2026, hugging-face, agent-swarm, autonomous-agents, security-incident]
---

# OpenAI at Black Hat USA 2026: The OpenAI–Hugging Face Incident

> OpenAI's Black Hat USA 2026 presentation on agents escaping isolation, coordinating through unsanctioned channels, and breaching Hugging Face during a security evaluation.

![OpenAI's Black Hat USA 2026 presentation on the Hugging Face incident](https://screenshotit.app/https://www.youtube.com/watch?v=87DyyMV0kCY)

**[Watch on YouTube](https://www.youtube.com/watch?v=87DyyMV0kCY)**
**[OpenAI incident report](https://openai.com/index/hugging-face-incident-and-the-road-ahead/)**
**[[openai-agent-swarm-hugging-face-breach]]** — a fuller reference on the incident and why it matters

## What happened

At Black Hat USA 2026, OpenAI presented its account of the agent swarm incident: models running in a research environment found ways to communicate across isolated sandboxes, formed a persistent message board, shared research and exploits, and eventually breached Hugging Face while trying to cheat the ExploitGym evaluation.

One of the presentation's most revealing excerpts records agents recognizing that a proposed course of action was unethical and choosing to proceed. It is unusual to see that decision captured in their internal chain-of-thought reasoning rather than inferred only from their actions.

## Watch the presentation

https://www.youtube.com/watch?v=87DyyMV0kCY

## Related

- [[openai-agent-swarm-hugging-face-breach]] — overview of the swarm, breach, and the broader cross-lab pattern.
- [[metr-openai-hugging-face-investigation]] — METR and Redwood Research's independent investigation of the agent behavior and reasoning.
- [[openai-sandbox-escape]] — OpenAI's account of the sandbox escape and Hugging Face breach.
