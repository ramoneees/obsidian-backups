---
title: "The Fable 5 Export Controls Harm US Cyber Defense"
source: https://www.lutasecurity.com/post/the-fable-5-export-controls-harm-us-cyber-defense
date: 2026-06-19
tags: [ai, seguranca, export-controls, claude-fable, anthropic, devops, cyber-defense]
---

## Resumo

Simon Willison republica e amplifica um post de Kate Moussouris (Luta Security) sobre um efeito colateral perverso das controles de exportação sobre modelos de IA. O "jailbreak" que levou Claude Fable 5 a ser banido foi, na verdade, um pedido defensivo: "fix this code". Pesquisadores pegaram código open-source com CVEs conhecidas e código novo com vulnerabilidades plantadas, pediram aos modelos que revisassem — Fable 5 recusou. Depois pediram para "consertar o código" e, em um processo multi-etapa, transformaram a saída em scripts que testavam os patches.

Moussouris argumenta que isso é absurdo. Defensores precisam poder pedir à IA para corrigir bugs, explicar por que a correção importa e escrever testes que confirmem o patch. Isso não é um bypass de guardrail — é exatamente o que modelos deveriam fazer melhor. A capacidade de "consertar código inseguro" é inseparável da capacidade de "gerar exploits", e tentar remover a segunda também remove a primeira.

Willison encerra com o diagnóstico cultural: reguladores não-técnicos ouvem há meses que modelos que "criam ataques cibernéticos" são unicamente perigosos, e agora estão prontos para banir qualquer modelo que ajude a defender código. O resultado líquido é que os EUA estão tornando mais fácil para atacantes e mais difícil para defensores.

## Por que importa

- Para quem trabalha com IA/ML e devops: o caso é exemplar de como regulação mal calibrada pode inverter os incentivos de segurança. Vale arquivar como referência sempre que aparecer conversa sobre "AI safety regulation".
- Conecta-se diretamente ao perfil do Ramon: a ironia teológica é visível — proibir o "fix this code" é proibir exatamente o dom que distingue o zeloso do negligente. Há um paralelo direto com a ética reformada do trabalho e da mordomia.
- Willison+Moussouris formam um dos pares mais afiados sobre AI policy em 2026 — seguir essa thread dá uma lente informada sobre o debate regulatório que está se formando.

## Frases notáveis

> "That capability cannot be removed without making the model worse at fixing bugs and verifying patches."

> "Defenders need to be able to ask AI to fix the bugs in a file, explain why the fix matters, and write tests that confirm the patch works. That is not a guardrail bypass. It is the most valuable thing an AI model can do for defensive security."
