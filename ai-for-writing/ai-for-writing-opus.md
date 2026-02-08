---
title: "Why Writing Hasn't Had Its Claude / Codex Moment Yet"
created: 2026-02-09
description: "AI-native coding tools have transformed how developers work. Writing — essays, books, screenplays, courses — deserves the same thing. Here's what exists, what's missing, and what you can do today."
---


## Executive summary

AI coding tools changed how developers work because they operate directly on the developer's own files, inside existing workflows, with repeatable commands and multi-step collaboration. Writing tools mostly have not crossed that threshold.

For prose, the dominant pattern is still: enter someone else's app, paste text, generate output, copy it back. That works for isolated chunks, but it breaks down for structured writing projects — essays, books, course material, scripts, research syntheses.

The finding is not that nothing exists. The finding is that the landscape is fragmented: many prose products, but inside closed editing environments; sophisticated users repurposing code agents to work on their own corpus; and no widely adopted, prose-native equivalent of the integrated coding-agent stack. The near-term path is pragmatic: use existing code-style agents on text repositories, formalise writing behaviours as files, and run a disciplined editorial workflow on content you control.

## The dream, stated plainly

I want AI tools that do for writing what AI-native coding tools now do for code.

Not chat. Not "generate me a blog post." I mean the full experience that tools like Claude Code, Codex CLI, Cursor, and Gemini CLI now provide for software: working *in situ* on an existing body of work, inside my editor or filesystem, with planning, context, iterative editing, and reusable skills.

If you've used any of these coding tools in the past year, you know the experience I'm describing. You open a terminal in your project directory. The tool sees your files, understands your codebase, and operates *on it* — not in some separate window. You can plan a multi-step refactoring, execute it piece by piece, roll back with Git, define reusable workflows. The AI is a collaborator sitting inside your project, not a chatbot in another tab.

Writing — real writing: essays, long-form nonfiction, books, novels, screenplays, research synthesis, courses, technical documentation — deserves this same treatment. These are structured creative artefacts. A book manuscript looks a lot like a codebase: multiple files, internal coherence, a need for planning, iterative revision, and style consistency. Even a substantial blog post is analogous to a small application.

And yet: nothing like this cleanly exists for prose today.

## What I specifically want to do

Before diving into what exists and what's missing, it helps to be concrete about the use cases. I'm talking about producing:

- **Essays and long-form blog posts** — structured arguments with research, citations, and a coherent arc. Even a "simple" blog post is like a small app: it has architecture, it needs context, it benefits from a plan.
- **Books and book-length nonfiction** — multi-chapter projects with internal consistency, character or argument tracking, and months of iterative revision. This is a large codebase.
- **Courses and educational material** — structured sequences of lessons with exercises, where coherence across modules matters as much as individual quality.
- **Screenplays and scripts** — highly formatted, structurally constrained prose where dialogue, scene structure, and pacing follow specific conventions.
- **Research synthesis** — pulling together sources, notes, and findings into a coherent written output. This is where the analogy to code is strongest: you have a corpus of inputs and need to produce a structured output.
- **Technical documentation** — already close to code in structure, and already partially served by code tools, but rarely with prose-quality editorial support.

What unites these is that they are *structured writing projects of non-trivial size*, where you want context across the whole project, you want to plan sections of work and execute them, and you want the AI to understand and respect the existing body of material. You don't want to copy-paste fragments into a chat window. You want the tool operating on your content, in your editor, against your files.

## The experience gap: what coding has and writing doesn't

To make this concrete, here's what a sophisticated developer gets today from tools like Claude Code, Codex CLI, or Cursor — and what a writer currently lacks:

| Coding workflow | Writing equivalent (desired) | Current status for writing |
|---|---|---|
| Tool operates on your local codebase | Tool operates on your manuscript files | Partially possible by repurposing code tools |
| `CLAUDE.md` / project instructions tell the AI how to behave | `tone.md` / style guide tells the AI your voice and conventions | No standard exists |
| Multi-step planning ("refactor auth, then update tests, then fix the API") | Multi-step editorial planning ("restructure chapter 3, then tighten the argument, then check consistency with chapter 1") | Ad hoc at best |
| Reusable skills (brainstorming, TDD, debugging, committing) | Reusable writing skills (outlining, developmental editing, line editing, fact-checking, style enforcement) | Barely emerging |
| Git for version control and rollback | Git for manuscript versioning | Works if you're technical enough |
| Linting and tests as quality gates | Style checking and editorial checklists as quality gates | Nothing standardised |
| Context window spans the full project | Context window spans the full manuscript | Works with code tools on small manuscripts |

The gap isn't that AI can't write prose — it clearly can. The gap is *infrastructure*: the surrounding system of editor integration, local file access, planning, skills, and iterative workflow that makes AI coding tools so much more powerful than a chat interface.

## What exists today: products

There are AI writing products. The problem is that almost all of them trap you inside their interface, exactly the way ChatGPT's web UI does.

**Prose-native AI tools:**

- **Sudowrite** — built specifically for fiction writers. Offers generative tools, rewriting, and brainstorming tailored to storytelling. But you work inside Sudowrite's editor. Your manuscript lives in their system.
- **Novelcrafter** — designed for long-form fiction with character management, lore tracking, and structure tools. Again: you're inside Novelcrafter, not working on your own files.
- **Type.ai** — supports books, essays, and screenplays up to 130,000+ words. Impressive scope, but the same fundamental constraint: you edit inside Type.ai's interface.

**General AI writing platforms:**

- **ChatGPT Canvas** / **Claude Artifacts** — these work well for creating one small piece of content, but there's a mismatch between where your content lives and where the AI operates. You're in the app. Your manuscript is somewhere else.
- **Notion AI**, **Lex**, **Writesonic**, **Frase** — various AI-augmented writing environments. All share the same pattern: come to us, work in our editor.

**Editor plugins:**

- **CoolWriter for VS Code** — integrates AI writing assistance into VS Code. Closer to the right model, but limited in scope.
- **Obsidian AI plugins** (community-maintained) — operate on your vault, which is genuinely local-first. But they're typically limited to single-note operations, not corpus-level reasoning.

The fundamental problem with all of these products is the same: **I end up inside the tool rather than the tool operating on my content.** I have to leave my files, my editor, my filesystem, and go work in someone else's environment. For a simple one-off piece this is fine. For a book, a course, a body of work — it's exactly the wrong model.

This is the problem that coding tools solved. You don't go to Claude Code's website to edit your codebase. Claude Code comes to your codebase.

## What exists today: patterns

If dedicated products don't solve the problem, what about patterns — how are people actually doing this? Based on documented workflows, blog posts, and community practice, five patterns are visible today. None is fully mature. All are being assembled by sophisticated users rather than offered as integrated products.

### Pattern 1: Code agents repurposed for prose

The most direct approach: take a tool like Claude Code, Codex CLI, or Gemini CLI — designed for code — and point it at a repository of Markdown or text files instead.

**Typical workflow:**
- A Git repo containing Markdown, LaTeX, or Fountain files
- Commands framed as editorial tasks: "revise this section for clarity," "tighten the argument in chapter 2," "apply the style described in tone.md"
- Git handles iteration and rollback; the agent handles transformation

**What works:** Precise, scoped edits. A familiar mental model for developers. Strong composability with Git and shell scripts. The tool genuinely operates on your files in your editor.

**What doesn't:** No prose-native abstractions. The tool behaves like a very powerful text editor, not an editor-in-chief. "Skills" exist only as prompts or shell scripts you write yourself. There's no built-in understanding of manuscript structure, narrative arc, or editorial process.

**Documented examples:**
- ["How I Built My Personal AI Writing Agent with Claude Code"](https://medium.com/@pa_sherman/how-i-built-my-personal-ai-writing-agent-with-claude-code-and-you-can-too-4f3ae29019d2) — step-by-step construction of a writing pipeline with Claude Code
- [claudecode-writer](https://github.com/WomenDefiningAI/claudecode-writer) — a GitHub template that turns Claude Code into a content creation system
- ["Streamlining Blog Writing with Claude Code"](https://www.aaronheld.com/post/streamlining-blog-writing-with-claude-code/) — a complete workflow from idea to published Markdown

The examples that exist tend to focus on blog posts rather than essays or books, but the underlying pattern works for longer material too — it just requires more manual setup.

### Pattern 2: Editor-embedded copilots

Users stay inside a general-purpose editor (VS Code, Obsidian, Cursor) and invoke AI as commands rather than conversation.

**Typical workflow:**
- VS Code or Obsidian as the writing environment
- AI invoked via slash commands, palette actions, or inline completion
- Context is typically the active file, possibly plus a few linked notes

**What works:** Low friction. Fine-grained control. Fits existing writing habits. You're genuinely working on your own files.

**What doesn't:** Weak corpus-level reasoning — the tool usually sees one file at a time, not your whole manuscript. "Skills" are ad hoc, not first-class. No real editorial planning across a project.

**Representative tools:** Cursor (commonly used on Markdown, not just code), Windsurf, various Obsidian AI plugins.

### Pattern 3: Prompt-as-infrastructure ("skills as files")

Instead of relying on a tool, users build reusable, versioned editorial behaviours stored as prompt files.

**Typical workflow:**
- A `/prompts/` directory in the project repo, with Markdown or YAML files
- Each file defines a role or skill: "developmental editor," "fact checker," "style enforcer," "outline critic"
- Invoked via CLI tool, editor command, or shell script

**What works:** Transparency — you can read and version your editorial process. Reusability across projects. Shareable editorial practice.

**What doesn't:** No UI support. Requires high technical sophistication. No built-in memory or continuity beyond what you manage yourself in files.

This pattern currently shows up mainly as community-shared prompt repos (like [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)) rather than polished writing-specific workflow collections. That itself is a useful signal: the infrastructure is there, but writing-specific skills haven't crystallised.

### Pattern 4: Agent frameworks adapted to writing pipelines

Multi-agent systems originally designed for software tasks (AutoGen, CrewAI, OpenDevin-style planners) repurposed for writing processes.

**Typical workflow:**
- Agents with distinct roles: outliner, drafter, critic, fact-checker
- Explicit stages: outline, draft, revise, polish
- Outputs written back to files

**What works:** Strong process modelling. Explicit division of labour. Good for highly structured, repeatable writing tasks.

**What doesn't:** Heavyweight. Fragile for subtle prose work — the nuance of good writing doesn't decompose neatly into agent roles. Often over-engineered for a solo writer.

### Pattern 5: Corpus-first note-to-manuscript systems

Writers treat their entire note corpus as the primary object, with AI used for synthesis and recombination.

**Typical workflow:**
- An Obsidian or Zettelkasten vault as the base
- AI for summarisation, clustering, finding connections, synthesising across notes
- Manual curation of AI output into essays or book chapters

**What works:** Deep contextual grounding. Excellent for research-driven nonfiction where the raw material already exists as notes.

**What doesn't:** Weak end-to-end drafting support. No unified "agentic" flow that takes you from notes to manuscript. You're assembling the pipeline yourself.

## The interim verdict

What exists today is **not a single "Codex for writing," but a set of partial convergences:**

- Code agents *can* edit prose effectively — but they don't know what prose is
- Editors *can* host AI-assisted writing — but without project-level intelligence
- Skills exist — but as informal prompt infrastructure, not as first-class editorial workflows
- Corpus-level reasoning remains awkward
- No tool yet integrates *editor + corpus + skills + continuity* cleanly

This explains why sophisticated users assemble custom workflows rather than adopt a single product. The pieces are all there. The integration isn't.

## What you can do right now

If you're a technical user comfortable with the command line, the most practical approach today is Pattern 1: repurposing a code agent for prose. Here's a concrete starting point using Claude Code (similar workflows work with Codex CLI or Gemini CLI):

**1. Structure your writing project like a codebase:**

```
my-book/
  CLAUDE.md          # project instructions + tone guide
  outline.md         # structural plan
  chapters/
    01-introduction.md
    02-the-problem.md
    03-what-exists.md
  research/
    notes.md
    sources.md
  prompts/
    developmental-edit.md
    line-edit.md
    fact-check.md
```

**2. Create a `CLAUDE.md` (or equivalent) that acts as your tone and style guide:**

```markdown
# Project: [Book Title]

## Voice and Style
- Write in first person, conversational but precise
- Prefer short sentences. Vary rhythm.
- Use concrete examples over abstractions
- British spelling (colour, analyse, behaviour)
- No emoji. No exclamation marks except in dialogue.

## Structure
- Each chapter is a separate Markdown file in chapters/
- The outline in outline.md is the source of truth for structure
- Research notes in research/ should be cited when used

## Editorial Rules
- Never pad with filler phrases ("it's important to note that...")
- Cut adverbs unless they change meaning
- Every paragraph should advance the argument or narrative
```

**3. Use the agent for editorial tasks, not generation:**

Rather than asking the AI to write from scratch, the most effective pattern is iterative editing on existing drafts:

- "Read chapter 2 and identify where the argument is weakest. Suggest specific cuts and restructuring."
- "Apply the style guidelines in CLAUDE.md to this section. Show me the diff."
- "Check this chapter for consistency with the outline. Flag any deviations."
- "Tighten this section: cut 20% of the word count without losing any key points."

**4. Use Git for versioning:**

Every significant edit pass becomes a commit. You can compare versions, roll back, branch for experimental rewrites. This is one area where the code-to-writing analogy works perfectly, with zero adaptation needed.

## What a real solution would look like

The dream — which no single tool currently delivers — combines these elements:

1. **Operates on your files.** My manuscript lives in my filesystem (Markdown, Google Docs, whatever). The tool comes to my content, not the other way around.

2. **Understands manuscript structure.** Not just individual files, but the whole project: chapters, sections, characters, arguments, themes, cross-references.

3. **Supports reusable editorial skills.** Not just free-form prompting, but defined, versioned, shareable writing skills: developmental editing, line editing, style enforcement, fact-checking, outline critique — analogous to brainstorming, TDD, debugging, and committing in code.

4. **Maintains continuity.** Remembers what we discussed about chapter 3 when I'm working on chapter 7. Knows the editorial decisions we've made. Tracks what's been revised and what hasn't.

5. **Works in my editor.** Whether that's VS Code, Obsidian, a terminal, or (for less technical users) Google Docs — the AI meets the writer where they already work.

6. **Supports a `tone.md` convention.** Just as `CLAUDE.md` or `agents.md` tells an AI how to behave in a code repository, a `tone.md` (or `STYLE.md`, `VOICE.md`) would tell it how to write in this project: voice, register, conventions, things to avoid. No standard for this exists yet, but it should.

The closest analogy is what happened with code: for years, AI could "write code" in a chat window. Then tools like Cursor and Claude Code arrived and made AI work *inside your project*, with context, planning, and iterative workflow. That transition — from chat-based generation to project-embedded collaboration — is what writing needs next.

## Why the gap persists

Three factors explain why writing hasn't had this moment yet:

**The market is smaller and less monetisable.** Software developers are a large, well-funded market with clear productivity metrics. Writers — especially the kind who would use CLI tools — are a smaller, more fragmented audience.

**Writing lacks formal correctness constraints.** Code has tests, type systems, and linters that provide objective quality signals. Prose quality is subjective, which makes it harder to build automated quality gates and harder to demonstrate measurable improvement.

**The existing tools work well enough for short content.** ChatGPT, Claude, and similar chat interfaces are genuinely good at helping with a single blog post or email. The pain only becomes acute with longer, structured projects — and fewer people are attempting those with AI assistance yet.

But the pieces are converging. Context windows are growing. Code agents already work on arbitrary text files. The skills-as-files pattern is emerging organically. Someone will put it together.

## Appendix: Toward a `TONE.md` standard

One small, concrete thing that could accelerate this convergence: a lightweight convention for describing writing style and voice in a machine-readable file, analogous to `CLAUDE.md` or `.editorconfig` for code.

There is no widely adopted standard for this today. What exists is fragmented: some users put style notes in their `CLAUDE.md`, some create ad hoc `STYLE.md` files, some embed instructions in prompts. No tool interoperates on a shared schema.

A minimal `TONE.md` might look like:

```markdown
# Tone

## Voice
- First person, direct
- Conversational but not casual
- Expert speaking to peers, not lecturing

## Style
- Short paragraphs (3-5 sentences max)
- Concrete before abstract
- Active voice preferred
- British English spelling

## Avoid
- Corporate jargon
- Hedge words (somewhat, fairly, quite)
- Filler phrases (it should be noted, importantly)
- Emoji and exclamation marks

## References
- Orwell's "Politics and the English Language" as a north star
- Sentence rhythm: vary between short punchy and longer flowing
```

This wouldn't need to be complex. The value would come from convention — the same way `.gitignore` is simple but universally understood. If multiple tools adopted even a rough convention, writers could define their voice once and have it respected across editing sessions, tools, and collaborators.

## Where this leaves us

Writing hasn't had its Codex moment. But the raw ingredients exist: code agents that work on any text, editors that can host AI assistance, prompt systems that define editorial skills, and version control that handles manuscripts exactly as well as it handles source code.

What's missing is integration — a tool, or a thin layer on existing tools, that combines these pieces into a coherent writing workflow. The writer's equivalent of opening a terminal in your project and saying: "Read the manuscript. Here's the style guide. Let's work on chapter 3."

For now, the best option for a sophisticated user is to repurpose a code agent, structure your writing project like a repo, define your style in a configuration file, and build up your own editorial skills as reusable prompts. It works. It's just not yet as elegant as what developers have.

Someone should fix that.

## Appendix B: A more developed writing-project scaffold

The `tone.md` above is a minimal starting point. For a serious project — a book, a course, a long research piece — you might want to separate concerns more carefully, the way a mature codebase separates configuration from logic. Here's a more developed version that splits voice, tone, structure, and workflow into distinct files, each with a clear responsibility.

```text
writing-project/
  drafts/
    00-idea.md
    01-outline.md
    02-draft.md
    03-revision.md
  references/
    notes.md
    sources.md
  prompts/
    developmental-editor.md
    line-editor.md
    fact-checker.md
  CHECKLISTS/
    structure.md
    style.md
    verification.md
  VOICE.md
  TONE.md
  STRUCTURE.md
  WORKFLOW.md
```

The key distinction is between files:

- **`VOICE.md`**: your durable writing identity — stance, reader relationship, diction, rhetorical defaults. This changes rarely. It's who you are on the page.
- **`TONE.md`**: context-sensitive modulation — what shifts by audience, medium, and section type. The same voice might be warmer in an introduction and more clipped in a methods section.
- **`STRUCTURE.md`**: canonical document architecture — how you handle openings, transitions, evidence density, conclusions. Your structural habits, made explicit.
- **`WORKFLOW.md`**: the exact multi-pass editorial process and acceptance criteria for each pass.
- **`prompts/*.md`**: reusable editorial operations that agents can run predictably.
- **`CHECKLISTS/*.md`**: gate checks before moving to the next pass.

Example `TONE.md`:

```markdown
# Tone Contract

## Audience
- Primary: technically literate general readers
- Secondary: practitioners evaluating workflow design

## Voice Targets
- Clear, direct, non-performative
- Analytical over promotional
- Concrete before abstract

## Style Constraints
- Prefer short declarative sentences
- Avoid hype terms and vague intensifiers
- Use examples when making process claims

## Do / Don't
- Do state trade-offs explicitly
- Do separate evidence from inference
- Don't anthropomorphise tools
- Don't hide uncertainty

## Revision Priorities (in order)
1. Argument coherence
2. Evidence quality
3. Clarity and compression
4. Rhythm and polish
```

Example `WORKFLOW.md`:

```markdown
# Writing Workflow

## Pass A: Structure
Goal: validate argument map and section order.
Exit criteria: each section has a single job and clear transition.

## Pass B: Draft Expansion
Goal: fill sections to target depth with concrete detail.
Exit criteria: every claim has at least one supporting example or reason.

## Pass C: Line Edit
Goal: improve readability and cadence without changing meaning.
Exit criteria: remove redundancy, sharpen verbs, tighten openings.

## Pass D: Verification
Goal: confirm factual claims and source integrity.
Exit criteria: uncertain claims flagged or removed; citations updated.
```

You can run this with any capable code-style agent by attaching task instructions to a pass, limiting scope to explicit files, and requiring diff-based outputs per pass.
