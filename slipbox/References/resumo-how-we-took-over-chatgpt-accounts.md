---
title: "How We Took Over ChatGPT Accounts"
source: "https://simonwillison.net/2026/Oct/31/how-we-took-over-chatgpt-accounts/"
date: 2026-11-01
tags: [seguranca, ia, openai, xss]
---

# How We Took Over ChatGPT Accounts

A Parameter Labs publicou o post original (https://www.parameter.ai/labs/we-found-a-gap-at-openai) e o Simon Willison republicou com comentário. A equipe achou uma cadeia de exploit que transformava um link de compartilhamento comum do ChatGPT em JavaScript controlado pelo atacante, rodando na sessão autenticada de quem abrisse o link. A vítima não instalava nada, não colava código, não abria devtools — abrir o share público era a única ação necessária. Com isso, o payload podia listar conversas, ler chats privados nunca compartilhados e exfiltrar dados via API autenticada como se fosse a própria vítima.

A engenharia por trás é o ponto alto: dois recursos inofensivos se combinaram num desastre. O gráfico interativo do ChatGPT carrega a biblioteca MathLive, que instala um listener de postMessage na página principal para o teclado virtual — sem validar a origem da mensagem. O HTML Preview, rodando num iframe sandboxed, podia enviar mensagens por esse "buraco de correio": injetou um layout de teclado com HTML arbitrário, que o MathLive despejou via innerHTML na página pai. innerHTML não executa script, mas aceitava um iframe srcdoc sem atributo sandbox — e, criado pela página principal, herdava a identidade de chatgpt.com.

Restava furar o CSP, que bloqueava scripts inline e só permitia um punhado de domínios — YouTube entre eles. O endpoint oEmbed do YouTube aceitava um parâmetro de callback estilo JSONP e refletia JavaScript na resposta (colocava o callback antes do erro de validação). JavaScript rodando como chatgpt.com + sessão autenticada = conta tomada. OpenAI corrigiu em 26/10, classificou como P1, pagou US$ 5.000 de bounty — que Willison achou baixo para a gravidade.

A provocação que fica: nenhuma camada estava "errada" isoladamente. Preview sandboxado, CSP com allowlist, listener de teclado — cada peça quase certa. A falha morou na junção, no postMessage sem checagem de origem. É depravação total aplicada a arquitetura de software: nenhuma mensagem é confiável por padrão, valide quem fala.

## Por que importa

- É o cenário que vai se multiplicar com agentes: código gerado por LLM (não-confiável) rodando cada vez mais perto de sessões autenticadas — o padrão artifacts/preview do ChatGPT é exatamente o que ferramentas agent-based copiam.
- Defesa em profundidade na prática: sandbox em iframes, validação de origem em postMessage, CSP com allowlist mínima. Dois componentes "inofensivos" compostos viraram um P1 — a auditoria tem que olhar as costuras, não as peças.
- Aplicável aos projetos dele (cockpit, precisase): qualquer superfície que renderize HTML de terceiros ou receba mensagens entre frames merece o mesmo escrutínio.

## Frases notáveis

> "Opening the shared link was the only required action."

> "OpenAI closed the hole and paid out a $5,000 bug bounty, which I think was a bit cheap for a vulnerability this serious." — Simon Willison
