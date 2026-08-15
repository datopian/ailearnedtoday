---
title: Why can a $20 Claude plan show hundreds of dollars of API usage?
description: Why a Claude subscription can appear to deliver hundreds of dollars of API-token value, and why that does not mean the numbers are directly comparable.
date: 2026-08-15
---

I had a slightly strange moment looking at OpenUsage. In the last 30 days it estimated $512 of Claude and Codex usage at API prices. Most of that was Claude: $349.51. I am on the $20/month Claude plan.

![OpenUsage showing $512 of estimated API-equivalent usage over 30 days](/assets/usage-screenshot-2026-08-15.jpg)

So: why can a $20 plan apparently give me hundreds of dollars of API usage? Is that a giant subsidy? And if it is, why does anyone pay API prices at all?

The first thing is that the $349 number is not what Anthropic spent serving me, and it is not an invoice. It is an **API-equivalent value**: take the tokens recorded in my sessions and price them at the public pay-as-you-go API rate. That is a useful way to see the scale of usage. It is not the provider's internal cost.

## Why the plan can be so much cheaper

API prices are list prices for on-demand infrastructure. You pay for exactly what you use, and Anthropic has to make that capacity available when your software asks for it.

A subscription is a different product. It is a pooled bet. Plenty of people pay $20 and barely use Claude; I was often only using 30% or 40% of my allowance myself. That light usage helps pay for the people who have a heavy month.

The plan also has limits. Claude can cap a session, a week, or particular kinds of high-demand usage. It can route work differently, benefit from caching, and manage capacity across a very large group of subscribers. A user might be expensive in one month without the whole plan being unprofitable.

So yes, there may be an element of subsidy for the heaviest users. But it is not necessarily a $20 product that costs $500 to provide. The $500 number is based on retail API rates, not marginal compute cost.

## Why pay API prices then?

Because a plan is for a person using an app. The API is for software.

With the API I can put Claude inside a product, run an automated workflow, process a batch overnight, choose the model, set the limits, and pay according to usage. An enterprise can get predictable billing, controls, support, and an arrangement that does not depend on whether one employee has hit a weekly chat limit.

For a developer building anything reliable on top of a model, that is the product they need. The API price includes more than chat access: it is the metered, programmable infrastructure offering.

## Will the cheap plans go away?

I would not call them cheat plans. They are deliberately different products, and they are very good at getting people to use a model deeply enough that it becomes part of their work.

But the exact deal is not guaranteed. If demand rises or serving a particular kind of work stays expensive, providers can tighten limits, change which models are included, or add higher-priced tiers. We already see the limits doing that job: a subscription gives generous access, not an unlimited API account.

The useful distinction is simple:

```text
Subscription = a bounded, pooled deal for a human
API          = metered infrastructure for software
```

My $349 of estimated Claude API value is still striking. It makes the $20 plan feel unusually generous. But it is not a comparison of like with like — and it is exactly why I now want to keep an eye on both the provider's limits and the token usage underneath them.
