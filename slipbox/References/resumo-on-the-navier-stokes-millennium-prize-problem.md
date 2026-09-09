---
title: "On the Navier–Stokes Millennium Prize Problem"
source: https://simonwillison.net/2026/Sep/8/on-navier-stokes/
date: 2026-09-09
tags: [ia, llms, etica-ia, matematica]
---

# On the Navier–Stokes Millennium Prize Problem

A OpenAI anunciou que um modelo interno (ainda não lançado) resolveu o problema de existência e suavidade de Navier–Stokes, um dos sete Problemas do Milênio com prêmio de US$ 1 milhão pendente desde 2000. Os agentes chegaram à resolução em ~88 horas após o lançamento, trocando 2,7 milhões de mensagens e consumindo ~130 bilhões de tokens de saída — verificação formal em Lean incluída. Em preços públicos de API, isso beiraria US$ 15 milhões em compute.

A façanha técnica, porém, ficou ofuscada pela polêmica: Tristan Buckmaster (NYU) e Levent Alpöge (Anthropic) trabalhavam no problema há quase um ano, usando Claude e Codex — com todos os rascunhos depositados em sessões do Codex. Rumores do breakthrough deles chegaram à OpenAI, que disparou sua própria corrida. Buckmaster alega que o primeiro prompt do time da OpenAI só foi enviado *depois* de informações sobre o trabalho deles terem chegado lá — e que nunca obteve resposta direta sobre se o modelo foi treinado com acesso às suas sessões.

A OpenAI nega ter visto o trabalho dos dois, mas admite: "não podemos descartar que dados desidentificados derivados do uso dos produtos por eles tenham ajudado a melhorar nossos modelos". Willison conecta isso à dinâmica atual de segurança: assim como "um rumor de bug basta para achar um exploit", agora basta saber que uma solução não publicada *existe* para disparar milhões de dólares em compute de LLM e chegar primeiro.

O ponto filosófico que interessa: o que realmente significa "usado para melhorar o modelo"? Se você brainstorma direções estratégicas com um LLM, qual a chance de isso vazar para um concorrente seis meses depois? O episódio transforma essa questão abstrata em caso concreto — e constrangedor.

## Por que importa

- **Fronteira do que agentes fazem**: um problema aberto de US$ 1 milhão, aberto há 26 anos, resolvido por agentes autônomos em 88 horas com verificação formal em Lean — novo padrão do que esperar de models internos das labs.
- **Treinamento com dados de usuários**: a admissão da OpenAI ("não podemos descartar") é o argumento mais concreto até agora para tratar sessões de LLM como informação sensível — relevante para qualquer segredo que passa pelos seus agentes (BB, work, ideas).
- **Corrida zero-sum em ciência**: a dinâmica scoop/competição entre labs agora se aplica à matemática fundamental, não só a produtos — mesmo padrão de "rumor vira exploit" que a segurança de software já vive.

## Frases notáveis

> "Just knowing that there is an unpublished solution to a problem might trigger millions of dollars in LLM spending to get there first."

> "While unlikely, we cannot rule out that de-identified data derived from their usage of our products helped improve our models." (OpenAI)
