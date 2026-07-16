---
source: Simon Willison
title: "Inkling: Our open-weights model"
url: https://simonwillison.net/2026/Jul/16/inkling/
published: 2026-07-16
ingested: 2026-07-16
type: link-blog
tags: [ai, llm-release, open-weights, thinking-machines, multimodal]
---

# Inkling: Our open-weights model

**Source:** Simon Willison's Weblog (link blog)
**Original:** Thinking Machines Lab (Mira Murati's company)
**Posted:** 2026-07-16 15:35
**URL (Simon):** https://simonwillison.net/2026/Jul/16/inkling/
**URL (original):** https://thinkingmachines.ai/news/introducing-inkling/

## TL;DR

Thinking Machines Lab (Mira Murati) lançou seu primeiro modelo **open-weights**: Inkling. Mixture-of-Experts de 975B parâmetros totais (41B ativos), Apache-2.0, multimodal (texto, imagem, áudio, vídeo), treinado em 45T tokens. Tem também Inkling-Small prometido (276B, 12B ativos), mas os pesos serão lançados "quando o trabalho estiver completo."

## Pontos Principais (via Simon)

### É um "base model", não um frontier model

A própria Thinking Machines admite: Inkling "não é o modelo mais forte disponível hoje, aberto ou fechado." Em vez disso, é um **base model forte para fine-tuning** via plataforma Tinker da empresa.

> "Inkling is not the strongest overall model available today, open or closed. Instead, a combination of qualities makes it a good open-weights base for customization: multimodal capabilities, efficient thinking, and availability on Tinker for fine-tuning."

### Por que isso é significativo

- **Apache-2.0 license** (não restrictive como Llama Community License)
- **Competitivo com modelos chineses open-weights** segundo Simon — boa adição ao ecossistema US, juntando NVIDIA Nemotron e Gemma 4 como alternativas abertas
- Multimodal nativo (raro em open weights)

### Documentação: notavelmente curta

[Model card](https://thinkingmachines.ai/model-card/inkling/) é "muito mais curto do que eu esperaria de labs americanos." Link para [Training Data Documentation](https://thinkingmachines.ai/training-data-documentation/) ainda mais seco. Resumo honesto:

> The datasets Thinking Machines Lab uses to develop its AI services includes content that is in the public domain as well as content that may be subject to intellectual property protection.
>
> Thinking Machines Lab's services were developed using publicly available content obtained from the open internet and publicly accessible data repositories. Certain datasets were also obtained from third parties.

Tradução: "usamos conteúdo público, e algumas fontes foram obtidas de terceiros." Vago. Sem lista de datasets, sem proporções, sem filtros explicitados. Críticos verão isso como evasão.

## Pelican Test (Simon sendo Simon)

Simon testou com o clássico prompt "Generate an SVG of a pelican riding a bicycle" via API da Tinker. Output completo em [gist](https://gist.github.com/simonw/8117ac4376371dd3fc2b5dbce27e0855).

A imagem resultante (pelican sobre bicicleta) Simon renderizou para JPEG, depois pediu ao modelo para descrevê-la (testando multimodal em loop fechado). O modelo identificou a si mesmo como "stork or seagull" — não percebeu que era pelican.

> "This is a cheerful, flat-vector cartoon illustration featuring a white bird riding a bicycle across a green landscape."

Análise detalhada da imagem correta, só errou a espécie. Comportamento típico de modelo multimodal atual: bom em descrever, fraco em classificação fina de espécie (especialmente quando o próprio output alimenta o input).

## Pricing/Access

- Modelo principal já disponível via [Tinker API](https://tinker.thinkingmachines.dev/)
- Pesos disponíveis open-weights (download provavelmente em HuggingFace ou similar)
- Inkling-Small: pesos prometidos para "quando trabalho estiver completo"

## Notas e Conexões

- **Murati's lab** — fundada pós-saida dela da OpenAI em 2024. Primeiro release público.
- **Open-weights vs open-source** nuance: Simon explicitamente usa "open-weights" (não open-source). Pesos disponíveis, mas dados de treino não documentados claramente. Discussão eterna.
- **Apache-2.0 license** é strong pro. Llama Community License tem restrictions comerciais; Mistral tem cases. Apache-2.0 = basically sem fricção para uso comercial.
- **Documentação vaga é yellow flag** — não é dealbreaker, mas vale monitorar quando Tinker publicar mais sobre pretraining data.
- **Base model para fine-tuning** posiciona Inkling como complemento, não competidor direto de GPT-5.6 ou Claude Opus. Estratégia interessante: ser o "engine" que outros customizam, não o "finished product".
- Conexão com [[Asian Efficiency-How to Use AI Safely]] — open-weights local é uma das formas mais seguras de rodar modelos para trabalho sensível (sem passar por servidores de terceiros).
- Pelican test tradition do Simon é referência fixa — ver também sqlite-utils posts dele.
