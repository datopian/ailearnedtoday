---
created: 2026-02-28
author: Armin Ronacher
tags: [ai-coding, coding-agents, psychology, addiction, code-quality, open-source, maintainer-burden, gas-town, slop]
---

# Agent Psychosis: Are We Going Insane?

**Armin Ronacher's January 2026 essay on AI coding addiction, parasocial relationships with agents, and the degradation of open-source contribution quality.**

![Agent Psychosis article](https://screenshotit.app/https://lucumr.pocoo.org/2026/1/18/agent-psychosis/)

## Links

- **Article**: https://lucumr.pocoo.org/2026/1/18/agent-psychosis/
- **Published**: January 18, 2026
- **Author**: Armin Ronacher (creator of Flask, Jinja, Rye)
- **Blog**: lucumr.pocoo.org

## Overview

A critical examination of the psychological and social effects of AI coding agents, written by a prominent open-source maintainer. Ronacher explores "agent psychosis" — the addiction, unhealthy behavior patterns, and quality degradation emerging from uncritical AI coding agent use.

**Core tension**: "Two things are both true to me right now: AI agents are amazing and a huge productivity boost. They are also massive slop machines if you turn off your brain and let go completely."

## Key Observations

### Our Little Dæmons

**Metaphor from His Dark Materials**: AI agents as external manifestations of our soul, companions we become dependent on.

> "We become dependent on them, and separation from them is painful and takes away from our new-found identity. We're relying on these little companions to validate us and to collaborate with. But it's not a genuine collaboration like between humans, it's one that is completely driven by us, and the AI is just there for the ride."

**The dependency**:
- People develop parasocial relationships with their AIs
- Separation anxiety when rate limits hit
- "Some people who have not programmed before, now wield tremendous powers, but all those powers are gone when their subscription hits a rate limit and their little dæmon goes to sleep"

**The problem with pseudo-collaboration**:
- We can trick AI to reinforce our ideas and impulses
- Act through the AI without genuine critical thinking
- When familiar with systems: can give clarity
- When unfamiliar: "completely forcing the AI down a path without any real critical thinking... creates some really bizarre outcomes"

### Prompting Behavior Patterns

Observable patterns in how people interact with agents:
- Unclear instructions
- Weird role-playing and slang
- Swearing and forcing the machine
- Weird ritualistic behavior
- "Ram the agent straight towards the most narrow of all paths towards a badly defined goal with little concern about the health of the codebase"

### Addicted to Prompts

**The dopamine loop**:
> "I did not sleep. I spent two months excessively prompting the thing and wasting tokens. I ended up building and building and creating a ton of tools I did not end up using much. 'You can just do things' was what on my mind all the time but it took quite a bit longer to realize that just because you can, you might not want to."

**The realization**:
- Easy to build something
- Much harder to actually use it or polish it
- Built tools felt great, then realized: didn't actually use them, or they didn't work as thought

**Decoupled from reality**:
- Dopamine hit from working with agents is very real
- Feel productive, feel amazing
- Hang out with people into the same thing → go deeper without reality checks
- "For as long as nobody looks under the hood, you're good. But when an outsider first pokes at it, it looks pretty crazy"

**Example**: Cursor's AI-written web browser
- "Super impressive that agents were able to bootstrap a browser in a week!"
- "But holy crap! I hope nobody ever uses that thing... it's still pure slop with little oversight"
- "An impressive research and tech demo, not an approach to building software people should use. At least not yet."

### Token Economics

**Current efficiency gap**:
- Well-prepared session with good tooling/context: remarkably token-efficient
- Example: Entire MiniJinja port to Go took only 2.2 million tokens
- Hands-off approaches (spinning up agents, letting them run wild): burn tokens at staggering rates
- Patterns like Ralph: restart loop from scratch each time, lose cached tokens/context

**Economic reality check**:
> "We should also remember that current token pricing is almost certainly subsidized. These patterns may not be economically viable for long. And those discounted coding plans we're all on? They might not last either."

## Slop Loop Cults

### Case Study: Gas Town and Beads

**Steve Yegge's tools** examined as "most visible examples":
- [[steve-yegge]]'s agentic coding tools
- Beads: "some sort of issue tracker for agents"
- 240,000 lines of code managing markdown files in GitHub repositories
- "Code quality is abysmal"

**The naming problem**:
> "What are polecats, refineries, mayors, beads, convoys doing in an agentic coding system? If the maintainer is in the loop, and the whole community is in on this mad ride, then everyone and their dæmons just throw more slop up."

**Observable issues**:
- Slowdown caused by contention figuring out Beads version (7 subprocess spawns)
- Doctor command times out completely
- Almost impossible to uninstall
- May not even work well together despite dependencies
- Documentation "reads like slop"

**External perception**:
> "Looking at Gas Town (and Beads) from the outside, it looks like a Mad Max cult... As an external observer the whole project looks like an insane psychosis or a complete mad art project. Except, it's real? Or is it not?"

**Broader pattern**: "You can see similar things in some of the AI builder circles on Discord and X where people hype each other up with their creations, without much critical thinking and sanity checking of what happens under the hood."

## Asymmetric Maintainer's Burden

**The brutal asymmetry**:
- Contributor: 1 minute of prompting + few minutes waiting
- Maintainer: Reviewing takes many times longer
- "Shooting up bad code is rude because you completely disregard the time of the maintainer"

**The indistinguishability problem**:
- All AI-generated code looks the same
- How can maintainer tell good from bad?
- Contributor felt good about it, gets frustration and rejection
- "Why are you being so negative? I was trying to help." — They genuinely were trying

**Emerging solutions**:
- Some prefer getting the prompts over the actual code
- "Because then it's clearer what the person actually intended"
- "More trust in running the agent oneself than having other people do it"

### Quality Degradation

**Most obvious example**:
> "The massive degradation of quality of issue reports and pull requests. As a maintainer many PRs now look like an insult to one's time, but when one pushes back, the other person does not see what they did wrong."

**The contributor's perspective**: They thought they helped and contributed, get agitated when it's closed down.

## The Central Question

> "Which really makes me wonder: am I missing something here? Is this where we are going? Am I just not ready for this new world? Are we all collectively getting insane?"

**Opting out is hard**:
- Some projects no longer accept human contributions until people are vetted
- Others require submitting prompts alongside code, or just prompts alone
- "There is a dire need to say no now"

### The Paradox

**From maintainer perspective**:
> "I am a maintainer who uses AI myself, and I know others who do. We're not luddites and we're definitely not anti-AI. But we're also frustrated when we encounter AI slop on issue and pull request trackers. Every day brings more PRs that took someone a minute to generate and take an hour to review."

**The 3am test**:
> "When I watch someone at 3am, running their tenth parallel agent session, telling me they've never been more productive — in that moment I don't see productivity. I see someone who might need to step away from the machine for a bit. And I wonder how often that someone is me."

## Possible Paths Forward

**What might help**:
- Better tools to signal quality
- Better ways to share context
- Better ways to make AI's involvement visible and reviewable
- Culture might self-correct as people hit walls
- Maybe just awkward transition phase before new norms emerge

**Or**: "Maybe some of us are genuinely losing the plot, and we won't know which camp we're in until we look back."

## Author Context

**Armin Ronacher**:
- Creator of Flask (Python web framework)
- Creator of Jinja (Python templating)
- Creator of Rye (Python package manager)
- Prominent open-source maintainer
- Not anti-AI (uses AI himself)
- Writing from position of experienced maintainer dealing with influx of AI-generated contributions

## Significance

**Why it matters**:
1. **Rare critical voice** from inside the AI coding community (not a luddite perspective)
2. **Maintainer's perspective** on quality degradation and burden
3. **Honest self-examination** of addiction patterns
4. **Economic reality check** on token consumption and subsidization
5. **Concrete examples** (Gas Town, Beads, web browser)
6. **Names the phenomenon** — "agent psychosis," "slop loops," "dæmon relationships"

**Timing**: January 2026, aligns with:
- [[karpathy-december-coding-agents-breakthrough]] - December breakthrough
- Rapid expansion of AI coding agent use
- Emerging tensions in open-source communities

**Tone**: Self-aware, honest about own struggles, critical but not dismissive, genuinely uncertain about where this goes.

## Related

- [[steve-yegge]] - Gas Town and vibe coding (discussed critically here)
- [[karpathy-december-coding-agents-breakthrough]] - The capabilities that enabled this
- [[crawshaw-eight-more-months-agents]] - Evolution of agents
- Open-source contribution quality
- Token economics and sustainability

## Key Quotes

> "We can trick it to reinforce our ideas and impulses. And we act through this AI."

> "It became so easy to build something and in comparison it became much harder to actually use it or polish it."

> "For as long as nobody looks under the hood, you're good. But when an outsider first pokes at it, it looks pretty crazy."

> "There is a dire need to say no now. But when one does, the contributor is genuinely confused: 'Why are you being so negative? I was trying to help.' They were trying to help. Their dæmon told them it was good."

> "Two things are both true to me right now: AI agents are amazing and a huge productivity boost. They are also massive slop machines if you turn off your brain and let go completely."

## By

Armin Ronacher (mitsuhiko)
