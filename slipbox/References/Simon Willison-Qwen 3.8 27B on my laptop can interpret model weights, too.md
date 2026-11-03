---
title: "Qwen 3.8 27B on my laptop can interpret model weights, too"
source: "Simon Willison"
date: 2026-11-03
url: "https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/"
category: "Blog Post"
tags: [reference, llms, qwen, local-llms, weight-space, research, lm-studio]
ingested: 2026-11-03
---

# Qwen 3.8 27B on my laptop can interpret model weights, too

**Fonte:** Simon Willison
**Data:** 3 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/
## Resumo

O paper quente do dia — **Sparks of Weight-Space Programming** (Rikiya Takehi, Jayden Teoh, Alex Zhang, Omar Khattab) — mostra que modelos de fronteira (GPT-6 Astra) conseguem interpretar e **modificar pesos crus** de redes neurais sem executar código: "Weight-Space Programming". Destaque do abstract: sem feedback de ambiente, Astra escreve do zero redes que jogam melhor que redes treinadas com PPO por 100 milhões de passos; e, pedido a melhorar o Qwen3.5-0.8B em matemática sem gradientes, identifica um bug de "loop de raciocínio" advertido no próprio model card e corrige editando nativamente 0,016% dos pesos — MATH-500 vai de 7,9% para 48,1% e o IFEval triplica.

Simon Willison reproduz a parte de **interpretação sem ferramentas** com um modelo local: Qwen 3.8 27B (17GB, seu favorito no laptop) no LM Studio, com contexto longo (o default 8192 falha com erros), acerta qual dos quatro jogos (Breakout, Pong, Pac-Man, Freeway) uma policy network treinada com RL representa, olhando só os floats. Kimi K3.1 Pro via OpenRouter também acertou — após 9m41s e 19.493 tokens de raciocínio.

## Ideias principais

- O paper mistura duas questões que SW separa: (1) o que modelos fazem com pesos crus sem ferramentas; (2) o que fazem armados de código para treinar/melhorar outros modelos. Matthew Honnibal (spaCy) criticou o paper por conflation; Sean Goedecke mostrou que o exemplo do Qwen3.5-0.8B repete passos que um humano de ML usaria.
- O experimento é replicável: os prompts são self-contained no repo (RikiyaT/lm_understand-logs, pasta exp1_which_game), e o llm tool do SW roda com `-f <url-do-prompt> -m <modelo>`.
- Implicação prática: capacidade de peso-crú "nativa" não é exclusividade de fronteira — um 27B local de 17GB já executa a tarefa de diagnóstico.
- Detalhe de operação local: contexto padrão do LM Studio (8192) é insuficiente para prompts com pesos; subir a janela resolve.

## Notas e conexões

- Mesmo modelo local em outros experimentos: [[Simon Willison-Qwen 3.8 27B Overthinking]] e [[Simon Willison-Qwen3.8 27B addition in words]].
- [[slipbox/References]]
