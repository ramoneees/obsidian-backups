---
title: "Quoting Calif Research — WeWorm"
source: "https://simonwillison.net/2026/Sep/10/calif-research/"
date: 2026-09-10
tags:
  - seguranca
  - ia
  - pesquisa
---

# Quoting Calif Research (WeWorm)

**Simon Willison · citação do relatório WeWorm da Calif Research**

## Resumo

Simon Willison sinaliza o release da demo do **WeWorm**, apresentado como o primeiro worm *zero-click* que se propaga por chamadas do WeChat entre iOS e Android. A vítima não precisa atender nem tocar no telefone; mesmo atendendo, não ouve nada — o exploit executa mesmo assim. Zero interação, propagação autônoma.

O detalhe que faz Willison destacar o texto é a logística do desenvolvimento: com assistência de IA, a equipe encontrou o bug e escreveu o primeiro RCE (execução remota de código) em **cerca de dois dias**. O worm completo levou mais uma semana. O contraste histórico é explícito no próprio texto: um worm nessa escala costumava exigir um time maior por meses.

A divisão de trabalho relatada é o ponto-chave: "a IA já faz a maior parte do trabalho aqui; nosso time forneceu o julgamento sobre o que atacar e como testar com segurança." Ou seja, o gargalo deslocou-se da execução técnica para a decisão estratégica — a mesma inversão que o artigo da Asian Efficiency descreve para escrita e Piper para maturidade doutrinária, agora com consequências de segurança global.

É um post-curto (uma citação), mas o sinal que carrega é grande: a barreira de entrada para malware de classe estatal despencou, e o worm WeChat é o primeiro marco público disso.

## Por que importa

- Demo concreta de que IA comprimiu o ciclo de desenvolvimento de exploits de meses para dias — mudança de regime para qualquer um que pensa em security posture (inclusive para a stack doméstica do Ramon: agentes com creds, APIs, dispositivos móveis).
- A frase "nosso time forneceu o julgamento" é a tese da era: execução barata, julgamento caro. Aplica-se a coding agents, automação e, no limite, à vida devocional — sempre a mesma anatomia.
- Willison é a fonte canônica de curadoria em IA/segurança; o que ele cita merece entrar no radar. O relatório original está em calif.io/research/weworm.

## Frases notáveis

> "Working with AI, our team found the bug and wrote the first remote code execution (RCE) exploit in about two days. Building the worm took one more week."

> "A worm at this scale used to be the kind of thing that took a larger team months. AI can already do most of the work here. Our team provided the judgment about what to target and how to test it safely."
