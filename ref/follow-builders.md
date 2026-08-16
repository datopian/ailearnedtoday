---
created: 2026-08-11
author: zarazhangrui
tags: [ai-agents, claude-code, openclaw, digest, builders, x-twitter, youtube]
---

# Follow Builders, Not Influencers

> An AI-powered digest that tracks top AI builders on X and YouTube podcasts, remixes their content into digestible summaries. Follow builders, not influencers.

![follow-builders GitHub](https://screenshotit.app/https://github.com/zarazhangrui/follow-builders)

**GitHub:** [github.com/zarazhangrui/follow-builders](https://github.com/zarazhangrui/follow-builders)
**Stars:** 6.3k | **Forks:** 838

## What it is

A skill you install in your AI agent (OpenClaw or Claude Code) that delivers a daily or weekly digest of what top AI builders are saying — researchers, founders, PMs, engineers actually building things — as opposed to influencers regurgitating information.

The digest pulls from three source categories:

- **Podcasts (6):** Latent Space, Training Data, No Priors, White House AI, Tough Things, Equity
- **X/Twitter builders (26):** Includes Andrej Karpathy, Dylan Patel, Bloomberg AI, Zvi Mowshowitz, Cathie Wood, and others
- **Official blogs (2):** Anthropic Engineering, Claude Blog

Available in English, Chinese, or bilingual. Delivered to Telegram, Discord, WhatsApp, email, or in-chat.

## How it works

1. A central feed is updated daily with the latest content from all sources (blog articles via web scraping, YouTube transcripts via Supadata, X/Twitter via official API)
2. Your agent fetches the feed — one HTTP request, no API keys
3. Your agent remixes the raw content into a digestible summary using your preferences
4. The digest is delivered to your messaging app (or shown in-chat)

No API keys needed. All content is fetched centrally. If you use Telegram/email delivery, those keys are stored locally in `~/.follow-builders/.env`. Your configuration, preferences, and reading history stay on your machine.

## Installation

**Claude Code:**

```bash
git clone https://github.com/zarazhangrui/follow-builders.git ~/.claude/skills/follow-builders
cd ~/.claude/skills/follow-builders/scripts && npm install
```

Then tell your agent: "set up follow builders" or invoke `/follow-builders`.

**OpenClaw:**

```bash
git clone https://github.com/zarazhangrui/follow-builders.git ~/skills/follow-builders
cd ~/skills/follow-builders/scripts && npm install
```

## Customization

The skill uses plain-English prompt files to control how content is summarized:

- `summarize-podcast.md` — how podcast episodes are summarized
- `summarize-tweets.md` — how X/Twitter posts are summarized
- `summarize-blogs.md` — how blog posts are summarized
- `digest-intro.md` — the overall digest format and tone
- `translate.md` — how English content is translated to Chinese

Changes via conversation ("make summaries more concise," "focus on actionable insights") or direct editing. Take effect on the next digest.

## Why interesting

Fills a real gap: keeping up with AI builder content is hard because it's scattered across X, YouTube, and company blogs. The "follow builders, not influencers" framing is a useful heuristic — and having an agent do the curation and summarization means you get a focused digest rather than a firehose.

The central-feed architecture is also interesting: one HTTP request, no API keys for content, all the heavy lifting (scraping, transcript extraction, summarization) happens upstream. The skill is effectively a thin client.

## License

MIT

## See also

- [[ai-editing]] — Using AI to edit Markdown notes in Obsidian (Claude Code, Codex)
- [[coding-agents]] — broader category
