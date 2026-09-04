---
title: "GPT-6 Astra"
source: https://simonwillison.net/2026/Sep/3/gpt6-astra/
date: 2026-09-04
tags: [ai, openai, llm, benchmarks]
---

Simon Willison faz a leitura fria e técnica do lançamento do GPT-6 Astra, o novo modelo de fronteira da OpenAI. O posicionamento é claro: é o concorrente direto da OpenAI ao Claude Fable, com preço de API idêntico ($10/milhão de tokens de entrada, $50/milhão de saída) e pontuação superior na maioria dos benchmarks autorreportados pela própria OpenAI.

O destaque mais impressionante — e mais contestável — é o ARC-AGI 3: 99,9%. Mas Willison aponta a pegadinha: esse resultado foi obtido com um harness customizado da OpenAI ("Provider Adapter harness") que preserva estado de raciocínio opaco entre requisições, custando $19K. Com o harness padrão do ARC-AGI, o modelo marcou 62,7% por $26K. Ou seja: o número headline depende criticamente da infraestrutura de orquestração, não só do modelo.

Astra é também descrita como uma "fera" em tarefas de segurança — reflexo do incidente Hugging Face. Marca 100% no ExploitBench (vs 78,5% do GPT-5.6 Sol), 42,4% no ExploitGym e 99,2% em engenharia reversa binária no SRE-Bench. E resolve um dos problemas persistentes de contexto longo: 100% no benchmark de oito agulhas a 256K–512K tokens, 96,3% a 512K–1M.

Nem tudo é vitória, porém. No Intelligence Index da Artificial Analysis, o Astra empata com o GPT-5.6 Sol (61) e fica 5 pontos atrás do Claude Fable 5.1, além de perder para o recém-lançado Muse Spark 1.3 da Meta. Onde ele se destaca em custo-benefício é no Coding Agent Index: com o mesmo custo do Sol, pontua 2 pontos acima — e custa menos da metade de um Claude Fable 5 por tarefa, para o mesmo resultado.

## Por que importa

- **Benchmarks são uma função do harness**: o contraste de 99,9% vs 62,7% no ARC-AGI conforme a infraestrutura de orquestração é um alerta permanente para quem avalia modelos — o número isolado não significa nada sem o setup.
- **Custo-benefício em coding agents**: a comparação no Coding Agent Index (metade do custo do Fable para o mesmo resultado) é dado diretamente acionável para escolher provedor de agente de código.
- **Segurança como categoria de benchmark**: o fato de um modelo de fronteira ser medido por capacidade ofensiva/defensiva (ExploitBench, ExploitGym) mostra que cyber virou eixo central de diferenciação de modelos.

## Frases notáveis

> "The Provider Adapter harness preserves opaque reasoning state between requests and uses compaction for longer conversations, allowing the model to reuse prior work."

> "Unsurprisingly, given the recent Hugging Face incident, Astra is a beast at security tasks."
