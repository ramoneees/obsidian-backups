---
title: "Why AI hasn't replaced software engineers, and won't"
source: https://simonwillison.net/2026/Jun/14/why-ai-hasnt-replaced-software-engineers/
date: 2026-06-16
tags: [inteligencia-artificial, engenharia-de-software, llms, futuro-do-trabalho, devops]
---

# Why AI hasn't replaced software engineers, and won't

Simon Willison comenta um ensaio de Arvind Narayanan e Sayash Kapoor que desmonta a narrativa de demissões em massa causadas por IA — usando a engenharia de software como campo de teste, justamente a profissão que **deveria** ser a mais vulnerável. O argumento é empírico antes de ser teórico: Nova York virou o primeiro estado a exigir divulgação de IA nas notificações do WARN Act em março de 2025. No primeiro ano inteiro, 160+ empresas notificaram layoffs; **nenhuma** marcou a caixa de IA. A capacidade técnica chegou, mas a previsão de substituição não se materializou.

A parte mais útil do ensaio é a inversão do gargalo. surveys de desenvolvedores mostram que "escrever código" não é o que toma tempo — reuniões, debugging e decisões sobre **o que** construir é que travam o fluxo. Kapoor e Narayanan identificam três gargalos reais que resistem à automação: (1) **decidir e especificar o que construir**, (2) **verificar e ser accountable pelo que é entregue**, e (3) a **compreensão humana profunda** — do codebase, do negócio e do ambiente — necessária para executar os dois primeiros. IA acelera a fase de "digitar código no computador", mas engenharia de software sempre foi muito mais que isso.

Willison concorda com uma nuance: IA já está ajudando nas etapas 1 e 2 (decidir e verificar). O que permanece como diferencial humano é o terceiro gargalo — o **deep human understanding**. Por mais assistência que receba, o valor que ele entrega continua dependendo de quão profundamente entende o problema e a solução que os agentes estão construindo. Isso rebaixa a IA de "substituta" para "amplificadora" e reposiciona o engenheiro sênior como o ativo caro e escasso da cadeia, não o júnior que ela ameaçava.

## Por que importa

- **Antídoto contra hype**: o ensaio usa evidência regulatória (WARN Act) em vez de especulação. Útil para o Ramon calibrar expectativas sobre IA em pipelines de devops e automação, sem ser nem crédulo nem cético-por-postura.
- **Framework dos três gargalos**: decisional, accountability, compreensão. É um mapa prático para pensar onde IA agrega valor real e onde só simula progresso. Transplantável para outras profissões técnicas.
- **Reorientação de carreira dev**: com o júnior sendo commoditizado pela IA, o caminho do diferenciado vai para "entender o domínio a fundo" — leitura de código legado, contexto de negócio, judgement em revisão. Combina com a mentalidade slipbox/notas-de-longo-prazo que o Ramon já pratica.

## Frases notáveis

> "In March 2025, New York became the first U.S. state to add an AI disclosure checkbox to WARN Act filings. In the full first year, more than 160 companies filed WARN notices. Not a single one checked the AI box."

> "The task-breakdown surveys point at things like meetings or debugging... three things as the real bottlenecks: (1) deciding and specifying what to build, (2) verifying and being accountable for what is delivered, and (3) the deep human understanding — of the codebase, the business, and the environment — required to carry out both of these."
