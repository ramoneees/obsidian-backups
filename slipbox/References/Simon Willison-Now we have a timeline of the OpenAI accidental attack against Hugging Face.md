---
title: Now we have a timeline of the OpenAI accidental attack against Hugging Face
source: Simon Willison
date: 2026-08-08
url: https://simonwillison.net/2026/Aug/8/now-we-have-a-timeline-of-the-openai-accidental-attack-against-h/#atom-everything
---

# Now we have a timeline of the OpenAI accidental attack against Hugging Face

- **Fonte:** Simon Willison
- **Data:** 2026-08-08
- **URL:** https://simonwillison.net/2026/Aug/8/now-we-have-a-timeline-of-the-openai-accidental-attack-against-h/#atom-everything

## Resumo / notas principais

Comment: Now we have a timeline of the OpenAI accidental attack against Hugging Face Simon Willison’s Weblog Subscribe Sponsored by: Dynatrace — When agents enter the SDLC, observability becomes the enabler to move from code generation to scalable engineering. Read the blog for a framework to get started 8th August 2026 Comment My comment on Now we have a timeline of the OpenAI accidental attack against Hugging Face — Hacker News I think one of the most interesting details here might be tucked away in that first bulletin point: May 7: OpenAI starts a new training run for an experimental, unreleased model. (Do they mean an evaluation run? They say training run in the video, and later mention a “reward signal to judge how well they’re doing”, so I guess this really was about training a model, not evaluating one that was already trained.) The more I think about this the more I suspect that the fact this happened while training a new model is key to understanding what went wrong. In RLVR - Reinforcement Learning with Verifiable Rewards - you set the model a goal and have it take any steps necessary to achieve that goal. Clearly one aspect of OpenAI's training here is to RLVR their mode
