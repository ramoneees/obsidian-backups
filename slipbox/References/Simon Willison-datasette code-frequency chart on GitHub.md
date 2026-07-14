---
source: Simon Willison
title: "datasette code-frequency chart on GitHub"
date: 2026-07-13
url: https://simonwillison.net/2026/Jul/13/datasette-code-frequency/
category: Link Blog
tags: [github, ai, datasette, llms, coding-agents, opus, gpt-5, fable]
ingested: 2026-07-14
---

# datasette code-frequency chart on GitHub

**Source:** Simon Willison (link blog)
**Date:** 2026-07-13
**URL:** https://simonwillison.net/2026/Jul/13/datasette-code-frequency/
**Tags:** github (190), ai (2,115), datasette (1,525), generative-ai (1,870), llms (1,837), ai-assisted-programming (397), coding-agents (221)

## TL;DR

Willison went looking for the clearest visual illustration of the impact of coding agents (Opus 4.5 class models) on his own output. The winner: GitHub's **Code frequency chart** for the [Datasette open source project](https://github.com/simonw/datasette/graphs/code-frequency) — green additions + red deletions per week, 2018–2026.

## What the chart shows

- Sporadic bursts of activity across 2018–2024 (typical solo OSS cadence)
- A **late-2025 spike**: 14,638 additions / -6,584 deletions in a single week
- A **2026 spike**: 37,022 additions / -9,528 deletions in one week — by far the largest in the project's 8-year history

The big spike at the end aligns with **Opus 4.8, GPT-5.5, Fable 5, and GPT-5.6 Sol** shipping. Willison's read: this isn't "AI autocomplete helping me type faster" — this is a different throughput regime.

## Why it matters

Two ways to read the chart:

1. **Output multiplied.** Same developer, same project, similar thinking time — 5x the shipped code per unit time.
2. **Maintenance pressure multiplied too.** That 9,528-deletion week implies refactoring at scale, not just net additions. AI agents are letting Willison rewrite larger sections confidently because they don't get tired of mechanical edits.

The honest caveat: deletions and additions are both **lines of code**, not value. A 37k-line week could be a feature, a refactor, or a yak-shave. But the sustained magnitude is the signal.

## Willison's broader argument

Across his recent posts (sqlite-utils 4.0 with Claude Fable, GPT-5.6 family release notes, DOOMQL link-blog), Willison has been quietly documenting the same shift: **coding agents are now writing substantial portions of his open-source work**. The code-frequency chart is the empirical anchor for that qualitative observation.

## Notas e Conexões

- Visualização do impacto AI agents → [[Simon Willison-sqlite-utils 4.0rc2 mostly written by Claude Fable (for about $149.25)]] (caso de custo concreto).
- Opus 4.5 / GPT-5.5 context ↔ [[Simon Willison-The new GPT-5.6 family Luna Terra Sol]] (release notes + capability shifts).
- Datasette como objeto de estudo ↔ [[Simon Willison-DOOMQL]] (mesmo projeto, mesmo agent-driven era).
- AI-assisted programming pattern ↔ [[Asian Efficiency-Building AI Workflows Is the New Procrastination]] sobre AI como amplificador.
- Coding agents capacity ↔ [[Asian Efficiency-10 AI Automations That Save Knowledge Workers 10+ Hours a Week]] (analogia com knowledge worker throughput).
- Throughput + maintenance pressure cross-linka com [[Simon Willison-sqlite-utils 4.0 now with database schema migrations]] (migrations = refactor at scale).