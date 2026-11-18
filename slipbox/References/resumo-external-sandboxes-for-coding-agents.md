---
title: "External sandboxes for coding agents"
source: https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/
date: 2026-11-18
tags: [coding-agents, sandboxing, security, devops]
---

Simon Willison, em parceria com o laboratório Prime Radiant, propõe o padrão de **sandbox externa**: o agente roda fora da sandbox, mas todo código que ele executa roda dentro de uma máquina isolada que ele não controla. É a inversão do modelo usual — em vez de prender o agente, prende-se o que ele executa. O alvo declarado é testar modelos locais sem o medo de que um prompt injection se converta em ação destrutiva na sua máquina.

Foram lançadas três implementações open source com a mesma API localhost: external-sandbox-v86 (Alpine Linux rodando em WebAssembly dentro de um servidor Node.js), external-sandbox-container (Alpine em Apple Containers) e external-sandbox-quicksand (a biblioteca Quicksand da Microsoft, que empacota QEMU e Alpine num pacote Python). Todas plugam direto no Pi, no Claude Code e no Codex — o agente passa a mandar cada execução de código para a sandbox em vez de rodar na sua máquina.

O detalhe que separa brinquedo de ferramenta de produção é a camada de rede: um proxy com allow-list HTTP/HTTPS define exatamente quais hosts o código do agente pode alcançar, reconfigurável por UI com a sandbox ainda rodando. E há substituição de credenciais: o agente consegue fazer chamadas a APIs autenticadas sem nunca ver o segredo — o token fica na sandbox, não no contexto do modelo.

Willison segue obcecado pelo problema de rodar código não-confiável, e o padrão externo tem uma virtude de engenharia: como as três implementações expõem a mesma API, fica fácil trocar de abordagem e comparar trade-offs de isolamento sem mudar nada no agente. Sandbox como infraestrutura intercambiável, não como projeto-heroico.

## Por que importa

- Ramon roda 2-3 agentes em worktrees paralelas (OpenCode/Sisyphus): sandbox externa é o próximo degrau de segurança para deixar agentes soltos sem arriscar a máquina.
- A substituição de credenciais resolve dor real de n8n/CI: o agente chama a API sem jamais ver o token.
- v86 significa Alpine rodando em WebAssembly — a mesma linha de raciocínio do Datasette-Lite/Pyodide: computação isolada até dentro do browser.

## Frases notáveis

> "the agent itself lives outside of that sandbox"

> "I continue to be fascinated by the challenge of safely running untrusted code."
