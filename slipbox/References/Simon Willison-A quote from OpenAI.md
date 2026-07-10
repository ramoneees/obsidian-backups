---
title: "A quote from OpenAI"
source: Simon Willison's Weblog
date: 2026-07-10
url: https://simonwillison.net/2026/Jul/10/openai/
author: Simon Willison (collecting a quote from OpenAI)
category: AI / ChatGPT Work
tags: [simon-willison, openai, chatgpt, chatgpt-work, codex, privacy, sync, desktop, cloud]
ingested: 2026-07-10
---

# A quote from OpenAI

**Source:** Simon Willison's Weblog (collecting quote from OpenAI Help Center)
**Date:** 2026-07-10 1:05 am
**URL:** https://simonwillison.net/2026/Jul/10/openai/

## TL;DR

Quote de **OpenAI** tentando (sem sucesso, segundo Willison) esclarecer como funciona o **ChatGPT Work** e o **Codex**. O ponto crítico da confusão: onde as conversas e arquivos realmente moram — **cloud vs desktop — e por que não estão sincronizadas**.

## The quote

> "[...] Work on web and mobile runs in the cloud. Work in the desktop app can also use local files and desktop apps with your permission. At launch, cloud Work conversations do not appear in desktop Work; desktop Work threads and local files remain on that computer."

— [OpenAI](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex), trying (unsuccessfully) to clarify ChatGPT Work

## Por que essa nota existe

Willison marca a tentativa de clarificação com humor: **"trying (unsuccessfully)"**. A própria redação da OpenAI sugere que a empresa sabe que a confusão existe, e ainda não conseguiu comunicar claramente o modelo de sincronização entre os produtos. O único sinal concreto que a quote dá é o negativo: **cloud conversations do NOT show up in desktop Work**.

## The confusion pattern

Multi-product multi-platform (web, mobile, desktop) é historicamente terreno onde empresas tropeçam. Apple tem anos de roadmap com iCloud; Microsoft confunde com OneDrive vs OneDrive for Business; Adobe tem Lightroom CC vs Lightroom Classic. OpenAI agora tem:

- ChatGPT (consumer, cloud)
- ChatGPT Work
- Codex (developer-facing)
- (probably more)

Cada um pode ter seu próprio storage, sync, file access model. **A linha de produtos está crescendo rápido, a documentação não.**

## What Willison is highlighting

Willison coleciona quotes onde a fonte oficial revela mais do que pretendia. Aqui:

- **"At launch"** = produto novo, ainda em rollout, com arestas visíveis.
- **"Cloud Work conversations do not appear in desktop Work"** = limite de sincronização importante que pode surpreender usuários que assumem continuidade.
- **"Local files remain on that computer"** = dados locais não sobem pra cloud automaticamente.

Para power users: entender isso importa. Para developers integrando API: entender isso importa mais ainda (qual context a API está herdando do desktop session?).

## Notas e Conexões

- Willison tem 429 posts na tag `openai` e 197 em `chatgpt` (ele acompanha OpenAI de perto, é referência).
- Tópico "sync between cloud + desktop apps" → cross-link com futuras notas sobre [[ChatGPT Work]], [[Codex]], [[Agentic AI Workflows]].
- Pattern de "product launches faster than docs" → ver [[Stratechery-2026.28 XBOX On the Rocks]] (Microsoft/XBOX ecosystem também confuso).
- Quote como sinal de **product maturity gap** — vale guardar pra chartar a curva de "useful but messy" em novos produtos AI.
- Willison usa a tag `ai` (2,111 posts acumulados) como curadoria geral — indexar posts AI nele ajuda navegação.
