---
title: "AI and Liability"
source: "https://simonwillison.net/2026/Jun/25/ai-and-liability/"
blog: "Simon Willison"
date: 2026-06-25
url: https://simonwillison.net/2026/Jun/25/ai-and-liability/
category: "Link Blog"
ingested: 2026-06-26
tags: [ai, liability, google, ai-overviews, schneier, simon-willison, regulação]
---

# AI and Liability

**Source:** Simon Willison's Weblog (link blog to Bruce Schneier)
**Date:** 2026-06-25
**URL:** https://simonwillison.net/2026/Jun/25/ai-and-liability/
**Categorias:** Link Blog

## Resumo

Link blog de Simon Willison apontando para um post de **Bruce Schneier** sobre uma decisão recente da corte alemã que **declarou o Google legalmente responsável por erros introduzidos em seus AI Overviews**. O argumento central de Schneier, citado por Simon: **"Agentes de IA são agentes da pessoa ou organização que os implanta — e devem ser tratados pela lei como tal."** Se uma empresa contratasse escritores humanos para escrever seus resumos, essa empresa seria responsável por imprecisões nesses resumos. Permitir que empresas se escondam atrás da desculpa de "IA defeituosa" nas mesmas circunstâncias seria um presente maciço às empresas, e introduziria incentivos desastrosos para mau comportamento corporativo.

A provocação de Schneier é direta: por que contratar escritores, advogados ou médicos humanos quando IAs são não apenas mais baratas, mas também **absolvem os empregadores sempre que cometem um erro**? Isso cria um incentivo perverso para substituir trabalho humano por IA não por ganho de produtividade, mas por transferência de risco. Schneier defende que o precedente legal deveria ser o de tratar a saída da IA como saída do implantador — sem cláusula de escape.

A decisão alemã específica (reportada no The Decoder) é a primeira a cravar essa posição com força legal: o Google não pode argumentar que os erros nos AI Overviews são "do modelo", são erros do Google enquanto editor da saída. A implicação mais ampla: **toda empresa que implanta IA em um produto voltado ao público passa a ter responsabilidade editorial sobre o output do modelo**, não responsabilidade zero por ser "máquina".

## Por que importa

- Precedente regulatório importante: a Alemanha acaba de cravar o princípio de que **output de IA é output do implantador**. Isso muda a economia de risco de qualquer feature de IA generativa em produto. Empresas não podem mais usar "a IA alucinou" como defesa universal.
- Para quem constrói produtos com IA: a regra prática passa a ser **trate o output do modelo como se fosse um humano seu escrevendo** — você responde pelo conteúdo, e o usuário tem direito a esperar o mesmo padrão. Isso justifica investimento pesado em curadoria, grounding, fact-checking, e disclaimers quando o sistema falha.
- Crossover com o trabalho de Ramon: agentes autônomos que agem em nome do usuário (enviam email, marcam reunião, fazem transação) herdam essa mesma lógica. **O usuário é responsável pelo que o agente faz em seu nome**, e o operador do agente (Hospedeiro) responde pelos outputs do agente para terceiros.
- Conecta com [[resumo-simon-willison-why-ai-hasnt-replaced-software-engineers]] — a substituição de trabalho humano por IA não sai "de graça" do ponto de vista legal. Accountability permanece humana, mesmo quando o executor é uma máquina.
- Schneier é fonte consistente de análise de segurança/regulação; vale seguir de perto para quem opera em tech.

## Frases notáveis

> "AI agents are agents of the person or organization that deploys them — and should be treated by the law as such."

> "To allow businesses to hide behind the excuse of faulty AI in those same circumstances would be a massive handout to companies, and would introduce disastrous incentives for corporate misbehavior."

> "Why hire human writers, lawyers or doctors when AIs are not only cheaper, but also absolve employers whenever they make a mistake?"
