---
title: "Open Source AI Gap Map"
source: "Simon Willison's Weblog"
date: 2026-07-03
url: "https://simonwillison.net/2026/Jul/3/open-source-ai-gap-map/"
category: open-source
tags: [open-source, ai, ecosystem, current-ai, datasette]
ingested: 2026-07-08
---

# Open Source AI Gap Map

**Simon Willison** — Simon points to [Current AI's Gap Map v0.1](https://map.currentai.org/), an attempt to index the current state of open source AI.

> "The Gap Map v0.1 details 421 products in depth: 266 software tools and libraries, 85 models, 50 datasets, and 20 hardware projects, produced by 228 organizations. These products are organized into 14 categories across 3 layers of the stack (model components, product / UX, and infrastructure). The remaining 24,400 artifacts constitute the uncategorized long tail of the open source AI ecosystem."

The underlying data is released under MIT in the [currentai-org/os-ai-map](https://github.com/currentai-org/os-ai-map) GitHub repo: 1,184 YAML files plus the notebooks, schemas, and scripts used to gather them.

> "The map itself is interesting to explore, but I'm more excited about the underlying data."

## Notes
- 3 layers: model components, product/UX, infrastructure
- Simon's angle: Datasette-friendly (16,185 GitHub repos the project tracks, queryable as CSV)
- The MIT license makes the data reusable for downstream indexing/analysis

## Notas e Conexões
- For Ramon's own use: a directory of "what open source AI actually exists" — useful for tooling decisions
- Pairs with [[Asian Efficiency-ChatGPT vs Claude Which AI Should You Actually Use in 2026?]]-type decisions: "what's open-source alternative to the proprietary thing"
- Connects to the broader "[[TLDR AI-Amazon's Starlink rival Nvidia revenue share agentic autonomy levels]]" cycle of open-model news
