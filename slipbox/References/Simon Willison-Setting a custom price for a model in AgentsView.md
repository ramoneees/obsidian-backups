---
date: 2026-06-09
source: "https://til.simonwillison.net/llms/agentsview-custom-model-price"
blog: "Simon Willison"
tags: [AgentsView, Wes McKinney, Claude Fable 5, pricing, AI, observabilidade, TIL]
---

# Simon Willison - Setting a custom price for a model in AgentsView

## Resumo

**TIL** (Today I Learned) de Willison: como definir um preço customizado para um modelo no **AgentsView** (de Wes McKinney, ex-Pandas). Willison é usuário recente da ferramenta, que analisa transcripts de coding agents rodando localmente.

O problema: Claude Fable 5 saiu no dia 09 jun 2026 e ainda não estava incluído na base de preços que o AgentsView usa. Willison usou Fable 5 para **fazer engenharia reversa** do AgentsView e descobriu uma receita para setar preços customizados.

O screenshot mostra seu uso de Fable 5 naquele dia: o maior bloco é **prod_datasette_agent** ($74.06, 89.3% do total), seguido de cloud ($3.98), datasette ($2.81), money ($1.92). Total com cache: $516.62 economizados vs uncached. Uma sessão de 55.9M tokens ($74.06) domina — uma revisão do Datasette Agent.

## Pontos Principais
- AgentsView (Wes McKinney) é uma ferramenta para analisar uso de tokens em coding agents
- Claude Fable 5 não estava na base de preços padrão
- Willison usou Fable 5 para fazer RE da ferramenta e descobrir como setar preço custom
- Receita publicada no TIL hospedado
- Custo dominado por uma sessão: 55.9M tokens = $74.06 numa única revisão
- Cache economizou $516.62 no total
- Padrão útil: como ajustar ferramentas internas para novos modelos rapidamente

## Notas e Conexões
- [[Simon Willison-Initial impressions of Claude Fable 5]]
- [[Simon Willison-llm 0.32a3]] — outro uso de Fable 5 no mesmo dia
- [[Asian Efficiency-My AI Agents Saved 83 Hours in One Week. Here's How I Know.]] — métricas de ROI de agentes AI
