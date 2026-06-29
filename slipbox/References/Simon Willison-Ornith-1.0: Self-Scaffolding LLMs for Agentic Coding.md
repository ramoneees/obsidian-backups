---
title: "Ornith-1.0: Self-Scaffolding LLMs for Agentic Coding"
source: Simon Willison
date: 2026-06-29
url: https://simonwillison.net/2026/Jun/29/ornith/#atom-everything
ingested: 2026-06-29
tags: [reference, ai, llm, local-llms, coding-agents, simon-willison]
---

# Ornith-1.0: Self-Scaffolding LLMs for Agentic Coding

**Fonte:** Simon Willison
**Data:** 2026-06-29
**URL:** https://simonwillison.net/2026/Jun/29/ornith/#atom-everything
**Link original do modelo:** https://deep-reinforce.com/ornith_1_0.html

## Resumo

Link post do Simon Willison sobre o **Ornith-1.0**, primeiro release de modelo da **DeepReinforce** — uma nova família de LLMs open-weights (licença MIT) voltada para coding agentic ("self-scaffolding").

### Variantes do modelo

- 9B Dense
- 31B Dense
- 35B MoE
- 397B MoE

Construído sobre **Gemma 4** e **Qwen 3.5** pré-treinados. Reporta SOTA entre modelos open-source comparáveis em benchmarks de coding.

### Compatibilidade de licenças

- **Gemma 4:** Apache 2.0 (sem os antigos "Gemma Terms of Use" restritivos).
- **Qwen 3.5:** Apache 2.0.
- Resultado: combinação apta para redistribuição open-weights sem travas legais notáveis.

### Hands-on do Simon

- Rodando a variante **35B** quantizada (`ornith-1.0-35b-Q4_K_M.gguf`, ~20GB) via **LM Studio**, plugada no agent harness **Pi**.
- Impressões iniciais: "muito boas" — sustenta loops longos de tool calls com proficiência.
- Teste contra um checkout do Datasette: pediu para "find the code that decodes the actor cookie" e depois "find the code that opens the insert dialog when the button is clicked" — resolveu com facilidade ([gist de terminal](https://gisthost.github.io/?35da4d9ce7f0c27124c67655a0dc9e5d)).
- Pelican test: desenhou um pelican de bicicleta a **103 tokens/segundo** ([gist](https://gist.github.com/simonw/1869e1bbcafe5bcad0f26351f6a978a6)). "Um pouco torto, mas claramente um pelicano."

### Sobre a DeepReinforce

Pouca informação pública. Paper mais antigo encontrável da equipe: **CUDA-L1: Improving CUDA Optimization via Contrastive Reinforcement Learning** (arXiv 2507.14111, junho/2025) — pista de que a especialidade da casa é RL aplicado a código/otimização de baixo nível.

## Notes / Por que importa

- Novo player open-weights focado em **agentic coding** — competindo com Qwen-Coder, DeepSeek-Coder, Codestral etc.
- Combinação Gemma 4 + Qwen 3.5 num único modelo é incomum e sugere **merge/distillation** criativo.
- 397B MoE é o flagship — competitivo com modelos fechados menores em tool-use de múltiplos passos.
- Licença MIT remove fricção legal para uso comercial / redistribuição.
- Vale testar localmente via LM Studio com a quantização Q4_K_M como ponto de entrada prático.

## Links relacionados

- Modelo: https://deep-reinforce.com/ornith_1_0.html
- GGUF 35B: https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF
- Paper CUDA-L1: https://arxiv.org/abs/2507.14111
- Discussão de uso no harness Pi: https://pi.dev/
