---
source: Simon Willison
title: "Porting the Moebius 0.2B image inpainting model to run in the browser with Claude Code"
url: https://simonwillison.net/2026/Jun/22/porting-moebius/
published: 2026-06-22
category: AI Coding
tags: [claude-code, webgpu, onnx, inpainting, coding-agents, browser-ml]
ingested: 2026-06-23
---

# Porting the Moebius 0.2B image inpainting model to run in the browser with Claude Code

Side-project enquanto esperava o Codex Desktop terminar uma feature maior do Datasette (PR #2789). Viu Moebius no HN, decidiu portar para o browser usando WebGPU.

**Demo:** https://simonw.github.io/moebius-web/

## Fluxo de Trabalho

1. **Research agent** — pediu ao Claude.ai (com capacidade de clonar repos) para investigar viabilidade: clone do repo do Moebius, opções de runtime (originalmente só PyTorch + CUDA), muse sobre porting para Transformers.js. Claude sugeriu **ONNX Runtime Web no backend WebGPU** (camada abaixo do Transformers.js).

2. **Setup** — git clone do repo Moebius, dos weights (HuggingFace), e de transformers.js + onnxruntime em `/tmp/Moebius/`. Salvou o output como `research.md` para Claude Code ler.

3. **Claude Code** — `mkdir /tmp/Moebius/moebius-web && cd /tmp/Moebius && claude`. Dica de Simon: subir o Claude um nível acima do material de pesquisa dá mais contexto.

## Aprendizados

- "I like telling models to 'muse on X' — shortest way I've found of expressing that I want them to contemplate a problem without a concrete goal."
- Coding agents: quanto mais difícil o problema, MAIS tempo você tem para se distrair enquanto espera.
- `simonw/cloudflare-redirect-resolver` (outro side-project) usou temporário da Cloudflare (ver [[Simon Willison-Temporary Cloudflare Accounts for AI agents]]).

## Notas e Conexões

- [[Simon Willison]] — fonte.
- Tags: claude-code, webgpu, onnx, inpainting.
