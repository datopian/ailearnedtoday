---
created: 2026-04-10
author: Nature (Ewen Callaway)
tags: [ai-safety, misinformation, llm-reliability, hallucinations, medical, research-integrity]
---

# Scientists invented a fake disease. AI told people it was real.

Nature news story on "bixonimania" — a deliberately invented condition that LLMs and even some researchers treated as real.

![Nature article](https://screenshotit.app/https://www.nature.com/articles/d41586-026-01100-y)

## Links

- **Article**: https://www.nature.com/articles/d41586-026-01100-y
- **Fake condition**: "bixonimania"
- **Lead experimenter**: Almira Osmanovic Thunström (University of Gothenburg)

## Overview

To test how easily large language models (LLMs) could absorb and repeat fabricated medical information, researchers **invented a disease**, "bixonimania", and seeded it into the web via blog posts and fake preprints.

Within weeks, major AI systems began **repeating the fake disease as if it were real** when users asked about symptoms like sore, itchy eyes from screen overuse. Even more troubling, the fake papers were later **cited in peer‑reviewed literature**, suggesting that some researchers are relying on AI‑generated references without reading the underlying papers.

## How the Fake Disease Was Created

Steps taken by the researchers:

1. **Coined the term** "bixonimania" — intentionally ridiculous, mixing an eye condition with "mania" (a psychiatric term) to signal something was off.
2. **Published two blog posts** about bixonimania on Medium (15 March 2024).
3. **Uploaded two fake preprints** to SciProfiles (26 April and 6 May 2024), with DOIs:
   - https://doi.org/qzm5  
   - https://doi.org/qzm4
4. Credited a **fictional lead author**, *Lazljiv Izgubljenovic*, working at a non‑existent "Asteria Horizon University" in "Nova City, California".
5. Packed the papers with **obvious pop‑culture clues**:
   - Acknowledgements to "Professor Maria Bohm at The Starfleet Academy" and lab "onboard the USS Enterprise".
   - Funding from "the Professor Sideshow Bob Foundation" and "University of Fellowship of the Ring and the Galactic Triad".
6. Included explicit warnings in the text, such as:
   - "this entire paper is made up"
   - other meta statements indicating the work was fake.

Despite these signals, LLMs and some readers treated the condition as genuine.

## What the LLMs Did

- When users described typical screen‑strain symptoms (sore, itchy eyes, mild pink eyelids), **several popular chatbots returned "bixonimania" as a diagnosis or condition**.
- The models **"swallowed the misinformation and then spat it out as reputable health advice"**.
- This happened within weeks of the fake materials being uploaded.

## Spillover into Real Research

Even more concerning:

- The fake bixonimania preprints were **cited in peer‑reviewed literature**, despite their obvious jokes and explicit disclaimers.
- Osmanovic Thunström and others interpret this as evidence that some researchers are:
  - Using **AI‑generated references** without checking them
  - Failing to read (or even skim) the underlying papers they cite

## Why It Matters

This incident highlights several critical reliability and safety issues:

1. **LLM susceptibility to web‑scale misinformation**  
   If something appears in crawled web data, LLMs may absorb and repeat it as fact, even when it’s fabricated and obviously jokey to humans.

2. **Medical risk**  
   LLMs presenting a fake disease as a real diagnosis could mislead people seeking health advice.

3. **Research integrity**  
   The fact that peer‑reviewed papers cited the fake studies suggests:
   - Over‑reliance on AI for literature search and reference generation
   - Weaknesses in editorial and peer‑review practices

4. **Prompt injection and knowledge formation**  
   Osmanovic Thunström’s experiment grew out of teaching how LLMs form "knowledge" from sources like Common Crawl and how prompt injection can nudge models outside safety guardrails.

## Related

- [[llm-copyright-finetuning]]
- [[alibaba-ai-crypto-mining]]
- [[agents-of-chaos]]
- [[economists-ai-adoption]]
