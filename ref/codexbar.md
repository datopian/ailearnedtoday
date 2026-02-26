---
created: 2026-02-26
author: Peter Steinberger (@steipete)
tags: [macos, menu-bar, codex, claude-code, cursor, usage-tracking, developer-tools, open-source]
---

# CodexBar

> Stay ahead of resets. CodexBar keeps session + weekly limits (and credits) in the menu bar, so you know when you're safe to ship.

![CodexBar](https://screenshotit.app/https://codexbar.app)

## Links

- **Website**: https://codexbar.app
- **GitHub**: https://github.com/steipete/CodexBar
- **Download**: https://github.com/steipete/CodexBar/releases/latest
- **Author**: [Peter Steinberger](https://steipete.me) (@steipete)
- **License**: MIT
- **Install**: `brew install --cask steipete/tap/codexbar`

## What Is It

A macOS menu bar app that tracks session and weekly usage limits for multiple AI coding agents — Codex, Claude Code, Cursor, Gemini, Antigravity, Droid, Copilot, and z.ai. Shows real-time usage bars, reset countdowns, and optional credits so you can monitor whether you're about to hit rate limits.

**Free and open source.**

## Key Features

### Multi-Provider Support
Tracks limits for:
- **Codex** (OpenAI)
- **Claude Code** (Anthropic)
- **Cursor**
- **Gemini**
- **Antigravity**
- **Droid**
- **Copilot**
- **z.ai**

Open to new providers — see the [provider guide](https://github.com/steipete/CodexBar/blob/main/docs/provider.md).

### Session + Weekly Tracking
- **Two-bar icon**: Session on top, weekly on bottom
- Dimmed on errors
- Reset time countdowns
- Optional credits display
- Code review limits (when available)

### Menu Card
Click the menu bar icon to see:
- Session usage (current / limit)
- Weekly usage (current / limit)
- Time until reset
- Credits remaining (when applicable)

### Web-Backed Limits
Reuses existing browser cookies (Safari, Chrome, Firefox) to fetch dashboard data for:
- Codex
- Claude Code
- Cursor
- Droid

When cookies are missing, falls back to local CLI output.

### Privacy
- **No passwords stored**
- Reuses existing browser cookies for dashboard access
- Full Disk Access only for Safari cookies
- Keychain access for tokens
- Audit notes in [issue #12](https://github.com/steipete/CodexBar/issues/12)

### CLI + Automation
Bundled `codexbar` CLI for scripts and CI. Linux CLI builds available on GitHub Releases.

### Status + Widgets
- Provider status polling with incident badges
- WidgetKit snapshot that mirrors the menu card

### Minimal UI
- One status item per provider
- No Dock icon
- Lives in the menu bar

## Requirements

- macOS 14+ (Sonoma or later)
- Apple Silicon or Intel

## Installation

### Homebrew (recommended)
```bash
brew install --cask steipete/tap/codexbar
```

### Linuxbrew (CLI only)
```bash
brew install steipete/tap/codexbar
```

### GitHub Releases
Download from [releases](https://github.com/steipete/CodexBar/releases/latest) — includes Sparkle auto-updates.

## Why It Matters

### The Rate Limit Problem
AI coding agents have session and weekly limits. Hit the limit mid-task and you're blocked until reset. Developers waste time:
- Guessing how much quota remains
- Getting surprised by rate limit errors
- Switching between providers manually
- Checking dashboards constantly

### The CodexBar Solution
> "So you know when you're safe to ship."

See your limits at a glance in the menu bar. Plan work around reset times. Switch providers proactively before hitting limits.

### Multi-Agent Workflow
As developers use multiple AI coding agents (Codex for one task, Claude for another, Cursor for editing), tracking limits across all of them becomes critical. CodexBar consolidates everything in one view.

### CI/CD Integration
The CLI enables scripts to check limits before kicking off expensive agent tasks:
```bash
# Check if Codex has quota before running automation
codexbar status codex
```

## Who Built It

**Peter Steinberger** ([@steipete](https://steipete.me)) — also built [trimmy.app](https://trimmy.app). Known for iOS development (PSPDFKit founder).

## Technical Details

- **Platform**: macOS (Swift + SwiftUI)
- **macOS permissions**:
  - Full Disk Access (Safari cookies only)
  - Keychain Access (tokens)
  - Files & Folders (when provider CLIs access projects)
- **Updates**: Sparkle (GitHub builds) or `brew upgrade` (Homebrew installs)

## Related

- **[[harness-engineering-openai]]** — Codex workflow at scale (where usage tracking becomes critical)
- **[[dmux]]** — Managing multiple agents in parallel (CodexBar shows their limits)
- **[[autonomous-dogfooding-skill]]** — agent-browser automation (uses Codex/Claude)
- **[[anthropic-skills-guide]]** — Claude Code usage (CodexBar tracks its limits)

---

*Added: February 26, 2026*
