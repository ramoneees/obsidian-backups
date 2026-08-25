---
title: "llm-anthropic 0.27"
source: https://simonwillison.net/2026/Aug/24/llm-anthropic/
date: 2026-08-25
tags: [llm, devops, agentes]
---

# llm-anthropic 0.27

**Simon Willison · 24/08/2026**

Nota curta de release, mas com duas camadas interessantes. A primeira: o plugin oficial do LLM (o CLI de Willison para acessar modelos) para Anthropic foi atualizado para acompanhar o SDK Python `anthropic` v1.0.0, que migrou de `httpx` para `httpx2` — mesma mudança que a OpenAI fez no SDK v3.0.0 duas semanas antes. Ou seja: o ecossistema Python de LLM está passando por uma transição de dependência coordenada em cascata.

A segunda camada é a mais provocativa: Willison **delegou o próprio upgrade a um agente**. O prompt foi de uma linha: "Upgrade to anthropic>=1 - read [a migration guide] and get the tests passing". Ele usou o Fable 5 dentro do Claude Code, e o resultado foi o PR #84 no repositório — agente lendo documentação oficial de migração, atualizando código e validando com a suíte de testes existente.

É o padrão "docs-as-spec para agentes" ganhando corpo: guias de migração estruturados viram insumo direto para automação, e testes existentes funcionam como a função de verificação que fecha o loop. O humano fica no review do PR, não no diff manual.

## Por que importa

- **Padrão replicável no fluxo do Ramon**: prompt de uma linha + migration guide + testes como critério de sucesso é exatamente o workflow de delegação a agentes de coding (OpenCode/Sisyphus) — com o mínimo de scaffold e o máximo de verificabilidade.
- **Rastilho de dependências no ecossistema Python**: a troca httpx → httpx2 varrendo SDKs de OpenAI e Anthropic em semanas sinaliza mudança de fundação — relevante para qualquer proxy/ferramenta própria (LiteLLM, wrappers) que pinne `httpx`.
- **Docs estruturadas viram contexto de máquina**: migration guides pensadas para humanos estão sendo consumidas por agentes — mais um empurrão na direção de "documentação é infraestrutura".

## Frases notáveis

> "This release of the Anthropic plugin for LLM mainly provides compatibility with the recently released anthropic v1.0.0 Python library, which switches from httpx to httpx2."

> "I prompted Fable 5 in Claude Code with: 'Upgrade to anthropic>=1 - read [MIGRATION.md] and get the tests passing'."
