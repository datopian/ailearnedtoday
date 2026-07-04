# Skills are to AI what libraries were to software

Software got good when we stopped rewriting code and started sharing it. Every language eventually grew the same stack: a package format, a registry, a CLI to install/publish/version. `pip`, `npm`, `cargo`, `gem` — different syntax, same trade: don't write it again, depend on it instead.

AI agents are rebuilding that stack right now, for know-how instead of code. A "skill" is the same idea — a packaged, reusable unit — just applied to *how to do something* rather than *code that does something*: a markdown file describing a workflow, maybe some scripts or examples, dropped where an agent looks for it. Instead of depending on a library at runtime, an agent depends on a skill at "thinking time" — it reads the skill and follows it. The parallel goes deeper than the surface metaphor:

| Libraries | Skills |
|---|---|
| Function/class you call | Procedure/workflow the agent follows |
| Installed into `node_modules`, imported | Dropped into a skills dir, loaded into context |
| Versioned, published to a registry | Mostly unversioned, copy-pasted or symlinked |
| Composable — libraries depend on libraries | Composable — a skill can point an agent at other skills |
| Discovered via npm/PyPI search | Discovered via directories like skills.sh (see appendix) |

![npm registry](https://screenshotit.app/https://www.npmjs.com)

The gaps in that second column are exactly where the ecosystem is right now: pre-npm. The *file format* has actually converged fast — SKILL.md, more below — but the plumbing around it (registries, versioning, a real dependency graph, an `npm link` equivalent) is still being invented by several different projects at once, none dominant yet.

A small personal example of that immaturity: I wanted a skill for how I lay out new projects — personal, half-baked, not something I'd publish. In npm-land that's `npm link`: point a local, in-development package at a project and use it as if it were installed, no publish step needed. There's no real equivalent for skills yet — mostly you just drop a folder in the right place and hope. It's a minor gap, but it's a symptom of the bigger one: we don't yet have the shared tooling that made libraries painless.

## Appendix: early "package managers" for skills

Registries and installers, roughly in order of how npm-like they feel:

![skills.sh](https://screenshotit.app/https://skills.sh)

- **[skills.sh](https://skills.sh)** (Vercel, launched Jan 2026) — the current frontrunner. `npx skills add owner/repo` installs a skill; works across 18+ agents (Claude Code, Cursor, Codex, Copilot, Windsurf...). Tens of thousands of skills, millions of installs. Closest thing to an actual npm registry.
- **[OpenSkills](https://github.com/numman-ali/openskills)** — `npm i -g openskills`, a universal loader that treats skills as npm dependencies: install, version, import. Most literal "npm for skills" take, built on npm itself.
- **[skillpm](https://github.com/sbroenne/skillpm)** and **[skillpkg](https://github.com/miles990/skillpkg)** — two more npm-style CLI package managers for skills, independently built, both doing roughly the same job as OpenSkills. A sign of how unsettled this layer still is: three different projects converged on "wrap npm" as the obvious first move.
- **[skild](https://skild.sh)** — another entrant styling itself "the npm for AI Agent Skills," one command to install/manage/push/share.
- **[SkillsMP](https://skillsmp.com)** — volume play: crawls GitHub for `SKILL.md` files and indexes them (reportedly 800K–1.9M+), minimal review. Useful for breadth, not for trust.
- **[Oh My Agents](https://oh-my-agents.app)** — local-first workspace, not a public registry: discover skills across your own projects, organize centrally, push distribution rules out per-project/per-agent, pull changes back. Closer to a dotfiles manager than an npm.
- **[Agensi](https://www.agensi.io)** — curated and paid: every skill passes an 8-point security check before listing, creators keep 70% of sales. The "vetted" counterweight to the crawl-everything registries.
- **[claudeskil.com](https://claudeskil.com)**, **[ClaudeSkills.info](https://claudeskills.info)**, and 2,500+ **[Claude Code plugin marketplaces](https://claudemarketplaces.com)** — a long tail of smaller, mostly Claude-specific directories, quality varying widely.

Two axes of disagreement so far: *centralized registry vs. local-first sync* (skills.sh vs. Oh My Agents), and *open crawl vs. curated/reviewed* (SkillsMP vs. Agensi). Nobody's converged on one winner — normal for this stage; npm itself didn't show up until years after JavaScript did.

## Appendix: is there a skill *format* standard?

Yes, and this part converged faster than the tooling around it.

![agentskills.io](https://screenshotit.app/https://agentskills.io/home)

**[agentskills.io](https://agentskills.io/home)** hosts "Agent Skills," the open specification for the `SKILL.md` format: a folder with a required `SKILL.md` (YAML frontmatter with `name`/`description`, markdown instructions below it) plus optional `scripts/`, `references/`, `assets/` directories. Agents load skills via progressive disclosure — just name+description at startup, full instructions only when a task matches.

The standard was originally Anthropic's (Claude's own skills system), released as an open spec in December 2025 and now governed at agentskills.io with its own GitHub org and Discord, open to outside contribution. The showcase lists ~40 adopting platforms as of mid-2026 — Claude Code, Codex CLI, Gemini CLI, Cursor, GitHub Copilot, VS Code, Kiro, Goose, Roo Code, and more — so a skill written once genuinely runs in most of them unmodified.

Claude's own implementation predates and still slightly leads the spec (progressive disclosure, the `references/`/`assets/` layout) — less a competing standard than the reference implementation the open spec was extracted from.

Worth distinguishing from a related but different convention: **[AGENTS.md](https://agents.md)**, championed by OpenAI/Codex and now used in 60,000+ repos. That's a single file of repo-level instructions for any agent working in that codebase — README-for-agents, not a packaged, reusable, portable unit like a skill. The two compose: an `AGENTS.md` can tell an agent which skills to reach for.
