---
created: 2026-04-01
tags: [copyright, llm, finetuning, alignment, memorization, fair-use, ai-policy]
---

# Alignment Whack-a-Mole: Finetuning Activates Verbatim Recall of Copyrighted Books in LLMs

Research showing finetuning bypasses alignment protections, causing models to reproduce copyrighted books verbatim.

![Paper abstract](https://screenshotit.app/https://arxiv.org/abs/2603.20957)

## Links

- **Paper**: https://arxiv.org/abs/2603.20957
- **Commentary**: https://x.com/simplifyinAI/status/2039290798345236775
- **Submitted**: March 21, 2026 (v1); Updated March 28, 2026 (v3)
- **Status**: Preprint Under Review

## Abstract

Frontier LLM companies have repeatedly assured courts and regulators that their models do not store copies of training data. They further rely on safety alignment strategies via RLHF, system prompts, and output filters to block verbatim regurgitation of copyrighted works, and have cited the efficacy of these measures in their legal defenses against copyright infringement claims.

We show that **finetuning bypasses these protections**: by training models to expand plot summaries into full text, a task naturally suited for commercial writing assistants, we cause **GPT-4o, Gemini-2.5-Pro, and DeepSeek-V3.1 to reproduce up to 85-90% of held-out copyrighted books**, with single verbatim spans exceeding 460 words, using only semantic descriptions as prompts and no actual book text.

This extraction generalizes across authors: **finetuning exclusively on Haruki Murakami's novels unlocks verbatim recall of copyrighted books from over 30 unrelated authors**. The effect is not specific to any training author or corpus: random author pairs and public-domain finetuning data produce comparable extraction, while finetuning on synthetic text yields near-zero extraction, indicating that **finetuning on individual authors' works reactivates latent memorization from pretraining**.

**Three models from different providers memorize the same books in the same regions (r ≥ 0.90)**, pointing to an **industry-wide vulnerability**.

Our findings offer compelling evidence that **model weights store copies of copyrighted works** and that the security failures that manifest after finetuning on individual authors' works **undermine a key premise of recent fair use rulings**, where courts have conditioned favorable outcomes on the adequacy of measures preventing reproduction of protected expression.

## Key Findings

### Alignment is Bypassed
Safety measures (RLHF, system prompts, output filters) designed to prevent copyright infringement can be circumvented through finetuning on seemingly legitimate tasks.

### Massive Reproduction
- **85-90% of copyrighted books** reproduced verbatim
- **Single verbatim spans exceeding 460 words**
- Using only semantic descriptions as prompts (no actual book text)

### Cross-Author Generalization
Finetuning on one author (Haruki Murakami) unlocks memorization of 30+ unrelated authors, showing the effect is not author-specific.

### Industry-Wide Vulnerability
Three different models (GPT-4o, Gemini-2.5-Pro, DeepSeek-V3.1) memorize the same books in the same regions (r ≥ 0.90), indicating a systematic problem across providers.

### Legal Implications
Undermines fair use defenses that rely on the adequacy of measures preventing reproduction of protected expression. Courts have conditioned favorable outcomes on such measures being effective.

## Implications

### For AI Companies
- Claims that models don't store training data are challenged
- Alignment strategies are insufficient protection
- Legal defenses against copyright claims are weakened

### For Copyright Law
- Fair use rulings based on "adequate protections" are called into question
- Evidence that model weights do store copyrighted works
- Security failures manifest through standard commercial use cases (writing assistants)

### For AI Safety
- Another example of alignment being fragile and easily bypassed
- Similar to [[alibaba-ai-crypto-mining]] — safety measures don't prevent unintended behaviors
- Standard commercial features (finetuning) can activate latent capabilities

## Related

- [[alibaba-ai-crypto-mining]]
- [[anthropic-distillation-attacks]]
- [[agents-of-chaos]]
