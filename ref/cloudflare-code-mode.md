---
created: 2026-03-25
original_date: 2025-09-26
author: Cloudflare (@threepointone, @KentonVarda)
tags: [mcp, agents, cloudflare, workers, isolates, code-generation, tooling]
---

# Code Mode: the better way to use MCP

Cloudflare's approach to MCP: convert tools to TypeScript API, let LLMs write code instead of calling tools directly.

![Cloudflare Code Mode blog](https://screenshotit.app/https://blog.cloudflare.com/code-mode/)

## Links

- **Blog post**: https://blog.cloudflare.com/code-mode/
- **Published**: September 26, 2025
- **Authors**: Sunil Pai (@threepointone), Kenton Varda (@KentonVarda)
- **Docs**: https://developers.cloudflare.com/agents/
- **Code Mode docs**: https://github.com/cloudflare/agents/blob/main/docs/codemode.md
- **Worker Loader API**: https://developers.cloudflare.com/workers/runtime-apis/bindings/worker-loader/
- **Beta signup**: https://forms.gle/MoeDxE9wNiqdf8ri9
- **Commentary tweet**: https://x.com/jpschroeder/status/2036448259724423482

## Overview

**Note**: This post from September 2025 introduced the Code Mode concept and the experimental Dynamic Worker Loader API. See [[cloudflare-dynamic-workers]] for the March 2026 open beta announcement.

LLMs are better at writing code to call MCP than at calling MCP directly. Cloudflare's Code Mode converts MCP tools into a TypeScript API and asks the LLM to write code that calls that API, rather than using traditional tool calling.

**Key results**:
- Agents handle many more tools and more complex tools
- LLMs have enormous real-world TypeScript in training data, but only small set of contrived tool call examples
- Multiple tool calls can be chained in code without feeding each through the neural network
- Code executes in milliseconds via Workers isolates (not slow containers)

## Why This Matters

From [@jpschroeder's explanation](https://x.com/jpschroeder/status/2036448259724423482):

> This is a much bigger deal than most people realize. If you don't know why, let me explain.
>
> Agents perform "work" right now by calling "tools". These are just pieces of context shoved into the context window saying "if you think you the next thing you should do falls into one of these categories, then respond with this format" — that format is the "tool" a JSONSchema response which a harness then uses to call a function.
>
> MCP, is best thought of as a way to shove more tools and context into your context window (it has a lot of shortcomings imo). The agent then has to pick which tool out of all the available tools it should call. So the more tools you have, the worse it selects the tools.
>
> @threepointone and @KentonVarda have an excellent article (https://blog.cloudflare.com/code-mode) where they introduced the idea of exposing the MCP tools as an SDK, so to call tools and compose them, the AI just does what it is ALREADY good at: write some code.
>
> The question, as always, is where do you run that code safely. Many have proposed sandboxes and containers as a possible solution, but these are hella slow and make the experience untenable.
>
> Thats what makes this announcement SO important, it allows you to run agent-written code in a matter of milliseconds with the explicit execution environment you specify pulled in (like a database, kv store, etc. Cloudflare calls these "bindings" btw).
>
> In practice, this means people can start building MUCH more effective agents that can *do* a lot more, because they can be exposed to more tools.
>
> Anyway, huge deal. Congrats to the CF team.

## The Problem with Traditional Tool Calling

**Tool calls use special tokens** LLMs have never seen in the wild. They must be specially trained on synthetic data. If you present too many tools or complex tools, LLMs struggle.

**LLMs are great at code**, not tool calling. They've seen millions of real-world code examples but only contrived tool call training sets. "Making an LLM perform tasks with tool calling is like putting Shakespeare through a month-long class in Mandarin and then asking him to write a play in it."

**Tool composition is inefficient**: Each tool output must feed through the neural network just to copy to the next tool's input, wasting time, energy, and tokens.

## The Solution

1. **Convert MCP tools to TypeScript API**: Fetch MCP schema, generate TypeScript definitions with doc comments
2. **LLM writes code**: Instead of calling tools, LLM writes code that calls the TypeScript API
3. **Execute in isolated sandbox**: Code runs in secure V8 isolate with no Internet access, only bindings to authorized MCP servers

## Dynamic Worker Loader API

**The killer feature**: Run agent-written code in milliseconds using V8 isolates, not containers.

- **Isolates vs. containers**: Start in milliseconds using only megabytes of memory
- **Disposable**: Create fresh isolate for every code snippet, no reuse/prewarming needed
- **Bindings model**: Sandbox has no network access, only live object bindings to authorized resources
- **No API keys to leak**: Bindings hide keys; agent supervisor holds tokens

**Worker Loader API**: New API for loading Worker code on-demand, right where the agent runs (not globally deployed).

## Usage

```typescript
import { codemode } from "agents/codemode/ai";

const {system, tools} = codemode({
  system: "You are a helpful assistant",
  tools: {
    // tool definitions or MCP servers
  },
});

const stream = streamText({
  model: openai("gpt-5"),
  system,
  tools,
  messages: [
    { role: "user", content: "Write a function that adds two numbers" }
  ]
});
```

Agent generates and runs code that calls the tools. Results returned via `console.log()`.

## Related

- [[cloudflare-dynamic-workers]] - March 2026 open beta: makes Code Mode practical with 100x faster sandboxing
- [[deerflow]]
- [[openclaw]]
- [[symphony-openai]]
- [[paperclip]]
