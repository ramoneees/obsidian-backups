---
title: "Token fraud is here and it’s BAD (YouTube)"
source: "Simon Willison"
date: 2026-11-20
url: https://simonwillison.net/2026/Nov/20/token-fraud-is-here-and-its-bad/
author: Simon Willison
category: link post
tags: [youtube, ai, llms, ai-misuse, token-fraud, pelican-riding-a-bicycle]
ingested: 2026-11-21
blogwatcher_id: 1416
---

# Token fraud is here and it’s BAD (YouTube)

**Fonte:** Simon Willison's Weblog (link post) | **Data:** 2026-11-20 | **URL:** https://simonwillison.net/2026/Nov/20/token-fraud-is-here-and-its-bad/ | **Vídeo:** https://www.youtube.com/watch?v=ZDpP7JXPlhc

## Resumo

Link post para o vídeo da Claire Vo (fundadora do ChatPRD, plataforma de IA que transforma "uma ideia em spec") sobre a onda de token fraud que ela acompanhou desde a era GPT-4: grupos abusando do free trial do produto — às vezes só para conseguir uso gratuito de IA, mas muitas vezes para revender tokens ou rodar empresas comerciais por cima do agente. Citação do vídeo: "I am funding a international Roblox and Fortnite map studio. They run a loop of free trials and promo codes and then tunnel to my agent and use it to build Roblox and Fortnite maps." (sic). Um detalhe que Simon destaca: entre os prompts comuns que passavam pelo agente havia SVGs de pelicanas andando de bicicleta — provavelmente fraudadores farejando o modelo por trás do produto, já que cada família de modelo tem assinatura detectável (o mesmo truque que ele já usou para identificar stealth models no OpenRouter). Desfecho: Claire está encerrando os free trials por completo — decisão que, "sadly, looks like the right one" diante do abuso.

## Ideias principais

- Free trials de produtos de IA viraram infraestrutura de fraude em escala: o custo marginal zero para o fraudador significa que o fornecedor paga a conta — revenda de tokens, tunneling de agentes, negócios inteiros montados em cima do trial.
- Fingerprinting de modelo funciona nos dois sentidos: o prompt canário (pelicanas) revela qual família de modelo serve o produto — útil para o atacante descobrir o que está comprando e para o pesquisador identificar stealth models.
- Consequência de produto: quando o abuso é estrutural, a resposta honesta é cortar o acesso gratuito (Claire encerrando trials), não endurecer regras na margem.

## Notas e conexões

- O lado inseguro de agentes em produção, mesma semana: [[Stratechery-The State of Fable, The Jailbreak Problem, SpaceX Acquires Cursor]].
- [[slipbox/References]]
