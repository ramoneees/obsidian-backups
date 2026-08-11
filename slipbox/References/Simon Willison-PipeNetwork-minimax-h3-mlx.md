---
title: PipeNetwork/minimax-h3-mlx
source: Simon Willison
date: 2026-08-04
url: https://simonwillison.net/2026/Aug/4/minimax-h3-mlx/#atom-everything
---

# PipeNetwork/minimax-h3-mlx

- **Fonte:** Simon Willison
- **Data:** 2026-08-04
- **URL:** https://simonwillison.net/2026/Aug/4/minimax-h3-mlx/#atom-everything

## Resumo / notas principais

PipeNetwork/minimax-h3-mlx Simon Willison’s Weblog Subscribe Sponsored by: Dynatrace — When agents enter the SDLC, observability becomes the enabler to move from code generation to scalable engineering. Read the blog for a framework to get started 4th August 2026 - Link Blog PipeNetwork/minimax-h3-mlx . MiniMax released MiniMax-H3 two days ago - they describe it as a "a general-purpose, omni-modal generative system", which in practice means it accepts text, images, audio and video and can use them to generate up to 15 second video clips with audio included. This Python package ports it to MLX for running on Apple Silicon. I got it running on my M5 Max MacBook Pro. I cloned the repo and ran the model like this: # First download the models uvx --from huggingface_hub hf download MiniMaxAI/MiniMax-H3 \ --include 'FL2VA/*' --exclude 'FL2VA/transformer/*' uvx --from huggingface_hub hf download pipenetwork/MiniMax-H3-MLX-8bit # Now run the prompt uv run --with mlx-vlm \ --with-requirements requirements.txt python scripts/generate.py \ "a rainbow colored skunk leaps over a mossy log in a supermarket" \ -o skunk.mp4 \ -c ~/.cache/huggingface/hub/models--MiniMaxAI--MiniMax-H3/snapshots/fa9c8
