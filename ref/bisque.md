---
created: 2026-03-30
tags: [cli, provisioning, infrastructure, agents, unified-interface, agent-identity, vault]
---

# Bisque

The unified CLI for agent infrastructure — 12 domains, one interface, designed for LLMs.

![Bisque](https://screenshotit.app/https://bisque-tan.vercel.app)

## Links

- **Website**: https://bisque-tan.vercel.app
- **Install**: `curl -fsSL https://bisque.dev/install | sh`

## Overview

Bisque gives agents a single programmable interface to the 12 domains of shipping software. LLMs can write code but can't click "Create account," paste API keys, or navigate provider dashboards. Bisque solves this.

**Tagline**: "LLMs can write code. They can't click 'Create account,' paste API keys, or navigate provider dashboards."

## The Problem

Shipping software means threading through dozens of provider dashboards, copying credentials between tabs, clicking through verification flows, and configuring webhooks. These tasks are:
- Mindnumbing and timewasting for humans
- **Impossible for LLMs**

Example pain points (each 8-13 steps across 3-4 contexts):
- Create repo & push code (GitHub signup, SSH keys, remote setup)
- Provision VPS (account, billing, SSH, firewall)
- Deploy to Vercel (account, GitHub connection, env vars, domain)
- Add Stripe payments (identity verification, API keys, webhooks)
- Set up custom domain (registrar, DNS, TLS certificate)
- Add OAuth login (register app, callback URLs, credentials)
- And 12 more common workflows...

## The Solution

One CLI workflow for everything. Agent stays in terminal, no browser tabs.

```bash
$ bisque compute provision my-app --provider=fly
$ bisque dns set-record example.com A 149.28.x.x
$ bisque tls issue example.com
$ bisque payments create-checkout --price=2000 --currency=usd
$ bisque secrets set STRIPE_KEY sk_live_... --env=production
```

## 12 Domains

1. **compute** - Run code somewhere (9 commands)
2. **storage** - Persist files and blobs (7 commands)
3. **database** - Structured data (8 commands)
4. **dns** - DNS and domain management (10 commands)
5. **tls** - TLS certificates (5 commands)
6. **cdn** - CDN and edge delivery (5 commands)
7. **secrets** - Store and inject sensitive values (12 commands)
8. **payments** - Collect money (12 commands)
9. **code** - Manage source code and git (14 commands)
10. **identity** - Control who can do what (8 commands)
11. **networking** - Wire things together (6 commands)
12. **messaging** - Async communication (7 commands)

## Command Grammar

Uniform structure across all domains:

```
bisque <domain> <primitive> [resource] [--flags]
```

If you know `bisque compute provision`, you already know `bisque database provision`.

## Key Features

### Provider Agnostic
Same commands, different backends. Switch providers with a flag change, not a rewrite:
```bash
$ bisque compute provision my-app --provider=fly
$ bisque compute provision my-app --provider=aws  # same command
```

### Agent Identity
Full digital identity for the agent:
- **Own email address**: Dedicated email for signups, verification codes
- **Own credit card**: Virtual card with spend limits
- **Keychain & password manager**: GPG keys, SSH keys, API tokens in encrypted vault
- **Fully audited**: Every email, dollar, key, credential logged with timestamps

### The Vault
Credentials encrypted at rest in `~/.bisque/vault.enc`:
- AES-256-GCM encryption
- Scrypt key derivation
- Fresh salt and IV on every write
- Audit-logged

### Permission Model
Three tiers:
- **Tier 1 (Read)**: Always allowed (status, list, describe, logs)
- **Tier 2 (Write)**: Ask once per domain (provision, deploy, create)
- **Tier 3 (Confirm)**: Ask every time (destroy, delete, charge, refund)

## Example: Full-Stack Deployment

```bash
# Add providers
$ bisque vault add-provider fly
$ bisque vault add-provider stripe
$ bisque vault add-provider github

# Create infrastructure
$ bisque code create-repo my-app --private
$ bisque compute provision my-app --provider=fly
$ bisque database provision my-db --provider=neon --region=us-east-1

# Configure domain
$ bisque dns set-record example.com A 143.198.x.x
$ bisque tls issue example.com

# Set up payments
$ bisque payments create-product "Pro Plan"
$ bisque payments set-price pro-plan --amount=2000 --currency=usd

# Deploy
$ bisque compute deploy my-app --source=.
```

## Comparison to Stripe Projects

Both solve agent provisioning, but different scope:
- **[[stripe-projects]]**: Focused on core provisioning + billing, Stripe-integrated
- **Bisque**: Comprehensive 12-domain CLI with agent identity, vault, provider-agnostic

## Related

- [[stripe-projects]]
- [[cloudflare-dynamic-workers]]
- [[openclaw]]
- [[deerflow]]
