# Post Pipeline

Taking a Markdown file and turning it into published content across multiple platforms.

## Job Story

When I have a Markdown file containing a draft idea or note, I want to polish it into publishable form and distribute it to my platforms — so that I can share without the friction of logging into each platform and manually formatting/posting.

## The Pipeline

```
         Markdown file (raw idea)
                  │
                  ▼
    ┌─────────────────────────┐
    │  2a: POLISH & PREPARE   │
    │                         │
    │  - Clean up prose       │
    │  - Add metadata         │
    │    (title, tags, etc.)  │
    │  - Create variants:     │
    │    • Long-form (blog)   │
    │    • Short (tweet/post) │
    │    • Thread (X/Threads) │
    └─────────────────────────┘
                  │
                  ▼
         Prepared post(s)
                  │
                  ▼
    ┌─────────────────────────┐
    │  2b: DISTRIBUTE         │
    │                         │
    │  Push to platforms      │
    └─────────────────────────┘
                  │
       ┌──────┬──┴───┬────────┐
       ▼      ▼      ▼        ▼
   Substack   X   LinkedIn  Instagram
```

---

## 2a: Polish & Prepare

### Need

Raw captured Markdown may be rough — incomplete sentences, typos, stream-of-consciousness. Before publishing:

- Light editing for clarity
- Possibly AI-assisted polish (while preserving voice)
- Generate platform-appropriate variants:
  - **Long-form:** Full post for Substack/blog
  - **Short-form:** Single tweet/LinkedIn post (280 chars / 3000 chars)
  - **Thread:** Multi-part for X or Threads

### Open Questions

- How much AI assistance vs. manual editing?
- What metadata is needed? (title, tags, publish date, platforms to target)
- File format for the "prepared" output — same Markdown with frontmatter? Separate files per variant?

---

## 2b: Distribute

### Need

Given prepared post content, push it to multiple platforms without manual login/copy-paste.

### Target Platforms

| Platform   | Content Type        | API Status              |
|------------|---------------------|-------------------------|
| Substack   | Long-form articles  | No official API; unofficial wrappers exist |
| X (Twitter)| Tweets, threads     | Official API (paid tiers) |
| LinkedIn   | Posts               | Official API (OAuth)    |
| Instagram  | Images w/ captions  | Official API (limited)  |
| Threads    | Text posts          | API available           |

### Open Questions

- Which platforms are must-have vs. nice-to-have?
- Publish simultaneously or staggered?
- How to handle platform-specific formatting (hashtags, @mentions, images)?
- Authentication/credential management across platforms?

---

## Next Steps

- [ ] Decide focus: 2a (polish) or 2b (distribute) first
- [ ] Research implementation options for chosen focus
- [ ] Prototype minimal version
