---
title: "What's new in Claude Sonnet 5"
source: Simon Willison
author: Simon Willison
url: https://simonwillison.net/2026/Jun/30/claude-sonnet-5/#atom-everything
published: 2026-06-30
category: Link Blog
tags: [anthropic, claude, claude-sonnet-5, llm-release, llm-pricing, pelican-riding-a-bicycle, tokenization]
model: Claude Sonnet 5
docs_link: https://platform.claude.com/docs/en/about-claude/models/whats-new-sonnet-5
ingested: 2026-07-01
article_id: 903
---

# What's new in Claude Sonnet 5

**Link oficial:** https://platform.claude.com/docs/en/about-claude/models/whats-new-sonnet-5 (via Hacker News)

Claude Sonnet 5 saiu na manhã de 30 de junho de 2026. Simon prefere ir direto para docs *“what's new”* porque tendem a ter mais informação acionável que o anúncio oficial.

**Anthropic sobre Sonnet 5:** *“its performance is close to that of Opus 4.8, but at lower prices.”*

[System card](https://www-cdn.anthropic.com/9e6a1044980d8c4ed85669faf9c2a8342e2e9f1e/Claude%20Sonnet%205%20System%20Card.pdf) explica como puderam lançar sem bloqueio do governo dos EUA:

> *“Sonnet 5 is significantly less capable at cyber tasks than Mythos 5: its safeguards are thus similar to those we apply to Opus 4.7 and Opus 4.8 (models that are more capable than Sonnet 5 but much less capable than Mythos 5).”*

## Mudanças principais
- **Sampling parameters , ,  removidos.**
- **Contexto: 1 milhão de tokens**
- **Output máximo: 128,000 tokens**
- Mesmas ferramentas e platform features do Sonnet 4.6
- **Adaptive thinking on by default** (a menos que  seja especificado)
- **Preços:** mesmos do Sonnet 4.6 ($3/M input, $15/M output), com desconto introdutório para **$2/$10 até 31 de agosto**.
- ⚠️ **Novo tokenizer:** *“The same input text produces approximately 30% more tokens than on Claude Sonnet 4.6.”* — **aumento efetivo de 30% no preço**.

## Tabela de comparação de tokenização
Testes via Simon's [Claude Token Counter](https://tools.simonwillison.net/claude-token-counter):

| Documento | Sonnet 4.6 | Opus 4.7 | Sonnet 5 |
| --- | --- | --- | --- |
| Universal Declaration of Human Rights (EN) | 2,356 | 3,347 (1.42x) | 3,341 (1.42x) |
| Universal Declaration of Human Rights (ES) | 3,572 | 4,753 (1.33x) | 4,747 (1.33x) |
| Universal Declaration of Human Rights (ZH, simplified) | 3,334 | 3,366 (1.01x) | 3,360 (1.01x) |
| sqlite_utils/db.py (4,279 linhas Python) | 44,014 | 56,118 (1.28x) | 56,113 (1.27x) |

**Conclusão:** token novo é **~1.4x mais caro** para inglês, **1.33x para espanhol**, **1.28x para Python**, mesmo custo para simplified Mandarin.

> [the pelican](https://gist.github.com/simonw/a89e756b621a31e8ffc210e3428efa77). Sonnet 5 pensa que parece um ganso.

Ilustração incluída: ganso branco andando de bicicleta.

## Conexões
- Conecta com [[Simon Willison-Quoting Anthropic]] — levantada das restrições de exportação em Mythos 5 / Fable 5
- Conecta com decisão sobre usar Sonnet 5 vs Opus 4.8 para workloads específicos
- Aplique em **[[projetos]] Hermes**: ajustar estimativas de custo e contexto para Sonnet 5
- Tokenização: cuidado com cálculos de cost ao migrar de Sonnet 4.6 para 5
