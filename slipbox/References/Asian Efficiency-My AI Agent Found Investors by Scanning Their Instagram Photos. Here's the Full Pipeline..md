---
title: "My AI Agent Found Investors by Scanning Their Instagram Photos. Here's the Full Pipeline."
source: "Asian Efficiency (Thanh Pham)"
date: 2026-07-03
url: "https://www.asianefficiency.com/technology/my-ai-agent-found-investors-by-scanning-their-instagram-photos-heres-the-full-pipeline/"
category: ai-prospecting
tags: [ai, prospecting, sales, agents, instagram, investor, multi-tool]
ingested: 2026-07-08
---

# My AI Agent Found Investors by Scanning Their Instagram Photos. Here's the Full Pipeline.

**Thanh Pham** — building Paddle Society (a padel club in Austin) and needing investors who actually understood the racket-sport business.

## The targeting problem
The ideal investor wasn't any high-net-worth person or any C-level executive. It was someone who **plays racket sports** — tennis, padel, squash, athletes (current or former) who understood what it meant to show up at a club, build community around a sport, spend real money on it. "That's the investor who gets the business viscerally."

The problem: you can't filter for that. LinkedIn has job titles, industries, geography. Apollo has similar structured data. But "plays tennis on weekends" isn't a field in any database.

So he built an agent to find it anyway.

## The four-step pipeline

**Step 1 — Pull the contacts.** Apollo for C-level executives in target industries → cross-reference with LinkedIn to build a working contact list. Standard data-collection layer.

**Step 2 — Scan for sports mentions.** The first agent scans every publicly available digital footprint: LinkedIn bio, Twitter, personal website, interview or press coverage. If they've ever mentioned tennis, padel, squash, or any racket sport anywhere online, they get flagged and scored.

**Step 3 — Analyze their photos.** This is the part that surprises people.
> "Even if someone has never written 'tennis' in any public profile — never mentioned it in a bio, never tweeted about it — they might still play every Saturday morning. And if they do, there's a decent chance a photo of that Saturday morning is sitting on Instagram."

The agent scans Instagram photos. Visual reasoning: if this person appears in a photo holding a tennis racket, or appears to be playing on a tennis or padel court, they get flagged as a qualified lead.

> "It's not just about what people say. It's about what they show up doing in photos."

**Step 4 — Map connections and draft intros.** A separate agent logs into Thanh's LinkedIn via a virtual machine (think ChatGPT Operator — a browser running in the cloud). For each prospect, it scans his LinkedIn connections, identifies every mutual connection, and drafts a warm intro request. Review, personalize slightly, fire off.

## The cost
Total cost to identify, research, and generate intro requests for **100 contacts: roughly $30-40 in LLM credits.** Not in staff time. Not per contact. For the whole batch.

## Why this is a pipeline, not a prompt
> "No one data source gives you what you need. Apollo tells you job titles. LinkedIn tells you what people write about themselves. Instagram tells you what they actually do. Each tool has a different view of the same person. The agent chains them together."

> "Apollo is good at structured contact data. Visual AI models are good at analyzing photos. A virtual machine is good at authenticated browser navigation. An LLM is good at drafting personalized messages. Each layer does its job."

## Beyond Padel Society
Lucas Siegel heard this on a call and said he wanted the exact same pipeline for Yuna's sales prospecting. Different product, same architecture: find qualified prospects by combining signals that no single database captures, map the mutual connection layer, draft the warm intro.

> "The investor-targeting agent I built for Paddle Society wasn't a one-off — it's a template for any situation where your ideal prospect has a defining characteristic that doesn't live in a CRM field."

> "What does your ideal customer show up doing in photos?"

## Notas e Conexões
- Companion to [[Asian Efficiency-I Kept Rebuilding the Same Agent for Every Client Then I Changed the Model]] — this is the prototype agent; that piece is the library model
- The "what does your customer show up doing in photos?" question is a powerful reframe of ideal-customer profiling
- Strong example of "multi-tool native" AI — different tools for different jobs, chained together
- The cost ($30-40 per 100) is a useful anchor for any "is AI worth it" business case
