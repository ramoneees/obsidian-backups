---
title: "Gemini Decisions API"
source: "https://simonwillison.net/2026/Nov/11/gemini-decisions-api/"
date: 2026-11-12
tags: [ia, llm, decision-models, gemini]
---

Google entrou na categoria "decision models" com o Gemini Decision 1, seguindo Jev e OpenAI. A ideia é provocativa: um modelo que não gera texto — só responde perguntas. Três formatos: sim/não, escolha entre opções, e avaliação por rubrica. A API é quase idêntica à da Jev, tanto que até reutiliza o termo "Noul" para questões de sim/não.

O preço é o mesmo do GPT-6 Luna decision model: 10 centavos por milhão de tokens de entrada, e saída é de graça (porque não há saída em texto). A Jev continua a mais barata das três, a 4,2 centavos por milhão. A diferença está no alcance: Jev só aceita texto e JSON, OpenAI aceita texto e imagens, e o Gemini Decision 1 é totalmente multimodal — texto, imagens, áudio, vídeo e PDFs.

Willison testou com vídeo, passando perguntas simples ("esse vídeo tem um dragão?") junto de um arquivo. Detalhe interessante: Jev e OpenAI retornam 1.0 ou 0.0 sem rodeio, mas o Gemini insiste em ser menos confiante — devolve probabilidades suaves tipo 0.92 e 0.05. Calibração versus decisão seca: três fornecedores, três filosofias de incerteza.

A categoria em si é o que importa. Em vez de pagar um LLM grande para escrever parágrafos e extrair a resposta de dentro deles, uma classe nova de modelos minústicos e baratos só classifica: um cheque por milésimo de centavo. É a commodity-ficação do "sim ou não" — e abre espaço para pipelines de triagem massivos onde 95% do trabalho é decisão binária.

## Por que importa

- Faz sentido pro seu stack LiteLLM: classificadores baratos podem assumir triagem (é fatura? é spam? é urgente?) sem queimar tokens de modelo pesado.
- O conflito de calibração (1.0/0.0 vs. probabilidades suaves) é o tipo de detalhe que decide arquitetura quando se encadeia decisões.
- Mais um sinal de que o futuro do LLM em produção é enxuto: modelos especialistas e baratos fazendo o trabalho chato, modelos pesados só onde precisam.

## Frases notáveis

> "Google joins Jev and OpenAI in the decision model category with 'Gemini Decision 1'. This new model API is almost identical to Jev: it supports the same three types of questions (yes/no, choice, and rubric-scoring)."

> "Jev and OpenAI both return 1.0 or 0.0 for yes/no questions, but Gemini insists on being a little less confident than that."
