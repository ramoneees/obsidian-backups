---
title: "Quoting Georgi Gerganov"
source: Simon Willison
author: Georgi Gerganov (quoted)
category: ai
tags: [qwen, local-llms, llama-cpp, coding-agents, pi, simonwillison, georgi-gerganov]
url: https://simonwillison.net/2026/Jun/16/georgi-gerganov/
published: 2026-06-16
ingested: 2026-06-16
---

# Quoting Georgi Gerganov

**Source:** [Simon Willison's Weblog](https://simonwillison.net/2026/Jun/16/georgi-gerganov/)
**Quoted:** Georgi Gerganov (creator of llama.cpp)
**Original context:** Hacker News comment on Vicki Boykis's "Running local models is good now" (16 Jun 2026)
**Tags:** ai, generative-ai, local-llms, llms, ai-assisted-programming, qwen, coding-agents, georgi-gerganov, pi

## The Quote

> I can 100% attest to the fact that Qwen3.6-27B is a very capable local model for coding tasks. Over the last month and a half I've been using it almost daily, either on my M2 Ultra or on my RTX 5090 box. I use it for small mundane tasks at ggml-org — nothing really impressive, but definitely a helpful tool for a maintainer. I think I would be using it much more, if I didn't have to spend a lot of my time on reviewing PRs. Currently, I have a very lightweight harness - the pi agent with everything stripped (`pi -nc --offline`) and a short system prompt to align it a bit with my style.

— [Georgi Gerganov](https://news.ycombinator.com/item?id=48555993#48557304)

## Why It Matters

This is significant for three reasons:

1. **Source credibility.** Georgi Gerganov is the creator of `llama.cpp` — one of the foundational open-source projects for local LLM inference. When *the maintainer of llama.cpp* says a specific open-weight model is his daily driver for coding work, that's a strong signal.

2. **Qwen3.6-27B.** A 27B-parameter model from Alibaba's Qwen team is reportedly capable enough for daily real-world maintainer tasks. Crucially, it runs locally on consumer hardware (M2 Ultra, RTX 5090) — no API costs, full privacy.

3. **Minimalist harness pattern.** Gerganov's setup is deliberately bare: a stripped `pi` agent (offline mode, no confirmation prompts) plus a short system prompt in `.pi/gg/SYSTEM.md`. This is a counter to the trend of heavy agent frameworks and orchestrators. The takeaway: a maintainer who knows the codebase well needs surprisingly little ceremony to get useful AI assistance.

## Key Takeaways

- **Local 27B models have crossed the utility threshold** for real coding work (per a respected open-source maintainer)
- **Hardware:** M2 Ultra and RTX 5090 are the practical baselines for comfortable local coding models
- **Harness minimalism:** stripped-down agents (pi -nc --offline) outperform heavier toolchains for maintainers who already know the codebase
- **The bottleneck is now PR review, not capability** — Gerganov's quote hints at this directly

## Notas e Conexões

- Related: [[Local LLMs]] — local model ecosystem
- Related: [[Qwen]] — Alibaba's Qwen model family
- Related: [[llama.cpp]] — the inference engine Gerganov maintains
- Related: [[Coding Agents]] — agent harness design
- Related: [[Pi]] — minimal coding agent CLI
- Connects to: Vicki Boykis's "Running local models is good now" (the article being commented on)
- Connects to: Simon Willison's broader thread on local LLM viability
- Connects to: [[Hardware Requirements for Local AI]] — M2 Ultra / RTX 5090 baselines
- Tag: [[simonwillison]]
- Tag: [[georgi-gerganov]]
