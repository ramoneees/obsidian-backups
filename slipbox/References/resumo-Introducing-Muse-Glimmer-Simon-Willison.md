---
title: "Introducing Muse Glimmer"
source: https://simonwillison.net/2026/Aug/10/introducing-muse-glimmer/
date: 2026-08-11
tags: [ia, llms, local-llms, meta, vision-llms]
author: Simon Willison
---

# Introducing Muse Glimmer

## Resumo

Meta voltou ao jogo de pesos abertos — e com estilo. O **Muse Glimmer** é um modelo de 30B parâmetros sob **Apache 2.0**, licença limpa (não as Llama-janky de antes), otimizado exatamente para o que Simon Willison — e qualquer pessoa que roda agentes localmente — quer: conclusão end-to-end de tarefas agentic (DeepSearch QA, MCP-Atlas, τ-Bench, SWE-Bench), uso de ferramentas com schemas precisos em workflows longos, e raciocínio multi-passo sustentado. Não é só mais um modelo bom em benchmarks: é um modelo que você consegue *usar*.

Willison testou em três frentes. **Primeiro**, gerou um pelicano (obrigatório, é o marcador da casa) via LM Studio com a versão de 18.16 GB — resultado: as peças estão lá, mas meio embaralhadas. **Segundo**, rodou contra um checkout fresco do Datasette com o prompt "how does auth work?" usando seu plugin `llm-coding-agent`: o modelo encadeou tool calls explorando o código de verdade, não fingindo. **Terceiro**, como Glimmer é vision, pediu descrição de uma foto de pelicanos em rochas — resposta detalhada e correta, com identificação de espécie (*Pelecanus occidentalis*) e plumagem.

O argumento prático: 30B é o sweet spot. Em uma máquina com 32 GB de RAM cabe o modelo + sobra pra outras aplicações; em 128 GB sobra bastante. Pela primeira vez em muito tempo, Meta entrega algo que ameaça tanto o ecossistema fechado de frontier labs quanto o nicho de modelos pequenos specialized — porque é aberto, competente em agentes, e barato de rodar.

## Por que importa

- Para quem trabalha com **devops + IA**, Muse Glimmer é candidato imediato a drop-in em pipelines locais de automação, classificação e agents — substitui Llama 3.1 70B em muitos casos com menos RAM e licença limpa.
- A migração Anthropic/OpenAI pra inferência fora do CUDA (que o artigo da Stratechery cobre) ganha concretude aqui: **a fronteira de "modelo útil rodando local" subiu**, e isso é estruturalmente ameaçador pro modelo de negócio de Nvidia.
- Vale o teste prático: o protocolo de Willison (gerar pelicano + descrever imagem + resolver problema de código em repo real) é um excelente **smoke test** pra qualquer modelo novo — replicável em ~10 minutos.

## Frases notáveis

> "Meta are back in the open weights game! Muse Glimmer is a brand new 30B model under a clean Apache 2.0 license (a step up from the janky Llama licenses of old)."

> "I really like this size of model, because if a machine has 32 GB of RAM or more (mine has 128GB) it leaves plenty of space for running other applications at the same time."
