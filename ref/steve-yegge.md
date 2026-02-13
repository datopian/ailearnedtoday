---
created: 2026-02-09
tags: [people, ai, coding-agents, orchestration, vibe-coding]
---

# Steve Yegge - Coding Agent Pioneer & Vibe Coding Evangelist

**Ex-Geoworks, ex-Amazon, ex-Google, ex-Grab, ex-Sourcegraph engineer with over 30 years of tech industry experience, 40 years coding total.**

## Links

- **Medium:** https://steve-yegge.medium.com/
- **LinkedIn:** https://www.linkedin.com/in/steveyegge
- **Gas Town:** https://github.com/steveyegge/gas-town (AI coding agent factory)
- **Beads:** https://github.com/steveyegge/beads (agent-friendly task/workflow system)
- **Book:** [Vibe Coding: Building Production-Grade Software with AI](https://www.amazon.com/Vibe-Coding-Building-Production-Grade-Software/dp/1966280025) (with Gene Kim)

## Who Is He?

Steve Yegge is a legendary engineer and prolific writer known for his extensive career at major tech companies and his recent pioneering work in AI-powered software development.

### Career Highlights
- **Geoworks** - Early career
- **Amazon** - Multi-year tenure
- **Google** - Extended tenure
- **Grab** - Southeast Asian ride-hailing/super-app
- **Sourcegraph** - 3 years (2021-2024)
- **Current** - Independent, building AI coding tools

### Writing & Influence
Known for long-form, opinionated essays about software engineering, programming languages, and developer productivity. His writing style is candid, technical, and often humorous.

## Key Contributions to AI Coding

### Gas Town (2026)
Creator of **Gas Town**, an "AI coding agent factory" that orchestrates multiple AI coding agents working together like a colony.

**Philosophy:** "Nature prefers colonies over individual super-workers."

Instead of building one giant coding agent, Gas Town coordinates swarms of agents:
- **Roles:** Mayor (orchestration), Librarian (documentation), Deacon (PRs), Dogs (testing), Refinery (code quality)
- **Workflow:** Uses Beads for task management, tmux for session coordination
- **Scale:** Enables massive parallel development with multiple AI agents

**Key Innovation:** Treats coding agents as "factory workers" rather than "human pair programmers."

### Beads
Created **Beads**, an agent-friendly task and workflow system that agents can use naturally without training. Uses the "Desire Paths" approach to UX design: watch what agents try to do, then implement it.

### Vibe Coding
Co-authored **Vibe Coding** book with Gene Kim, formalizing the practice of AI-assisted development:

**Core Thesis:** Programming has always been vibe coding - "a best-effort, we'll-fix-shit-later endeavor." AI doesn't change that; it accelerates it.

Key principles:
- Ship with bugs, fix iteratively
- Focus on meeting customer needs
- Quality comes from tests and verification, not pristine code
- Engineers have always been "black boxes" that produce imperfect work

## Views on Temporal

In his article "The Future of Coding Agents," Yegge discusses his experience building multiple orchestrators:

**v1: Vibecoder** - Built atop [[temporal-io-ai]]
> "Temporal is the gold standard for workflow orchestration. I still believe Temporal will be a key piece of the puzzle for scaling AI workflows to enterprise level. Models love to offload cognition to powerful tools, and Temporal is as powerful as it gets: the Bagger 288 of workflow orchestrators."

**Why he moved away for Gas Town:**
- Temporal proved "cumbersome" for micro-workflows
- AI tasks need to be severely decomposed for LLMs to follow them
- Lost some vertical scalability (Gas Town is "machine-sized")
- Felt Temporal needs a "lite" version for dev tools

**But still essential:**
- For enterprise-scale AI workflow orchestration
- For tasks that need Temporal's full power
- "As powerful as it gets" for workflow orchestration

## Predictions & Philosophy

### The Future of Coding Agents (2026)
From his article:

**1. Colonies Will Win**
> "Everyone is focused on making their ant run longer, perform more, and do bigger things. Making the super-worker. The super-ant... But colonies are going to win. Factories are going to win. Automation is going to win."

**2. Agents Need to Become Better Colony Workers**
Coding agents will shift focus from being "human pair programmers" to being coordinated colony workers with proper platform APIs.

**3. Small Shops Will Outperform Big Companies**
> "The entire world is going to explode into tiny companies... small shops dramatically outperform large ones, to a degree we've never seen in all history."

Real example: Friends at startups going so fast that work from 2 hours ago is "ancient history."

**4. IDEs Are Goners**
If you're still using traditional IDEs, "you need to get your ass in gear and start using coding agents before you acquire the equivalent of severe body odor on the open market."

### On Programming Languages for AI Coding

**TypeScript:** Too verbose for AI, wastes tokens on type manipulations  
**Python:** "Fine" for server-side, but feels like scripts for client deployment  
**Go:** "Just good. Boring in the best way." Evolutionary advantage for AI coding because diffs are readable and predictable

### Evolution of Coders (2024-2026)
Created a spectrum of 8 levels showing developer trust in AI agents:
1. No trust - manual everything
2-5. Gradual adoption of AI assistance
6-7. AI takes over IDE, spills into CLI
8. Multi-agent orchestration (Gas Town territory)

## Workshops & Community

Hosts hands-on workshops with Gene Kim throughout 2026 for "premium educational experience to jumpstart enterprise devs in this brave new world."

## Output & Scale

Estimated **~1 million lines of vibe-coded code in 2025**, rivaling his entire 40-year career output (~1.1M lines) combined:
- **Beads + Gas Town:** Already pushing 500k lines including contributions
- Speed increasing as models improve

Burning significant API costs (reported $60k/year by peers) but achieving "dev-salary territory" in productivity.

## Key Quotes

On factories vs individual agents:
> "Anyone who thinks otherwise is, well, not a big fan of history, I guess."

On Temporal:
> "Temporal is as broadly useful as PostgreSQL; just as Postgres can be used to store and query most datasets people care about, Temporal can be used to model and execute most workflows people care about."

On vibe coding:
> "Programming has always been a best-effort, we'll-fix-shit-later endeavor. We always ship with bugs. The question is, how close is it? How good are your tests?"

## Why He Matters

Steve Yegge represents the frontier of AI-assisted software development:
- Actually using AI agents for serious production work at scale
- Building meta-tools (orchestrators for AI agents)
- Documenting the journey and philosophy
- Pushing the limits of what's possible today

His work with Gas Town and Beads, combined with his writing and workshops, makes him a key figure in understanding where AI coding is headed.

## Related

- [[temporal-io-ai]] - Workflow orchestration he used and advocates for enterprise
- [[crawshaw-eight-more-months-agents]] - Similar reflections on AI coding evolution
- [[exe.dev]] - Related to the infrastructure needs for AI development
