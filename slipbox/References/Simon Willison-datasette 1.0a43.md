---
title: "datasette 1.0a43"
source: "Simon Willison"
date: 2026-11-15
url: "https://simonwillison.net/2026/Nov/15/datasette/"
tags: [reference, datasette, release, python, seguranca, streaming, simon-willison]
blogwatcher_id: 1360
ingested: 2026-11-16
---

# datasette 1.0a43

**Fonte:** Simon Willison (série de releases)
**Data:** 15 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/15/datasette/

## Resumo

Nova alpha do trilho 1.0 — milestone agora **53% completo**, com o autor "leaning hard" no Claude Fable 5.2 para derrubar itens da lista. O maior item da release: **streaming para output renderers** — TSV e CSV nativos já usam, e plugins podem registrar streaming de todas as linhas de uma tabela de uma vez via o novo `Response.stream()`.

## Ideias principais

- **Streaming de renderers:** exportações de tabelas grandes sem carregar tudo em memória — `Response.stream()` como API pública de plugins.
- **Correções de segurança:** uma delas mereceu advisory no GitHub — queries privadas armazenadas podiam expor título e SQL da query (sem permitir execução).
- **UX do 1.0:** representação JSON da row page finalmente com design digno de 1.0; novo Web Component `<datasette-copy-button>` para copy-schema; utilitário JS `DatasetteModal.confirm()`; JSON em colunas com pretty-print.
- **Detalhe favorito do autor:** CSS multi-page view transitions (cross-document view transitions) — polimento perceptível com pouquíssimo código.
- **Contribuições externas:** dezenas de bug fixes de Zihan Dai, Peter Olkhovets, Ilya Khalafi e Ankita Advitot.

## Notas e conexões

- Alpha anterior da série: [[Simon Willison-datasette 1.0a41]].
- O fix de segurança da rota `add_database` foi backportado para o trilho estável: [[Simon Willison-datasette 0.65.6]].
- [[slipbox/References]]
