---
title: "The Two-Agent Chain: How to Make AI Agents Work Together (With a Spreadsheet)"
source: "Asian Efficiency"
date: 2026-08-20
url: "https://www.asianefficiency.com/technology/make-ai-agents-work-together/"
tags: [reference, technology, ai, agents, automacao, padrao]
ingested: 2026-08-21
---

# The Two-Agent Chain: How to Make AI Agents Work Together (With a Spreadsheet)

**Fonte:** Asian Efficiency
**Data:** 20 de agosto de 2026
**URL original:** https://www.asianefficiency.com/technology/make-ai-agents-work-together/

## Resumo

Padrão para conectar dois agentes: o output de um vira o input do outro, sem humano no meio — e o ponto de handoff é uma planilha (Google Sheet). Exemplo canônico: Agente 1 pesquisa jornalistas e popula a sheet (nome, veículo, email, pautas recentes); Agente 2 monitora a sheet, acorda com linha nova, pesquisa o trabalho do jornalista, escreve pitch personalizado e envia.

## Notas principais

- **A planilha é arquitetura, não conveniência:** corrida de revezamento — o corredor 1 não precisa saber a ruta do 2, só passar o bastão. Agentes desacoplados = qualquer um dos dois pode ser trocado sem quebrar o sistema; fácil adicionar Agente 3 (ex.: categorizar respostas: interested / not now / unsubscribe).
- **Onde funciona:** qualquer processo de duas fases — (1) coletar/achar dados (research, scraping, monitoring, intake) + (2) agir (emails, CRM, conteúdo, relatórios). Exemplos: lead gen via LinkedIn, hiring, follow-ups de CRM parados há 7 dias, monitoring de concorrência, onboarding.
- **Sales outbound:** agente pesquisa prospect e envia mensagem personalizada por <$1/mensagem; capacidade deixa de ser "ligações por dia".
- **Como construir:** identificar o handoff → Agente 1 (só popula a sheet; testar até dados limpos) → Agente 2 (trigger "linha nova"; testar com linhas manuais) → conectar e rodar lote pequeno end-to-end.
- **Anti-padrão:** um agente gigante que faz tudo (brittle; qualquer passo quebrando derruba tudo). Dois agentes pequenos com jobs focados > um monólito.
- Começar: processo de 2 passos que já repete manualmente; 5 colunas que realmente usa; rodar à mão 5 linhas antes de deixar agente escrever as próximas 5.

## Conexões

- Tópicos: [[AI agents]], [[automação]], [[handoff]], [[padrões de agentes]].
- Dialoga com [[Asian Efficiency-Before You Automate It, Run the Workflow by Hand|run by hand primeiro]] e com [[Asian Efficiency-My Client Said AI Knows Him Better Than Most People Do. He Was Right.|context profile]].
