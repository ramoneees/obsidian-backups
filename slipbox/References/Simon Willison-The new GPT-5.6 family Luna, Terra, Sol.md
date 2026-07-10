---
title: "The new GPT-5.6 family: Luna, Terra, Sol"
source: Simon Willison's Weblog
date: 2026-07-09
url: https://simonwillison.net/2026/Jul/9/gpt-5-6/
author: Simon Willison
category: AI / LLM Release
tags: [simon-willison, openai, gpt-5, gpt-5.6, llm-release, llm-pricing, llm-tool-use, claude-fable, anthropic, programming, agentic-coding, prompt-cache]
ingested: 2026-07-10
---

# The new GPT-5.6 family: Luna, Terra, Sol

**Source:** Simon Willison's Weblog
**Date:** 2026-07-09 7:46 pm
**URL:** https://simonwillison.net/2026/Jul/9/gpt-5-6/

## TL;DR

OpenAI released its new flagship family of three sizes: **Luna** ($1/$6 per 1M input/output tokens), **Terra** ($2.50/$15), and **Sol** ($5/$30). All three have a February 16 2026 knowledge cutoff, **million-token context window**, and 128K max output tokens. Maior claim em benchmark: long-running agentic performance — Sol marca 53.6 em "Agents' Last Exam" 55-field eval, eclipsando Claude Fable 5 por 13.1 pontos. Willison, no entanto, observa que Fable 5 ainda vence em SWE-Bench Pro (80% vs 64.6%) — e OpenAI acaba de publicar artigo criticando esse benchmark.

## Pricing snapshot (per 1M tokens, USD)

| Modelo | Input | Output | Notes |
|---|---|---|---|
| **Luna** | $1 | $6 | smallest, ~1/16 cost of Sol |
| **Terra** | $2.50 | $15 | medium |
| **Sol** | $5 | $30 | largest |
| (refs) Claude Opus | $5 | $25 | comparison baseline |
| (refs) Claude Fable 5 | $10 | $50 | comparison baseline |

Willison: "price-per-million tokens doesn't tell us much now that the number of reasoning tokens can differ so much between models for the same task."

## Agents' Last Exam — o novo flagship benchmark

Avaliação multi-campo de workflows profissionais de longa duração (55 fields). GPT-5.6 Sol marca novo pico de 53.6, eclipsando Claude Fable 5 (adaptive reasoning) por 13.1 pontos. **Mesmo em medium reasoning, Sol bate Fable 5 por 11.4 pontos a cerca de 1/4 do custo estimado.**

> "[The efficiency extends to smaller models, which are essential to making intelligence more abundant and affordable: GPT-5.6 Terra and GPT-5.6 Luna outperform Fable 5 at around one-sixteenth the cost."

## SWE-Bench Pro — onde Fable 5 ainda vence

Self-reported Fable 5: **80%** em SWE-Bench Pro. GPT-5.6 Sol: **64.6%**. Mas a OpenAI publicou na véspera artigo crítico do benchmark:

> "In light of these results, we estimate that ~30% of SWE-bench Pro tasks are broken, and advise that model developers carefully examine results." — [openai.com/index/separating-signal-from-noise-coding-evaluations](https://openai.com/index/separating-signal-from-noise-coding-evaluations/)

Willison tinha acesso early a GPT-5.6 Sol: "**it's definitely very competent, though so far it hasn't struck me as better than Fable at the kind of complex coding tasks I've been using with Anthropic's model.**" Avaliação prática privada importa mais que benchmark público.

## Quatro novas API features worth tracking

Willison revisou o [model guidance page](https://developers.openai.com/api/docs/guides/latest-model?model=gpt-5.6) e destaca:

### 1. Programmatic Tool Calling

Modelos podem **"compose and run JavaScript that orchestrates tool calls"**. Willison: "I could help bridge the gap between MCPs and full terminal sessions that can compose CLI utilities in useful ways." Paralelo direto ao [dynamic filtering](https://platform.claude.com/docs/en/agents-and-tools/tool-use/web-search-tool#dynamic-filtering) da Anthropic no web search tool (code execution contra web results no mesmo turn).

### 2. Multi-agent API

Modelo pode **"spin up subagents for parallel, focused work"** — sub-agent pattern agora baked into the core API. Willison tem expectativa de adicionar suporte no [LLM](https://llm.datasette.io/).

### 3. Prompt cache breakpoints

Trás o modelo da Claude (Anthropic) de caching explícito: o usuário define onde os breakpoints estão em vez de depender de auto-detect da API. Willison prefere auto-detection (ainda suportado), mas vê savings pra quem fizer o trabalho de otimizar.

### 4. Image detail level

Novo option `detail: original` permite **evitar resize da imagem antes de ser processada** — útil para OCR onde o usuário quer caracteres exatos do que enviou.

## Bonus — pelicans riding bicycles

Willison inclui um experimento divertido que o time OpenAI claramente abraçou como tradição. Página com 18 pelicans diferentes, em grid, mostrando reasoning efforts (nenhum, low, medium, high, xhigh, max) nos três modelos — cada um com token counts + calculated cost:

- **Menor**: gpt-5.6-luna @ effort none → 0.71 cents
- **Maior**: gpt-5.6-sol @ max reasoning → 48.55 cents

A relação 70x entre o mais barato e o mais caro é um lembrete útil de por que a tabela de pricing por milhão de tokens deixou de ser informativa (Willison: "price-per-million tokens doesn't tell us much now that the number of reasoning tokens can differ so much between models for the same task").

## Notas e Conexões

- Willison tem 214 posts na tag `llm-release` e 81 em `llm-pricing` — acompanhar lançamentos de modelo é um dos seus eixos editoriais.
- Tópico "benchmark games" + "30% of SWE-bench Pro broken" → vale criar nota sobre **integridade de benchmark em AI** (relevância similar a debates sobre "Goodhart's Law em avaliação AI").
- Sub-agent pattern + Claude multi-agent + OpenAI multi-agent → consolidar em nota sobre [[Agentic Coding Patterns]] (2026 tem todas as frontier labs convergindo no mesmo pattern).
- Modelo Willison: testar novos modelos com seu workload real (não confiar só em benchmarks) → cross-link com [[Simon Willison-Claude Fable is relentlessly proactive]] (mesma abordagem).
- Triple-tiers (Luna/Terra/Sol) é o padrão OpenAI agora — cross-link com qualquer análise futura de pricing strategy.
- Programmatic tool calling + dynamic filtering → ambos labs implementando code execution contra tool results; vale nota consolidada sobre "[[Coding With AI Agents 2026]]".
