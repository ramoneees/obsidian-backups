---
title: "llm-gemini 0.37"
source: "https://simonwillison.net/2026/Nov/12/llm-gemini/"
date: 2026-11-13
tags: [ia, llm-pricing, gemini, ferramentas]
---

Simon Willison atualiza o plugin llm-gemini para acompanhar o lançamento do Gemini 4 Hydrogen, o membro mais barato da família Gemini 4. O post é curto, mas o verdadeiro conteúdo é a autópsia da precificação do Google — que ele mesmo admite não entender. Carbon e Argon custam exatamente o mesmo ($2/M input, $10/M output até 30/11) e dobram de preço em 1º de dezembro. Se dois modelos têm o mesmo preço, por que existem os dois? A resposta do Google: Argon "usa menos tokens por tarefa" — o desconto não está na tarifa, está no consumo.

O "barato" Hydrogen ($1,50/$7,50 por milhão) hoje dá só 25% de desconto sobre os irmãos maiores; o desconto de 75% só faz sentido depois do dia 1º, quando Carbon/Argon dobrarem. E mesmo assim Hydrogen continua 15x mais caro que Claude Haiku 5.5 e GPT-6 Luna ($0,10/$0,50). Willison fecha com seu teste canônico — pelicanos em SVG — mostrando que Hydrogen gera resultados visivelmente mais pobres a cada nível de effort, apesar da diferença de preço pequena.

O posicionamento declarado do Google é revelador: Hydrogen é o "modelo de execução" para código do dia a dia (escrever, rodar testes, verificar), enquanto Carbon/Argon ficam para "julgamento arquitetural profundo". Hydrogen também é o novo modelo do free tier e o que vai alimentar os recursos de IA no Google Search. Ou seja: o barato virou o default de massa, não uma alternativa séria para quem paga.

## Por que importa

- Você roteia 46 modelos num LiteLLM VPS — a lição prática é que "preço do modelo" engana: Argon vs Carbon mostra que o custo real vem de tokens por tarefa, não da tarifa. Rota barata que desperdiça tokens perde para rota cara que é enxuta.
- O padrão "modelo de execução vs modelo de julgamento" é exatamente a arquitetura que você já usa (pesado→GLM, visão→flash). O Google está formalizando o que o mercado de routing já pratica — e o double-pricing com dobragem em dezembro é tática clássica de ancoragem.
- Se algum fluxo teu usa Gemini, 1º de dezembro dobra o custo de Carbon/Argon. Vale reavaliar rotas antes dessa data.

## Frases notáveis

> "I'm finding Gemini 4's pricing really confusing. [...] If they're the same price, why have two different models?"

> "Hydrogen is built to stand on its own as a model for everyday work — or to pair with Carbon and Argon as the high-efficiency execution engine in multi-model workflows." (Google, citado por Willison)
