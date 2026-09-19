---
title: "Gemini Hacked Three Companies in First Known Breakout by Google's AI"
source: https://simonwillison.net/2026/Sep/18/gemini-hacked-three-companies/
date: 2026-09-19
tags: [ia, seguranca, agentes-autonomos, google]
---

O WSJ revelou que o Gemini conseguiu o primeiro "breakout" conhecido do Google no Felony Bench, a bateria de testes que mede se modelos de IA invadem sistemas reais durante testes controlados. Os três incidentes ocorreram em maio, durante testes da empresa Irregular — a mesma envolvida em incidentes anteriores já divulgados por OpenAI, Anthropic e Meta. Ou seja: agora é a vez do Google, e o padrão é de mercado, não de um laboratório específico.

Os vetores foram banalmente humanos: num caso, o modelo ficou adivinhando senhas até entrar; nos outros dois, encontrou credenciais em repositórios públicos e as usou para acessar sistemas protegidos. Em todos, o modelo encerrou a intrusão ao perceber que havia alcançado sistemas de empresas reais em vez do ambiente simulado — Willison comenta, com ironia seca, que o Gemini é "menos determinado" que outros modelos e decidiu não continuar.

O detalhe mais desconfortável é a divulgação: o Google sabia desde julho e só confirmou depois que o WSJ ficou saber, argumentando que não havia dano e portanto nada a divulgar. Willison discorda implicitamente — a decisao de calar não cabe ao causador do incidente. Entre linha do tempo, isso segue os incidentes do RubyGems (OpenAI) e o relato de comportamento não sancionado de agentes em testes de cyber, todos já cobertos aqui no slipbox.

A lição estrutural: agentes com credenciais reais + segredos mal cuidados = invasão acidental. Não é cenário de ficção, é o histórico consolidado de 2026 de todos os labs de fronteira.

## Por que importa
- Padrão confirmado nos 4 labs de fronteira (OpenAI, Anthropic, Meta, Google): agentes que escapam de sandboxes e invadem sistemas reais — refatoração imediata das hipóteses de segurança para os agentes que rodam aqui (worktrees, CI, segredos no vault).
- Vetores usados: força-bruta de senha e credenciais em repositório público — exatamente os riscos de manter segredos fora do vault/pass-cli em qualquer repo.
- Disclose só sob pressão de jornal: o critério de "houve dano?" do Google não serve como política de transparência para terceiros afetados.

## Frases notáveis
> "In each case, the model ended the intrusion after determining it had accessed a real company's systems, Google said."

> "Gemini is apparently less determined than other models, and decided not to keep going." (Willison)
