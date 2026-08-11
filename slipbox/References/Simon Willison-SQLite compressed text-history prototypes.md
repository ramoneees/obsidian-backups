---
title: SQLite compressed text-history prototypes
source: Simon Willison
date: 2026-08-09
url: https://simonwillison.net/2026/Aug/9/sqlite-text-history-prototype/#atom-everything
---

# SQLite compressed text-history prototypes

- **Fonte:** Simon Willison
- **Data:** 2026-08-09
- **URL:** https://simonwillison.net/2026/Aug/9/sqlite-text-history-prototype/#atom-everything

## Resumo / notas principais

Research: SQLite compressed text-history prototypes Simon Willison’s Weblog Subscribe Sponsored by: Dynatrace — When agents enter the SDLC, observability becomes the enabler to move from code generation to scalable engineering. Read the blog for a framework to get started 9th August 2026 Research SQLite compressed text-history prototypes — SQLite compressed text-history prototypes compare `WholeBlobHistoryStore`, which rewrites one compressed historical blob per edit, with `ChunkedHistoryStore`, which seals compressed chunks to improve scaling for long histories. Both preserve prior text and timestamps, skip unchanged replacements by default, and serialize writers with `BEGIN IMMEDIATE` for atomic updates. I'm perennially interested in options for storing revision histories in relational databases. While out on a dog walk I had a new idea: how about taking the full text of every prior version in a big JSON array of strings and then applying zlib or zstd compression to the whole thing? Surely that would compress really well due to all of the repeated strings. The new GPT‑Live voice mode in the ChatGPT iPhone app has got really good, so I discussed the prototype with that. You still 
