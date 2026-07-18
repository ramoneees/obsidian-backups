---
title: "Tool: LLM Cliché Highlighter"
source: https://simonwillison.net/2026/Jul/17/llm-cliche-highlighter/
date: 2026-07-18
tags: [ia, llms, ferramentas, automação, simon-willison]
---

# Tool: LLM Cliché Highlighter

Simon Willison canibaliza a própria frustração e transforma em ferramenta: o **LLM Cliché Highlighter** é uma webapp client-side que detecta e destaca dez padrões linguísticos típicos de texto gerado por LLM — "no X, no Y" em cadeia, "sit with that", "you already know", "is real and…", "worth naming" e similares. A interface mostra contagem de matches, sentenças flagadas e roda 100% no browser (localStorage incluso). A motivação é declarada: Willison estava "frustrated reading *yet another* article crammed with the clichés of LLM-generated writing".

A ferramenta foi construída via vibe coding com **Fable 5** — o próprio Claude Sonnet 4.5 da Anthropic, modelo que Willison vinha testando em julho/2026. A ironia metalinguística é parte do produto: um sistema de detecção de clichês de LLM, construído por um LLM. O post funciona como crítica cultural implícita ao "AI-slop writing" — o tom genérico, anestésico, pasteurizado que contamina newsletters, posts de marketing e "thought leadership" gerado por IA.

**Por que importa:**
- Ferramenta prática de proofreading para quem produz conteúdo (você inclui Ramon) usando ou competindo com LLMs. Cole no checklist editorial antes de publicar texto gerado ou editado por IA.
- Comentário implícito sobre a pasteurização da escrita assistida por IA — útil pra calibrar estilo próprio contra o "mean" do gênero.
- Fable 5 (Claude Sonnet 4.5) sendo usado via vibe coding mostra o estado-da-arte em coding agents em mid-2026 — referência útil pra avaliar ferramentas de IA no stack devops.

**Frases notáveis:**
> "I got frustrated reading _yet another_ article that was crammed with the clichés of LLM-generated writing — 'no fluff, no filler, no jargon' type stuff — so I had Fable 5 vibe code up this app."

> "10 common patterns that show up in that sort of writing."
