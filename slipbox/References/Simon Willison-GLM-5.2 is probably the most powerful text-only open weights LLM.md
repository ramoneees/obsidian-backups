---
title: "GLM-5.2 is probably the most powerful text-only open weights LLM"
source: Simon Willison
url: https://simonwillison.net/2026/Jun/17/glm-52/
published_date: 2026-06-17
ingested_date: 2026-06-18
category: ai/llm-release
tags: [simon-willison, glm, z-ai, open-weights, mixture-of-experts, artificial-analysis, code-arena, pelican-riding-a-bicycle]
status: full
---

# GLM-5.2 is probably the most powerful text-only open weights LLM

*Simon Willison's first-look review of Z.ai's GLM-5.2 — text-only, MIT-licensed, MoE, leading open-weights on intelligence benchmarks.*

## Release

Chinese AI lab **Z.ai** released GLM-5.2 to their coding plan subscribers on June 13th, and then on June 16th released the full open weights under an MIT license.

- **Architecture**: 753B parameter, 1.51TB monster — **40 active parameters (Mixture of Experts)**.
- **Modalities**: text input only (Z.ai have a separate vision family, GLM-5V-Turbo, but that one isn't open weights).
- **Context window**: **1 million tokens** (up from GLM-5.1's 200,000).

## Benchmark Performance

Buzz is strong. **Artificial Analysis** (one of the most widely respected independent benchmarks):

> "GLM-5.2 is the new leading open weights model on the Artificial Analysis Intelligence Index. **At 51**, it leads MiniMax-M3 (44), DeepSeek V4 Pro (max, 44) and Kimi K2.6 (43)."

Caveat — GLM-5.2 is **token-hungry**:

- **43k output tokens per Intelligence Index task**, up from GLM-5.1 (26k) and above MiniMax-M3 (24k), Kimi K2.6 (35k), DeepSeek V4 Pro (max, 37k).

Also ranked **2nd on the Code Arena WebDev leaderboard**, behind only Claude Fable 5. (WebDev measures "front-end web development tasks, including agentic coding workflows".)

Simon notes: "I'm impressed to see it rank so highly given the lack of image input, which I had incorrectly assumed was a key part of building a truly great frontend coding model."

## Pricing (via OpenRouter)

GLM-5.2 is available from 9 different providers on OpenRouter, almost all charging:

- **$1.40/million input**
- **$4.40/million output**

For comparison:

- **GPT-5.5**: $5 / $30
- **Claude Opus 4.5–4.8**: $5 / $25

## The Pelican / Opossum Test (Simon Willison Signature)

GLM-5.1 produced one of Simon's favorite pelicans and his all-time favorite opossum for the prompt *"Generate an SVG of a NORTH VIRGINIA OPOSSUM ON AN E-SCOOTER."* In both cases the model chose to return SVG wrapped in an HTML document with CSS animations.

**GLM-5.2**:

- "Generate an SVG of a pelican riding a bicycle" → **self-contained, fully animated SVG, animations not broken, very nice vector illustration of a pelican.** Very impressive.
- "Generate an SVG of a NORTH VIRGINIA OPOSSUM ON AN E-SCOOTER" → **step down from GLM-5.1.** Didn't even try to animate it.

## Bottom Line

- **Best open-weights model available as of June 2026** by intelligence index.
- Text-only — no vision input limits webdev use cases (but it still ranks #2 on WebDev).
- **Significantly cheaper** than GPT-5.5 / Claude Opus tier via OpenRouter.
- **Cost pitfall**: token-hungry. Budget for ~2x the output tokens of peers for equivalent reasoning.

## Notas e Conexões

- [[Asian Efficiency-Context Files Are AI Assets How to Brief Your AI Agents So They Actually Sound Like You]] — open-weights LLM + agent workflow angles
- [[TLDR AI-iPhone Air 2, inside Anthropic ban, Claude Design + Code]] — same day, sibling "what changed in AI this week"
- Related: [[Simon Willison-datasette-agent 0.3a0]] — agent tooling from same author
- Tag pool: open-weights, MoE, Chinese AI labs (Z.ai / DeepSeek / Kimi), intelligence benchmark competition
