---
title: "sqlite-utils 4.0rc2, mostly written by Claude Fable"
source: https://simonwillison.net/2026/Jul/5/sqlite-utils-fable/
date: 2026-07-05
tags:
  - ia
  - coding-agents
  - sqlite
  - devops
---

## Resumo

Simon Willison aproveita os últimos dias de acesso ao Claude Fable (modelo Mythos-tier) no plano Max para conduzir uma revisão pré-release do `sqlite-utils 4.0`. O fluxo é um experimento notável de engenharia agentic: 37 prompts, 34 commits, +1.321/−190 linhas em 30 arquivos, conduzido majoritariamente pelo Claude Code for web no iPhone enquanto Willison assistia ao desfile de 4 de julho em Half Moon Bay.

A revisão automatizada pegou um bug crítico que Willison não havia encontrado sozinho: `Table.delete_where()` rodava via `self.db.execute()` sem wrapper `atomic()`, deixando a conexão em `in_transaction=True`. O efeito cascata é que **toda chamada subsequente a `atomic()` entrava no branch de savepoint e nunca commita** — perda de dados silenciosa. Willison caracteriza como "release blocker" e celebra ter pego antes do stable. O modelo também forçou Willison a confrontar uma dívida técnica que ele mesmo admitia não ter pensado: o suporte ao `autocommit=True/False` introduzido no Python 3.12 quebra o modelo de transações do `sqlite-utils` de forma sutil.

A jogada mais interessante é a segunda camada de revisão: Willison passou o trabalho do Claude Fable para o **GPT-5.5 xhigh** via Codex Desktop. Achei superstição inicialmente, ele admite — mas funciona: o modelo da OpenAI encontrou dois bugs P1 que o Fable tinha deixado passar, relacionados a `db.query()` fazer auto-commit antes de levantar `ValueError`, e ao commit de `INSERT ... RETURNING` depender do iterador ser esgotado. A correção veio em PR separado. Willison encerra com o custo não-subsidiado estimado da sessão: **US$ 149,25**.

## Por que importa

- Para o Ramon (IA/ML + devops): o artigo é quase um manual prático de **workflow agentic para bibliotecas de produção**. Willison demonstra o pipeline ideal — Claude Code para implementação, modelo cruzado para revisão, humano para governança — e é transparente sobre custos e limites.
- Dois insights raros: (a) modelos top-tier ainda precisam de revisão por modelo concorrente (a fronteira entre labs virou asset de QA); (b) a estratégia de revisar primeiro a *documentação* antes do código é contraintuitiva mas funciona como mapa de mudanças.
- O timing cria urgência: o "Fablepocalypse" (7 de julho) marca quando mesmo assinantes Max pagarão API cheia. É um marcador de ciclo — quem está construindo workflows dependentes de modelo Mythos tem uma janela curta para institucionalizar o que aprendeu antes do custo mudar a equação.

## Frases notáveis

> "Every method in this library that writes to the database... runs inside its own transaction and commits it before returning. Your changes are saved to disk as soon as the method call finishes."

> "I used to think that the idea of having one model review the work of another was somewhat absurd—it felt weirdly superstitious. The problem is *it really does work*."
