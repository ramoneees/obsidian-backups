---
title: "There's No Limit to How Bad Code Can Get"
source: https://zachkehs.com/blog/theres_no_limit_to_how_bad_code_can_get/
date: 2026-09-06
tags: [software-engineering, technical-debt, metaphors, ai]
---

Ensaio de Zach Kehs (ex-Amazon), destacado por Simon Willison em 6/set. A tese: metáforas físicas para codebases podres — "navio afundando", "prédio prestes a desabar" — são falsas e perigosas, porque implicam um fim. Software não tem fim: o código pode piorar infinitamente, sempre cabe mais uma camada de indireção, sempre dá para perder mais performance. Um prédio desaba; um codebase fica num "estado de colapso permanente" sem nunca desabar de vez.

Kehs conta sua experiência num sistema de processamento de pedidos da Amazon que deveria exigir ~24 engenheiros e consumia centenas. Conhecimento institucional erodido, "cemitérios assombrados" de código que ninguém ousava tocar, regras de negócio que só existiam na cabeça de gente que já saiu. E o ciclo clássico: chega um líder novo, declara que "as coisas estão ruins", a re-arquitetura falha por falta de tempo político para entender o sistema, os restos são enxertados na arquitetura, o líder sai promovido. O headcount inchado fica para sempre.

O ponto mais afiado: dívida técnica não tem falência. Dívida financeira tem reset forçado; software quase nunca tem (rewrite completo é notoriamente ruim, e o "side-channel" — um sistema novo desconectado — não limpa nada, só adiciona a dor de decidir qual usar). Quem acredita que existe uma escotilha de fuga toma decisões piores hoje. E não, LLMs não mudam isso: é o negócio que morre muito antes de o código atingir qualquer piso hipotético.

## Por que importa
- **Delegação total de coding ao OpenCode exige isso**: agentes geram código em volume industrial — sem disciplina de review e dogfood QA, o "colapso infinito" acelera. O balde é seu, não do agente.
- **Anti-visionário por excelência**: valida seu princípio "reset-over-patch" e "gastar agora < manter depois" — não existe rewrite salvador no horizonte, então qualidade se impõe a cada commit.
- **Doc << código**: Kehs descreve exatamente o "living document" esperançosamente desatualizado; a verdade só vive no código executável.

## Frases notáveis
> "Software faces no such constraint. The code can *always* get worse. There can *always* be a new layer of indirection or a reduction in performance."

> "Software will only stay high quality if we put in the effort to stop the sinking. Grab a bucket."
