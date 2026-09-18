---
source: "Simon Willison"
title: "Be alert: targeted attacks on prominent Rustaceans"
date: 2026-09-17
author: "Simon Willison"
url: https://simonwillison.net/2026/Sep/17/targeted-attacks-on-rustaceans/
category: "Segurança / Open Source"
tags: [seguranca, supply-chain, rust, open-source]
ingested: 2026-09-18
---

# Be alert: targeted attacks on prominent Rustaceans

**Fonte:** Simon Willison
**Data:** 2026-09-17
**URL:** https://simonwillison.net/2026/Sep/17/targeted-attacks-on-rustaceans/

## Resumo

Aviso de Adam Harvey e da equipe de segurança do crates.io: há uma campanha ativa mirando membros do rust-lang e donos de crates populares, comprometendo dispositivos/contas para publicar malware na supply chain.

## Ideias principais

- O vetor: vídeo-chamada com pretexto positivo (emprego, projeto, contrato) usada para convencer a vítima a instalar algo (ex.: "codec de áudio faltando") ou executar comando (ex.: comando colocado no clipboard).
- O golpe já funcionou: ataque à supply chain do crate `arrayref` em agosto de 2026.
- Qualquer software que dependa de open source herda uma rede de humanos como superfície de ataque — todo mundo com direitos de publicação na cadeia de dependências.
- Defesa prática apontada por Simon: dependency cooldowns — esperar alguns dias antes de atualizar para releases novas, deixando que ataques sejam detectados por outros.

## Notas e conexões

- Risco de supply chain vale também para as dependências dos meus apps (npm/CocoaPods) — cooldown de dependências é política defensável nos repos.
- Conecta com o ataque ao RubyGems por agentes da OpenAI (Simon Willison, set/2026).
- Ver [[slipbox/References]]
