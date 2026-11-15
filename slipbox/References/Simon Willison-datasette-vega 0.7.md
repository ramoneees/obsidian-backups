---
title: "datasette-vega 0.7"
source: "Simon Willison"
date: 2026-11-14
url: "https://simonwillison.net/2026/Nov/14/datasette-vega/"
author: "Simon Willison"
category: "Release"
tags: [release, datasette, vega-lite, visualizacao, datasette-lite, ia]
blogwatcher_id: 1352
ingested: 2026-11-15
---

# datasette-vega 0.7

**Fonte:** Simon Willison
**Data:** 14 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/14/datasette-vega/

## Resumo

Nova versão do datasette-vega, o plugin do Datasette para renderizar gráficos (via Vega-Lite) contra dados de uma tabela ou query customizada. O detalhe que Simon destaca: era o plugin mais tempo intocado do ecossistema — o release anterior era de julho de 2018. O bump traz compatibilidade com os alphas mais recentes do Datasette e ajustes cosméticos para funcionar melhor no Datasette Lite, que acabou de ganhar a capacidade de rodar plugins JavaScript como este. O demo ao vivo do README agora roda direto no Datasette Lite, plotando um CSV de segurança aérea do FiveThirtyEight (companhias × fatalidades) como gráfico de barras.

## Ideias principais

- Plugins de 2018 ainda compilando em 2026: a API de plugins do Datasette manteve compatibilidade por 8 anos — estabilidade de interface como ativo de ecossistema.
- Datasette Lite rodando plugins JavaScript muda a equação: plugins antes presos ao Datasette serverizado agora rodam 100% no browser (Pyodide + JS), sem instalação — o demo do vega vira vitrine disso.
- Padrão de manutenção em lote: o ciclo recente de releases ([[Simon Willison-datasette-cluster-map 0.19]], [[Simon Willison-datasette-leaflet 0.3]], [[Simon Willison-datasette-llm 0.1a10]]) sugere uma passada de compatibilidade pelos plugins antigos por causa do ciclo orientado a agentes/alphas.

## Notas e conexões

- [[Simon Willison-datasette-cluster-map 0.19]] e [[Simon Willison-datasette-leaflet 0.3]] — releases da mesma semana, mesmo padrão de manutenção de plugins de visualização/mapa.
- [[Simon Willison-datasette-llm 0.1a10]] — o lado de integração LLM do mesmo ecossistema de plugins.
- [[slipbox/References]]
