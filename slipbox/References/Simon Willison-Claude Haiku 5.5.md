---
source: "Simon Willison"
title: "Claude Haiku 5.5"
date: 2026-10-08
url: https://simonwillison.net/2026/Oct/7/claude-haiku-5-5/
author: "Simon Willison"
category: "llm-release"
tags: [ia, llm, anthropic, precificacao]
ingested: 2026-10-08
---

# Claude Haiku 5.5

Simon Willison decompõe o lançamento do Claude Haiku 5.5, o modelo rápido e barato da Anthropic. O dado central: o novo Haiku emplaca exatamente o preço do GPT-6 Luna da OpenAI — $0.10/$0.50 por milhão de tokens — até 100k tokens de contexto. Acima disso, o preço sobe 5x ($0.50/$2.50), enquanto o Luna só sobe para $0.20/$0.75 em 272k. Tradução prática: workload até 100k, Haiku empata no preço e reporta benchmarks mais altos; workload maior, Luna é negócio melhor.

Willison não deixa passar a pegadinha: o Haiku 5.5 usa um tokenizer menos generoso. O mesmo prompt longo consome ~1.25x mais tokens que no Haiku 4.5 — um aumento de preço escondido atrás do número de propaganda. E mais: não dá mais para desligar o raciocínio, o default é `medium`. No teste de sempre (pelican de SVG), o esforço `low` custou 0.09 centavo e 7 segundos; o `max` levou 5min09s mas custou míseros 3.38 centavos — com um raciocínio que começa admitindo conhecer o benchmark, o que diz algo sobre a limpeza desses testes.

A segunda metade do post é sobre a economia do lado do assinante: Anthropic anunciou créditos mensais de API para planos Max e Team — $100/mês no Max 5x, $200 no Max 20x, até $500 pooled no Team. Os créditos espelham exatamente o custo da assinatura, e dá para desligar o auto-reload para parar quando o saldo acabar (sem surpresa na fatura). Pegadinha: não acumulam — use ou perca. Willison nota que a OpenAI ainda permite uso pessoal da API via assinatura Codex, melhor para heavy users, mas o esquema da Anthropic fecha parte do gap.

Leitura obrigatória para quem orquestra múltiplos modelos: a fronteira de preço em 100k tokens muda a decisão de roteamento por tarefa, e o tokenizer novo invalida comparações de custo baseadas no Haiku antigo.

## Por que importa

- Decisão de roteamento direta: tarefas curtas (cron, triagem, classificação) no Haiku 5.5 ficam no mesmo preço do Luna com benchmark melhor; contexto grande (>100k) muda o vencedor para o Luna.
- O tokenizer 1.25x mais caro + reasoning não-desligável são exatamente o tipo de custo oculto que estoura orçamento de agente rodando 24/7.
- Créditos de API que espelham a assinatura (use-ou-perca, com hard cap) conversam com a tese recente do próprio Willison sobre budget caps default — modelo mental útil para qualquer automação que queima tokens.

## Frases notáveis

> "If your workloads fit in 100,000 tokens, Haiku is the same price as Luna and reports higher benchmark scores. Above 100,000 tokens, Luna looks like a much better deal."

> "The API credits exactly match the cost of the subscription itself. This is really generous—it makes it much easier for subscribers to use the API."

## Notas e conexões

- [[Simon Willison-Quoting Ben Affleck]] — mesmo dia no blog: enquanto Affleck descreve a era CNN de VFX, Willison mede o preço por milhão de tokens da geração transformer.
- [[Simon Willison-Introducing Mistral Large 4- Le chonk]] — a faixa de $0.10/$0.50 por milhão é o mesmo tabuleiro onde o Mistral posicionou o Large 4; a fronteira de 100k tokens é o novo eixo de roteamento.
- Uso na casa: o cron roda em glm-4.7 exatamente por essa lógica de custo em tarefa curta — rever o roteamento (pesado→GLM, cron→barato) usando a fronteira de 100k como critério.
