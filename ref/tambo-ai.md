---
created: 2026-02-18
author: Tambo AI
tags: [generative-ui, react, ai-agents, sdk, mcp, open-source, streaming]
---

# Tambo — Generative UI SDK for React

> Build agents that speak your UI. Register your components — Tambo handles streaming, state management, and MCP.

![Tambo AI GitHub](https://screenshotit.app/https://github.com/tambo-ai/tambo)

## Links

- **GitHub**: https://github.com/tambo-ai/tambo
- **Website**: https://tambo.co
- **Docs**: https://docs.tambo.co
- **npm**: `@tambo-ai/react`
- **Discord**: https://discord.gg/dJNvPEHth6
- **Twitter**: [@tambo_ai](https://twitter.com/tambo_ai)
- **Announcement**: [Introducing Tambo: Generative UI for React](https://tambo.co/blog/posts/introducing-tambo-generative-ui)

## What Is It

Tambo is an open-source React toolkit for building agents that render UI — sometimes called "generative UI." Instead of an AI returning text, it picks the right React component and streams props directly to it.

> "Show me sales by region" renders your `<Chart>`. "Add a task" updates your `<TaskBoard>`."

You register components with Zod schemas. Those schemas become LLM tool definitions — the agent calls them like functions, and Tambo renders the result. The UI adapts to what the user asks for rather than being fixed.

## What Problem Does It Solve

Most chat AI UIs return text that describes actions or data. Tambo lets the AI *render* the right interface — a chart, a form, a task board — directly in response to user intent. The UI becomes an output of the agent, not just a wrapper around it.

## Key Features

### Two Component Types

**Generative components** — render once in response to a message (charts, summaries, visualizations):
```js
const components = [{
  name: "Graph",
  description: "Displays data as charts",
  component: Graph,
  propsSchema: z.object({
    data: z.array(z.object({ name: z.string(), value: z.number() })),
    type: z.enum(["line", "bar", "pie"]),
  }),
}];
```

**Interactable components** — persist and update as users refine requests (shopping carts, spreadsheets, task boards):
```js
const InteractableNote = withInteractable(Note, {
  componentName: "Note",
  description: "A note supporting title, content, and color modifications",
  propsSchema: z.object({ title: z.string(), content: z.string(), color: z.enum(["white", "yellow", "blue", "green"]).optional() }),
});
```

### Fullstack Solution
- **Agent included** — Tambo runs the LLM conversation loop; bring your own API key (OpenAI, Anthropic, Gemini, Mistral, or any OpenAI-compatible provider)
- **Streaming infrastructure** — props stream to components as the LLM generates them; cancellation, error recovery, and reconnection handled automatically
- **Tambo Cloud or self-host** — Cloud is a hosted backend; self-hosted runs via Docker

### MCP Integration
Full MCP protocol support: tools, prompts, elicitations, and sampling. Connect to Linear, Slack, databases, or custom MCP servers:
```js
<TamboProvider mcpServers={[{ name: "filesystem", url: "http://localhost:8261/mcp", transport: MCPTransport.HTTP }]}>
```

### Other Features
- **Local tools** — functions that run in the browser (DOM manipulation, authenticated fetches, React state access)
- **Context helpers** — pass user state, app settings, current page to AI for better responses
- **Suggestions** — generates clickable prompts based on what users are doing
- **Pre-built UI library** — [ui.tambo.co](https://ui.tambo.co) with agent and generative UI primitives

## Quick Start

```bash
npm create tambo-app my-tambo-app
cd my-tambo-app
npm run dev
```

## How Tambo Compares

| Feature | Tambo | Vercel AI SDK | CopilotKit | Assistant UI |
|---------|-------|---------------|------------|--------------|
| AI picks components | ✅ | Manual mapping | Via LangGraph | Chat-focused |
| MCP integration | Built-in | Experimental | Recently added | Requires AI SDK v5 |
| Persistent stateful components | ✅ | ❌ | Shared state | ❌ |
| Client-side tool execution | Declarative | Manual | Agent-side | ❌ |
| Self-hostable | MIT (SDK + backend) | Apache 2.0 (SDK only) | MIT | MIT |
| Hosted option | Tambo Cloud | ❌ | CopilotKit Cloud | Assistant Cloud |

## Why It Matters

Tambo represents a shift in how AI integrates with application UIs. Instead of the AI being a chat sidebar that describes things, it becomes a first-class citizen that *renders* the interface. The application UI becomes dynamic — shaped by user intent rather than hardcoded routes and views.

This is part of a broader trend toward "agent-native" application design where the AI doesn't just assist — it drives UI state.

## License

MIT (SDK), Apache-2.0 (API backend)

## Related

- **[[moc-planning-work]]** — agent-driven workflows that could use generative UI for output
- **[[temporal-io-ai]]** — orchestration layer that could drive Tambo agents
- **[[openspec.dev]]** — spec-first approach compatible with Tambo's schema-driven component registration
- **[[exe.dev]]** — AI coding environment where tools like Tambo get built

---

*Added: February 18, 2026*
