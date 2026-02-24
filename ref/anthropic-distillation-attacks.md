---
created: 2026-02-24
author: Anthropic
tags: [ai-security, model-distillation, export-controls, national-security, deepseek, moonshot, minimax]
---

# Detecting and Preventing Distillation Attacks

> Industrial-scale campaigns by three AI labs—DeepSeek, Moonshot, and MiniMax—illicitly extracted Claude's capabilities through 16 million exchanges and 24,000 fraudulent accounts.

![Anthropic Distillation Attacks Article](https://screenshotit.app/https://www.anthropic.com/news/detecting-and-preventing-distillation-attacks)

## Links

- **Article**: https://www.anthropic.com/news/detecting-and-preventing-distillation-attacks
- **Publisher**: Anthropic
- **Date**: February 2026

## Summary

Anthropic identified three Chinese AI labs—DeepSeek, Moonshot, and MiniMax—conducting massive distillation attacks to steal Claude's capabilities. Over 16 million exchanges were generated through ~24,000 fraudulent accounts, violating terms of service and regional access restrictions.

**Distillation** is a legitimate technique where you train a smaller model on outputs from a larger one. But when used illicitly, competitors can acquire capabilities in a fraction of the time and cost, bypassing export controls and stripping out safety guardrails.

## Scale of Attacks

- **DeepSeek**: 150,000+ exchanges — targeted reasoning, reward modeling, censorship-safe query generation
- **Moonshot AI**: 3.4 million exchanges — targeted agentic reasoning, tool use, coding, computer vision
- **MiniMax**: 13 million exchanges — targeted agentic coding, tool orchestration

## Key Quotes

> "Illicitly distilled models lack necessary safeguards, creating significant national security risks. Anthropic and other US companies build systems that prevent state and non-state actors from using AI to, for example, develop bioweapons or carry out malicious cyber activities. Models built through illicit distillation are unlikely to retain those safeguards."

> "Foreign labs that distill American models can then feed these unprotected capabilities into military, intelligence, and surveillance systems—enabling authoritarian governments to deploy frontier AI for offensive cyber operations, disinformation campaigns, and mass surveillance."

> "Without visibility into these attacks, the apparently rapid advancements made by these labs are incorrectly taken as evidence that export controls are ineffective. In reality, these advancements depend in significant part on capabilities extracted from American models."

## Attack Techniques

### DeepSeek
- Synchronized traffic across accounts ("load balancing")
- Prompts asking Claude to articulate internal reasoning step-by-step (generating chain-of-thought training data)
- Censorship-safe query generation for politically sensitive topics
- Traced to specific researchers via request metadata

### Moonshot AI (Kimi models)
- Hundreds of fraudulent accounts across multiple pathways
- Targeted approach: extracting and reconstructing Claude's reasoning traces
- Matched request metadata to public profiles of senior Moonshot staff

### MiniMax
- Detected **while still active** — before model launch
- When Anthropic released a new model, MiniMax pivoted within 24 hours, redirecting half their traffic to the new system
- Timings confirmed against their public product roadmap

## How They Bypass Restrictions

Anthropic doesn't offer Claude access in China, so labs use **commercial proxy services** with "hydra cluster" architectures:
- Sprawling networks of 20,000+ fraudulent accounts
- Traffic distributed across API and third-party cloud platforms
- No single point of failure — when one account is banned, another replaces it
- Mix distillation traffic with legitimate customer requests

## Detection Patterns

What distinguishes distillation from normal usage:

> "A prompt like [expert data analyst delivering insights] may seem benign on its own. But when variations of that prompt arrive tens of thousands of times across hundreds of coordinated accounts, all targeting the same narrow capability, the pattern becomes clear. Massive volume concentrated in a few areas, highly repetitive structures, and content that maps directly onto what is most valuable for training an AI model."

## Anthropic's Response

- **Detection**: Classifiers and behavioral fingerprinting to identify attack patterns (including chain-of-thought elicitation detection)
- **Intelligence sharing**: Sharing technical indicators with other labs, cloud providers, authorities
- **Access controls**: Strengthened verification for educational, research, startup accounts (commonly exploited pathways)
- **Countermeasures**: Product/API/model-level safeguards to reduce efficacy without degrading legitimate use

## Why It Matters

### National Security
Stripped-out safeguards mean dangerous capabilities (bioweapons development, malicious cyber ops) proliferate without protections. If distilled models are open-sourced, risks multiply beyond any single government's control.

### Export Control Undermining
Distillation attacks bypass export controls designed to maintain US AI advantage. Labs subject to Chinese government control can close the gap through theft rather than innovation. Export controls on chips remain critical — they limit both direct training and the scale of distillation.

### Industry-Wide Threat
> "These campaigns are growing in intensity and sophistication. The window to act is narrow, and the threat extends beyond any single company or region. Addressing it will require rapid, coordinated action among industry players, policymakers, and the global AI community."

## Related

- **[[cognitive-debt-ai]]** — When models are built without understanding (distillation at scale)
- **[[harness-engineering-openai]]** — Frontier model development that distillers target
- **[[openai-mission-evolution]]** — AI safety concerns that distillation undermines

---

*Added: February 24, 2026*
