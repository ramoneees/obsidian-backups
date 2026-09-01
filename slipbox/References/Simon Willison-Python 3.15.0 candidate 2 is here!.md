---
source: Simon Willison
title: "Python 3.15.0 candidate 2 is here!"
author: Simon Willison
date: 2026-09-01
url: https://simonwillison.net/2026/Sep/1/python-315-rc-2/
category: technology
tags: [python, release-candidate, github-actions, testing, open-source]
ingested: 2026-09-01
status: summary
---

# Python 3.15.0 candidate 2 is here!

## Fonte

- **Source**: Simon Willison
- **Author**: Simon Willison
- **Published**: 2026-09-01
- **URL**: https://simonwillison.net/2026/Sep/1/python-315-rc-2/

## Resumo

Link post: Hugo van Kemenade (release manager do Python 3.14 e 3.15) anunciou o release candidate final do Python 3.15, com lançamento previsto para outubro. Na fase RC, só bug fixes revisados entram até a versão final.

**Ponto principal**: maintainers de projetos third-party são fortemente encorajados a testar contra o RC **agora** e publicar wheels do 3.15 no PyPI. Wheels binárias compiladas contra RCs funcionarão nas versões 3.15.x finais.

**Anedota de Simon**: em 2021 ele achou um bug no Python 3.10 rodando suas test suites contra ele — mas fora do período de RC, então o bug já tinha shipped. Desde então ele acompanha os RCs de perto.

**GitHub Actions**: o RC ainda não está disponível em `actions/python-versions`. Workaround: adicionar `"3.15"` à testing matrix com `allow-prereleases: true` e `check-latest: true` no `actions/setup-python@v7` — hoje testa contra RC1, migra sozinho para RC2 quando disponível e depois para a estável.

## Key Takeaways

1. Python 3.15.0 final chega em outubro; RC2 é o último teste real da comunidade.
2. Se você mantém biblioteca Python: compilar e publicar wheels contra o RC já é seguro (binário compatível com a final).
3. O pattern `allow-prereleases` + `check-latest` no setup-python mantém a matrix sempre na RC mais recente sem intervenção manual.
4. Testar durante o RC é o momento de pegar bugs antes do ship — não depois.

## Notas e Conexões

- Prática de testar em RCs: [[Simon Willison-sqlite-utils 4.1]] (mesmo princípio de exercitar código real contra versões novas).
- Relevante para CI dos projetos: matrix Python 3.14/3.15 com allow-prereleases.
