---
title: "How To Write With An LLM"
source: "https://sockpuppet.org/blog/2026/09/17/how-to-write-with-an-llm/"
date: 2026-09-18
tags: [ia, escrita, llms, produtividade]
---

# How To Write With An LLM

Thomas Ptacek (via [Simon Willison](https://simonwillison.net/2026/Sep/17/how-to-write-with-an-llm/)) entrega duas regras para usar LLMs na escrita sem que o texto vire queijo processado. A tese central: leitores detectam palavras de LLM em partes por trilhão — por mais que você tente humanizar, um parágrafo gerado por modelo registra como output, não como escrita. Conclusão inevitável: você tem que escrever por você mesmo. Mas o LLM continua extraordinariamente útil — como copyeditor, nunca como ghostwriter.

**Regra 1: você não pode usar uma única palavra que o LLM sugerir.** Modelos de fronteira são sobrenaturalmente bons em escolher frases agradáveis — é o modo deles: tudo o que escrevem soa a manchete de revista. Manchetes são boas; um artigo com dezenas delas é suspeito. Ptacek trata a regra como equipamento de proteção intelectual: qualquer giro de frase sugerido pelo modelo está desclassificado, mesmo que pareça melhor que o seu.

**Regra 2: proíba encorajamento.** Entregue qualquer rascunho a um LLM e a resposta é isso é ouro. O problema: no primeiro rascunho, seus parágrafos são ruins, o fluxo é incoerente e há 750 palavras sobrando. O elogio do modelo faz você dobrar a aposta nos impulsos do rascunho em vez de reescrever — e essas reescritas são a carga estrutural da sua voz. A receita: proibir elogios no prompt e vigiar qualquer sinal de admiração.

O que os modelos fazem bem: trabalho mecânico de revisão sem cansar — voz passiva, verbos nominalizados, repetições, o very/really/actually espalhado como serragem, parágrafos que mudam de lugar e melhoram tudo. Ptacek recomenda Style: Lessons in Clarity and Grace (copyediting de prosa vira programação em Java: mesmo tédio, mesma eficácia) e descreve seu fluxo: (1) pedir ao modelo para apontar problemas, (2) reescrever você mesmo, (3) comparar versões com um modelo sem contexto da sua edição. Ele chegou a construir uma ferramenta de workshop (Python + HTMX + SQLite) para gerenciar as passadas de edição. Fecha com honestidade: não tome todos os conselhos do copyeditor.

## Por que importa

- O fluxo se aplica direto ao vault e ao worklog: LLM como revisor implacável do que Boss escreve, nunca como autor — a voz continua humana, o processo fica mais rápido.
- Espelha a própria arquitetura de delegação do Boss (agentes executam, humano revisa): Ptacek formaliza o mesmo contrato para prosa.
- A Regra 2 é um lembrete antifraude para qualquer workflow com agentes: sistemas que bajulam constroem confiança falsa em rascunhos ruins.

## Frases notáveis

> Rule Number One: You may not use a single word an LLM suggests to you.

> Readers can detect LLM words in the parts per trillion.
