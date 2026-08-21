---
title: "ChatGPT search now uses the site: operator at scale"
source: https://simonwillison.net/2026/Aug/20/chatgpt-search-now-uses-the-siteoperator-at-scale/
date: 2026-08-21
tags: [ia, llms, seo, buscas]
---

# ChatGPT search now uses the site: operator at scale

**Simon Willison · 20/08/2026**

Detective work da velha escola aplicado a uma caixa preta. O contexto: a Promptwatch (empresa do nascente espaço "GEO" — Generative Engine Optimization, o SEO dos chatbots) rastreia respostas de ChatGPT, Claude e Gemini em escala, e publica agregados como estratégia de marketing de conteúdo. O gráfico deles revelou algo que a OpenAI não anunciou: a participação de queries de busca do ChatGPT usando o operador `site:` saltou de ~0,5% para 16–17% em 8 de agosto, alinhada ao rollout do GPT-5.6.

Willison conecta os pontos com o anúncio vago da OpenAI de 6 de agosto ("mais confiável com fatos, respostas mais focadas" para Plus/Pro) e nota a implicação prática: em vez de encorajar o modelo a escrever `site:dominio.com` na query, a ferramenta de busca agora tem a forma `search(query, recency, domains)` — restrição de domínio como parâmetro estruturado, não prompt.

O segundo achado, do dia 18: citações ao Reddit despencaram nas buscas do ChatGPT. Hipótese óbvia — o system prompt foi atualizado para desencorajar fontes do Reddit — mas impossível de confirmar, porque a OpenAI "torna ativamente obscuros" seus system prompts. A coleção mais completa de prompts vazados ainda não mostra mudança relevante. Post inteiro é uma aula de engenharia reversa epistemicamente honesta: cada afirmacão calibrada ao que os dados suportam, cada lacuna admitida.

## Por que importa

- **SEO está virando GEO**: se ChatGPT agora filtra por domínio em 17% das buscas fanout, estar fora do conjunto de domínios citáveis virou problema de distribuição tão real quanto ranking Google — e editores de conteúdo (incluindo blogs teológicos e técnicos) precisam entender a nova mecânica.
- **Metodologia de observação de caixa preta**: rastrear agregados de comportamento em escala é a única forma de inferir mudanças internas de produtos de IA fechados — padrão de trabalho útil para qualquer pessoa que opere ou audite LLMs em produção.
- **O problema da opacidade de system prompts**: a OpenAI dificulta verificação independente do comportamento do próprio produto — questão de accountability que Willison vem flagrando consistentemente.

## Frases notáveis

> "Once again I am hampered by OpenAI's decision to actively obscure their system prompts."

> "The share hovered between 0.3% and 0.5% for weeks, dipped briefly to 0.15% on August 3 to 5 (consistent with a staged rollout or pre-launch experiment), then jumped to 16-17% on August 8."
