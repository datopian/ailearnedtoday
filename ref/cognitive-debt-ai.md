# Cognitive Debt in AI-Assisted Development

**URL**: https://simonwillison.net/2026/Feb/15/cognitive-debt/  
**Author**: Simon Willison (commentary on Margaret-Anne Storey's concept)  
**Date**: February 15, 2026  
**Type**: Article / Commentary  
**Tags**: #cognitive-debt #technical-debt #ai-coding #vibe-coding #developer-experience

## What Is It

Cognitive debt refers to the mental burden and loss of understanding that accumulates when developers use AI tools to generate code without fully comprehending the implementations. Unlike technical debt (which lives in the code), cognitive debt lives in developers' brains and affects their ability to reason about, modify, and confidently extend their systems.

The term has been gaining traction in discussions about AI-assisted development, particularly as tools like Claude Code, GitHub Copilot, and other AI agents make it easier to generate complex code without understanding every line.

## What Problem Does It Highlight

When AI agents produce code quickly, developers face a new risk: **losing the plot**. Even if the generated code is clean and well-structured, developers may not understand:

- Why certain design decisions were made
- How different parts of the system work together
- What the program is actually supposed to do
- How to confidently make changes without breaking unexpected things

This creates a situation where speed of development comes at the cost of comprehension, eventually paralyzing teams when they need to adapt or extend the system.

## Key Insights

### From Margaret-Anne Storey

Margaret-Anne Storey's [original article](https://margaretstorey.com/blog/2026/02/09/cognitive-debt/) describes a real-world case:

> "By weeks 7 or 8, one team hit a wall. They could no longer make even simple changes without breaking something unexpected. When I met with them, the team initially blamed technical debt: messy code, poor architecture, hurried implementations. But as we dug deeper, the real problem emerged: no one on the team could explain why certain design decisions had been made or how different parts of the system were supposed to work together. The code might have been messy, but the bigger issue was that the theory of the system, their shared understanding, had fragmented or disappeared entirely. **They had accumulated cognitive debt faster than technical debt, and it paralyzed them.**"

### From Simon Willison

Simon reflects on his own experience with "vibe coding" (prompting entire features into existence):

> "I've been experimenting with prompting entire new features into existence without reviewing their implementations and, while it works surprisingly well, I've found myself getting lost in my own projects. I no longer have a firm mental model of what they can do and how they work, which means each additional feature becomes harder to reason about, eventually leading me to lose the ability to make confident decisions about where to go next."

## Why It Matters

### For Individual Developers
- **Loss of agency**: When you don't understand your own code, you lose the ability to make confident design decisions
- **Feature paralysis**: Each new feature becomes harder to reason about, slowing development despite AI assistance
- **Debugging difficulty**: Without a mental model, troubleshooting unexpected behavior becomes nearly impossible

### For Teams
- **Shared understanding evaporates**: When different team members use AI to generate different parts of the system, no one has the full picture
- **Onboarding becomes impossible**: New team members can't learn from existing code if no one understands it
- **Documentation debt compounds**: AI-generated code often lacks the context of "why" decisions were made

### For the AI Coding Movement
This concept challenges the "move fast and break things" approach enabled by AI agents. It suggests that:
- **Code review remains essential**, even for AI-generated code
- **Comprehension can't be automated away** - developers still need to understand their systems
- **Speed without understanding has a hidden cost** that manifests later in the development cycle

## Related Concepts

- **[[vibe-coding]]** - The practice of prompting AI to generate entire features without detailed review (mentioned by [[steve-yegge]])
- **[[technical-debt]]** - Traditional concept of code-level debt that needs refactoring
- **[[exe.dev]]** - AI coding tool that attempts to address this by providing transparency
- **[[claude-code]]** - AI coding assistant that this concern applies to
- **[[openspec.dev]]** - Planning tool that could help maintain mental models through specifications

## Original Sources

- **Margaret-Anne Storey's article**: [How Generative and Agentic AI Shift Concern from Technical Debt to Cognitive Debt](https://margaretstorey.com/blog/2026/02/09/cognitive-debt/)
- **Media Lab paper**: [Your Brain on ChatGPT](https://www.media.mit.edu/publications/your-brain-on-chatgpt/)
- **Martin Fowler mention**: [Fragments 2026-02-13](https://martinfowler.com/fragments/2026-02-13.html)
- **Simon Willison's commentary**: https://simonwillison.net/2026/Feb/15/cognitive-debt/

## Screenshot

![](https://screenshotit.app/https://simonwillison.net/2026/Feb/15/cognitive-debt/)

---

*Added: February 15, 2026*
