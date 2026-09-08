---
title: "Creepy crawlies — a infraestrutura da internet sendo comida por scrapers de IA"
source: https://simonwillison.net/2026/Sep/7/creepy-crawlies/
date: 2026-09-08
tags: [ia, devops, infraestrutura, ética-de-dados]
---

# Creepy crawlies (Konstantin Ryabitsev, via Simon Willison)

Konstantin Ryabitsev, que administra o git.kernel.org (o repositório Git oficial do kernel Linux), finalmente tem números duros sobre o custo dos crawlers de IA — e são feios: **14 dos 90 núcleos de CPU dos 5 nós geo-distribuídos ficam permanentemente renderizando commits como HTML para scrapers**. Mais ciclos de CPU gastos servindo bots do que todo o acesso legítimo somado, incluindo `git clone`. Pedidos legítimos são ~2% do tráfego; o resto é scraping.

A ironia é que o kernel é uma mina de ouro justamente por ser conteúdo pré-IA garantido (treinar LLM em output de LLM dá "doença do príon digital"). E o modo mais burro de colher isso: em vez de clonar os repositórios — que eles oferecem de graça, com todo o histórico — os scrapers renderizam bilhões de URLs de commits, diffs e patches via cgit, duplicando 922 vezes os mesmos 1,48 milhão de commits.

A escalada da defesa é um thriller de devops: fail2ban por user-agent → bloqueio por IP → bloqueio por ASN → e então o golpe baixo: crawlers vindos de milhões de IPs residenciais e móveis via "proxy SDK monetization" (sua smart TV provavelmente faz parte do enxame). A resposta foi o Anubis (proof-of-work na borda): funcionou por meses na dificuldade 4, os bots aprenderam, subiu para 5 (que esquenta o celular dos usuários legítimos), os bots aprenderam de novo. Hoje 33% dos 6 milhões de requests diários resolvem a matemática e passam.

Não há solução simples. O kernel.org vai começar a desligar funcionalidades anônimas para reduzir URLs crawláveis, mas promete continuar oferecendo todos os dados para download — com mais hoops. Simon Willison adiciona a preocupação do ponto de vista do Datasette, que serve enormes quantidades de páginas crawláveis.

## Por que importa

- **Custo real e externalizado da corrida de IA**: o "background radiation" que sustenta os modelos que Ramon usa todo dia está saindo do bolso de infraestrutura pública/comunitária. Contexto essencial para qualquer posição ética ou prática sobre IA.
- **Devops na linha de frente**: o caso Anubis (proof-of-work adaptativo vs. bots que escalam dificuldade) é um estudo de caso de adversarial ops — relevante para quem roda serviços expostos (Gitea, APIs fly.dev, EAS).
- **O dado mais barato é o que já existe em bulk**: os scrapers ignoram o `git clone` gratuito. Lembrete de que otimizar o caminho óbvio (mirror próprio, shallow clone condenado) resolve 90% dos problemas antes de qualquer bloqueio.

## Frases notáveis

> "TL;DR: we spend more CPU cycles rendering commits for scrapers than we spend on all other kinds of legitimate access, including git clones."

> "Training an LLM on content produced by the LLM gives it the equivalent of a digital prion disease, so when a source is guaranteed to be LLM-free, like the entire history of kernel commits, it's worth its weight in gold."
