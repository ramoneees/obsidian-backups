---
title: "Running Python code in a sandbox with MicroPython and WASM"
source: https://simonwillison.net/2026/Jun/6/micropython-in-a-sandbox/
date: 2026-06-10
tags: [python, wasm, sandbox, seguranca, ia-agentes, simon-willison]
---

# Running Python code in a sandbox with MicroPython and WASM

Simon Willison destrava um problema antigo do ecossistema Python: plugins para Datasette, LLM e sqlite-utils rodam com privilégio total via Pluggy. Um plugin bugado ou malicioso pode vazar dados, quebrar a aplicação, comprometer a máquina. Ele queria um sandbox real — não uma promessa, não um "na maioria das vezes está isolado", mas um limite físico que o código não atravessa.

A solução que ele finalmente julgou viável combina **MicroPython + WebAssembly**. WASM oferece isolamento de memória e CPU, deny-by-default de I/O, e instrumentação determinística. MicroPython, compilado para WASM, dá uma runtime Python completa que cabe num pacote distribuível via PyPI com wheels multiplataforma. O resultado é o pacote alpha `micropython-wasm` e o plugin `datasette-agent-micropython` que permite agentes de IA executarem código arbitrário em ambiente controlado.

A lista de requisitos que Willison escreveu é o checklist que todo engenheiro de plataforma devia ter colado no monitor: dependências instaláveis via `pip install` puro, limites estritos de **memória e CPU** (nada de `while True: s += "x"`), filesystem opt-in com leitura e escrita explicitamente permitidas, rede mediada por camada controlada, e suporte a *host functions* (a sandbox precisa conversar com o sistema sem ser o sistema). Crucialmente: o projeto precisa ser *mantido e documentado* — Willison admite que já viu dezenas de sandboxes Python abandonados com aviso de "não usar em produção".

A motivação vai além de plugins: ele quer rodar jobs agendados que puxam JSON de fonte aprovada, transformam via código do usuário, e inserem em SQLite. Tudo isso sem dar ao código do usuário o poder de, digamos, deletar a tabela de produção.

## Por que importa

- Para o Ramon que está construindo agentes de IA: a fronteira real entre "agente útil" e "agente perigoso" é o sandbox. Este artigo é a referência canônica em 2026 para quem quer dar execução de código a um LLM sem abrir a porta do servidor. Vale ler inteiro antes de montar qualquer agent architecture.
- O princípio "limites de memória e CPU" aplicados a execução de LLM é o equivalente funcional de rate-limiting em APIs — proteção contra runaways que virou negligência comum. Willison está formalizando o que SRE já sabe sobre blast radius.
- O approach é "vibe-coded" e alpha — Willison é transparente que ainda não é production-grade. Mas o caminho (WASM + runtime minimalista) é a direção que a indústria vai seguir. Quem plantar nessa tendência agora sai na frente.

## Frases notáveis

> "A buggy or malicious plugin could break everything or leak private data. I'd love to be able to run plugin-style code in an environment where it is unable to read unapproved files, connect to a network, or generally operate in a way that's risky or harmful to the rest of the application or the user's computer."

> "I've lost count of the number of sandbox projects I've seen in repos with warnings that they aren't actively maintained!"
