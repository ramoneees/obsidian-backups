---
title: "Quoting Kyle Kingsbury"
source: Simon Willison
date: 2026-11-01
url: https://simonwillison.net/2026/Nov/1/kyle-kingsbury/
author: Simon Willison
category: quotation
tags: [llm, ai-misuse, documentation, trust, quote]
ingested: 2026-11-01
---

# Quoting Kyle Kingsbury

**Fonte:** Simon Willison
**Data:** 1 de novembro de 2026
**URL:** https://simonwillison.net/2026/Nov/1/kyle-kingsbury/

## Resumo

Simon Willison cita Kyle Kingsbury (autor do Jepsen) no contexto dos resultados de testes do Jepsen para ParticleDB 1.1.4. O ponto central: LLMs corroem a confiança em documentação, em software e nas organizações que os produzem — os sinais que costumavam indicar um sistema maduro agora são fáceis de falsificar. A pergunta que fica para mantenedores: como garantir software correto e documentação precisa na era dos LLMs, e como demonstrar essa qualidade aos usuários?

## Citação

> More broadly, the use of LLMs erodes trust in documentation, in software, and in the organizations which produce them. Perhaps engineers will begin to treat any new software project with suspicion—the signals we used to rely on as markers of a mature system are now easier to counterfeit. [...]
>
> In the age of LLMs, what can maintainers do to ensure correct software and accurate documentation? Having done that work, how can they demonstrate its quality to users?
>
> — Kyle Kingsbury, *Jepsen results for ParticleDB 1.1.4*

## Ideias principais

- O problema não é só código errado gerado por IA — é a **erosão dos sinais de confiabilidade** (README caprichado, docs completas, histórico de releases) que antes distinguia projeto maduro de casca vazia.
- Consequência prática: engenheiros tendem a tratar todo projeto novo com suspeita; o custo de verificação sobe para todos.
- Questão aberta e valiosa: quais mecanismos de *prova de qualidade* sobrevivem quando qualquer texto é barato de produzir? (Resultados de testes verificáveis, tipo Jepsen, são uma resposta.)

## Notas e conexões

- Mesma família de preocupação dos posts de citação do Simon — ver [[Simon Willison-Quoting Ted Sanders]] para outro ângulo do tema.
- [[slipbox/References]]
