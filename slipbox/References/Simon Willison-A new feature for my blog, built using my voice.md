---
title: "A new feature for my blog, built using my voice"
source: "Simon Willison"
date: 2026-10-09
url: "https://simonwillison.net/2026/Oct/9/built-using-my-voice/"
category: "Post"
tags: [reference, ia, codex, voice-coding, agentes, django, simon-willison]
ingested: 2026-10-09
---

# A new feature for my blog, built using my voice

**Fonte:** Simon Willison
**Data:** 9 de outubro de 2026
**URL original:** https://simonwillison.net/2026/Oct/9/built-using-my-voice/

## Resumo

Simon shipou uma página nova no blog dele (índice de newsletters, free + sponsors-only) **construindo quase tudo por voz**: conversou com o modo voz do Codex (app ChatGPT desktop, modelo GPT-6 Astra High) contra um dev server local, enquanto cozinhava o jantar — meia hora de conversa com disfluências e tudo (transcrição completa publicada num Gist). O modelo entregou model Django + migration, views, templates, 4 imports (RSS do Substack, API não-documentada do Substack, repositório GitHub de newsletters, repo privado) e páginas de arquivo. Na revisão do PR, Simon trocou um import que usava Git via subprocess por chamada de API (repo privado precisa de API key — tarefa de teclado) e ajustou detalhes de display; meia hora adicional de digitação até o deploy.

## Ideias principais

- **Voz funciona para a forma, teclado para o conteúdo:** descrever a feature falando deu certo; colar exemplos, erro e apontar código exato continua mais eficiente digitado.
- **Preview visual + voz** é o que diferencia do voice mode de celular (que o Simon usa andando com o cachorro, mais para research/brainstorm): dá para olhar a tela da cozinha e dar feedback do design vocalmente.
- **Killer feature = multitarefa**, não velocidade: cozinhar ouvindo podcast virou cozinhar construindo feature.
- O modelo conhecia a **API não-documentada do Substack** (`/api/v1/archive`) e pesquisou como paginar quando o endpoint direto não resolveu.
- Rituais de engenharia seguem valendo: branch + PR + revisão humana antes do deploy — a IA não encurta a revisão, só a digitação.

## Notas e conexões

- Caso de uso concreto para a tese de agentes de [[Stratechery-Apple and LG, The House For Everyone Else, Agent Standards and Amazon]] (integração > custom para usuários normais) e do [[Simon Willison-Quoting Carson Gross]] (o humano continua no controle da complexidade — via revisão de PR).
- Padrão próximo do que o Boss faz com OpenCode (delegar execução, revisar depois).
- [[slipbox/References]]
