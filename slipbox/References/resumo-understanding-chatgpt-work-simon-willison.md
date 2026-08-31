---
title: "Understanding ChatGPT Work"
source: https://simonwillison.net/2026/Aug/30/understanding-chatgpt-work/
date: 2026-08-31
tags: [ia, agentes, openai, segurança]
---

Simon Willison destrincha o ChatGPT Work depois de quase dois meses de experimentação — e o veredito é duplo: "extraordinariamente confuso e muito poderoso". O produto na verdade são dois: o **Work Cloud** (rodando em chatgpt.com e nos apps móveis) e o **Work Local** (o app de desktop que antes se chamava Codex, rebrandado para assustar menos leigos). Ambos exclusivos para assinantes de US$20/mês ou mais.

O que separa Work de Chat não é marketing, é capacidade: seleção dos modelos Sol, Luna e Terra com níveis de raciocínio até Ultra; ambiente de execução de código **com acesso aberto à internet** (o Chat bloqueia isso no proxy); um **Chrome headless completo** que navega, preenche formulários, roda JavaScript via Playwright e até permite que o usuário assuma o login com 2FA sem passar credenciais pelo modelo; filesystem persistente compartilhado entre sessões; sub-agentes paralelos; e prompts agendados. O código com internet é o que mais empolga Willison, veterano do padrão Code Interpreter: dá pra clonar um repo do GitHub, instalar dependências e usá-lo contra o resto da web.

O ponto alto (literalmente): **ChatGPT Sites**. O Work constrói e publica sites inteiros sobre Cloudflare Workers, com server-side, D1 e R2. Com um único prompt — "descubra todos os lugares de Londres com um pelicano in pietate e monte um site com os dados" — ele gerou um censo iconográfico medieval com 28 pontos, JSON para download e layout de museu. Prototipagem por prompt, deploy incluído.

O contraponto é o de sempre: segurança. O modelo da **trifeta letal** de Willison (dados privados + conteúdo não confiável + canal de exfiltração) se aplica inteiro — "ChatGPT Work combina os três!". Ele espera que a proteção seja o mesmo mecanismo de auto-review do Codex, mas nota que a OpenAI não explica nada, e reclama da ausência de changelogs decentes.

## Por que importa

- É o estado da arte em agentes cloud: browser real + código com internet + sub-agentes + deploy. Referência direta para avaliar o que delegar a agentes gerenciados vs. rodar no próprio stack (Hermes, n8n, OpenCode local).
- A trifeta letal é o framework prático para a regra "privado → Qwen, pesado → GLM": antes de dar acesso a dados sensíveis a qualquer agente cloud, os três fatores precisam estar separados.
- ChatGPT Sites muda o custo de prototipagem de apps — pressão direta sobre fluxos tipo Next.js/EAS para MVPs descartáveis.

## Frases notáveis

> "It is an extraordinarily confusing and very powerful product. Here's what I've figured out about it so far."

> "My lethal trifecta model warns about the risks inherent in any agent system that combines access to private data with exposure to untrusted content and a way to communicate stolen information back to an attacker. ChatGPT Work combines all three!"
