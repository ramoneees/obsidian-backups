---
title: "Open Source AI Gap Map"
source: https://simonwillison.net/2026/Jul/3/open-source-ai-gap-map/
date: 2026-07-04
tags: [ia, open-source, local-llms, infraestrutura, governanca]
---

## Resumo

Simon Willison comenta o lançamento do Gap Map da Current AI, uma parceria global criada como nonprofit na Cúpula de Ação em IA de Paris (fevereiro de 2025) e já com $400M comprometidos. A ambição é construir "uma opção pública para IA" — e o Gap Map é o primeiro entregável: um inventário aberto do ecossistema de IA open source, hoje em 421 produtos pesquisados em profundidade (266 ferramentas/libs, 85 modelos, 50 datasets, 20 projetos de hardware) produzidos por 228 organizações. O restante, ~24.400 artefatos, está catalogado mas sem score até ser pesquisado.

O que Willison acha mais interessante não é o mapa visual em si, e sim os dados por baixo: 1.184 arquivos YAML lançados sob licença MIT no GitHub (currentai-org/os-ai-map), junto com os notebooks e scripts usados para coletar. É uma base de dados que pode ser cruzada com Datasette Lite — Willison já publicou um link explorando os 16.185 repositórios GitHub rastreados. Em outras palavras, é infraestrutura de infraestrutura: dados sobre quem está construindo o quê, em quais camadas da stack (componentes de modelo, produto/UX, infraestrutura), com cobertura dos 14 nichos do ecossistema.

A leitura geopolítica é clara: enquanto o debate público se concentra nas big labs fechadas, existe um movimento coordenado de capital público/filantrópico para tornar a IA auditável. O Gap Map é o equivalente open source de um registro de saúde da indústria — não impede nada por si só, mas torna possível falar de "estado da arte" com evidência em vez de especulação.

## Por que importa

- Para o lado devops/automação: o YAML schema do os-ai-map é matéria-prima para qualquer agente que precise decidir "qual modelo open source usar para X" sem reinventar a curadoria. Vale clonar o repo para o vault.
- Cruza com IA/ML e teologia reformada de um jeito raro: a ideia de "opção pública" para uma tecnologia tão concentrada ecoa debates antigos sobre bens comuns e stewardship. Para um cristão que trabalha com IA, é o tipo de iniciativa que pode ser apoiada sem cair em tecnoutopianismo.
- Conecta diretamente ao artigo do Piper: a Current AI tenta exatamente o que Piper pede à igreja — uma lealdade acima das facções. O Gap Map é geopolítica feita infraestrutura, não marketing.

## Frases notáveis

> "The Gap Map v0.1 details 421 products in depth: 266 software tools and libraries, 85 models, 50 datasets, and 20 hardware projects, produced by 228 organizations."

> Current AI is "a global partnership building a public option for AI".
