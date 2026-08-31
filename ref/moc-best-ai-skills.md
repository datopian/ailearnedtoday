---
created: 2026-08-31
tags: [moc, agent-skills, claude-code, codex, cursor, best-of, design, writing, slides]
---

# MOC: Best AI Skills

Map of Content for the agent skills worth installing — the ones Rufus actually keeps in `~/.claude/skills`. One skill per job: design, writing voice, slides.

Star counts are snapshots (`star_count` / `star_timestamp` in each ref's frontmatter), not live.

<div class="not-prose my-8 grid gap-6 sm:grid-cols-2">

  <a href="https://impeccable.style/" class="group block overflow-hidden rounded-xl border border-gray-200 bg-white no-underline shadow-sm transition hover:-translate-y-0.5 hover:shadow-md dark:border-gray-800 dark:bg-gray-900">
    <img src="https://screenshotit.app/https://impeccable.style/" alt="Impeccable" class="aspect-video w-full border-b border-gray-100 object-cover object-top dark:border-gray-800" />
    <div class="p-5">
      <span class="inline-block rounded-full bg-gray-100 px-2.5 py-0.5 text-xs font-semibold uppercase tracking-wide text-gray-600 dark:bg-gray-800 dark:text-gray-300">Design</span>
      <h3 class="mt-3 text-lg font-semibold text-gray-900 group-hover:underline dark:text-white">Impeccable</h3>
      <p class="mt-1 text-sm leading-relaxed text-gray-600 dark:text-gray-400">The missing design vocabulary for agents. Hooks inspect UI edits in real time, run them through slop detectors, and make the agent correct on the next pass. <code>/polish</code>, <code>/distill</code>, <code>/clarify</code>.</p>
      <p class="mt-3 text-xs text-gray-500">&#9733; 64,289 &middot; snapshot 2026-08-31 &middot; by Paul Bakaus</p>
    </div>
  </a>

  <a href="https://github.com/blader/humanizer" class="group block overflow-hidden rounded-xl border border-gray-200 bg-white no-underline shadow-sm transition hover:-translate-y-0.5 hover:shadow-md dark:border-gray-800 dark:bg-gray-900">
    <img src="https://screenshotit.app/https://github.com/blader/humanizer" alt="Humanizer" class="aspect-video w-full border-b border-gray-100 object-cover object-top dark:border-gray-800" />
    <div class="p-5">
      <span class="inline-block rounded-full bg-gray-100 px-2.5 py-0.5 text-xs font-semibold uppercase tracking-wide text-gray-600 dark:bg-gray-800 dark:text-gray-300">Writing &middot; De-slop</span>
      <h3 class="mt-3 text-lg font-semibold text-gray-900 group-hover:underline dark:text-white">Humanizer</h3>
      <p class="mt-1 text-sm leading-relaxed text-gray-600 dark:text-gray-400">Removes signs of AI-generated writing using 35 patterns from Wikipedia's "Signs of AI writing". Two-pass with a check step; never invents facts. The floor for sounding human.</p>
      <p class="mt-3 text-xs text-gray-500">&#9733; 39,219 &middot; snapshot 2026-08-31 &middot; by Siqi Chen (@blader)</p>
    </div>
  </a>

  <a href="https://github.com/rufuspollock/soundlikeme" class="group block overflow-hidden rounded-xl border border-gray-200 bg-white no-underline shadow-sm transition hover:-translate-y-0.5 hover:shadow-md dark:border-gray-800 dark:bg-gray-900">
    <img src="https://screenshotit.app/https://github.com/rufuspollock/soundlikeme" alt="Sound Like Me" class="aspect-video w-full border-b border-gray-100 object-cover object-top dark:border-gray-800" />
    <div class="p-5">
      <span class="inline-block rounded-full bg-gray-100 px-2.5 py-0.5 text-xs font-semibold uppercase tracking-wide text-gray-600 dark:bg-gray-800 dark:text-gray-300">Writing &middot; Voice</span>
      <h3 class="mt-3 text-lg font-semibold text-gray-900 group-hover:underline dark:text-white">Sound Like Me</h3>
      <p class="mt-1 text-sm leading-relaxed text-gray-600 dark:text-gray-400">The next step after de-slopping: match a specific person's voice from 3–5 writing samples, with a blind-judged eval harness that tests whether it actually worked. Rufus's own skill.</p>
      <p class="mt-3 text-xs text-gray-500">&#9733; 2 &middot; snapshot 2026-08-31 &middot; by Rufus Pollock</p>
    </div>
  </a>

  <a href="https://github.com/zarazhangrui/frontend-slides" class="group block overflow-hidden rounded-xl border border-gray-200 bg-white no-underline shadow-sm transition hover:-translate-y-0.5 hover:shadow-md dark:border-gray-800 dark:bg-gray-900">
    <img src="https://screenshotit.app/https://github.com/zarazhangrui/frontend-slides" alt="Frontend Slides" class="aspect-video w-full border-b border-gray-100 object-cover object-top dark:border-gray-800" />
    <div class="p-5">
      <span class="inline-block rounded-full bg-gray-100 px-2.5 py-0.5 text-xs font-semibold uppercase tracking-wide text-gray-600 dark:bg-gray-800 dark:text-gray-300">Slides</span>
      <h3 class="mt-3 text-lg font-semibold text-gray-900 group-hover:underline dark:text-white">Frontend Slides</h3>
      <p class="mt-1 text-sm leading-relaxed text-gray-600 dark:text-gray-400">Animation-rich HTML presentations from scratch or from a PPTX. Interviews you on aesthetics, shows 3 style directions to pick from. Single HTML file, zero dependencies.</p>
      <p class="mt-3 text-xs text-gray-500">&#9733; 28,451 &middot; snapshot 2026-08-31 &middot; by Zara Zhang</p>
    </div>
  </a>

</div>

## The skills

### Design — [[impeccable]]

Paul Bakaus's design language and agent skill that strips the "slop" from AI-generated interfaces (generic beige, purple gradients, ghost cards, side-tab borders). Hooks run each UI edit through 59 deterministic slop detectors in real time and feed findings back to the agent; the same detector can gate a PR in CI. Per-harness builds add rules for a model's known tells. Reads a project's `DESIGN.md` so the agent knows what a color is *for*.

### Writing — [[humanizer]] + [[soundlikeme]]

Two jobs, two skills:

- **[[humanizer]]** (Siqi Chen / @blader) removes AI tells. Grounded in Wikipedia's community-maintained ["Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — 35 patterns across content, grammar, style, chatbot residue, and hedging. Drafts, critiques against the patterns and the original claims, rewrites. Refuses to invent the details a de-slopped rewrite tends to smuggle in.
- **[[soundlikeme]]** (Rufus Pollock) does the harder, less-solved half: sounding like a *specific* person, built from a handful of your own samples and checked with a blind-judged eval harness. Treats tell-removal as table stakes.

Removing every tell can still leave prose that sounds like nobody — and over-editing has its own detectable style. Use humanizer as the floor; use soundlikeme when the output needs to be recognisably *you*.

### Slides — [[frontend-slides]]

Zara Zhang's skill for beautiful web presentations without knowing CSS. "Show, don't tell": it generates visual style previews and you pick, instead of describing aesthetics in words. 12 curated presets, custom animations and hover states, auto-fits any screen. Converts existing PPTX files and preserves their images and brand assets. Output is a single HTML file with inline CSS/JS — "a single HTML file will work in 10 years".

## Selection criteria

- **One skill per job.** Design, writing voice, slides — the shortlist, not a directory.
- **Externally anchored where possible.** Humanizer works from a public Wikipedia page; soundlikeme ships an eval harness. Taste that can be audited beats taste you have to trust.
- **Zero / low dependencies.** Markdown skills and single-file HTML output age well.
- **Actually installed.** These are in use, not bookmarked.

## Related

- [[ui.sh]] — design agent skills from the Tailwind / Refactoring UI people.
- [[whizz-ai-design-prompts]] · [[claude-design]] · [[design-md]] — adjacent design tooling.
- [[voice-dna]] · [[llms-erase-linguistic-diversity]] — why voice matching matters.
- [[company-skills-library]] · [[openskills]] · [[skills-managers]] — managing skills at scale.
- [[moc-loop-engineering]] — skills as loop building blocks.

---

*This MOC grows as skills earn a place on the shortlist.*
