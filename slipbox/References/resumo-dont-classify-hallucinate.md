---
title: "Don't classify. Hallucinate!"
source: https://softwaredoug.com/blog/2026/08/10/hypothetical-classifications
date: 2026-08-15
tags: [IA/ML, embeddings, LLM, automação]
---

# Don't classify. Hallucinate!

Doug Turnbull descreve um padrão elegante para classificação com LLMs que inverte a abordagem tradicional. Em vez de usar structured outputs para forçar o modelo a escolher entre centenas de categorias legais pré-definidas (o que exige enviar um schema gigante e tem limite de tamanho), você pede a um modelo barato e "burro" para *inventar* classificações plausíveis. Depois usa embeddings vetoriais para casar a classificação alucinada com a categoria real mais próxima do seu catálogo.

O problema clássico: classificar uma query como "brown coffee table" em uma taxonomia de e-commerce com 500+ categorias. A abordagem com structured outputs funciona, mas é cara — você envia a lista inteira de valores legais a cada chamada e fica limitado pelo tamanho máximo do schema. Turnbull mostra que isso é desnecessário.

A solução é brilhante na sua simplicidade. O prompt pede ao LLM para gerar classificações "novel, never seen before" no formato correto, sem conhecer a taxonomia real. O modelo produz algo como "Furniture / Living Room / Tables / Coffee" — que não existe no catálogo. Mas semanticamente está perto. Aí entra a segunda etapa: embeddings MiniLM das categorias reais, pré-computados em memória, e um dot product simples encontra a correspondência mais próxima. O resultado sai correto: "Furniture / Living Room Furniture / Coffee Tables & End Tables / Coffee Tables".

A vantagem prática é dupla: você usa modelos menores e mais baratos (não precisa de um modelo que conheça todo o vocabulário) e não transmite o schema inteiro a cada chamada. É um padrão que escala melhor para taxonomias grandes e mudam com frequência.

## Por que importa

- **Padrão aplicável a qualquer sistema de automação com LLM** — sempre que houver um vocabulário controlado (tags, categorias, labels), a técnica de "alucinar e depois resolver via embeddings" é mais barata e mais flexível que structured outputs.
- **Decisão de arquitetura relevante para devops/ML** — separa a geração semântica (LLM barato) da validação estrutural (busca vetorial), o que é mais resiliente a mudanças de taxonomia e mais fácil de manter.
- **Conecta dois mundos do seu stack** — LLMs para linguagem natural + busca vetorial para matching determinístico. É exatamente o tipo de cruzamento entre técnicas que tende a aparecer em pipelines reais de IA.

## Frases notáveis

> "Just ask a dumb LLM to invent plausible, fake classifications for your query."

> "It'll then make up some BS that doesn't actually exist in your real taxonomy. Well that's not very helpful. Actually it's extremely helpful."
