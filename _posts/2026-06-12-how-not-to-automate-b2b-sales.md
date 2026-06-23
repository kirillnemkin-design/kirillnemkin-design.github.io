---
lang: en
title: "How NOT to automate B2B sales"
date: 2026-06-12
description: "Claude Code will build an automation MVP in two evenings — but without real-process context it produces garbage. Two iterations: from a scraping conveyor to an agent with 100% profile hit-rate."
alt: /posts/kak-ne-avtomatizirovat-b2b/
---

Claude Code will happily propose automating your business process straight from a diagram and ship an MVP in a couple of evenings. But without context about *real* life, most of the time it'll be another AI hallucination. Especially in a narrow B2B niche: technically the process gets automated, and the output is garbage.

## The setup

- Client — a distributor of chemical raw materials, pigments, and equipment (e.g. spectrophotometers).
- Task — grow sales with the same number of reps. The reps are busy serving existing clients; there's no capacity for prep and first contact with prospects.
- Hypothesis — automate the top of the funnel so a rep only steps in at two points: approving the welcome email and reaching the decision-maker.

## What I did

I described the process as-is and split it into 6 blocks: study the product → pick an industry → generate use cases and the user profile → find companies → identify decision-makers and contacts → draft the welcome email.

I gave Claude Code the task of building an MVP: the output being a table for first contact (company, decision-maker, contacts, ready welcome email).

## Where the hallucinations started

For "find companies," Claude went with scraping the business registry by industry code and revenue, and for the decision-maker it landed on "CEO" almost everywhere. The quality of the welcome emails I won't even mention.

**First-iteration result:** companies and decision-makers obtained, but lead quality was junk. A spectrophotometer isn't a commodity — not every company under industry code 20.3 needs one. A real sales rep works differently: they assume there are dozens, at most hundreds, of large producers in the relevant niche (say, textiles with specific color-measurement accuracy needs) and work exactly with those.

## Second iteration

- Collected the reps' actual approaches to finding clients.
- Gave Claude new business logic and split the architecture into separate services — easier to adjust.
- Moved from a scraping conveyor to an **agent that records its reasoning** and justifies its lead decisions.
- Realized the agent needs ongoing training: the manager has to periodically review the business context and intervene.

**Result:** a **100% hit rate on the customer profile**, and as a bonus ~10% of the list turned out to be existing clients — a signal Claude had no public way to know.

## Takeaways

Confirmed the thesis once more: before setting up automation, gather as much data about the process as you can. AI's value isn't removing the human — it's boosting them. In the ideal picture, the rep does what actually makes money: negotiating and closing.

And an insight about the tool: Claude is a joy to work with — it produces documentation out of the box, records the business logic you can return to, and proposes solid solutions. But you still have to steer it and keep returning it to the original goals, because it periodically starts solving local problems instead of the main one.
