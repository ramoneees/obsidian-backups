---
title: "Locating the source of a mysterious beep with Claude"
source: "https://simonwillison.net/2026/Nov/9/mysterious-beeps/"
date: 2026-11-10
tags: [ai, coding-agents, automacao, hardware]
---

Simon Willison tinha um bip intermitente num quarto cheio de caixas sem etiqueta — o tipo de problema que consumiria uma tarde. Em vez de caçar no dedo, ele mandou o Claude Code construir o Beep Locator: um servidor Python que coordena iPads, iPhone, MacBook e Surface espalhados pelo quarto, todos virando microfones do sistema via navegador (WebAudio + WebSockets). O próprio agente pesquisou e encontrou o paper acadêmico certo (BeepBeep, SenSys 2007, localização acústica com hardware commodity) antes de escrever uma linha.

A engenharia é elegante: cada listener roda detecção de bip no browser com FFT e filtro high-pass; quando um bip é detectado, o servidor dispara um chirp de um dispositivo para alinhar os clipes gravados entre si, e triangula pela diferença de tempo de chegada. Há modo "rough" (você arrasta os dispositivos no mapa e o sistema refina), modo palmas para validar o sistema, replay de áudio de cada listener para confirmar qual gravação era o bendito bip, e até sugestão de onde posicionar um listener extra para apertar a estimativa. Resultado: localizou a fonte a ~40 cm. Era um detector de monóxido de carbono antigo implorando por bateria.

O insight central do post vai além do gadget: Willison demonstrou que é possível dar ouvidos a um coding agent. O Claude não tem input de áudio nativo — mas pode escrever e executar o código que escuta por ele, consultar os logs de áudio e reconfigurar os próprios "sensores" ao vivo. O detalhe que viabilizou tudo: um mecanismo de hot-swap que injeta JavaScript novo nos listeners via WebSocket, sem recarregar a página (recarregar peditaria permissão de microfone de novo em cada dispositivo).

A conclusão dele ecoa uma tendência: outro dev debugava computadores de conference badge apontando uma webcam para a tela para o agente "ver" se o update funcionou. A fronteira divertida agora é dar aos agentes percepção do mundo físico — e deixá-los construir os próprios órgãos sensoriais.

## Por que importa

- É o blueprint exato do fluxo que o Ramon já usa: descrever o problema em um problem.md, deixar o agente pesquisar e construir, e o humano só iterar features em linguagem natural.
- O hot-swap de código em clientes via WebSocket (deploy sem reload) é padrão reaproveitável em automações domésticas e no monitoramento do Olympus.
- A ideia de agentes com sensores que eles mesmos constroem abre frente nova: um agente de homelab que escuta, observa e diagnostica o ambiente físico.

## Frases notáveis

> "I think the most interesting part of this project is that I demonstrated it's possible to give Claude Code ears."

> "Figuring out ways to let coding agents perceive the world around them is a whole lot of fun."
