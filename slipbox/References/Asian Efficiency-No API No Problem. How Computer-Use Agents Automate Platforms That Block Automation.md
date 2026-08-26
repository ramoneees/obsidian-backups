---
title: "No API? No Problem. How Computer-Use Agents Automate Platforms That Block Automation"
source: "Asian Efficiency (Thanh Pham)"
date: 2026-08-26
url: "https://www.asianefficiency.com/productivity/no-api-no-problem-computer-use-agents/"
category: ai-tools
tags: [ai, agents, computer-use, automation, no-api, linkedin, mls]
ingested: 2026-08-26
---

# No API? No Problem. How Computer-Use Agents Automate Platforms That Block Automation

**Fonte**: Asian Efficiency (Thanh Pham)
**Data**: 2026-08-26 · **URL**: https://www.asianefficiency.com/productivity/no-api-no-problem-computer-use-agents/

## Resumo

Atualização do argumento "no API, no automation" — a objeção que circula no mundo de automação com IA (LinkedIn outreach, MLS, portais de saúde, CRMs proprietários). A premissa parou de ser verdade "a few months ago": spin up uma virtual machine na cloud, apontar um AI agent com instruções, e o agente abre browser, faz login, navega, preenche forms e extrai dados — "from the website's perspective, it is a human".

### Caso 1: MLS (real estate)
- Pipeline de equipe imobiliária dependia de velocidade de ofertas; gargalo era puxar *comparables* do MLS manualmente.
- Resposta padrão do mercado: "MLS doesn't have an API. No API, no automation."
- Com o agente em VM: credenciais + descrição do processo de busca → agente loga, roda a busca, puxa números e alimenta o workflow de offer-prep. "The thing that had been a hard wall turns out to be nothing more than an assumption that nobody questioned."

### Caso 2: LinkedIn
- API limita agressivamente outreach; devs que tentaram workarounds foram banidos.
- VM loga como pessoa; a partir de lista de leads, agente acha perfis, rascunha mensagem personalizada com research pública e coloca na fila para revisão. Rodou em background; o time focou nas respostas.

### Princípio e checklist
> "If a human can log into something and do it, an agent can do it too."

Checklist da lista "can't automate": plataformas setoriais sem API (legal, saúde, imóveis); plataformas onde a automação é possível mas policy-restricted (LinkedIn, review sites); portais que exigem login+navegação; sistemas legados sem integration layer. A pergunta certa deixou de ser "tem API?" e passou a ser "uma pessoa consegue logar e fazer isso num browser?"

### Riscos
- Menos estável que integração de API: quebra quando o site muda layout; exige monitoring; questões legítimas de ToS — checar antes de deployar.
- Para uso interno, bases setoriais e plataformas que nunca restringiram automação (só nunca construíram API): opção prática e cada vez mais estável.

> "The 'no API' wall has a door in it. Most people just haven't found it yet."

## Notas e Conexões

- Terceira passada da AE no mesmo tema — mais direta que as anteriores: [[Asian Efficiency-Your Software Doesn't Have an API That's No Longer an Excuse.]] (julho, com HEB/SalonBiz) e o post linkado "no-api-objection-computer-use". O núcleo não muda: computer-use é a forma mais geral de agente.
- Liga diretamente ao workflow real do Hermes (computer_use tool) — a tese do artigo é literalmente a stack que já uso aqui.
- publicado no mesmo dia que [[Asian Efficiency-The Best AI Demo Is One They Don't See Coming]] — ambas sobre agentes operando invisivelmente no fluxo normal de trabalho.
