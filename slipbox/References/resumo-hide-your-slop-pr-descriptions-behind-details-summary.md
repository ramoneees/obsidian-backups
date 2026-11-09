---
title: "Hide your slop PR descriptions behind <details><summary>"
source: https://simonwillison.net/2026/Nov/9/details-summary/
date: 2026-11-09
tags: [ai-assisted-programming, coding-agents, github, workflow]
---

Simon Willison resolveu um problema que qualquer um que roda coding agents reconhece na hora: PRs escritas por agentes são precisas, completas — e ilegíveis. A descrição cobre problema, solução detalhada e passos de verificação, e o efeito na prática é o mesmo do "slop" de IA: ninguém lê. A ironia é que a informação está correta; é o volume que mata a atenção do revisor.

A solução dele é quase ofensivamente simples: o GitHub Markdown suporta `<details><summary>`, então ele escreve (ou destila) um parágrafo curto de abertura com julgamento humano — o mínimo que o revisor precisa saber para decidir se o PR merece atenção — e enterra o resto do ensaio do agente dentro de um bloco colapsado. O `summary` do bloco carrega o nome do modelo e o nível de esforço ("Claude Opus 5.5 Medium"), deixando explícito quem escreveu aquilo. Às vezes abre com screenshot, porque imagem ilustra feature melhor que prosa.

O ponto provocativo: Willison se compromete publicamente com uma promessa editorial — o parágrafo de abertura representa juízo humano sobre o que vale o tempo do leitor. O agente produz o volume; o humano produz a curadoria. Ele nem sempre escreve a abertura do zero — às vezes o agente já a deixou pronta, escondida na avalanche de texto, e cabe a ele reconhecê-la e promovê-la.

É um padrão aplicável hoje, sem ferramenta nova, em qualquer repo — inclusive nos fluxos onde agentes abrem PRs em série e o dono do repo vira gargalo de leitura.

## Por que importa

- Ramon delega praticamente todo o coding a agentes (OpenCode/Sisyphus, PRs como unidade de trabalho) — esse padrão organiza exatamente o gargalo seguinte: ler e revisar o que os agentes produzem.
- Custo zero de adoção: é só Markdown em PR description, funciona no GitHub e qualquer renderer compatível — dá para padronizar nos templates de PR dos projetos (precisase, pack, tend).
- A promessa editorial ("o opener é curadoria humana") é uma política de review interessante: separa o que o agente escreveu do que o humano endossa.

## Frases notáveis

> "It doesn't matter how accurate or useful the information is, I'm instantly put off by the thought that it will take me longer to read than it took the driving author to write... even when that driving author is me!"

> "My promise to the reader is that the short opener will represent my human judgement as to what is definitely worth their time."
