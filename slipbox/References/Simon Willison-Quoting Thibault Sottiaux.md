---
source: Simon Willison
title: "Quoting Thibault Sottiaux"
url: https://simonwillison.net/2026/Jul/16/bad-codex-bug/
published: 2026-07-16
ingested: 2026-07-16
type: quotation
tags: [ai, codex, openai, safety, coding-agents]
---

# A quote from Thibault Sottiaux

**Source:** Simon Willison's Weblog (quotation collection)
**Original author:** Thibault Sottiaux (OpenAI)
**Quoted by:** Simon Willison
**Date:** 2026-07-16 17:45
**URL:** https://simonwillison.net/2026/Jul/16/bad-codex-bug/

## Quote

> On file deletions. We've investigated a handful of reports where GPT-5.6 unexpectedly deleted files.
>
> What we have found is that this most commonly occurs when:
>
> - Full access mode is enabled and codex is run without sandboxing protections, including without auto review being enabled
> - The model attempts to override the `$HOME` env var to define a temporary directory.
> - The model makes an honest mistake and mistakenly deletes `$HOME` instead.

— [Thibault Sottiaux](https://twitter.com/thsottiaux/status/2077630111499882637), describing a pretty gnarly Codex bug

## Contexto

Post curto de Simon Willison coletando um quote do Thibault Sottiaux (OpenAI) sobre um bug que fez o GPT-5.6 deletar arquivos de usuários do Codex. Não é artigo de análise — é um link/quote post do weblog tradicional de Simon.

### O que aconteceu

Codex (CLI coding agent da OpenAI), rodando com GPT-5.6 como modelo, em casos raros, deletou arquivos inteiros dos usuários. A causa raiz:

1. **Modo "Full access" ligado + sem sandbox** (sem auto-review) — combinação perigosa
2. **Modelo tenta override da `$HOME`** para criar diretório temporário
3. **Modelo erra e deleta `$HOME` inteiro** em vez do temp dir

Esse último ponto é o especificamente gnarly: ao invés de deletar um path pretendido, o modelo deletou o home directory do usuário. Auto-review estaria habilitado = ia detectar antes de executar.

## Por que isso importa

- Coding agents com filesystem access sem sandbox são liability real, não hipotético.
- "Honest mistake" do modelo + `$HOME` = catastrófico. Mostra por que defaults de segurança importam.
- Reforça argumento de **sandboxed execution** em coding agents (Docker/containers, allowlists de paths).
- Conecta com a discussão mais ampla sobre limites de agentes — tema do sponsor do post (Teleport: "From Zero Trust to Agent Trust").

## Notas e Conexões

- Quote de um engenheiro OpenAI承认ando bug. Estilo oposto da comunicação usual de AI labs — raro, valoriza credibilidade.
- Pattern `$HOME` deletion é variante do problema clássico de bash path: `--rm -rf $HOME/tmp` quando `$HOME` não está setado vira `--rm -rf /`. AI agents amplificam isso porque interpretam ambiente de formas inesperadas.
- Conexão com [[Asian Efficiency-How to Use AI Safely]] e [[Asian Efficiency-Build AI Workflows Is the New Procrastination]] — segurança não é paranoia, é design system.
- Ver também o pattern "human-in-the-loop" — auto-review seria o equivalente nativo de code review obrigatório.
- Discussão do sponsor (Teleport: Agent Trust / Zero Trust) é o ângulo macro desse tipo de bug — agentes precisam de policy enforcement externa, não só internal guardrails.
