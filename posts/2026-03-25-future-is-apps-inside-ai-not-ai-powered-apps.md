---
title: The Future Is Apps Inside AI, Not AI Inside Apps
description: From AI-powered tools to AI as the operating system.
date: 2026-03-25
---

Cross-posted from [rufuspollock.com](https://rufuspollock.com/post/future-is-apps-inside-ai-not-ai-powered-apps).

It's time to stop talking about "AI-powered apps." That framing is wrong at a fundamental level. It's like saying "PC-powered software" in 1995 — it's a misunderstanding of the centre of gravity. The personal computer wasn't a feature inside applications. It was the platform everything else sat on.

The same inversion is happening now with frontier AI. Many of the first wave of AI startups built specialised tools: AI writing apps, AI PDF readers, AI flashcard generators etc. Each one wrapping a frontier model inside a custom UI. You upload your content and you operate inside their environment. The AI is there but mediated, constrained (and often degraded). I think this is a dead end. These products are the equivalent of the dedicated word processor in 1985: useful today, obsolete tomorrow.

The winning architecture is the opposite. You don't put AI inside your app. Put your app inside the AI. Use the frontier model directly, connect it to your files and workflows, and layer modular *skills* on top — capabilities the AI can invoke rather than environments you have to enter. AI is not a feature to embed. It's the new general-purpose computer. And just as the PC absorbed the word processor, frontier AI will absorb all these narrow tools.

## The Canon Word Processor

When personal computers were appearing in the 1980s, my father — a lawyer — went out and bought a dedicated Canon word processor. Not an IBM PC. Not an Apple II. A machine that did exactly one thing: word processing.

![The Canon StarWriter circa early 90s](/assets/starwriter.jpg)

*Fig 1: The Canon StarWriter circa early 90s*

And it was perfect for what he wanted. You turned it on and you had a world built entirely for writing. No configuration. No bugs. Small enough to carry around when laptops weren't even a thing.

And as a dedicated word processor, all the internals from the CPU to the operating system were hidden. It was a "CPU-powered word-processor".

For years this made sense. The dedicated device was focused, affordable, it was portable and it worked. My father used his Canon happily until one day ... something happened.

The general-purpose computer got better. Fast. Word processing became just another application you could run **on the computer** — and it was *good* word processing, because the underlying machine had so much more capacity. Then spreadsheets appeared on the same machine. Then databases. Then email.

The Canon word processor didn't evolve. It couldn't. It was a brilliant solution to a problem that the general-purpose computer was about to dissolve entirely. Within a decade, dedicated word processors were gone.

We went from **computer-*powered* word-processors** to **word processors *on* computers**.

## The Pattern Repeating

I see the same pattern playing out right now with AI. It crystallised for me while looking at flashcard tools to generate flashcards from books I'm reading. This is a specific, well-defined task. There are plenty of AI-powered apps for this. You upload your PDF, the system uses AI to extract key concepts, and out come flashcards. Neat. But you're *inside their system*. Your book is in their silo. Their AI is doing the work behind a wall you can't see or direct.

![Humata's AI PDF tool](/assets/humata.ai-pdf-ai-powered.jpg)

*Fig 2: Sorry to pick on you Humata, I'm sure you're really great ...*

Same thing with AI writing tools. I looked at several of them a few months ago — dedicated apps where you enter their text editor and the AI assists you. Again: you're inside their world. Your documents, your context, your way of working -- and their use of whatever AI model they've chosen.

These tools are Canon word processors. Each one takes a powerful general-purpose technology — frontier AI — and buries it inside a single-purpose application.

But the future is the inverse of that: what I want (and everyone else will) is to sit in my own environment, with my own files, connected to the best AI that I've chosen, and say "make flashcards from this PDF" or "help me write this essay in my voice." I don't want to enter an app. I want a *capability* — a **skill** the AI can perform, right where I already am.

## The Architecture: Three Layers

The analogy with computing maps cleanly. In the PC world, you had three things:

1. **The computer** — a general-purpose CPU and operating system
2. **Peripherals and storage** — monitor, keyboard, hard drive, printer
3. **Applications** — word processing, spreadsheets, databases

The computer wasn't hidden inside the word processor. It was the platform everything else sat on.

The AI equivalent:

1. **Frontier AI** — Claude, GPT, or whatever is best. This is your CPU.
2. **Storage and tools** — your files, PDFs, notes, APIs, browser, code execution
3. **Skills** — flashcard generation, essay writing in your voice, research workflows, coding patterns

```
           ┌─────────────────────────┐
           │   Skills / Capabilities  │
           │  (flashcards, writing,   │
           │   coding, research ...)  │
           └────────────┬────────────┘
                        │
  ┌─────────────┐  ┌────┴─────┐  ┌──────────────┐
  │ Storage &   │──│ Frontier │──│  Interfaces  │
  │ Tools       │  │ AI (LLM) │  │  (chat, CLI,  │
  │ (files,     │  │          │  │   editor ...) │
  │ APIs, DBs)  │  └──────────┘  └──────────────┘
  └─────────────┘
```

The key insight: skills are not apps. They're more like programs you load onto the computer. They shape the AI's behaviour for a particular task, but you stay in your environment, with your files, using the full power of the underlying model. When you're done making flashcards, you switch to writing an essay. Same AI, same context, same files. The skill changes; the platform doesn't.

## Skills Are the New Apps

This is already being built. [Agent skills](https://agentskills.io/specification) provide a standard way to package capabilities that any AI can invoke. A skill is a structured unit of know-how — instructions, references, examples — that plugs into the AI rather than wrapping around it.

To make this concrete: here's [frontend-slides](https://github.com/zarazhangrui/frontend-slides), a skill that lets any AI agent create polished HTML presentations from scratch or convert PowerPoint files. You don't open a slide-building app. You tell your AI "make me a presentation" and the skill gives it everything it needs.

That's the pattern. Not an app you enter, but a capability you give to your AI.

![frontend-slides skill on GitHub](https://screenshotit.app/https://github.com/zarazhangrui/frontend-slides)

*Fig 3: an "app" today to make slides. This is one of the leading skills to create slides. There is no UI because you do everything via prompting. What matters is token economy and quality of output. The "programming language" is plain English.*

## The Bitter Lesson, Applied

There's a concept in machine learning called the ["bitter lesson" — Rich Sutton's observation that methods which scale with more compute always win over methods that try to bake in human knowledge](https://bitterlesson.org/). The clever hand-engineered approach works for a while, then gets steamrolled by the dumb-but-scalable one.

Something similar applies here. The clever, hand-crafted AI application — with its bespoke UI, its custom pipelines, its carefully designed workflow — works for a while. But the frontier model keeps getting better. And every time it gets better, [the scaffolding around it matters less](https://ampcode.com/news/the-coding-agent-is-dead).

This is exactly what the coding agent teams have discovered. Early AI coding tools built elaborate orchestration: complex pipelines, multi-step prompt chains, careful error handling. But as the models improved, the teams kept stripping layers away. The better the model got, the less the scaffolding mattered. Now the most effective approach is something close to: give the model access to the codebase, tell it what you want, and get out of the way. Claude Code, Codex CLI — these are thin wrappers around a powerful core, not elaborate applications with AI bolted on.

The same will happen everywhere. The specialised AI writing app, the dedicated AI research tool, the custom AI flashcard generator — each one is a layer of scaffolding around a model that is rapidly making that scaffolding redundant.

## What This Means If You're Building

If you're building products in this space, ask yourself one question: *am I wrapping the AI, or extending it?*

If your product requires users to upload data into your silo, operate inside your interface, and depend on your workflow — you're building a word processor. It'll work for a while. It might even be a good business for a few years. But structurally, you're on the wrong side of the platform shift.

The alternative is to build *around* the AI. Build skills, not apps. Build connectors that bring the AI closer to users' own files and tools. Build command line tools. Build interfaces that are thin and composable, not monolithic. Think of yourself as making software for the new operating system, not building a replacement for it.

**The winners won't be those who build the prettiest AI-*powered* writing tool. They'll be the ones who understood that AI *is* the tool — and built everything else to plug into it.**
