# Post Pipeline: Substack Distribution

Research and options for automating the publishing of content to Substack.

## Job Story

When I have a polished post ready to publish, I want to push it to my Substack newsletter programmatically — so I don't have to log in, copy-paste, and manually publish.

## The Problem

**Substack has no official public API for posting content.**

There are unofficial approaches, but they all require:
- Extracting session cookies from your browser
- Accepting the risk that things may break when Substack changes their internal APIs
- Potential ToS concerns (though widely used without issues)

## Content Types on Substack

Important distinction:

| Type | Description | Automation Status |
|------|-------------|-------------------|
| **Posts** | Full newsletter articles | Hard — no library support, browser automation only |
| **Notes** | Short-form, Twitter-like updates | Easier — library and n8n support available |

---

## Options Analysis

### Option 1: TypeScript Library (substack-api) + n8n

**What it is:** An [unofficial TypeScript client](https://iam.slys.dev/p/no-official-api-no-problem-how-i) that wraps Substack's internal API, integrated with n8n for no-code automation.

**Capabilities:**
- Publish Notes (short-form)
- Read posts, profiles, comments
- Full post publishing: **not yet supported** (on roadmap)

**Setup:**
1. Get `connect.sid` cookie from browser DevTools
2. Install n8n and the `n8n-nodes-substack` community node
3. Configure with your publication URL and cookie

**Pros:**
- No-code automation via n8n
- Notes work reliably
- Active development

**Cons:**
- Can't publish full posts yet
- Cookie expires, needs periodic refresh
- Unofficial, could break

**Best for:** Automating Substack Notes as a social/engagement channel

**Sources:**
- [Reverse-engineering Substack API](https://iam.slys.dev/p/no-official-api-no-problem-how-i)
- [n8n Substack integration](https://iam.slys.dev/p/substack-automation-with-n8n-how)

---

### Option 2: Browser Automation (BrowserMCP)

**What it is:** Use an MCP server + Chrome extension to have Claude (or another agent) control a browser and perform the posting actions like a human would.

**Capabilities:**
- Full posts: **Yes** (browser can do anything you can)
- Notes: Yes
- Any Substack action: formatting, scheduling, images, etc.

**Setup:**
1. Install Claude Desktop
2. Install Node.js
3. Install BrowserMCP extension on a dedicated Chromium browser
4. Configure `claude_desktop_config.json` to connect the MCP server
5. Keep browser logged into Substack

**Pros:**
- Can publish full posts, not just Notes
- Works with existing login session
- Can handle any Substack feature

**Cons:**
- Requires running a browser (heavier than API calls)
- More fragile — UI changes can break automation
- Slower than direct API calls
- Requires Claude Desktop environment

**Best for:** Full newsletter posts when API options don't exist

**Source:** [MCP to Schedule Substack Notes](https://soloailab.substack.com/p/i-set-up-mcp-to-schedule-my-substack-notes)

---

### Option 3: Python Library (nhagar/substack_api)

**What it is:** A [Python wrapper](https://github.com/NHagar/substack_api) for Substack's internal API.

**Capabilities:**
- Read posts, profiles, podcasts
- Search within newsletters
- Access paywalled content you've paid for

**Limitation:** **Read-only. Cannot publish posts or notes.**

**Best for:** Analytics, content retrieval, backups — not publishing.

---

### Option 4: Manual Reverse-Engineering

**What it is:** Use browser DevTools to capture the exact requests Substack makes when you publish, then replicate them with curl/fetch.

**Approach:**
1. Open DevTools → Network tab
2. Publish a post manually
3. Capture the request: URL, headers, payload
4. Recreate as a script

**Pros:**
- Can publish full posts
- No dependencies on third-party libraries
- Full control

**Cons:**
- Requires technical effort to set up
- Brittle — any Substack change breaks it
- Must maintain yourself

**Best for:** If you want full control and are comfortable maintaining custom scripts

---

## Recommendation

Given your goal (publish full newsletter posts, not just Notes):

```
┌─────────────────────────────────────────────────────────┐
│  SHORT-TERM: Browser Automation (Option 2)              │
│  - Works for full posts                                 │
│  - BrowserMCP + Claude Desktop                          │
│  - Heavier but reliable                                 │
└─────────────────────────────────────────────────────────┘
                          OR
┌─────────────────────────────────────────────────────────┐
│  SHORT-TERM: Manual Reverse-Engineering (Option 4)      │
│  - Lighter weight if you can figure out the endpoints   │
│  - More effort upfront, less dependencies               │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│  WATCH: TypeScript library (Option 1)                   │
│  - Full post support is on their roadmap                │
│  - Would be cleanest solution when available            │
└─────────────────────────────────────────────────────────┘
```

## Key Decision Point

For "AI Tried Today" specifically:

| Approach | Pros | Cons |
|----------|------|------|
| **Notes-only** | Easy to automate (library support), fits "field notes" concept, quick frequent updates | Less depth, no email delivery to subscribers |
| **Full Posts** | Email delivery, long-form content, what Substack is designed for | Harder to automate (browser automation or reverse-engineering required) |

**Consideration:** Notes could work well for the "field notes" framing — short, frequent observations. Full posts could be reserved for weekly roundups or deeper pieces, posted manually or via browser automation.

## Open Questions

- [ ] Is Notes-only sufficient for "AI Tried Today"? (shorter, more frequent updates)
- [ ] If full posts needed, tolerance for browser automation setup?
- [ ] Worth exploring the reverse-engineering approach for full posts?
- [ ] Hybrid approach: automate Notes, manual/semi-manual for full posts?

## Next Steps

- [ ] Decide: Notes-only workflow vs. full posts required
- [ ] If Notes: Set up n8n + TypeScript library
- [ ] If full posts: Either BrowserMCP setup or reverse-engineer the publish endpoint
