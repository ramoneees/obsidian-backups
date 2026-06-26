---
title: "datasette-export-database 0.3a2"
source: "https://simonwillison.net/2026/Jun/25/datasette-export-database/"
blog: "Simon Willison"
date: 2026-06-25
url: https://simonwillison.net/2026/Jun/25/datasette-export-database/
category: "Release"
ingested: 2026-06-26
tags: [datasette, sqlite, release, open-source, simon-willison]
---

# datasette-export-database 0.3a2

**Source:** Simon Willison's Weblog
**Date:** 2026-06-25
**URL:** https://simonwillison.net/2026/Jun/25/datasette-export-database/
**Categorias:** Release

## Resumo

Release mínimo do plugin `datasette-export-database`, versão 0.3a2. Simon Willison é direto: "An embarrassingly tiny release". O `pyproject.toml` tinha pinado acidentalmente para `datasette==1.0a27`, tornando o plugin incompatível com todas as outras versões do Datasette. A correção foi mudar para `datasette>=1.0a27` em vez do pin exato. O release existe apenas para corrigir esse bug de empacotamento. **O plugin agora funciona com qualquer versão do Datasette >= 1.0a27.**

A função do plugin em si: exportar uma cópia de um banco SQLite mutável sob demanda. É o tipo de utilidade que resolve um problema real para quem usa Datasette em produção — conseguir tirar um snapshot do banco sem ter que parar o serviço, fazer dump manual, e servir de novo.

## Por que importa

- Lição de packaging Python: pins exatos em `pyproject.toml` viram grilhões desnecessários quando você está publicando uma biblioteca/plugin. Restrições inferiores (`>=`) são quase sempre o padrão certo para plugins; pins exatos deveriam ser reservados para aplicações finais, não bibliotecas.
- Mostra o ritmo de manutenção de Simon Willison — releases pequenos saem rapidamente quando o problema é identificado, sem inflar changelog ou esperar por feature maior. Bom exemplo de **release early, release small**.
- Para quem opera Datasette (ou qualquer plugin ecosystem), vale a pena auditar as próprias dependências. Um pin acidental em uma versão alpha pode bloquear meses de upgrades.
- Crossover com [[Simon Willison-click-to-play — a still that plays]] e [[Simon Willison-Claude Fable is relentlessly proactive]] — todos releases/posts pequenos do mesmo autor, mostrando consistência de cadência.

## Frases notáveis

> "An embarrassingly tiny release."

> "It's now `datasette>=1.0a27` instead."
