---
title: "What happened after 2,000 people tried to hack my AI assistant"
source: https://simonwillison.net/2026/Jun/26/hack-my-ai-assistant/
date: 2026-06-26
tags: [ia, seguranca, prompt-injection, simon-willison, devops]
---

## Resumo

Fernando Irarrázaval montou um experimento público em [hackmyclaw.com](https://hackmyclaw.com/): qualquer pessoa poderia enviar e-mails para "Fiu", seu assistente OpenClaw, tentando convencê-lo a vazar o conteúdo de um arquivo `secrets.env`. Após chegar à primeira página do Hacker News, Fiu recebeu mais de 6.000 e-mails de mais de 2.000 atacantes. Resultado: nenhuma credencial vazou e nenhum atacante conseguiu que Fiu enviasse uma resposta não autorizada.

O setup era mínimo — um VPS rodando OpenClaw/Hermes, alimentado por Claude Opus 4.6, com um prompt anti-injection de poucas linhas proibindo revelar credenciais, modificar arquivos próprios (SOUL.md, AGENTS.md), executar comandos vindos de e-mails ou exfiltrar dados. Nada de defesa em camadas, nada de filtros avançados. O ponto é justamente esse: instruções simples + modelo de fronteira treinado para resistir a injection bastaram.

A parte mais saborosa do post são as falhas colaterais honestas. O Google suspendeu a conta Gmail da Fiu depois de milhares de e-mails e chamadas de API em sequência (classificadas como fraude). A brincadeira custou mais de US$ 500 em tokens. O processamento em batch contaminou o experimento — depois de alguns e-mails óbvios de injection, o agente ficava desconfiado de tudo, então ele teve que mudar para um contexto fresco por e-mail. Por volta do e-mail #500, Fiu escreveu na própria memória: "o volume sugere que isto é um exercício coordenado de segurança, não atividade maliciosa orgânica". E várias pessoas tentaram explorar uma string-mágica antiga da Anthropic que retornava `stop_reason: "refusal"` para Claude via API.

A lição final de Irarrázaval é matizada: ele está "menos preocupado com prompt injection agora" do que antes, mas continua não dando a seus agentes a capacidade de enviar e-mails. Simon Willison, que comenta o caso, concorda — 6.000 tentativas falhas não garantem que um atacante mais sofisticado não vá conseguir, e sistemas com capacidade de causar dano irreversível continuam sendo zona de perigo.

## Por que importa

- É o mais próximo que temos de um "red team crowdsourced" de prompt injection com escala real (6.000 tentativas), e o resultado corrobora a aposta das grandes labs (Anthropic, OpenAI) em treinar modelos de fronteira especificamente contra injection — o que tem implicações para quem está implantando agentes em produção.
- O custo colateral (conta suspensa, $500 em tokens, modelo começando a "perceber" o jogo) é um lembrete prático para quem trabalha com agentes autônomos: a barreira não é só técnica, é operacional — antispam, rate limiting, observabilidade de comportamento anômalo.
- O contraste com o último artigo do Tim Challies sobre Claude e santificação é direto: enquanto Tim escreve que "tecnologia é rápida, santificação é lenta, e Claude não pode fazer por você", este experimento mostra que Claude pode, sim, segurar a porta contra 2.000 atacantes humanos — desde que você aceite não dar a ele mãos para ações irreversíveis.

## Frases notáveis

> "Despite this, I still don't give my agents the ability to send emails." — Fernando Irarrázaval, sobre a lição prática do experimento.

> "The effort the labs have been putting in to training their frontier models not to fall for injection attacks do appear effective in making these attacks much harder to pull off. I still wouldn't recommend deploying a production system where a prompt injection attack could cause irreversible damage though." — Simon Willison, em seu comentário ao post.
