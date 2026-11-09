---
title: "parse_number() as a SQLite extension: C vs Rust"
source: https://simonwillison.net/2026/Nov/8/sqlite-parse-number-c-vs-rust/
date: 2026-11-09
tags: [sqlite, rust, c, ai-assisted-programming]
---

Willison voltou da caminhada com o cachorro com uma curiosidade: como seria uma extensão SQLite em C que adiciona parse_number() — converter strings como "-$1,234.56" ou "12.5%" em números somáveis e ordenáveis. Em vez de escolher linguagem por fé, ele pediu ao Claude (Opus 5.5, no chat comum) que construísse as duas versões e comparasse: performance, complexidade e tamanho do binário.

Primeiro placar contraintuitivo: a extensão Rust ficou em ~300 KB (duas implementações, rusqlite e sqlite-loadable-rs) contra 14 KB do C — mas o Rust era mais rápido. O motivo: o equivalente Rust do strtod do C é "duas vezes mais rápido". A resposta seguinte é o coração do post: ele pediu ao modelo para escrever sua própria função de parsing em C que alcançasse ou batesse o Rust — e o modelo entregou, usando o "Clinger's fast path". C final: 16–19 ns por linha, o dobro da velocidade das versões Rust, e consistência validada por 8 milhões de checks de fuzz.

Fora o benchmark, o post é um caso de estudo do loop de pesquisa com IA em miniatura: prompt inicial com contexto → hipótese testada (Rust mais rápido que C naive) → prompt direcionado para fechar o gap → resultado documentado como relatório de pesquisa no repositório simonw/research. Curiosidade de fim de semana que vira artefato reutilizável.

## Por que importa

- Derruba o mito de performance "Rust sempre ganha": com o caminho rápido certo, C simples venceu com binário 20x menor — dado concreto para escolhas de stack em ferramentas de dados.
- É a demonstração prática do workflow que o Ramon já usa (delegar coding a agentes, review humano): o insight que moveu o projeto foi humano ("por que o Rust é mais rápido?") e a execução foi do agente.
- SQLite é onipresente no stack dele (Vault, caches, apps) — uma função parse_number dessas resolve limpeza de dados sujos (valores monetários com símbolo/vírgula) direto no banco.

## Frases notáveis

> "Try writing your own C function for parsing text into a decimal number that catches up to or beats the Rust implementation" — e o modelo entregou, via Clinger's fast path.

> "The optimized C implementation was fastest at 16–19 ns per row, about twice as fast as the Rust versions and far faster than SQL replace()."
