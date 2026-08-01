---
created: 2026-07-26
author: DeepSeek
tags: [deepseek, deepseek-v4, model-release, llms, agentic-coding, api, pricing, context-engineering, open-weights, major-news]
---

# DeepSeek V4 Preview Release

DeepSeek's V4 Preview — open-sourced MoE models with 1M context standard, agentic-coding optimizations, and API pricing far below comparable closed models.

![DeepSeek V4 Preview release](https://screenshotit.app/https://api-docs.deepseek.com/news/news260424/)

## Links

- **News post**: https://api-docs.deepseek.com/news/news260424/
- **Tech report**: https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro/blob/main/DeepSeek_V4.pdf
- **Open weights**: https://huggingface.co/collections/deepseek-ai/deepseek-v4
- **API docs**: https://api-docs.deepseek.com/
- **Coverage / claims**: r/Anthropic post by u/hibzy7 — "DeepSeek V4 Flash API is 18x cheaper on input, 28x cheaper on output, and matches Opus 4.8"
- **Date**: Released ~July 2026 (API live; legacy `deepseek-chat`/`deepseek-reasoner` retired Jul 24, 2026)

## Overview

DeepSeek-V4 Preview is officially live and open-sourced, billed as "the era of cost-effective 1M context length." Two variants ship:

- **DeepSeek-V4-Pro** — 1.6T total / 49B active params. Performance rivaling the world's top closed-source models; open-source SOTA in agentic coding benchmarks, world-leading world knowledge (trailing only Gemini-3.1-Pro), and world-class reasoning (beats all current open models in Math/STEM/Coding).
- **DeepSeek-V4-Flash** — 284B total / 13B active params. Reasoning close to V4-Pro, on par on simple agent tasks, with smaller size, faster responses, and highly cost-effective API pricing.

The release is a major cost disruption: the V4 Flash API is ~18x cheaper on input and ~28x cheaper on output than comparable APIs (e.g. Opus 4.8) while matching Opus 4.8-level quality — verified against the official DeepSeek price sheet.

## Structural Innovation & Context Efficiency

- **Novel attention**: Token-wise compression + DSA (DeepSeek Sparse Attention).
- **Peak efficiency**: World-leading long context with drastically reduced compute and memory cost.
- **1M standard**: 1M context is the default across all official DeepSeek services.

## Agent Capabilities

- DeepSeek-V4 is integrated with leading AI agents: Claude Code, OpenClaw, and OpenCode.
- Already driving DeepSeek's in-house agentic coding.

## API Availability

- Keep `base_url`; just update the model to `deepseek-v4-pro` or `deepseek-v4-flash`.
- Supports both OpenAI ChatCompletions and Anthropic APIs.
- Both models support 1M context and dual modes (Thinking / Non-Thinking).
- ⚠️ `deepseek-chat` and `deepseek-reasoner` were fully retired after Jul 24, 2026, 15:59 UTC (previously routing to V4-Flash).

## Significance

A major open-weights release that pairs frontier-ish quality with drastically lower API cost and native 1M context. Its explicit agent-tooling integrations (Claude Code, OpenClaw, OpenCode) and cost profile make it directly relevant to the loop-engineering and context-engineering practices documented elsewhere in this repo — cheap, long-context, agent-friendly models lower the token-cost barrier that Addy Osmani and Brittany Ellich flag as the main caveat of running loops.

## Related

- [[moc-loop-engineering]] - Loop engineering; cheap long-context APIs make unattended loops more viable
- [[loop-engineering]]
- [[trq212-claude-5-context-engineering]] - Context engineering for Claude 5
- [[openclaw]]
