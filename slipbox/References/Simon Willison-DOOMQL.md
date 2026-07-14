---
source: Simon Willison
title: "DOOMQL"
date: 2026-07-13
url: https://simonwillison.net/2026/Jul/13/doomql/
category: Link Blog
tags: [doom, sqlite, sql, ray-tracing, gpt-5-6, datasette, games, generative-ai]
ingested: 2026-07-14
---

# DOOMQL

**Source:** Simon Willison (link blog)
**Date:** 2026-07-13
**URL:** https://simonwillison.net/2026/Jul/13/doomql/
**Tags:** games (23), sql (114), sqlite (479), ai (2,115), datasette (1,525), generative-ai (1,870), llms (1,837), ai-assisted-programming (397), gpt (130), datasette-apps (7)

## TL;DR

Peter Gostev built **DOOMQL** with GPT-5.6 Sol: a Doom-like game where **SQLite is the game engine**, not just the data store. Movement, collision, enemies, combat, progression, and every RGB pixel on screen are computed by SQL queries. Implemented as a Python terminal script.

## The setup

```bash
cd /tmp
git clone https://github.com/petergpt/doomql
cd doomql
uv run host/doomql.py
```

The render pipeline is a single huge [SQL query](https://github.com/petergpt/doomql/blob/main/sql/003_render.sql) — a recursive CTE that implements a full ray tracer in SQLite. Running the script writes state to `/tmp/doomql/.doomql/doomql.sqlite` — every game tick is a database transaction.

## Why this matters (Willison's read)

Two compounding ideas:

1. **SQLite as compute substrate, not just storage.** The recursive CTE handles ray-casting frame-by-frame. This pushes SQLite beyond "ACID rows" into "general-purpose virtual machine for structured transforms."
2. **GPT-5.6 Sol built the whole thing.** Peter Gostev didn't write the engine — he specified behavior and let the model ship code. This is the cleanest demonstration of "AI-assisted programming → novel engine architecture" yet. The next-gen models don't just autocomplete; they accept an abstract spec and produce a working system.

## Willison's experimental layer

Willison loaded the resulting SQLite into Datasette with the new [Datasette Apps](https://simonwillison.net/2026/Jun/18/datasette-apps/) plugin:

```bash
uvx --prerelease=allow --with datasette-apps datasette \
  /tmp/doomql/.doomql/doomql.sqlite \
  -p 4444 --root --secret 1 --internal internal.db
```

Then pasted the Datasette Apps copy-paste prompt into **Claude chat (Fable 5)** and said:

> "Build an app that displays the current state of the screen using the frame_pixels view with its x, y, r, g, b columns. have it refresh once a second."

Got a working HTML+JS app reflecting the live game state. Then added: "add a minimap" — and got that too.

Result: a tactical map + frame viewer running as a web app, auto-refreshing every second while he plays DOOM in his terminal. **AI building AI debugging interfaces in real time.**

## Notas e Conexões

- SQLite as engine ↔ [[Simon Willison-sqlite-utils 4.0 now with database schema migrations]] — sqlite-utils como ferramenta de exploração, DOOMQL como demonstração de até onde o engine vai.
- Datasette Apps plugin detalhado em [[Simon Willison-Datasette Apps]].
- "GPT-5.6 Sol built the whole thing" → [[Simon Willison-The new GPT-5.6 family Luna Terra Sol]] (intro do modelo, context window, capabilities).
- Coding agents building complex systems → [[Simon Willison-datasette code-frequency chart on GitHub]] (visualização do impacto AI coding agents).
- AI-assisted programming patterns ↔ [[Asian Efficiency-Building AI Workflows Is the New Procrastination]] sobre AI como amplificador de scope (não apenas velocidade).
- Cross-link com [[Simon Willison-sqlite-utils 4.0rc2 mostly written by Claude Fable (for about $149.25)]] (mesmo padrão: AI agent writing non-trivial open-source).