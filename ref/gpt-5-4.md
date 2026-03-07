---
created: 2026-03-07
author: OpenAI
tags: [gpt-5, frontier-model, computer-use, coding, reasoning, tool-search, knowledge-work, openai]
---

# GPT-5.4

**OpenAI's most capable and efficient frontier model for professional work — first general-purpose model with native computer-use capabilities, 1M context window, combines GPT-5.3-Codex coding with advanced reasoning and agentic workflows.**

![GPT-5.4 announcement](https://screenshotit.app/https://openai.com/index/introducing-gpt-5-4/)

## Links

- **Announcement**: https://openai.com/index/introducing-gpt-5-4/
- **System Card**: https://deploymentsafety.openai.com/gpt-5-4-thinking
- **API Model**: `gpt-5.4` (standard), `gpt-5.4-pro` (maximum performance)
- **Released**: March 7, 2026

## Overview

GPT-5.4 brings together best of recent advances in reasoning, coding, and agentic workflows into single frontier model. Incorporates industry-leading coding capabilities of GPT-5.3-Codex while improving how model works across tools, software environments, and professional tasks involving spreadsheets, presentations, documents.

**Result**: Model that gets complex real work done accurately, effectively, efficiently — delivering what you asked for with less back and forth.

## Key Capabilities

### 1. Native Computer Use (First General-Purpose Model)

First general-purpose model with native, state-of-the-art computer-use capabilities, enabling agents to operate computers and carry out complex workflows across applications.

**Performance**:
- **OSWorld-Verified**: 75.0% (vs GPT-5.2: 47.3%, human: 72.4%)
- **WebArena-Verified**: 67.3% (vs GPT-5.2: 65.4%)
- **Online-Mind2Web**: 92.8% screenshot-based (vs ChatGPT Atlas Agent Mode: 70.9%)

**Capabilities**:
- Writing code to operate computers via libraries like Playwright
- Issuing mouse and keyboard commands in response to screenshots
- Steerable via developer messages
- Configurable safety behavior with custom confirmation policies

### 2. Massive Context Window

Supports up to **1M tokens of context**, allowing agents to plan, execute, and verify tasks across long horizons.

**Long context performance** (new benchmarks at 256K-1M):
- Graphwalks BFS 256K-1M: 21.4%
- Graphwalks parents 256K-1M: 32.4%
- OpenAI MRCR v2 8-needle 256K-512K: 57.5%
- OpenAI MRCR v2 8-needle 512K-1M: 36.6%

### 3. Tool Search

Revolutionary approach to tool use: instead of including all tool definitions upfront (adding thousands of tokens), GPT-5.4 receives lightweight list of available tools plus tool search capability. When needed, looks up tool definition at that moment.

**Efficiency gains** (MCP Atlas benchmark with 36 servers):
- 47% reduction in total token usage
- Same accuracy as full tool definitions
- Enables agents to work with much larger tool ecosystems
- Preserves cache, making requests faster and cheaper

### 4. Knowledge Work Excellence

**GDPval** (well-specified knowledge work across 44 occupations):
- GPT-5.4: 83.0% matching or exceeding industry professionals
- vs GPT-5.2: 70.9%
- vs GPT-5.3-Codex: 70.9%

**Specific improvements**:
- Investment banking modeling: 87.3% (vs GPT-5.2: 68.4%)
- Presentations: Human raters preferred 68.0% of time (stronger aesthetics, greater visual variety, better image generation)
- Factual accuracy: 33% less likely to have false claims, 18% less likely to contain any errors (vs GPT-5.2)

### 5. Coding

Combines coding strengths of GPT-5.3-Codex with leading knowledge work and computer-use capabilities.

**SWE-Bench Pro (Public)**: 57.7% (vs GPT-5.3-Codex: 56.8%, vs GPT-5.2: 55.6%)

**Fast mode in Codex**: Up to 1.5x faster token velocity (same model, same intelligence, just faster)

**Excels at**: Complex frontend tasks with more aesthetic and functional results than any previous models

**New Codex skill**: "Playwright (Interactive)" - allows Codex to visually debug web/Electron apps, test apps as it builds them

### 6. Improved Tool Calling

**Toolathlon** (real-world tools/APIs for multi-step tasks): 54.6% (vs GPT-5.2: 45.7%, vs GPT-5.3-Codex: 51.9%)

**BrowseComp** (agentic web search): 82.7% (vs GPT-5.2: 65.8%, GPT-5.4 Pro: 89.3% SOTA)

### 7. Vision Improvements

**MMMU-Pro** (visual understanding/reasoning): 81.2% without tools (vs GPT-5.2: 79.5%)

**Original image input detail**: Full-fidelity perception up to 10.24M total pixels or 6000-pixel max dimension

**OmniDocBench** (document parsing): 0.109 avg error (vs GPT-5.2: 0.140)

## ChatGPT Features

### Upfront Planning with Mid-Response Steering

GPT-5.4 Thinking now outlines work with preamble for complex queries. Can add instructions or adjust direction mid-response without starting over.

**Benefits**:
- Easier to guide model toward exact outcome
- No additional turns required
- Available now on chatgpt.com and Android app (coming to iOS)

### Longer Thinking with Better Context

Can think longer on difficult tasks while maintaining stronger awareness of earlier conversation steps. Handles longer workflows and complex prompts while keeping answers coherent and relevant.

### Improved Deep Web Research

Stronger at answering questions requiring pulling together information from many sources. More persistent search across multiple rounds, particularly for "needle-in-a-haystack" questions.

## Token Efficiency

Most token efficient reasoning model yet — uses significantly fewer tokens to solve problems vs GPT-5.2, translating to reduced usage and faster speeds.

## Performance Highlights

### Professional
- **GDPval**: 83.0% (vs 70.9%)
- **Finance Agent v1.1**: 56.0%
- **Investment Banking Modeling**: 87.3% (vs 68.4%)

### Coding
- **SWE-Bench Pro**: 57.7%
- **Terminal-Bench 2.0**: 75.1%

### Computer Use
- **OSWorld-Verified**: 75.0% (vs 47.3%, exceeds human 72.4%)
- **WebArena-Verified**: 67.3%

### Tool Use
- **BrowseComp**: 82.7% (Pro: 89.3%)
- **MCP Atlas**: 67.2%
- **Toolathlon**: 54.6%

### Academic
- **Frontier Science Research**: 33.0% (Pro: 36.7%)
- **FrontierMath Tier 4**: 27.1% (Pro: 38.0%)
- **Humanity's Last Exam** (with tools): 52.1% (Pro: 58.7%)

### Abstract Reasoning
- **ARC-AGI-1**: 93.7% (Pro: 94.5%)
- **ARC-AGI-2**: 73.3% (Pro: 83.3%)

## Pricing (API)

| Model | Input | Cached Input | Output |
|-------|--------|--------------|---------|
| gpt-5.2 | $1.75/M | $0.175/M | $14/M |
| **gpt-5.4** | **$2.50/M** | **$0.25/M** | **$15/M** |
| gpt-5.2-pro | $21/M | - | $168/M |
| **gpt-5.4-pro** | **$30/M** | **-** | **$180/M** |

**Also available**:
- Batch and Flex pricing: half standard API rate
- Priority processing: 2x standard API rate

## Availability

### ChatGPT
- **GPT-5.4 Thinking**: Available to Plus, Team, Pro users (replaces GPT-5.2 Thinking)
- **GPT-5.2 Thinking**: Remains available for 3 months (retires June 5, 2026)
- **Enterprise/Edu**: Enable via admin settings
- **GPT-5.4 Pro**: Available to Pro and Enterprise plans

### API
- Available now as `gpt-5.4` and `gpt-5.4-pro`

### Codex
- Rolling out gradually with experimental 1M context window support
- Configure via `model_context_window` and `model_auto_compact_token_limit`
- Requests exceeding 272K count at 2x normal rate
- Fast mode: up to 1.5x faster token velocity

## Safety

**Preparedness Framework**: Treated as High cyber capability

**Protections**:
- Expanded cyber safety stack
- Monitoring systems
- Trusted access controls
- Asynchronous blocking for higher-risk requests (ZDR surfaces)
- Request-level blocking for certain customers on ZDR

**CoT Controllability**: New open-source evaluation shows GPT-5.4 Thinking has low ability to control its CoT (positive for safety — can't hide reasoning, CoT monitoring remains effective)

## Significance

**First general-purpose model with native computer use**: Major step forward for developers building agents that complete real tasks across websites and software systems.

**Unified frontier model**: Combines previously separate capabilities (reasoning, coding, computer use, knowledge work) into single model.

**Tool search innovation**: Fundamentally changes how models work with large tool ecosystems — 47% token reduction while preserving accuracy.

**Knowledge work SOTA**: 83.0% on GDPval representing matching or exceeding professionals across 44 occupations.

**Human-level computer use**: 75.0% on OSWorld-Verified exceeds human performance at 72.4%.

## Related

- [[gpt-5-3-codex]] - Coding capabilities incorporated into GPT-5.4
- [[harness-engineering-openai]] - 0 lines of human code using these models
- [[symphony-openai]] - Autonomous work management for agents
- [[paperclip]] - Orchestration for zero-human companies
- Frontier model development
- Computer use and agents
