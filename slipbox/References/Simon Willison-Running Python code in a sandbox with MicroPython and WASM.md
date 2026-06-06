---
title: "Running Python code in a sandbox with MicroPython and WASM"
source: "https://simonwillison.net/2026/Jun/6/micropython-in-a-sandbox/#atom-everything"
date: 2026-06-06
tags:
  - devops
  - wasm
  - python
  - sandbox
---

# Running Python code in a sandbox with MicroPython and WASM

**Autor:** Simon Willison | **Fonte:** Simon Willison's Weblog | **Publicado:** 2026-06-06

## Resumo

Simon Willison apresenta sua solução mais recente para um problema que o persegue há anos: como executar código Python de forma segura dentro de aplicações. Ele lançou o pacote `micropython-wasm` (alpha) e o plugin `datasette-agent-micropython` para o Datasette Agent, usando MicroPython compilado para WebAssembly como camada de sandbox.

O problema central é elegante: todos os projetos open-source de Simon — Datasette, LLM, sqlite-utils — suportam plugins via Python e Pluggy. Plugins são mecanismo de extensão fantástico, mas executam com privilégios totais na aplicação. Um plugin malicioso ou buggy pode quebrar tudo ou vazar dados privados. Simon precisava de um ambiente onde código pudesse rodar sem acesso irrestrito a filesystem, rede, memória ou CPU.

O checklist de requisitos é um modelo de thinking claro: instalação limpa via PyPI, limites de memória e CPU, filesystem estritamente controlado, rede controlada, interação com funções do host, e robustez documentada. Depois de anos testando alternativas, WebAssembly emergiu como a solução ideal — navegadores já operam no ambiente mais hostil imaginável e WASM foi projetado exatamente para esse tipo de isolamento.

MicroPython, variante leve do Python para microcontroladores, compilado para WASM oferece o equilíbrio certo: familiaridade sintática com Python, footprint mínimo, e o modelo de segurança do WASM por baixo. O pacote é instalável via `pip install micropython-wasm` e permite executar código sandboxed que interage com funções do host através de uma API controlada.

## Por que importa

- **Sandbox como padrão de arquitetura.** Para quem pensa em devops e automação, esse é o debate central: como confiar em código de terceiros sem abdicar de segurança. A abordagem WASM é relevante para qualquer pipeline que execute código dinâmico — CI/CD, plugins, automação de IA.
- **Agentes de IA e segurança.** Conecta-se diretamente à conversa sobre agentes autônomos (como o artigo do Kim acima): se agentes de IA vão executar código em nome do usuário, o sandbox é a camada de proteção entre autonomia e desastre. Simon está construindo a infraestrutura para isso.
- **Pensamento de produto aplicado.** O artigo é um mestre-classe em design de requisitos. Simon articula exatamente o que precisa antes de começar a implementar — uma disciplina que serve para qualquer projeto de automação.

## Frases notáveis

> "I absolutely love plugins as a mechanism for extending software. A carefully designed plugin system reduces the risk involved in trying new things to almost nothing — even the wildest ideas won't leave a lasting influence on the core application itself."

> "Web browsers operate in the most hostile environment imaginable, and WebAssembly was designed specifically to safely execute untrusted code within that context."
