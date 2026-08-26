---
title: "The End of Programming"
source: https://pauldix.com/the-end-of-programming
date: 2026-08-26
tags: [ia, engenharia, coding-agents, futuro]
---

# The End of Programming

Paul Dix (criador do InfluxDB) parte do fato mais absurdo da engenharia recente: o Bun 1.4 foi reescrito de Zig para Rust por agentes de IA — 1 milhão de linhas, 6.778 commits em 11 dias, ~$165k em tokens — dirigido por um único desenvolvedor, Jarred Sumner, com acesso pré-release ao Fable 5. O software resultante roda hoje em milhões de máquinas. A tese: escrever código manualmente e tê-lo revisado linha a linha por humanos está caminhando para a extinção.

O argumento central não é hype — é verificação. Dix rebate quem diminui o feito ("tinham um oracle, era só traduzir de uma linguagem pra outra"): se você constrói um sistema de verificação e dá direção adequada, a IA produz software complexo e continua refinando até funcionar. O review humano deixa de ser linha a linha e migra pro resultado final. Os desenvolvedores da Anthropic e OpenAI já operam assim — dezenas ou centenas de PRs por semana, foco em systems/prompts/verificação, não em leitura de diff.

Ele traz dois relatos de campo próprios: integração Iceberg no InfluxDB (14h de agentes) e um sistema de replicação edge completo (28h, arquitetura + supervisão dele). Ambos funcionando meses depois — sem uma linha revisada por olhos humanos. O protótipo é o começo; o loop de melhoria com IA também endurece o produto final.

Previsões práticas: Astra da OpenAI em setembro, modelos que cruzam o patamar do Opus 4.5/GPT 5.2 até início do ano que vem, e inteligência de fronteira barata e abundante pra todos até fim do próximo ano. Inércia organizacional garantirá uma década de empresas escrevendo código à mão — mas os mais produtivos já estarão dirigindo fábricas de software com agentes, harnesses e QA automatizado. O gargalo deixa de ser escrever código e vira: **o que enviar, e o que suportar?**

## Por que importa

- É a tese do Boss levada ao extremo natural: delegar TODO o coding a agentes (OpenCode/Sisyphus) deixa de ser excentricidade e vira a curva padrão. O trabalho humano migra pra escopo, arquitetura e verificação — exatamente o fluxo escopo→plano→review→revisão→código.
- Valida o padrão de QA dele: code review pós-agente + dogfooding como camada de garantia, em vez de review linha a linha. O artigo chama isso de "verification system" — é a mesma coisa com outro nome.
- Timeline acionável: se inteligência de fronteira barata chega até fim de 2027, vale planejar agora a infra de agentes (harnesses, loops de melhoria) em vez de escalar revisão manual.

## Frases notáveis

> "I think the act of writing code manually and having other humans review it to create useful, working software is headed for extinction."

> "The only question will be what do you want to ship? And what do you want to support?"
