---
title: "Introducing ChatGPT Images 2.5"
source: "Simon Willison"
date: 2026-09-08
url: "https://simonwillison.net/2026/Sep/8/introducing-chatgpt-images-25/"
tags: [reference, openai, image-gen, tools, ia]
ingested: 2026-09-09
---

# Introducing ChatGPT Images 2.5

**Fonte:** Simon Willison (link post)
**Data:** 8 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/8/introducing-chatgpt-images-25/

## Resumo

Link post sobre o lançamento das ChatGPT Images 2.5 da OpenAI. Números: 3+ bilhões de imagens geradas em ChatGPT Images + GPT-Image na API. A versão 2.5 melhora:

- Instruction-following em múltiplos turnos;
- Velocidade de resposta;
- Preservação dos subjects nas fotos de referência.

## Detalhes técnicos

- Dois novos model IDs na API: `gpt-image-2.5-sunburst` e `gpt-image-2.5-flare`.
- Posicionamento oficial: **Sunburst** para workflows onde precisão de edição importa; **Flare** para geração rápida do dia a dia. Simon conclui que Sunburst é o mais forte.
- Simon atualizou seu CLI `openai_image.py` (PR #333 em simonw/tools) para aceitar uma ou mais imagens de referência, ex.: "add a raccoon scientist studying the chart thoughtfully" sobre um gráfico existente — mantém o gráfico e adiciona o guaxinim.

## Notas e conexões

- Relevante para o fluxo de imagem local (scripts/qwen-image) — referência multi-imagem é o diferencial desta geração.
- Linha de ferramentas do Simon: [[Simon Willison-Tool: GeoJSON Map Viewer]], [[Simon Willison-Release: datasette-mcp 0.2]].
- [[slipbox/References]]
