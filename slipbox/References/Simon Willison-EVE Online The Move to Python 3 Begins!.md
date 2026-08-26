---
title: "EVE Online: The Move to Python 3 Begins!"
source: "Simon Willison (link post)"
date: 2026-08-25
url: "https://simonwillison.net/2026/Aug/25/eve-online-move-to-python-3/"
category: python
tags: [python, python3, stackless, eve-online, migrations, legacy-code, scale]
ingested: 2026-08-26
---

# EVE Online: The Move to Python 3 Begins!

**Fonte**: Simon Willison — link post (aponta para [anúncio da CCP](https://www.eveonline.com/news/view/the-move-to-python-3-begins), via Lobsters)
**Data**: 2026-08-25 · **URL**: https://simonwillison.net/2026/Aug/25/eve-online-move-to-python-3/

## Resumo

EVE Online é há 20+ anos um dos estudos de caso mais interessantes de Python em escala — roda em Stackless Python desde o lançamento (2003), e a última grande atualização foi para Stackless 2.7 em 2010 (16 anos atrás).

O upgrade para Python 3 começa com:
- Script **futurize** (python-future) contra **2,4 milhões de linhas de código**.
- Revisão manual cuidadosa dos **~20.000 pontos** onde Python 2 e 3 divergem em comportamento — ex.: `1 / 2` retorna `0` no Py2 mas `0.5` no Py3.

O anúncio não diz como substituirão o Stackless, mas na conferência do ano passado a CCP apresentou "Scheduling in Carbon: Leaving Stackless Python Behind" — como trocaram o Stackless no engine Carbon do EVE Frontier com a biblioteca open source [carbonengine/scheduler](https://github.com/carbonengine/scheduler).

## Notas e Conexões

- Migração Py2→Py3 no extremo: a técnica (futurize + revisão dos pontos de divergência) é a mesma de qualquer codebase legacy — só que com 3 ordens de magnitude mais código.
- "Legacy com 16 anos de runtime congelado" é o pesadelo de dependência que toda base legada tem; a saída da CCP foi reescrever o scheduler por fora (EVE Frontier) antes de migrar o core.
- Simon cobre migrações Python há décadas (tag `migrations`); o ponto permanente dele: diferenças semânticas silenciosas (`1 / 2`) são o risco real de migração, não a sintaxe.
