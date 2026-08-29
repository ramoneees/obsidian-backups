---
title: "Just a Rumour of a Bug Is Enough to Find a Security Exploit These Days"
source: https://simonwillison.net/2026/Aug/28/just-a-rumour-of-a-bug/
date: 2026-08-29
tags: [seguranca, ia, open-source, coding-agents]
---

# Just a Rumour of a Bug Is Enough

Simon Willison destaca um relato assustador de Anil Madhavapeddy (professor em Cambridge e mantenedor do compilador OCaml): minutos depois de compartilhar um patch de segurança para discussão, seu site já recebia sondas automatizadas testando sequências de path traversal. Cerca de **dez minutos** entre a menção pública ao bug e a primeira tentativa de exploração — vigias automatizados monitoram repositórios públicos em tempo real.

A causa não é mágica: coding agents modernos ficaram tão bons em encontrar falhas que a mera **insinuação** de um bug já é informação suficiente. Madhavapeddy demonstrou isso com os próprios agentes — trocando para DeepSeek V4 Pro quando o Claude Fable se recusou à tarefa. O custo de achar um exploit despencou; o de defender código, não.

O mantenedor do rclone, Nick Craig-Wood, confirma a escala nos comentários do Hacker News: em 10 anos de projeto recebeu ~20 divulgações de segurança pelo GitHub; no último mês foram **mais de 40** — com taxa de acerto de ~75%. O gargalo institucional também estourou: a atribuição de CVEs pela GitHub caiu de 2-3 dias para 3-4 semanas, forçando releases com "CVE-PENDING" no changelog.

A conclusão é direta: essa velocidade de descoberta é **incompatível com as práticas atuais de embargo** em open source. Se um rumor vira exploit em minutos, a janela tradicional de "discussão privada → patch → disclosure coordenado" deixou de existir. A comunidade precisa inventar novos processos — ou os agentes continuam ganhando a corrida.

## Por que importa

- **A economia da segurança inverteu**: exploração automatizada barata vs. triagem humana cara — atinge qualquer stack open source em produção (devops, APIs, CI).
- **Agentes de código como adversários**: as mesmas ferramentas usadas para construir (OpenCode, Claude Code) agora encontram exploits com um rumor de pista — a linha entre copiloto e atacante é só o prompt.
- **Disclosure coordenado morreu?**: processos de embargo e CVE precisam ser repensados; relevante para qualquer mantenedor ou contribuidor de projetos open source.

## Frases notáveis

> "Within about ten minutes (!) this website was fielding probes for percent-encoded traversal sequences, indicating that automated watchers are keeping an eye on public repositories." — Anil Madhavapeddy

> "In the first 10 years of the rclone project we received about 20 security disclosures through GitHub. We had to deal with over 40 in the last month!" — Nick Craig-Wood (rclone)
