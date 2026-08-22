---
title: "llm 0.32.1"
source: "https://simonwillison.net/2026/Aug/21/llm/"
date: 2026-08-22
tags: [devops, llm, python, dependencias]
---

# llm 0.32.1

**Resumo**

Nota curta e cirúrgica de Simon Willison: instalações novas do LLM (o CLI dele para acessar LLMs via terminal) pararam de funcionar porque a biblioteca Python da OpenAI removeu o uso do `httpx` — e o LLM dependia do `httpx` apenas como dependência transitiva do `openai`, nunca declarada diretamente. O dot-release 0.32.1 aplica o pino `openai<3` como band-aid; o 0.33, "em breve", migra de `httpx` para `httpx2` (o fork sob guarda da Pydantic).

O caso é um exemplo didático perfeito de fragilidade de cadeia de dependências: seu código quebra não pelo que você declarou, mas pelo que uma lib de terceiros resolveu deixar de usar internamente. Dependência transitiva não declarada é dependência invisível — até o dia em que ela some.

Para quem roda tooling de IA em CLI (o setup do Boss usa LiteLLM como ponte), a lição operacional é dupla: pino explícito quando a estabilidade importa, e dot-releases de correção são o mecanismo certo para conter sangramento enquanto a migração de verdade é preparada.

## Por que importa

- O setup local do Boss (LiteLLM, pontes, scripts de imagem) depende exatamente desse tipo de cadeia Python — vale conferir se há dependências transitivas não declaradas em produção.
- É o padrão "migração em dois tempos" (band-aid pino → rewrite na minor seguinte) aplicado a maintainers de ferramenta pública — bom template para o versionamento do tend/pack.
- httpx2 sob guarda da Pydantic sinaliza a consolidação do ecossistema de HTTP clients Python pós-fragmentação — movimento que afeta qualquer stack que fala com APIs de modelo.

## Frases notáveis

> "Fresh installs of LLM stopped working the other day because the OpenAI Python library dropped its usage of `httpx`, and it turned out LLM depended on that library but only installed it via a transitive `openai` dependency."

> "A soon-to-drop 0.33 release will switch from `httpx` to `httpx2`."
