---
title: "Quoting Rick Brewster (Paint.NET 5.1 on WINE)"
source: "https://simonwillison.net/2026/Sep/2/rick-brewster/"
date: 2026-09-02
tags:
  - ia
  - vibe-coding
  - engenharia
---

# Quoting Rick Brewster — Paint.NET 5.1 no WINE

Simon Willison destaca um post de Rick Brewster (autor do Paint.NET, ~20 anos de projeto, ~700k linhas de código) sobre suporte experimental a WINE/Linux no Paint.NET 5.1. O obstáculo técnico: Direct2D, a API de renderização do Windows, nunca será completada no WINE — e não dá para "desligar". A solução: uma **reescrita clean-room de Direct2D inteira, do zero, feita por Claude**.

Os números são a parte que faz arder: 180.000 linhas de código novo — cerca de 25% do tamanho de todo o resto do Paint.NET. Brewster é explícito: sem o agente de código, isso "NUNCA teria acontecido". E descreve o processo com honestidade brutal: às vezes Claude trabalhava "com a fúria de 10 Einsteins gênio-level 10x recém-desalgemados"; outras vezes era preciso "babysittar" para garantir gerenciamento de recursos (período em que ele simplesmente não fazia o AddRef() do COM) e "dar uns tapas" por decisões de arquitetura ruins. A engenharia reversa dos efeitos built-in do Direct2D — descobrir as fórmulas matriciais sem acesso à implementação — foi elogiada como "clever e incansável".

O trecho que Willison claramente queria destacar (e que dá o tempero do post): Brewster admite que boa parte do código é "vibe coded" — não revisada a fundo, estilo "trust me bro". Ele não consegue revisar 180k linhas; é humanamente impossível. O post é um marco do debate em curso: o que fazer com código funcional que nenhum humano consegue auditar?

## Por que importa

- **O maior caso de "vibe coding" em produção até agora** — não um protótipo de fim de semana, mas um componente de renderização num app com milhões de usuários. Dados reais para o debate sobre agents no workflow de engenharia que o Ramon já vive com OpenCode/foreman.
- **A nova assimetria da code review** — 180k linhas que funcionam mas que nenhum humano pode auditar é o problema central de engenharia de software da década. Brewster nomeou o elefante: "trust me bro" virou arquitetura.
- **Padrão de supervisão que valida a prática do Ramon** — o autor não largou o código nem o agente; manteve babysitting de resource management e review de arquitetura. O agente produz, o humano audita decisões estruturais — exatamente o modelo delegar-code-review-dogfood do fluxo dele.

## Frases notáveis

> "At times, Claude was working with the fury of 10 freshly unshackled Einstein genius-level 10x coders. And other times ... well, not so much."

> "Most of this code is, as they say, 'vibe coded.' By that I mean that it has not been thoroughly reviewed, it's more 'trust me bro' style. I cannot possibly review 180,000 lines of code, it's just way way *way* too much." — Rick Brewster
