# Text-to-Lottie v1.0.0 - AI-Generated Lottie Animations

**Date:** June 15, 2026  
**Author:** Konstantin Paulus (@konstipaulus)  
**Tweet:** https://x.com/konstipaulus/status/2066534707496444317  
**GitHub:** https://github.com/diffusionstudio/lottie  
**License:** MIT  
**Stars:** 2.8k

## What It Is

An open-source framework for generating production-ready Lottie animations using Claude Code, Codex, or any coding agent that supports skills.

## v1.0.0 Features

- **Multi-project, multi-scene support** - Organize complex animation workflows
- **Drag-and-drop Lottie file import** - Import existing animations for refinement
- **Complete UI rewrite** - Enhanced player interface with live updates
- **Real-time preview** - Animations auto-reload as the agent edits them

## Quick Start

```bash
npx skills add diffusionstudio/lottie
```

Then prompt your coding agent to create animations with natural language.

## Example Prompt

> Create a Lottie animation from the SVG path in [URL]. Reveal the path with an animation that follows the natural path direction. Apply a premium apple themed gradient to the path. Use ease-in-out timing, a transparent background, and preserve the original SVG geometry.

## Prompt Engineering Tips

1. **Ground the model** - Provide SVGs, real-world data, or screenshots for better results
2. **Use motion design terminology** - ease-in, ease-out, ease-in-out
3. **Think like a camera operator** - Request camera pushes, pans, zooms
4. **Request controls explicitly** - Ask for specific customizable properties
5. **Specify FPS and duration** - Include frame rate and total frames if needed

## Platform Support

- **Web** - vanilla HTML + lottie-web
- **React Native** - LottieView or React Native Skia
- **iOS** - Swift with Lottie framework
- **Android** - Kotlin
- **Flutter** - Lottie package
- **After Effects** - Export for further refinement

## Significance

Demonstrates growing ecosystem of AI-powered creative tools. Text-to-Lottie bridges natural language prompting with professional animation workflows, making motion graphics accessible through coding agents.

## Tags

#ai-tools #lottie #animations #claude-code #codex #coding-agents #creative-ai #skills
