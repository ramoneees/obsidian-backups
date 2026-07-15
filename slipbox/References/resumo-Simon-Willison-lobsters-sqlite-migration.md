---
title: "lobste.rs is now running on SQLite"
source: https://simonwillison.net/2026/Jul/14/lobsters-sqlite/
date: 2026-07-15
author: Simon Willison
tags: [devops, sqlite, infraestrutura, rails, migração-de-dados]
---

# lobste.rs Agora Roda em SQLite

A comunidade Lobsters, que discutia migrar para fora do MariaDB desde 2018, concluiu neste fim de semana a migração para SQLite — abandonando a ideia original de PostgreSQL. O resultado operacional é um dos relatórios mais claros de devops minimalista de 2026: **uso de CPU caiu, memória caiu, site ficou mais responsivo, custo de VPS caiu pela metade** depois que o servidor MariaDB foi desligado. A app Rails inteira agora roda em uma única VPS, com um banco primário de conteúdo de ~3.8GB, mais um banco de cache de 1.1GB, um de filas de 218MB, e um de 555MB crescendo devagar para o middleware Rack::Attack (rate limiting).

Willison destaca que o PR de migração, escrito por Thomas Dziedzic, **adicionou 735 linhas e removeu 593** em 30 commits e 188 arquivos — incluindo a remoção líquida de código, sinal raro em migrações. O trabalho encadeia três PRs anteriores (#1705, #1871, #1924) e abre caminho para que Lobsters se torne referência de "stack de servidor único" em produção.

A provocação implícita de Willison — repetida em vários posts recentes — é direta: em 2026, dá para fazer **muita coisa** com um único servidor e SQLite. A velha presunção de que Postgres é obrigatório para qualquer carga "real" está se dissolvendo; o caso Lobsters é mais um tijolo nessa demolição.

## Por que importa

- Case study prático e replicável de **infra enxuta** — útil para o trabalho de devops/automação: prova empírica de que o "boring stack" venceu em mais um caso de produção real com carga não trivial.
- Conecta-se diretamente à tendência **SQLite em produção** que Willison vem documentando (ver também os lançamentos de sqlite-utils 4.0 e Datasette no mesmo blog).
- Para quem desenha sistemas: a métrica "linhas removidas > linhas adicionadas" numa migração deveria ser o padrão, não a exceção.

## Frases notáveis

> "SQLite parece ter passado com folga: cpu usage caiu, memória caiu, site está mais snappy pelo menos para mim, e o custo de VPS caiu pela metade depois que a VPS do mariadb foi desligada."

> "Este é um estudo de caso muito útil, e um ótimo lembrete de que dá para fazer muita coisa com um único servidor e SQLite em 2026."
