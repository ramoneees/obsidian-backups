---
title: "Apple and a Hacker's Future"
source: Stratechery
url: https://stratechery.com/2026/apple-and-a-hackers-future/
author: Ben Thompson
category: Articles
date: 2026-10-05
tags: [ia, agentes, apple, seguranca]
ingested: 2026-10-05
---

Ben Thompson teve o Mac Mini sempre ligado — que roda nada além de Claude e Codex — invadido via CVE-2026-65400: bug de state management no Screen Sharing do macOS, explorado por quem deixou a porta 5900 aberta na internet. Resultado: root comprometido e minerador de Monero plantado. Campanha automatizada, comentários em chinês, nada pessoal.

A reviravolta: quem detectou foi o próprio agente. O Claude Code achou um hook em /etc/zshenv injetando /var/tmp/.xmr como root, notou datas falsificadas (31/12/1969), parou de rodar comandos sozinho e disparou alerta URGENT. Thompson usou o próprio agente para fazer a forense, identificar a janela de 4 segundos da invasão, criar um watchdog e wipear a máquina. Ironia: o Mac "vazio" dedicado aos agentes foi o que salvou a operação — teria sido pior sem agente rodando.

A crítica estrutural é ao TCC da Apple: prompts de permissão GUI que nenhum software headless consegue ver. Programas falham em silêncio, o agente não sabe por quê, e o humano precisa abrir screen share — do celular — só para clicar OK. TCC opera no nível errado de abstração: o que se precisa é de uma camada de permissão para o agente, não para cada programinha que ele escreve. E o agravante: "instalar atualizações de segurança automaticamente" não cobria fixes de CVE — que chegam em point releases. Ele ficou anos mais exposto do que achava.

Fechamento com Paul Graham ("Return of the Mac", 2004): o Mac venceu os hackers porque era Unix bonito. Vinte anos depois, agentes transformam qualquer pessoa em hacker — e, nesse mundo, walled garden deixa de ser proteção e vira prisão. Thompson já comprou servidor novo: vai rodar Linux, e ele "nunca mais põe um Mac num rack".

## Por que importa

- Cenário idêntico ao daqui: Macs headless sempre ligados rodando agentes (Hermes, gateway, mark-one). Vale checar hoje: porta 5900/Screen Sharing exposto e se "atualizações de segurança automáticas" está realmente instalando os CVE fixes.
- TCC invisível é exatamente a classe de problema que a gente vive no Hermes (keychain fail em background, prompts GUI). O artigo explica o porquê arquitetural.
- Tese estratégica: agentes que usam a web ganham integração com tudo de graça; Apple casada com o paradigma de apps/APIs fica para trás. Relevante para tekton, precisase e para onde colocar os próximos servidores.

## Frases notáveis

> "The thing about AI, however, particularly agents, is that they make anyone a hacker."

> "…once you embrace that, a walled garden feels less like protection and more like a prison."
