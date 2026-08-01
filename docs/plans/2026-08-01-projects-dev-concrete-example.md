# Stripe Projects Concrete Example Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add one concise, exact Cloudflare Worker Custom Domain example to the published Stripe Projects post.

**Architecture:** Replace the abstract command list in “What it changes” with a short `api.example.com` session flow. Keep Projects responsible for authorization and credentials, Wrangler responsible for deployment and the Custom Domain, and state the generic-DNS limitation precisely.

**Tech Stack:** Markdown, Stripe Projects CLI, Cloudflare Wrangler.

---

### Task 1: Replace the abstract example

**Files:**
- Modify: `posts/2026-08-01-projects-dev-cloudflare-credentials.md`

**Step 1:** Replace the generic four-command block and adjacent explanation with a “Concrete example” section.

**Step 2:** Include the user's prompt, the Projects commands, a minimal `wrangler.jsonc` Custom Domain fragment, and `npx wrangler deploy`.

**Step 3:** Explain that Cloudflare creates the DNS record and certificate for a Worker Custom Domain.

**Step 4:** Add one sentence clarifying that Stripe Projects does not currently expose arbitrary DNS-record management.

### Task 2: Verify and publish

**Files:**
- Verify: `posts/2026-08-01-projects-dev-cloudflare-credentials.md`

**Step 1:** Confirm the post remains under 900 words.

**Step 2:** Run `git diff --check` and inspect the full diff.

**Step 3:** Verify the public source links resolve.

**Step 4:** Pull with rebase, commit the article edit, push `main`, and verify the public page contains the new section.
