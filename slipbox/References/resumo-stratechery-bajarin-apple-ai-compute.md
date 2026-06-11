---
title: "An Interview with Ben Bajarin About Apple, AI, and Compute"
source: https://stratechery.com/2026/an-interview-with-ben-bajarin-about-apple-ai-and-compute/
date: 2026-06-11
tags: [ia, apple, compute, hardware, stratechery]
author: Ben Thompson
---

# An Interview with Ben Bajarin About Apple, AI, and Compute

Ben Thompson (Stratechery) entrevista Ben Bajarin, analista do setor de hardware, sobre dois temas quentes da semana: as movimentações da Apple após a WWDC e o estado da indústria de **compute para IA** — ou seja, a infraestrutura física (chips, data centers, energia) que sustenta a corrida dos modelos. A conversa é típica do Stratechery: densa, técnica, mas com implicações estratégicas claras para qualquer pessoa que esteja acompanhando o ciclo atual da IA.

Bajarin traz o olhar do analista de cadeia de suprimentos. A tese central é que 2026 consolidou uma divisão de papéis: os **hyperscalers** (Nvidia, Microsoft, Google, Amazon) estão construindo a base de compute que alimenta a próxima geração de modelos, enquanto Apple e Meta seguem uma rota de integração vertical focada em **inference on-device** — capacidade de rodar modelos localmente, no hardware do usuário final. As duas estratégias não competem pelo mesmo mercado: a Apple quer que o modelo rode no seu chip Neural Engine; a OpenAI/Anthropic precisam de clusters massivos de GPUs para treinar e servir modelos cada vez maiores.

A discussão sobre compute toca num ponto estratégico fundamental: a **escassez estrutural de capacidade computacional** virou a principal restrição do setor. Bajarin sugere que a maioria das empresas subestima o tempo de maturação de novos data centers (2-4 anos entre anúncio e operação) e que isso cria uma janela onde "quem tem compute, tem produto". A consequência é geopolítica: países e empresas sem acesso a chips avançados ficam presos a uma camada de middleware que os EUA controlam.

A parte sobre Apple foca no dilema estratégico da empresa: ela tem o melhor chip on-device (M-series, A-series) e a melhor base instalada, mas a WWDC mostrou que ainda não decidiu **como monetizar a IA** — se via assinatura, como OpenAI, ou via溢价 de hardware, como sempre fez. A aposta parece ser a segunda: o valor da IA aparece como feature que justifica o preço do dispositivo.

## Por que importa

- Conecta diretamente a **arquitetura de IA** (cloud vs edge, treino vs inferência) com a estratégia de produto. Para quem monta pipelines de ML, a distinção é prática: alguns workloads fazem sentido só na nuvem; outros (latência, privacidade, custo) são candidatos naturais a rodar localmente.
- A tese de **compute como gargalo estrutural** explica por que a Anthropic e a OpenAI estão levantando rodadas bilionárias e por que Nvidia continua sendo o "pá-picareta" do ciclo. Tem implicações óbvias para devops e automação: se a camada de compute está restrita, a diferenciação vai para software, integração e orquestração.
- O dilema da Apple é um caso de estudo sobre **monetização de IA**: o mesmo produto pode ser entregado como assinatura ou como feature. Para qualquer empresa construindo produto sobre LLMs, a decisão Apple vs OpenAI define go-to-market.

## Frases notáveis

> "Quem tem compute, tem produto" — a escassez estrutural de capacidade computacional virou a restrição dominante do ciclo de IA em 2026.

> A Apple aposta em inference on-device como diferencial de hardware; os hyperscalers apostam em escala massiva de treino. As duas estratégias não competem pelo mesmo mercado.
