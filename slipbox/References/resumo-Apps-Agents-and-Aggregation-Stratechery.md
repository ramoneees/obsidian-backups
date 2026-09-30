---
title: "Apps, Agents, and Aggregation"
source: "https://stratechery.com/2026/apps-agents-and-aggregation/"
date: 2026-09-30
tags: [ia, agentes, estrategia, devops]
---

## Resumo

Ben Thompson pega o "Are you getting it?" do Jobs no lançamento do iPhone e o aplica a 2026: você entendeu que a interface natural com IA é conversa, que nós não vamos mais programar computadores — agentes vão usá-los —, e que UI pré-construída está morta? A tese central: agentes não são "IA + prompt", são IA com acesso a um computador. Por isso o lançamento do Muse da Meta importa menos pelo modelo e mais pela infraestrutura: a Meta provisiona uma VM de verdade para cada usuário (2 cores, 8GB RAM). Thompson pediu ao Muse que organizasse receitas salvas no Instagram e terminou a conversa — caminhando com o cachorro — com um app novo instalado. O "infinito app": UI gerada sob demanda, descartável porque infinita.

A extensão da Aggregation Theory: na web, distribuição ficou abundante e o gargalo virou descoberta (Google/Meta agregaram demanda). Com agentes, fazer coisas fica abundante e o escasso passa a ser a volição — o gargalo não é descoberta, é inspiração. Quem resolver inspiração vira o gatekeeper não só da demanda, mas do desejo. Tudo abaixo do agente vira fornecedor, destino das publicações sob agregadores.

Dois players estão posicionados para ganhar essa disputa: Meta (chega a quase toda pessoa do planeta) e Microsoft (chega a quase todo funcionário — o Copilot com Autopilot, agente enterprise com identidade, memória e computador próprio no tenant, é o "OS do trabalho" de sempre). Modelos são substituíveis; agentes ficam melhores quanto mais contexto e acessos têm de você — stickiness máxima, e a maioria das pessoas terá UM agente, não vários. A implicação desconfortável: quem usa agentes já vive isso, quem não usa vai achar "bárbaro" o jeito antigo.

## Por que importa

- Descrição exata do setup do Ramon em estágio avançado: Hermes/OpenCode operando computador, com computador próprio por agente (gateway, VMs, CI). O artigo projeta pra onde esse fluxo evolui — agente único com contexto acumulado.
- Tese de volição > descoberta é provocação útil para produtos: no precisase (matching de voluntariado/doações), o "job to be done" importa mais que a interface — agents podem ser o canal, não o site.
- Aposta Meta × Microsoft como donos da distribuição de agentes: relevante para as escolhas de stack e APIs que o Ramon faz hoje (Fleet API, ASAs, integrações).

## Frases notáveis

> "Agents are not just AI: they are an AI that has access to a computer."

> "What is happening with agents is that the ability to do stuff is becoming abundant; what is scarce is volition."
