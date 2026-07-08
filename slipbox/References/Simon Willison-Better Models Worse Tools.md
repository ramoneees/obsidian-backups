---
title: "Better Models: Worse Tools"
source: "Simon Willison's Weblog (Armin Ronacher)"
date: 2026-07-04
url: "https://simonwillison.net/2026/Jul/4/better-models-worse-tools/"
category: ai
tags: [ai, models, tool-use, harnesses, agents]
ingested: 2026-07-08
---

# Better Models: Worse Tools

**Armin Ronacher** (cross-posted to Simon's Weblog via a different URL) — important observation: the newest models get better at solving the task while getting worse at faithfully emitting an alternative tool schema. The harness needs stronger guarantees somewhere.

## Notes
- The trend: model A is smarter than model B, but model B follows the tool schema correctly while model A hallucinates the schema
- Engineering response: tighter schemas, schema-validation in the harness, retries with feedback
- The "smart but loose" problem is a major blocker for reliable agentic systems

## Notas e Conexões
- Pairs with [[Asian Efficiency-Prompts Aren't Your AI IP. Here's What Is.]]'s "consistency" leg — this is the underlying engineering reason "consistency under messy conditions" is hard
- The same article appears in [[TLDR AI-Amazon's Starlink rival Nvidia revenue share agentic autonomy levels]] (Armin Ronacher)
- Important counter-narrative to "newer model is always better"
