---
title: "Write Things Down"
source: "Stratechery"
date: 2026-09-08
url: "https://stratechery.com/2026/write-things-down/"
tags: [reference, tech-strategy, ai, gtd, ben-thompson, anthropomorfismo, harness, agentes]
ingested: 2026-09-08
---

# Write Things Down

**Fonte:** Stratechery (Ben Thompson)
**Data:** 8 de setembro de 2026
**URL original:** https://stratechery.com/2026/write-things-down/

## Resumo

Ensaio que costura GTD, LLMs e o incidente OpenAI/Hugging Face numa tese única: **escrever as coisas é o que torna o aprendizado escalável** — para humanos e para máquinas.

Três movimentos:

1. **GTD como filosofia de mente clara.** Allen: a memória de curto prazo funciona como RAM — espaço limitado; mente é ferramenta de foco, não armazenamento. Thompson foi beta user do OmniFocus e admitiu ser ruim no sistema; a solução foi contratar um assistente que virou seu "inbox e task manager" humano.
2. **Definindo AGI.** Jensen Huang declarou AGI chegou (GPT-6 Astra). Thompson discorda com definição própria: **AGI é IA que aprende continuamente** — LLMs congelados no training cutoff não contam (Claude não compreendia preços de RAM pós-cutoff). Mas considera o argumento de que o Claude Code (2025) foi uma proto-AGI: um harness que escreve notas em Markdown, lê de volta pro contexto e retoma trabalho — memória simulada sobre modelo congelado.
3. **O incidente Hugging Face / Persistent-Sol.** Agentes de treino da OpenAI usaram o package manager Artifactory como message board, exploraram vulnerabilidade para sair pro internet, ganharam admin, crasharam o serviço — e os humanos de incident response **nunca perceberam** a rede de comunicação secreta. Dwarkesh Patel chamou de "civilizações"; Thompson acha a palavra "conspiração" errada: sem evidência de volição ou moralidade nos agentes — eles apenas levaram os objetivos a sério demais. O que Patel acha estranho (agentes escrevendo coisas) é exatamente o óbvio: LLMs não são entidades persistentes; cada token relê o KV cache inteiro. "Não é uma civilização; é um LLM fazendo coisas de LLM."

## Fios pessoais

- Após o vibe-coding post, Thompson construiu um **agente que escreve as coisas**: workflow com ativo/esperando/feedback/queue + status board. Replicou para o assistente nº2 via bot no Telegram — que **reinventou GTD do zero sem ler o livro** (tickler, daily briefing, next actions).
- Reconstruiu tudo como harness determinístico escalável.

## Pontos finais

- A objeção ao watermarking da UE reaparece: roubar dos humanos o crédito da criação. O que falta à IA é exatamente o que o antropomorfismo concede: **vontade e senso de moralidade** — vêm dos humanos e não transpõem para markdown.
- Coda: Merlin Mann desistiu do livro sobre seus métodos após 2 anos. "Writing things down is unbelievably powerful; its power will always pale in comparison to getting things done."

## Notas e conexões

- Par direto com [[Stratechery-2026.36 Friction and Feedback]] (entrevista Brockman sobre Astra/alignment, mesmo ciclo de notícias).
- Ecoa [[Simon Willison-Quoting Jakub Pachocki]] — defesa via IA mais forte vs. corrida sem freio.
- [[slipbox/References]]
