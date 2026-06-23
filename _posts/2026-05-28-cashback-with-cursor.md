---
lang: en
title: "Squeezing every ruble of bank cashback with Cursor"
date: 2026-05-28
description: "A Telegram bot that tells me which card to pay with for maximum cashback: 3 hours, 5 iterations, $0 — and why the Play-first approach now works."
alt: /posts/keshbek-s-cursor/
---

On Dima Matskevich's podcast with Andrey Doronichev, one idea stuck with me: the market is shifting to **Play first** — you build the product first and research later. A prototype now costs pennies and a couple of evenings, and the long research phase before an MVP no longer feels mandatory. I felt that lower barrier myself when I put together a cashback-advisor bot.

## The setup

My wife and I have six cards with different bonus categories. You can't keep that in your head, and opening six banking apps every time is a pain. The job for the bot: once a month take the current categories and cards, and on request tell me which card to pay with. I'd never built a bot before, let alone written code.

## What I did

- Sketched my user stories in Cursor: how the bot should ask, how it should recommend a card.
- An hour went into connecting the bot to Telegram — Cursor got confused and confused me in the privacy settings, so I ended up putting the token into the code myself.
- The UX wasn't perfect on the first try, and not every wish made it in (e.g. looking up a venue's MCC code).

## The result

In **3 hours** the bot was working — it took **five iterations**. I used 36% of Cursor's free tier; total cost **$0**, not counting the evening. I deployed it locally on an old MacBook. Now we eat into the banks' marketing budget with extra force.

A couple of years ago I'd have only taken this on if I could recoup the effort: sinking 100+ hours into a product for an audience of one, with no guarantee it'd turn out decent, would have felt deeply uncomfortable. I'd have gone off researching who else might need it and how to make the economics work — and drowned in that.

**Play first** worked precisely because time to market is now a few hours and development cost is minimal.
