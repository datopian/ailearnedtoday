---
created: 2026-04-10
author: Google DeepMind
tags: [models, open-models, gemma, multimodal, agents]
---

# Gemma 4

Google's most intelligent open models, built from Gemini 3 research, optimized for intelligence‑per‑parameter and agentic workflows.

![Gemma 4](https://screenshotit.app/https://deepmind.google/models/gemma/gemma-4/)

## Links

- **Model page**: https://deepmind.google/models/gemma/gemma-4/
- **Model card & benchmarks**: https://ai.google.dev/gemma/docs/core/model_card_4
- **Fireship overview video**: https://www.youtube.com/watch?v=-01ZCTt-CJw

## Overview

Gemma 4 is Google's next generation of **open models**, derived from **Gemini 3** research and technology. The focus is **maximum intelligence‑per‑parameter** and **maximum compute/memory efficiency** so the models can:

- Deliver **frontier‑level intelligence on personal computers**
- Run on **mobile and IoT devices** with tight resource budgets

## Capabilities

According to the model page, Gemma 4 is designed for:

- **Agentic workflows**  
  Build autonomous agents that plan, navigate apps, and complete tasks on your behalf, with native support for **function calling**.

- **Multimodal reasoning**  
  Strong **audio and visual understanding** for rich multimodal applications.

- **Support for 140 languages**  
  Multilingual experiences that go beyond translation and understand cultural context.

- **Fine tuning**  
  Improve performance for specific tasks with your preferred frameworks and techniques.

- **Efficient architecture**  
  Run models on your own hardware for efficient development and deployment.

## Performance (Selected Benchmarks)

Gemma 4 variants (e.g., 31B IT Thinking, 26B A4B IT Thinking, E4B/E2B) are compared against Gemma 3 27B IT. Highlights from the page:

- **Arena AI (text)** (as of 2026‑04‑02)  
  Gemma 4 31B IT Thinking: **1452**  
  Gemma 3 27B IT: **1365**

- **MMMLU (Multilingual QA, no tools)**  
  Gemma 4 31B: **85.2%**  
  Gemma 3 27B: **67.6%**

- **MMMU Pro (Multimodal reasoning)**  
  Gemma 4 31B: **76.9%**  
  Gemma 3 27B: **49.7%**

- **AIME 2026 (Mathematics, no tools)**  
  Gemma 4 31B: **89.2%**  
  Gemma 3 27B: **20.8%**

- **LiveCodeBench v6 (Competitive coding)**  
  Gemma 4 31B: **80.0%**  
  Gemma 3 27B: **29.1%**

- **GPQA Diamond (Scientific knowledge, no tools)**  
  Gemma 4 31B: **84.3%**  
  Gemma 3 27B: **42.4%**

- **τ2‑bench (Agentic tool use, retail)**  
  Gemma 4 31B: **86.4%**  
  Gemma 3 27B: **6.6%**

The model card lists additional benchmarks and breakdowns.

## Positioning

Gemma 4 is positioned as:

- **Open**: Part of the Gemma family of open models  
- **Agent‑ready**: Built for tool use and agentic workflows (τ2‑bench numbers are a strong signal)  
- **Multimodal**: Audio + vision support  
- **Edge‑friendly**: Designed to run on PCs, mobile, and IoT with high efficiency

The **Fireship video** (linked above) gives a concise community overview and early impressions of model behavior and tooling support.

## Related

- [[cloudflare-dynamic-workers]]
- [[deerflow]]
- [[openclaw]]
- [[anthropic-glasswing]]
