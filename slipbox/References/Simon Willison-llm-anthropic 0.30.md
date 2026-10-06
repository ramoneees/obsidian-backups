---
title: "llm-anthropic 0.30"
source: Simon Willison
date: 2026-09-28
url: https://simonwillison.net/2026/Sep/28/llm-anthropic/
author: Simon Willison
category: Release
tags: [llm, anthropic, cli, ferramentas, token-counting]
ingested: 2026-10-06
---

# llm-anthropic 0.30

**Fonte**: Simon Willison
**Data**: 2026-09-28 . **URL**: https://simonwillison.net/2026/Sep/28/llm-anthropic/

> "— LLM access to models by Anthropic, including the Claude series"

## Resumo

Release do plugin Anthropic para o `llm`: além de adicionar o Claude Sonnet 5.5, a versão 0.30 traz duas mudanças de usabilidade que eliminam o atrito de manutenção. `llm anthropic refresh` atualiza a lista de modelos direto da API da Anthropic — sem precisar de release nova a cada modelo lançado. E `llm anthropic count` usa a API gratuita de contagem de tokens para dizer quantos tokens um prompt vai consumir *antes* de enviá-lo.

## Ideias principais

- **Fim do "release para adicionar modelo"**: refresh puxa o catálogo da API — o plugin deixa de ser gargalo entre o lançamento de um modelo e o suporte na CLI. Padrão inteligente para qualquer wrapper de API de modelos.
- **Token counting pré-voo**: saber o custo do prompt antes de enviar muda a ergonomia de montar contextos grandes (anexar arquivos, templates) — vira engenharia em vez de tentativa e erro.
- O `llm` continua sendo a cola CLI padrão para acessar modelos locais e remotos com a mesma interface.

## Notas e conexoes

- Ferramenta direta para a bancada do Boss: contagem de tokens pré-voo é útil para os prompts do Hermes/kanban e para orçar contexto antes de rodar em modelo pago.
- [[slipbox/References]]
