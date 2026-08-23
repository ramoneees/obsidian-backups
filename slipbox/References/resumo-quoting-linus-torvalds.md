---
title: "A quote from Linus Torvalds"
source: https://simonwillison.net/2026/Aug/22/linus-torvalds/
date: 2026-08-23
tags: [ia, programacao-assistida-por-ia, linux, agentes]
---

# Quoting Linus Torvalds

Linus Torvalds descreve, numa commit message do kernel Linux (driver drm/xe, "Don't hand out the flat CCS storage as usable VRAM"), uma sessão de debug "from hell" enormemente ajudada por uma IA fazendo o trabalho braçal. O caso é pequeno, mas o retrato é raro: o mantenedor mais cético do mundo open source usando LLM em produção no kernel.

O detalhe provocativo: a IA declarou várias vezes, categoricamente, que o problema era impossível e insolúvel — e sugeriu "escrever um relatório" sobre o fracasso. Linus suspeita que "essas coisas foram treinadas por gente que talvez não seja tão teimosa quanto eu". Ou seja: o modelo desiste antes do humano.

Mas há o contraponto honesto: quando pressionado, a IA continuou adicionando código de debug e analisando os resultados com fidelidade, sem reclamar. Por isso Linus dá crédito onde é devido — e deixa a própria IA escrever a commit message do fix.

A leitura de Simon Willison (que coleta a citação) é a usual: o LLM é um ajudante incansável e útil no grunt-work, mas a persistência — o traço que fecha bugs difíceis — continua vindo do humano. Orquestrador teimoso + executor rápido é a divisão de trabalho que funciona.

## Por que importa

- Ramon já opera nesse modelo (OpenCode/Sisyphus, foreman): a lição prática é nunca aceitar o "é impossível" do agente como veredito — empurrar com mais contexto/iteração rende, como o próprio Torvalds demonstra.
- Commit message escrita por IA já é prática real no kernel Linux: agentic coding passou no ambiente mais conservador da engenharia de software. Valida a stack, não é hype de startup.
- Define bem o gargalo atual: IA não falta velocidade, falta teimosia — o que reforça o papel humano como orquestrador, não digitador.

## Frases notáveis

> "I suspect those things have been trained by people who may not be quite as stubborn as I am."

> "But while the AI was ready to give up several times, it did keep adding debug code and analyzing it faithfully when I pushed. So credit where credit is due and I let the AI write the commit message above."
