---
created: 2026-03-25
original_date: 2026-03-24
author: Cloudflare
tags: [cloudflare, workers, isolates, sandboxing, ai-agents, code-execution, open-beta]
---

# Sandboxing AI agents, 100x faster

Cloudflare's Dynamic Worker Loader API enters open beta: run agent-written code in milliseconds using V8 isolates.

![Cloudflare Dynamic Workers blog](https://screenshotit.app/https://blog.cloudflare.com/dynamic-workers/)

## Links

- **Blog post**: https://blog.cloudflare.com/dynamic-workers/
- **Published**: March 24, 2026
- **Docs**: https://developers.cloudflare.com/dynamic-workers/
- **Pricing**: https://developers.cloudflare.com/dynamic-workers/pricing/
- **Discord**: https://discord.com/channels/595317990191398933/1460655307255578695
- **Status**: Open beta (all paid Workers users)
- **Context**: [[cloudflare-code-mode]] (September 2025 announcement)

## Overview

Dynamic Worker Loader API is now in open beta. This API allows a Cloudflare Worker to instantiate a new Worker, in its own sandbox, with code specified at runtime — all on the fly.

**The breakthrough**: V8 isolates are ~100x faster to start and 10x-100x more memory efficient than containers. A few milliseconds to start, a few megabytes of memory. This makes [[cloudflare-code-mode|Code Mode]] practical at consumer scale.

## Why This Matters

Agents need secure sandboxes to run AI-generated code. Most people use containers, but containers are expensive and slow (hundreds of milliseconds to boot, hundreds of megabytes of memory). You need to keep them warm and may reuse them, compromising security.

**Dynamic Workers solve this**: Create a new isolate for every user request, run one code snippet, throw it away. No warmup, no reuse needed.

## Key Features

### 100x Faster
- **Isolates vs. containers**: ~100x faster startup, 10x-100x more memory efficient
- **Millisecond execution**: Start isolate on-demand, run code, dispose
- **No warmup needed**: So lightweight you create fresh isolate per request

### Unlimited Scalability
- No limits on concurrent sandboxes or creation rate
- Built on same tech powering entire Workers platform
- Seamlessly scale to millions of requests per second

### Zero Latency
- Runs on same machine/thread as parent Worker
- No global lookup for warm sandbox
- Supported in hundreds of Cloudflare locations worldwide

### Battle-Hardened Security
- Nearly a decade securing isolate-based platform
- V8 patches deployed within hours (faster than Chrome)
- Custom second-layer sandbox with dynamic tenant cordoning
- Extended V8 sandbox with hardware features (MPK)
- Novel Spectre defenses
- Automatic malicious pattern scanning

### TypeScript Tools (Not JSON Schemas)
- Define APIs in TypeScript, not OpenAPI or MCP schemas
- Far fewer tokens (see comparison in [[cloudflare-code-mode]])
- Cap'n Web RPC bridge between sandbox and harness
- Agent writes code against typed interfaces

### HTTP Filtering & Credential Injection
- `globalOutbound` option intercepts all HTTP requests
- Inject auth keys, rewrite requests, block, or respond directly
- Agent never knows secret credentials (cannot leak)

## Usage

```typescript
let agentCode: string = `
  export default {
    async myAgent(param, env, ctx) {
      // AI-generated code
    }
  }
`;

let worker = env.LOADER.load({
  compatibilityDate: "2026-03-01",
  mainModule: "agent.js",
  modules: { "agent.js": agentCode },
  env: { CHAT_ROOM: chatRoomRpcStub },
  globalOutbound: null, // Block internet
});

await worker.getEntrypoint().myAgent(param);
```

## Helper Libraries

- **[@cloudflare/codemode](https://www.npmjs.com/package/@cloudflare/codemode)**: Simplifies running model-generated code with DynamicWorkerExecutor, code normalization, globalOutbound control
- **[@cloudflare/worker-bundler](https://www.npmjs.com/package/@cloudflare/worker-bundler)**: Pre-bundles modules, resolves npm dependencies, returns module map for Worker Loader
- **[@cloudflare/shell](https://www.npmjs.com/package/@cloudflare/shell)**: Virtual filesystem with typed state methods, SQLite + R2 backing, transactional batch writes

## Real-World Usage

### Zite
Building app platform where users interact via chat. LLM writes TypeScript to build CRUD apps, connect to Stripe/Airtable/Google Calendar, run backend logic. Every automation runs in its own Dynamic Worker.

> "To enable server-side code for Zite's LLM-generated apps, we needed an execution layer that was instant, isolated, and secure. Cloudflare's Dynamic Workers hit the mark on all three, and out-performed all of the other platforms we benchmarked for speed and library support... Zite now services millions of execution requests daily thanks to Dynamic Workers." — Antony Toron, CTO and Co-Founder, Zite

### Cloudflare MCP Server
Entire Cloudflare API exposed through just two tools (search, execute) in under 1,000 tokens. Agent writes code against typed API instead of navigating hundreds of tool definitions.

## Pricing

- **$0.002 per unique Worker loaded per day** (plus standard CPU time and invocation pricing)
- For one-off AI-generated Workers: $0.002 per Worker loaded
- **Beta period**: $0.002 charge waived
- Cost typically negligible vs. inference costs

## Starters

- **[Dynamic Workers Starter](https://github.com/cloudflare/agents/tree/main/examples/dynamic-workers)**: Hello world example
- **[Dynamic Workers Playground](https://github.com/cloudflare/agents/tree/main/examples/dynamic-workers-playground)**: Write/import code, bundle at runtime, execute, see real-time logs

## Related

- [[cloudflare-code-mode]] - The "why" (September 2025 context)
- [[deerflow]]
- [[openclaw]]
- [[symphony-openai]]
