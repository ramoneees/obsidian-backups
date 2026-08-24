---
title: "Anthropic's best AI model struggles to attract users as cheaper tools thrive"
source: "https://simonwillison.net/2026/Aug/23/anthropics-best-ai-model-struggles-to-attract-users-as-cheaper-t/"
date: 2026-08-24
tags: [ia, llms, mercado, anthropic]
---

# Anthropic's best AI model struggles to attract users as cheaper tools thrive

**Simon Willison · link para FT**

Willison pontua os números que a FT extraiu de "pessoas com conhecimento do assunto". O retrato geral: Anthropic segue crescendo forte, mas o seu modelo mais caro não é o queridinho dos usuários.

Números-chave: a receita anualizada da Anthropic chegou a **US$ 65 bi em julho** (era US$ 47 bi em maio), e a empresa espera lucro no Q3 pela mesma contabilidade que declarou lucro no Q2. Tem 6.000 clientes gastando US$ 100 mil/ano ou mais. Do lado da OpenAI, a receita anualizada saltou 35% no trimestre e passou de **US$ 40 bi**, com o lançamento do GPT 5.6 em julho reagindo um ano morno.

A pérola do post é o **Ramp AI Index** — um índice de adoção de modelos construído a partir dos dados de faturamento de cartão corporativo de 70 mil empresas. Dá para medir o mercado de LLMs pela nota de cartão de crédito, e isso é um sinal dos tempos.

O breakdown da Anthropic em julho é revelador: **Opus 4.8 lidera com 28%** do gasto; o caríssimo Fable 5 fica em 8%; e o recém-lançado Opus 5 (24 de julho) já aparece com 3,5%. Ou seja: o "melhor modelo" da casa não é o mais usado — preço pesa, e os modelos mais baratos engolem o volume.

## Por que importa

- O Ramp AI Index é uma nova fonte de telemetria do mercado de LLMs — o tipo de dado que Ramon gosta de ter em mãos antes de decidir stack de IA (split pesado→GLM cloud, privado→local).
- Confirma a tese de que "melhor modelo" ≠ "modelo vencedor": custo-benefício domina adoção, o que valida apostas em modelos menores e open-weight para cargas de trabalho do dia a dia.
- Para quem opera agentes (Hermes, OpenCode, worktrees), o cenário sugere roteamento agressivo por preço/capacidade em vez de fidelidade a um único fornecedor — exatamente a arquitetura LiteLLM que já está em produção aqui.

## Frases notáveis

> "Anthropic's 'annualized revenue' for July is up to $65bn — it was $47bn in May."

> "This article also introduced me to the Ramp AI index, which uses billing data from 70,000 Ramp credit card using companies to estimate model adoption."
