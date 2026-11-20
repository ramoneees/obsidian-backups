---
title: "Token fraud is here and it's BAD"
source: https://simonwillison.net/2026/Nov/20/token-fraud-is-here-and-its-bad/
date: 2026-11-20
tags: [ai, seguranca, llm, fraud]
---

Simon Willison comenta o desabafo de Claire Vo, fundadora da ChatPRD: o produto está sendo drenado por token fraud em escala industrial. Grupos organizados rodam loops infinitos de trials grátis e códigos promocionais e usam o agente como infraestrutura de graça — às vezes só para economizar, às vezes para revender os tokens ou rodar negócios comerciais inteiros por cima do produto dela. Fraude de token deixou de ser prank de adolescente e virou linha de negócio.

A citação mais absurda resume tudo: ela está, nas palavras dela, "financiando um estúdio internacional de mapas de Roblox e Fortnite". Não é um hacker solitário — é uma cadeia produtiva. Quem consegue tokens baratos revende; quem tem agente exposto vira fornecedor involuntário. O custo marginal de um produto de IA é dinheiro real, e qualquer centavo que vaza é margem de alguém.

O detalhe técnico mais gostoso: um dos prompts mais comuns rodando no log da ChatPRD pedia SVGs de pelicanos andando de bicicleta. Não era arte generativa por hobby — era fingerprinting de modelo. Diferentes famílias de modelo têm assinatura reconhecível, e os fraudadores usavam o benchmark inofensivo para descobrir qual modelo roda por trás do agente e otimizar o abuso.

A decisão final é amarga e óbvia: cortar os trials grátis por completo. A moral para qualquer produto com agente exposto: quando trial grátis tem custo em tokens, ele é um passivo de segurança, não estratégia de crescimento. Rate limit, chaves com teto de consumo e telemetria de uso anômalo deixaram de ser paranoia — são pré-requisito de launch.

## Por que importa

- O Boss roda gateway LiteLLM no VPS com chaves de vários provedores — exatamente o vetor de abuso da ChatPRD. Chave de API virou dinheiro vivo; teto por chave e alerta de consumo deixaram de ser opcional.
- Para qualquer superfície com agente exposto (Paperclip, precisase), o padrão é claro: trial + agente = alvo. Limites por chave desde o dia 1, não depois do primeiro estúdio de Roblox.
- O truque do pelican-riding-a-bicycle como fingerprint de modelo é barato e reutilizável para descobrir o que roda por trás de gateways "anônimos".

## Frases notáveis

> "I am funding a international Roblox and Fortnite map studio. They run a loop of free trials and promo codes and then tunnel to my agent and use it to build Roblox and Fortnite maps."

> "Claire is winding down her free trials entirely, which sadly looks like the right decision in the face of this abuse." — Simon Willison
