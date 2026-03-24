---
created: 2026-03-24
tags: [skills, management, package-manager, agents, tooling]
---

# Skills Managers

Tools that help discover, organize, and distribute agent skills across projects and coding agents.

## Category Overview

Skills management tools act like package managers for AI agent capabilities. They help developers:
- Discover and collect skills from various sources
- Organize prompts, system instructions, and agent configurations
- Distribute skills across multiple projects and agents
- Keep skills in sync as they evolve

Think "npm for agent skills" — centralized registries, local managers, and sync tools that treat agent capabilities as reusable, versioned assets.

## Tools

### skills.sh (Vercel)
**Status**: Current frontrunner  
**Type**: Directory/Registry  
**Link**: https://skills.sh

Agent Skills Directory by Vercel. Aggregates skills from major repositories (Microsoft GitHub Copilot for Azure, Azure Skills, Inferen, Impeccable, and community sources). Central discovery hub for finding existing skills.

**Key value**: Search and discover skills from 2.4M+ total across multiple repos.

See: [[skills-sh]]

### Oh My Agents
**Type**: Local manager + sync tool  
**Link**: https://oh-my-agents.app

Local workspace tool for managing skills across multiple agents. Discover prompts/skills in your projects, organize in central library, configure distribution rules per-project/per-agent, deploy with preview, pull changes back from projects to keep everything in sync.

**Key value**: "One Source. Every Agent. In Sync." — treats your local skills as evolving assets.

See: [[oh-my-agents]]

### OpenSkills
**Type**: Universal loader (npm package)  
**Link**: https://github.com/numman-ali/openskills (9.2k ⭐)

Universal skills loader for AI coding agents. Install globally via npm (`npm i -g openskills`), load skills programmatically. CLI-first approach for developers who want skills as code dependencies.

**Key value**: Treat skills like npm packages — install, version, import.

See: [[openskills]]

## Related Concepts

- [[skill-vs-agents-vs-claude-md]] - Different skill file formats and conventions
- [[anthropic-skills-guide]] - Anthropic's official skills documentation
- [[simon-willison-not-boring-tech]] - Skills adoption by projects (Remotion, Supabase, Vercel, Prisma)
- [[boris-cherny-claude-code-tips]] - Using skills effectively in Claude Code

## Ecosystem Trends

- **Official skills**: Major projects (Remotion, Supabase, Vercel, Prisma) releasing official agent skills
- **Format convergence**: SKILL.md as emerging standard (with variations like CLAUDE.md, .claud)
- **Distribution challenge**: How to share, version, and sync skills across projects/agents/teams
- **Local-first vs. registry**: Trade-offs between centralized discovery (skills.sh) and local management (Oh My Agents, OpenSkills)
