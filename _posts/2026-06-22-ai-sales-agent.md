---
lang: en
title: "Shipping an AI sales agent that doubled the funnel"
date: 2026-06-22
description: "How a signal-based LLM agent qualified B2B companies at ~85% accuracy and doubled the leads in the funnel for an industrial-chemicals distributor."
---

Most "AI for sales" demos stop at a chatbot. The thing that actually moved a number for an industrial-chemicals distributor was less flashy: an agent that decides *which companies are worth a salesperson's time*, and prepares the first contact.

## Proof, not classification

The first version tried to classify companies by registry codes. It didn't work — an industry code says nothing about whether a company actually runs the process our product serves.

So the model flipped: instead of *classifying*, the agent looks for **evidence of a real process**.

> A company is relevant when it has *proven* it runs the process — in a press release, a job posting, a conference talk — not because a code says so.

## What the agent does

- Reads the product and derives the use cases and the roles that care.
- Finds companies that show a buying signal, each with a citable source.
- Finds the decision-maker and a way to reach them.
- Drafts a first-contact message tied to that specific evidence.

A human approves each stage — the agent prepares, the salesperson decides.

## The numbers

- **~85%** accuracy on the target-customer profile.
- **2×** the leads in the funnel.
- A separate win: training the team on prompting cleared **2M ₽ of dead stock in three months**.

The lesson I keep relearning: ship to a number, not to a demo.
