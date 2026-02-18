---
created: 2026-02-18
author: OliverHenry (@OllieWazza)
tags: [clawhub, skill, tiktok, marketing, ai-agents, automation, social-media]
---

# Larry — TikTok Marketing Automation Skill

> Automate your entire TikTok slideshow marketing pipeline: generate → overlay → post → track → iterate.

![Larry on ClawHub](https://screenshotit.app/https://clawhub.ai/OllieWazza/larry)

## Links

- **ClawHub**: https://clawhub.ai/OllieWazza/larry
- **Creator**: [@OllieWazza](https://x.com/OllieWazza) (OliverHenry)
- **Install**: `clawhub install larry` (or download zip from page)

## What Is It

Larry is an [OpenClaw](https://openclaw.ai) / ClawHub skill that acts as an AI-powered TikTok marketing agent for app and product promotion. It handles the full pipeline: competitor research → AI image generation → text overlays → posting via Postiz → daily analytics → iteration.

**Proven results (per the SKILL.md):** 7M views on viral X article, 1M+ TikTok views, $670/month MRR — "all from an AI agent running on an old gaming PC."

## Key Features

- **Onboards conversationally** — talks to you like a marketing partner, asks about your app, audience, and goals
- **Competitor research** — browses TikTok to analyze what's working in your niche before building strategy
- **AI image generation** — via OpenAI `gpt-image-1.5` (strongly recommended), Stability AI, Replicate, or local images. Generates portrait 1024×1536px slides
- **Text overlays** — uses `node-canvas` to add readable text with dynamic sizing, white fill + thick black outline. Centered at 28% from top, sized by word count
- **Posts as drafts** — sends to TikTok inbox (SELF_ONLY) so you can add trending music manually before publishing. Music = reach; silent slideshows get buried
- **Daily analytics cron** — pulls Postiz per-post data + RevenueCat conversion data; diagnoses which part of the funnel is broken (hook? CTA? app onboarding?)
- **RevenueCat integration** — connects views to paying subscribers. "A post with 200K views and zero conversions is worthless. A post with 5K views and 10 paid subscribers is gold."
- **Cross-posting** — Postiz supports Instagram Reels, YouTube Shorts, Threads, and 20+ other platforms simultaneously

## Stack

Node.js · node-canvas · Postiz (posting + analytics API) · RevenueCat (conversion tracking) · OpenAI gpt-image-1.5

## Security Note

ClawHub security scan: VirusTotal ✅ Benign, OpenClaw ⚠️ Suspicious (medium confidence) — stores many API keys; review config handling and run in sandbox before trusting.

## Related

- **[[clawhub]]** — the skill marketplace Larry lives on
- **[[alfred-portable-openclaw]]** — another OpenClaw-ecosystem project

---

*Added: February 18, 2026*
