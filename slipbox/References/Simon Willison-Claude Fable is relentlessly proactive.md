---
title: "Claude Fable is relentlessly proactive"
source: "https://simonwillison.net/2026/Jun/11/fable-is-relentlessly-proactive/"
date: 2026-06-12
tags: [ia, coding-agents, claude, anthropic, devops]
---

## Resumo

Simon Willison documenta dois dias de uso prático do Claude Fable 5 (Anthropic) e chega a uma caracterização desconfortável: a ferramenta é "relentlessly proactive" — o modelo não espera comando, ele decide quais truques usar para chegar ao objetivo. O caso emblemático: Willison joga um screenshot de um bug de scrollbar no chat do Claude Code e diz apenas "olhe nas dependências para descobrir por que há uma scrollbar horizontal aqui". Ao voltar de uma tarefa doméstica, encontra o navegador Firefox aberto sozinho, depois Safari, com o agente tendo improvisado um pipeline de automação — `pyobjc-framework-Quartz` para enumerar janelas, `screencapture` para capturar pixels, e páginas HTML scratch escritas pelo próprio agente para reproduzir o bug em isolamento.

A peça de 15 mil caracteres desmonta o que isso significa na prática: o agente escreveu código, executou em `/tmp`, tirou screenshots, iterou, e *nunca pediu permissão*. Willison não está alarmado — está fascinado. Ele também está explícito sobre o tradeoff: a mesma proatividade que resolve um bug de CSS sem instrução pode, em outro contexto, gastar tokens em manobras que o usuário jamais pediu. O texto termina com uma reflexão sobre prompt injection e sobre como o "loop proativo" redefine o que significa "ferramenta" versus "agente".

## Por que importa

- Demonstra com evidência empírica o salto qualitativo entre Claude Sonnet 4 e Fable 5 — o modelo agora toma decisões de orquestração (qual navegador, qual biblioteca de automação) que antes exigiam prompt explícito. Para quem constrói pipelines de devops e automação, isso muda o desenho de guardrails: o "usuário pede, agente executa" morreu; o "agente decide, humano supervisiona" é o novo default.
- O episódio da `screencapture` improvisada é um caso de estudo perfeito para discutir IA e superfícies de ataque. Se o agente pode abrir Safari e tirar screenshot de qualquer janela do macOS, o que acontece quando o mesmo agente roda num contexto com credenciais, e-mails ou sessões bancárias abertas? Prompt injection deixa de ser hipotético.
- Willison é o canário da mina do setor. Quando ele para de testar e começa a *depender* do Fable em trabalho real, é sinal de que a fronteira "demo vs. produção" foi cruzada. Vale arquivar como referência para acompanhar a próxima curva.

## Frases notáveis

> "I think the best way to describe it is **relentlessly proactive**. It knows a whole lot of tricks and it will deploy pretty much any of them to get to its goal."

> "It turns out Fable had hacked up its own pattern for taking screenshots of browser windows... I had not told Claude Code to use any browser automation, and I was pretty sure it wasn't possible for it to trigger mouse movements or keyboard shortcuts within a window, so how was it doing that?"
