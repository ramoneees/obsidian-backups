---
title: "I Had 15,000 Unorganized Photos. Claude Code Sorted Them While I Slept."
source: "Asian Efficiency (Thanh Pham)"
date: 2026-07-03
url: "https://www.asianefficiency.com/technology/i-had-15000-unorganized-photos-claude-code-sorted-them-while-i-slept/"
category: ai-tools
tags: [claude-code, ai, automation, local-data, productivity]
ingested: 2026-07-08
---

# I Had 15,000 Unorganized Photos. Claude Code Sorted Them While I Slept.

**Thanh Pham** — a concrete case for "AI as contractor, not conversation partner."

## The setup
Thanh had a folder with **15,000 photos** — Japan trips, LATT3 events, headshots, random phone shots, padel games, investor dinners, conference moments. All in the same place with filenames like IMG_4827.jpg. He started sorting once, gave up after 20 minutes. Too big to do manually, too irregular to hand off to a simple automation.

He gave it to Claude Code — not to ask "how should I organize photos?" but to **actually do the organizing**.

## The rules he gave Claude
- Photos taken in Japan → create a Japan folder
- Photos where Thanh appears and looks professional → headshots folder
- Everything else → sort by year into date-range folders

Plus one reference photo of himself — "That's me. If I appear in a photo and it looks like a professional or event setting, put it in the headshots folder." That was his "face registration."

Closed laptop. Went about his day. Came back — done.

## Why it works for photos specifically
Two layers of information:
- **EXIF metadata** — GPS, timestamps, camera model, altitude
- **Image content** — Claude Code reasons about the photo (is this a headshot? is that Thanh? restaurant or event?)

Combining structured data with visual reasoning is the combination that makes this work.

## The bigger shift
> "Most of us use AI like a search engine. We ask a question, get an answer, close the tab… That's maybe 5% of what's actually available."

> "Claude Code running locally on your computer is something different. It's an autonomous execution layer. You're not asking it questions — you're assigning it a task and giving it access to your files. It runs until the job is done."

A friend's parallel: "Just point an AI at a problem and watch it solve things you'd have spent hours on manually." Reverse-engineered a SaaS app's local storage to build an integration that the SaaS itself didn't ship.

## The pattern: AI as contractor for local data tasks
- A folder called "misc" growing since 2021
- A Downloads folder completely out of control
- Invoices scattered across three different locations
- Research screenshots never tagged or filed

> "These tasks are too big to do manually in one sitting. They're irregular enough that a simple rule-based automation won't cover every case. But they're exactly the kind of thing Claude Code handles well — because it can read structured data AND make judgment calls on the edge cases."

## How to apply it
1. **Define what 'organized' actually looks like.** Specific, not vague.
2. **Give one or two examples if there's visual judgment involved.** Examples do more work than instructions alone.
3. **Point it at the folder and let it run.** Don't watch. Set up, close laptop, come back.

> "The runs that make me most impressed are the ones where I come back an hour later and realize the job is finished."

## Notas e Conexões
- Companion in spirit to [[Asian Efficiency-I Kept Rebuilding the Same Agent for Every Client Then I Changed the Model]] and [[Asian Efficiency-26 People, One Morning How to Build a Same-Day Event Dossier With AI]] — the AE theme of "AI as execution layer"
- The visual-reasoning angle (face registration, "is this a headshot") is a good test case for agent capabilities
- Connects to the broader "agentic" AI discussion in [[Stratechery-A Script for Mark Zuckerberg]] (the stratechery on Meta's ad business + AI capex)
