---
title: "Running the full server-side Datasette Python app in the browser with service workers and Pyodide"
source: "Simon Willison"
date: 2026-11-17
url: https://simonwillison.net/2026/Nov/17/datasette-lite/
author: "Simon Willison"
category: "Projects"
tags: [reference, python, webassembly, pyodide, service-workers, datasette, urls, ia]
blogwatcher_id: 1385
ingested: 2026-11-17
---

# Running the full server-side Datasette Python app in the browser with service workers and Pyodide

**Fonte:** Simon Willison's Weblog
**Data:** 17 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/17/datasette-lite/

## Resumo

Rewrite completo do Datasette Lite (o port do Datasette para o browser via WebAssembly/Pyodide, original de 2022) usando Service Workers — agora "quase indistinguível da aplicação server-side real". A versão antiga era um hack: Datasette rodava num web worker com requests simulados e HTML injetado via innerHTML, o que quebrava qualquer feature com JavaScript (script tags em innerHTML não executam). A nova registra um service worker para todo o domínio lite.datasette.io que intercepta requests HTTP e serve tudo de código client-side.

## Ideias principais

- **URLs que montam instâncias completas:** parâmetros como `?install=datasette-maplibre` (plugins do PyPI ou wheels), `&url=` (SQLite/JSON/CSV/SQL com CORS aberto — Gists resolvem), `&metadata=`, `&ref=` (versão/commit/tag do Datasette) e `?sqlite=` (versão do SQLite) — demos de features em progresso e reproduções de bug viram um link, sem subir servidor.
- **Sessões via prefixo:** cada tab gera um session ID aleatório e prefixa os requests (`/app/<session>/...`) para o service worker rotear para uma instância Datasette dedicada por tab — necessário porque o service worker é compartilhado entre todas as tabs. Pyodide ainda roda num web worker separado: num service worker propriamente dito, o estado não sobrevive mais de ~30s.
- **Origin story honesto:** o sistema nasceu em maio como spike de pesquisa gerado com Claude Opus 4.8; só em novembro, com Claude Fable 5.2 ajudando a construir os diagramas SVG e esclarecer o funcionamento, ele se sentiu confiante para pôr em produção. IA como ferramenta de compreensão, não só de geração.
- **Bonus — escolha de versão do SQLite:** 163 wheels WASM de pysqlite3 no repo datasette/pysqlite3-wasm-wheels (de 3.25/2018 até 3.54.1), mais uma ferramenta de comparação de SQL entre versões construída com Claude Fable 5.2. Perfeito para demonstrar features novas e debugar comportamentos estranhos de SQLite sem instalar nada no Mac.
- **Uso real no desenvolvimento:** ele já usa o Lite no processo de desenvolvimento do Datasette — comentários em issues com links demonstrando o bug na 1.0a42 e o fix na 1.0a43.
- **O padrão é geral:** nada disso é exclusivo do Datasette — quase qualquer app Python pode rodar no browser como preview environment barato. Extensões C/Rust já compilam para WASM compatível com Pyodide (e o PEP 783, de abril/2026, permite publicá-las no PyPI). SQLite é trivial; PostgreSQL/MySQL em WASM ainda é caminho pouco pisado.

## Notas e conexões

- Demo usa o plugin [[Simon Willison-datasette-maplibre 0.1a0]] e o fix demonstrado saiu na release [[Simon Willison-datasette 1.0a43]]; o padrão de agentes trabalhando sobre Datasette segue nos releases do [[Simon Willison-datasette-agent 0.6a0]].
- Filosofia de dependências mínimas que atravessa o trabalho dele hoje: [[Simon Willison-Quoting Go Proverbs]].
- [[slipbox/References]]
