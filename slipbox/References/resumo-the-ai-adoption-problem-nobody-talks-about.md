---
title: "The AI Adoption Problem Nobody Talks About (And the Simplest Fix I've Found)"
source: https://www.asianefficiency.com/technology/the-ai-adoption-problem-nobody-talks-about-and-the-simplest-fix-ive-found/
date: 2026-06-10
tags: [ia, automacao, devops, adocao-tecnologica, asian-efficiency]
---

# The AI Adoption Problem Nobody Talks About

Thanh von Asian Efficiency nomeia o ponto cego que toda implementação de IA enfrenta: a tecnologia funciona tecnicamente, mas as pessoas não usam. O modo de falha quase nunca é "o modelo é ruim" — é que o sistema exigiu mudança de comportamento e comportamento não mudou. Toda nova ferramenta é um imposto cognitivo: novo login, novo processo, novo formulário. Sem onboarding constante, a adoção morre em abandono silencioso.

A tese central é provocativa: **ferramentas que vencem são as que se encaixam em como as pessoas já trabalham**, não as que pedem algo diferente. O caso emblemático é o trigger de e-mail customizado do Lindy — cada workflow recebe um endereço único (ex.: `expenses@empresa.lindy.ai`). O usuário só encaminha um e-mail; o agente lê, categoriza e atualiza o registro. Zero treinamento, zero app novo, zero mudança de hábito — a interface é um gesto que a pessoa já faz.

O padrão se generaliza: o que está na inbox da pessoa é input natural. Inquirições de cliente viram registros de CRM; notas fiscais viram lançamentos contábeis; pedidos de equipe viram tickets — tudo via forward de e-mail. A lição é de design organizacional: **encontre a ação que a pessoa já executa e transforme essa ação no trigger**. A IA não precisa de uma revolução de processo, precisa de um hook comportamental.

A analogia de "meet people where they are" também aparece no caso do Hudson, que mandava fotos de recibos via iMessage para o assistente — o telefone já estava na mão, o app já estava aberto, bastou plugar.

## Por que importa

- Para o Ramon em devops/automação: a métrica real de um sistema não é uptime nem acurácia, é **aderência humana**. Pega direto em pipelines de CI/CD, runbooks, SRE — quantas vezes ele implantou uma automação que morreu porque ninguém seguia o procedimento?
- O pattern "trigger no canal existente" é a versão AI-first do princípio UNIX de composabilidade. Em vez de criar uma nova superfície de interação (UI, app, dashboard), reusa o canal que já transporta 90% da informação do time: e-mail.
- Aplicação prática imediata: revisar os workflows de IA dele e perguntar "qual trigger eu já tenho rodando sem fricção?" — qualquer ferramenta nova deve ser avaliada por esse critério antes de ser comprada.

## Frases notáveis

> "There's a version of AI implementation that works technically and fails practically. The tool does exactly what it's supposed to. The automation runs cleanly. The output is good. And nobody uses it."

> "Find the action people already take and make it the trigger."
