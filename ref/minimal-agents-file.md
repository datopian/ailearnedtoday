---
created: 2026-08-03
author: Marcos Hernanz
tags: [agents, coding-agents, prompts, software-engineering]
---

# Minimal AGENTS.md for Side Projects

A small set of practical instructions for keeping AI coding agents focused on simple, maintainable implementations.

![Minimal AGENTS.md for Side Projects](https://screenshotit.app/https://x.com/MarcosHernanz/status/2083954734487212511)

## Links

- **Source**: https://x.com/MarcosHernanz/status/2083954734487212511

## Sample file

```markdown
# AGENTS.md
- Do not preserve backward compatibility. Remove obsolete paths instead of adding compatibility layers, fallbacks, or migrations.
- Choose the simplest implementation that fully meets the current requirements. Avoid speculative abstractions, configuration, and indirection.
- Grow the system in layers. Start from the smallest version that works end to end, and add each new capability on top of a product that already works. Never trade a working product for unfinished complexity.
- Keep components modular and concerns clearly separated.
- Prefer established, well-maintained libraries when they reduce overall complexity or improve reliability. Do not reimplement common functionality without a clear reason.
- Lean on the dependencies already in the project before writing your own implementation or adding packages. Do not assume a library lacks a capability without checking its documentation and types.
- Make architectural decisions for the long term. Do not accept a stopgap that only works for now and is meant to be replaced later.
- Study how established products solve the problem before designing a solution. Adopt their proven patterns and conventions rather than inventing an approach from scratch.
```

The emphasis is on removing obsolete paths, avoiding speculative complexity, building incrementally, and learning from established products before designing new patterns.
