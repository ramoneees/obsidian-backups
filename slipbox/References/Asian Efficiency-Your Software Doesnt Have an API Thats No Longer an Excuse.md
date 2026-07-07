---
date: 2026-07-07
source: "https://www.asianefficiency.com/technology/your-software-doesnt-have-an-api-thats-no-longer-an-excuse/"
blog: "Asian Efficiency"
tags: [AI, automação, computer-use, API, browser-agent, small-business, SalonBiz, MLS]
---

# Asian Efficiency - Your Software Doesn't Have an API? That's No Longer an Excuse.

## Resumo

O artigo derruba a objeção clássica de "nosso software não tem API" para automação de pequenos negócios. A virada tecnológica é o **computer use**: agentes de IA com acesso a um browser virtual podem logar, navegar, clicar e preencher formulários exatamente como um humano — sem precisar de API, developer ou acesso especial ao backend.

O caso concreto é o HEB Agent do autor: lê uma Google Sheet com lista de compras, navega até HEB.com, loga com credenciais, busca cada item, adiciona ao carrinho, manda email de confirmação. Zero integração por API. O mesmo princípio foi aplicado a um cliente de imóveis que precisava puxar listings de um MLS com paywall e database fechado — um agente de VM loga, busca, extrai dados e popula uma Google Sheet que dispara o resto do pipeline, rodando 24/7.

A restrição real mudou: não é mais "o software tem API?" mas sim "o workflow segue um padrão consistente o bastante para um agente rodar com segurança?". Para admin de rotina, a resposta costuma ser sim.

## Pontos Principais

- **Computer use**: agente com browser virtual que navega, clica, preenche forms como humano
- **HEB Agent**: lê Google Sheet → loga em HEB.com → busca itens → adiciona ao carrinho → manda confirmação
- Caso SalonBiz (POS de salões sem API): o que antes era "não dá para automatizar" agora é viável via computer use
- Caso MLS (real estate): listings extraídos automaticamente para Google Sheet, 24/7, sem humanos
- **A restrição mudou**: de "tem API?" para "o workflow é consistente o bastante para um agente?"
- Candidatos naturais: relatórios semanais de POS, inventário com threshold, data entry entre web apps, form submissions
- **Caveat importante**: computer use é menos estável que API real — páginas mudam, layouts mudam, login flows atualizam
- Tradeoff vale a pena para: alta frequência, alto valor, padrão consistente (grocery semanal, relatórios mensais, buscas diárias)
- A objeção "não tem API" precisa aposentar — foi verdade, hoje não é mais

## Conexões

- Conecta com [[Asian Efficiency-I Built an AI Agent in 20 Minutes Before a Client Meeting. Here's What Happened]] — mesmo tema de agentes rápidos
- Conecta com [[Asian Efficiency-My AI Agents Saved 83 Hours in One Week. Here's How I Know.]] — ROI de automação por agentes
