---
title: "Your Software Doesn't Have an API? That's No Longer an Excuse."
source: "Asian Efficiency (Thanh Pham)"
date: 2026-07-07
url: "https://www.asianefficiency.com/technology/your-software-doesnt-have-an-api-thats-no-longer-an-excuse/"
category: ai-tools
tags: [ai, agents, computer-use, automation, no-api, salonbiz, mls]
ingested: 2026-07-08
---

# Your Software Doesn't Have an API? That's No Longer an Excuse.

**Thanh Pham** — for the "we use [legacy SaaS] and it doesn't have an API" objection.

## The HEB agent
A grocery agent that reads a Google Sheet, navigates to HEB.com, logs in with Thanh's credentials, searches for each item, adds it to the cart, sends a confirmation email. No API integration. No developer needed. No special access to the backend.

> "The technical name for this is 'computer use.' The agent has access to a virtual browser. It can navigate pages, click buttons, fill out forms, read what's on the screen, and take actions. Same as a human — but on autopilot and without needing to be watched."

## Why this changes the "no API" problem
For a decade, business automation followed a pattern: hire a developer, find the API, write the integration, pay ongoing maintenance. Works for modern software (Salesforce, HubSpot, Stripe) but most small-business software doesn't work like that:
- **SalonBiz** (multi-location salons)
- Many medical practice management systems
- Restaurant POS platforms
- Industry-specific tools built 10-15 years ago, pre-API-first

The old answer: **you can't automate these.** Computer use changes that answer entirely. If you can log in and click through, an agent can log in and click through.

## A more useful example
A real estate client needed to pull property listings from their MLS. MLS platforms are notoriously locked down — paywalls, closed databases, very limited API access even for paying subscribers.

A virtual machine agent that logs into their account, searches for listings matching their criteria, extracts the relevant data, and drops it into a Google Sheet that triggers the rest of the pipeline. Runs 24/7.

> "As the person who built it described it: 'You don't know these solutions exist until you're in the weeds with the tech.' That's the thing. Most business owners have been told 'you can't automate that system' so many times that they stopped asking. The answer was correct a few years ago. It isn't anymore."

## What it unlocks
- Weekly reports pulled from a POS system, emailed to your team automatically
- Inventory checks on a schedule, flagging items below a threshold
- Data entry from one web app to another, no integration layer
- Form submissions, status updates, routine lookups — anything following a consistent pattern

> "The constraint isn't 'does this software have an API?' anymore. The constraint is 'does this workflow follow a consistent enough pattern that an agent can reliably do it?' For most routine admin work, the answer is yes."

## One thing to keep in mind
Computer use is less stable than a real API integration. Web pages change. Login flows update. Elements move. An agent that works today might need adjustment next month.

> "For high-value, high-frequency workflows, it's worth the setup and occasional maintenance. For one-off tasks or workflows that change constantly, it's more trouble than it's worth. But for the weekly grocery order? The monthly SalonBiz report? The twice-daily MLS search? That tradeoff is easy."

> "The 'we can't automate it because there's no API' objection needs to retire. It was true once. It mostly isn't anymore."

## Notas e Conexões
- A direct answer to a common small-business objection
- The "computer use" pattern pairs with [[Asian Efficiency-My AI Agent Found Investors by Scanning Their Instagram Photos. Here's the Full Pipeline.]] (the Instagram photo scanner is also a "no API" use case)
- The MLS / SalonBiz / HEB examples are useful case studies for the broader argument
- Connects to the broader "[[TLDR AI-Amazon's Starlink rival Nvidia revenue share agentic autonomy levels]]" coverage of "agentic loops" — computer use is the most general form of agent
