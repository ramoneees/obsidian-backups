---
title: "Soft-deprecating re.match()"
source: "Simon Willison"
date: 2026-09-11
url: "https://simonwillison.net/2026/Sep/11/soft-deprecating-re-match/"
tags: [reference, simon-willison, python, regex]
ingested: 2026-09-11
---

# Soft-deprecating re.match()

**Fonte:** Simon Willison (link post → Hugo van Kemenade)
**Data:** 11 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/11/soft-deprecating-re-match/
**Linkado:** https://hugovk.dev/blog/2026/soft-deprecating-re.match/

## Resumo

O release manager do Python 3.15, Hugo van Kemenade, explica a **soft deprecation** do `re.match()` na versão 3.15.

- Soft deprecation (PEP 387): marcar API como "não usar em código novo" **sem** promessa/ameaça de remoção futura.
- `re.match()` é notoriamente confuso: ancora no **início** da string, mas não no fim.
- Novo nome alternativo, mais claro: **`re.prefixmatch()`** — reflete exatamente o comportamento (prefixo).
- Na maioria dos casos o que se quer é `re.search()` (padrão em qualquer posição) ou `re.fullmatch()` (string inteira).

## Notas e conexões

- Regra prática para lembrar: `match()` = prefixo; `search()` = contém; `fullmatch()` = igual.
- Python 3.15 fica no radar de breaking-ish changes suaves.
- [[slipbox/References]]
