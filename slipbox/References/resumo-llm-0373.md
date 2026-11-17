---
title: "llm 0.37.3"
source: https://simonwillison.net/2026/Nov/16/llm/
date: 2026-11-17
tags: [ia, llm-cli, sqlite, devops]
---

Simon Willison lançou o LLM 0.37.3, um patch com um único motivo: o Homebrew atualizou o SQLite para 3.54.1 e a nova versão quebrou o código de logging do LLM. É a continuação direta de [[resumo-llm-037]] — a 0.37 trouxe embeddings multimodais e triagem de PRs por IA; a 0.37.3 existe porque uma dependência upstream mudou de comportamento por baixo da ferramenta.

O detalhe técnico é uma micro-aula de semântica de JSON no SQLite. No 3.54.0, select json_object(a, (select json_array(1))) retornava o array aninhado de verdade. No 3.54.1, a mesma query retorna o array como STRING. Motivo: a subquery retorna texto SQL, não JSON — o comportamento antigo era o bug, e o 3.54.1 o corrigiu. O workaround é embrulhar a subquery com json(): json((select json_array(1))).

O provocativo está na resposta de D. Richard Hipp: um fix documentado, correto segundo a spec — e que quebrou todo mundo que dependia do comportamento acidental anterior. Não houve aviso de deprecação nem migração: quem fez brew upgrade descobriu o logging do LLM morto na prática. A cadeia foi hipp corrige o SQLite -> Homebrew empacota -> toda CLI que parseia JSON no banco para de logar.

Lição devops em duas camadas. Primeira: mudanças corretas upstream são breaking changes downstream — pin de versão resolve, mas só se você souber QUE dependência quebrou; e o sintoma aqui é o pior tipo, logging silencioso, porque você só detecta quando precisa do histórico. Segunda: se o seu pipeline depende de funções json_* do SQLite (blogwatcher-cli local, crons de dados), um teste de fumaça depois de brew upgrade custa menos que o debug às cegas.

## Por que importa

- Você roda SQLite em quase toda automação da casa (blogwatcher, crons de dados, containers no OrbStack) e atualiza o Homebrew sem cerimônia — brew upgrade é, tecnicamente, uma mudança de produção.
- Logging quebrado silenciosamente é falha de baixa visibilidade: sistemas que você audita pelo histórico falhariam sem erro aparente.
- O formato do bug (comportamento acidental corrigido pela spec) é exatamente o cenário que testes de regressão contra dependência pinada existem para pegar.

## Frases notáveis

- "That was a bug fix. Per the documentation, (SELECT json_array(...)) returns SQL text, not JSON. Hence the 3.54.1 behavior is correct and 3.54.0 was a bug." — D. Richard Hipp
