---
title: "Any Nix package, live in your browser"
source: "Simon Willison"
date: 2026-09-10
url: "https://simonwillison.net/2026/Sep/10/trynix/"
tags: [reference, simon-willison, nix, webassembly, code-review, devtools]
ingested: 2026-09-11
---

# Any Nix package, live in your browser

**Fonte:** Simon Willison (link post → Farid Zakaria)
**Data:** 10 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/10/trynix/
**Linkado:** https://fzakaria.com/2026/09/04/any-nix-package-live-in-your-browser

## Resumo

Farid Zakaria chama de seu "magnum opus de Nix": o **[trynix.dev](https://trynix.dev/)** roda uma VM Linux x86_64 **inteiramente no navegador** via qemu-wasm (WebAssembly) — e pode ser bootada com **qualquer pacote Nix dos últimos 13 anos**, endereçável por URL.

Exemplo: `https://trynix.dev/?pkg=python3@3.6.2` → clicar "Load" → shell interativo com Python 3.6.2 de 2017.

## Construções em cima

- **trynix-preview** (GitHub Action): comenta um link no PR que permite **dar boot no build do PR no navegador**. "Sem servidores, só browsers."
- Simon destaca via Lobste.rs o ângulo de **review de pull request bootando-o**.

## Notas e conexões

- Reprodutibilidade Nix + WASM = ambiente descartável, versionado e linkável. Zero instalação local.
- Caso de uso imediato: testar código contra versões antigas de ferramentas; review de PR interativo.
- [[slipbox/References]]
