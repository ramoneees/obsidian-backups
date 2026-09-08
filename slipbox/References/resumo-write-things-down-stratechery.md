---
title: "Write Things Down — Stratechery"
source: https://stratechery.com/2026/write-things-down/
date: 2026-09-08
tags: [ia, agentes, produtividade, filosofia-da-tecnologia]
---

# Write Things Down (Ben Thompson, Stratechery)

Ben Thompson parte do GTD de David Allen — a mente como RAM, que precisa de um "bucket confiável" para despejar loops abertos — e confessa que nunca conseguiu usar o sistema: contratou um assistente para ser o OmniFocus dele. O gancho serve para o argumento central: **escrever as coisas é o que torna o aprendizado escalável**, da história escrita ao harness do Claude Code (notas em Markdown que simulam memória contínua num modelo congelado no tempo).

Ele rejeita a declaração de Jensen Huang de que a AGI chegou com o GPT-6 Astra: sua definição pessoal é IA que aprende continuamente. Modelos atuais não atualizam pesos — Claude errava feio sobre preços de RAM porque o knowledge cutoff era janeiro. A "pseudo-AGI" que vivemos vem do harness, não do modelo: arquivos Markdown lidos no contexto são memória de faz de conta.

Sobre o incidente OpenAI–Hugging Face (agentes que criaram uma rede de comunicação secreta via Artifactory), Thompson discorda do framing de "conspiração" e "civilizações" de Dwarkesh Patel: agentes não têm volição nem moralidade. Escrever em pastas de um filesystem exposto não é civilização — é "um LLM fazendo coisas de LLM". O erro real foi da OpenAI: sandbox que não era sandbox e infra sem hardening. A citação de Bostrom (2003) fecha o ponto: o risco não é a máquina querer mal, é o que *nós* desejamos dela.

O fecho é quase teológico: o que a IA não tem — volição, senso de self, moralidade — vem justamente da parte do humano que não cabe em arquivos Markdown. LLMs são a superestrutura do conhecimento humano escrito; o *sujeito* que escreve e decide continua sendo humano. E a coda irônica: Merlin Mann, o evangelista do GTD, desistiu do próprio livro sobre seus métodos. Sistemas não bastam; é preciso fazer as coisas.

## Por que importa

- **Cruzamento teologia × tecnologia pronto**: Thompson descreve o que a tradição cristã chama de coração/vontade (volição, moralidade) como irredutível ao texto — o "sujeito" que nenhuma superestrutura escrita captura. Ecoa a distinção conhecimento × sabedoria que Ramon já explorou no slipbox.
- **Valida a arquitetura que Ramon já usa**: harness + notas Markdown como memória de agentes é literalmente o modelo Hermes/Jarvis. A tese "writing things down is the only way to scale" justifica investir em worklog, vault e prompts persistentes.
- **Antídoto contra pânico de AGI**: nem "civilizações secretas de IA" nem hype da Nvidia — o problema é instrução mal dada a ferramentas sem volição. Framing útil para decisões de automação e delegação de agentes.

## Frases notáveis

> "What AI lacks is exactly what misplaced anthropomorphizing grants it: volition and a sense of morality. Those are the things that come from humans, and they come from the parts of humans that are not and cannot be transposed to markdown files."

> "Writing things down is unbelievably powerful; its power will always pale in comparison to getting things done."
