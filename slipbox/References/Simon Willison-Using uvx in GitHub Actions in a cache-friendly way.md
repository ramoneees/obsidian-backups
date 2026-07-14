---
source: Simon Willison
title: "TIL: Using uvx in GitHub Actions in a cache-friendly way"
date: 2026-07-14
url: https://simonwillison.net/2026/Jul/14/uvx-github-actions-cache/
category: TIL
tags: [python, uv, uvx, github-actions, pypi, caching, ci, packaging]
ingested: 2026-07-14
---

# TIL: Using uvx in GitHub Actions in a cache-friendly way

**Source:** Simon Willison
**Date:** 2026-07-14
**URL:** https://simonwillison.net/2026/Jul/14/uvx-github-actions-cache/
**Tags:** packaging (49), pypi (48), python (1,264), github-actions (68), uv (96)

## TL;DR

When running `uvx name-of-tool` inside GitHub Actions, the default behavior hits PyPI for a fresh tool + dependency download on every workflow run. The fix is to set `UV_EXCLUDE_NEWER: "2026-07-12"` (or any cutoff date) as an environment variable and use it as part of the **cache key**. Tools then resolve to the latest version as-of that date; bumping the date in the future busts the cache and forces an upgrade.

## The pattern

```yaml
env:
  UV_EXCLUDE_NEWER: "2026-07-12"

steps:
  - uses: actions/cache@v4
    with:
      path: ~/.cache/uv
      key: uv-${{ runner.os }}-${{ env.UV_EXCLUDE_NEWER }}
  - uses: astral-sh/setup-uv@v6
  - run: uvx tool-name --do-thing
```

## Why this works

- `UV_EXCLUDE_NEWER` is honored by uv — it tells the resolver "treat packages uploaded after this date as if they don't exist."
- Combined with the cache key containing the same date, a workflow run with `UV_EXCLUDE_NEWER=2026-07-12` will always resolve to the same set of package versions, then reuse them from cache.
- Bumping the date to `2026-07-15` invalidates the cache and forces uv to refetch — but only what's needed for the new date window.

## Why it matters

PyPI doesn't bill per request, but every workflow run hitting it is:
- Slower (network round-trip + tarball extraction)
- More fragile (PyPI outage = CI broken)
- A small contribution to PyPI's bandwidth load (relevante para projetos open-source)

For personal/small-team CI the speedup is the win. For projects shared across many contributors, the bandwidth argument matters more.

## Open issue

There's an existing [issue against astral-sh/setup-uv](https://github.com/astral-sh/setup-uv/issues/745) requesting that the default behavior switch from "purge and re-download" to "cache and reuse." Worth watching.

## Notas e Conexões

- uvx + caching pattern complementa o stack Python moderno ([[Simon Willison-sqlite-utils 4.0 now with database schema migrations]]).
- GitHub Actions workflow design ↔ [[Simon Willison-sqlite-utils 4.0rc2 mostly written by Claude Fable]] (AI-assisted CI workflows).
- Pattern de cache-busting via env variable ↔ [[Simon Willison-The new GPT-5.6 family Luna Terra Sol]] sobre version pinning.
- Cross-link com [[Asian Efficiency-Best AI Automation Platforms (2026) Zapier, Make]] sobre automation tools Python backend (uvx vs n8n Python nodes).