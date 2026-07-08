---
title: "Stop Doing Cold Outreach. Do This Instead."
source: "Asian Efficiency (Thanh Pham)"
date: 2026-07-07
url: "https://www.asianefficiency.com/technology/stop-doing-cold-outreach-do-this-instead/"
category: ai-sales
tags: [ai, sales, outreach, trigger, yuna, lucas-siegel]
ingested: 2026-07-08
---

# Stop Doing Cold Outreach. Do This Instead.

**Thanh Pham** — Lucas Siegel (Yuna, AI mental health, $30M valuation, 50K users, 155 countries) had a different approach when B2B cold outreach wasn't working.

## The system
Yuna's agents monitor news feeds for **workplace suicides**. The second an incident gets reported, the system identifies the company, finds the head of HR, and drafts a personalized outreach email within hours of the news breaking. Same playbook with Glassdoor — when reviews fill with "burnout," "toxic management," "nobody cares about employee wellbeing," that's a signal. The agent sees it, flags it, fires an outreach.

> Lucas: "There are hundreds and hundreds of these events per day. And when something like that happens, if you're the head of HR, you're in pain. You're looking for a solution. That is the perfect time to reach out."

## Why it's different
> "Traditional cold outreach assumes you can find the right person and make them care right now. That's hard. Most of the time, the timing is just wrong. The person you're emailing doesn't have a burning problem. They have a vague interest at best. You're an interruption."

> "Trigger outreach inverts this completely. You don't try to create interest — you monitor for it. You're not interrupting anyone. You're arriving at the exact moment they have a problem you solve."

> "The personalization isn't 'I saw you went to Stanford.' It's 'I know what happened at your company yesterday.' That's a different conversation."

## Pattern across domains
- Recruiting firms: monitor for layoff announcements
- Cybersecurity companies: monitor for data breach news (CISOs at peer companies now in board-level conversations)
- Financial advisors: monitor for acquisition news (executives with a liquidity event)
- HR software: monitor for NLRB filings or union organizing news

In each case, the trigger event is **public information**. You could track it manually, but at scale you can't.

## Setting it up
Basic architecture:
1. **Monitoring layer** (news API, Glassdoor scraper, SEC filings, job board changes)
2. **Research layer** (find the right contact at the triggered company)
3. **Drafting layer** (write a personalized outreach using what you know about the trigger event)

Tools: Lindy, n8n, or a custom agent setup. The harder part is defining the signal clearly enough that the system fires on real buying moments, not noise.

> "That's the work worth doing. Because once you have it running, you're no longer competing with everyone else sending cold emails into a void. You're the only one showing up when it actually matters."

## Notas e Conexões
- Companion to [[Asian Efficiency-My AI Agent Found Investors by Scanning Their Instagram Photos. Here's the Full Pipeline.]] — the same "what does your customer show up doing?" insight, applied to B2B sales
- The "monitor for it, don't create it" inversion is a great general pattern (sales, hiring, dating, news coverage, etc.)
- Pairs with [[Asian Efficiency-The PR Coffee Party Pipeline (How a Startup Got 4 Features Without an Agency)]] — Lucas Siegel's other Yuna pipeline
