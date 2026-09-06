---
title: "The purpose of DNS is to spread scams"
source: Simon Willison
author: Simon Willison (link post sobre Terence Eden)
date: 2026-09-06
url: https://simonwillison.net/2026/Sep/6/the-purpose-of-dns-is-to-spread-scams/
category: Link Blog
tags: [dns, scams, terence-eden, icann, cybersecurity]
ingested: 2026-09-06
---

# The purpose of DNS is to spread scams

## Resumo

Link post de Simon Willison destacando o argumento provocativo de Terence Eden: "o propósito do Domain Name System parece ser um vetor para criminosos aplicarem golpes em pessoas a uma taxa assustadoramente alta". Eden cita o relatório da Interisle sobre demanda de domínios cibercriminosos (via Andrew Campling no RIPE Labs) com estatísticas que Simon admite não conhecer.

## Pontos-chave

- **Os números (relatório Interisle 2025)**: 85 milhões de novos registros de gTLDs em 2025. Desses, 8,5 milhões já estavam em blocklists até maio de 2025 — 10%.
- **Piso, não teto**: o relatório estima que 10% de abuse rate é o *piso* provável; o número real provavelmente se aproxima de 20%. Ou seja: 1 em cada 5 domínios gTLD recém-registrados é scam. Eden: "That's a bloody crisis."
- **ICANN sabe**: aparentemente a ICANN discute esse problema há anos, sem resolução efetiva.
- **Fontes encadeadas**: post original em shkspr.mobi/blog → relatório interisle.net/insights/cybercriminaldomaindemand → análise de Andrew Campling no labs.ripe.net ("DNS Abuse and Criminal Infrastructure: Beyond Definitions and Blocklists").
- Reação de Simon: "I had no idea" — o dado de 20% não circula como deveria.

## Notas e Conexões

- Implicação prática: dominios recém-registrados são, estatisticamente, de alta suspeição — reforça heurísticas de phishing/scam em qualquer triagem de email ou inbox (relevante para o fluxo de finanças e para o email-inbox-triage do Boss).
- Blocklists capturam só a ponta visível (10%); o abuse real é maior — confiar só em blocklist é falso conforto de segurança.
- Tema recorrente na semana no blog do Simon: [[Simon Willison-OpenAI's rogue agents were caught communicating via public wikis]] (4 set 2026) — infraestrutura pública da internet sendo cooptada por atores maliciosos (agents, nesse caso; scammers, aqui).
- Terence Eden como voz de infra/web standards — vale seguir (shkspr.mobi) se o tema DNS abuse voltar.
