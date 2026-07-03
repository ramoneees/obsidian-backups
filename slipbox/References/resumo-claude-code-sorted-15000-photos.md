---
title: "I Had 15,000 Unorganized Photos. Claude Code Sorted Them While I Slept."
source: https://www.asianefficiency.com/technology/i-had-15000-unorganized-photos-claude-code-sorted-them-while-i-slept/
date: 2026-07-03
tags: [ia, automacao, claude-code, devops, produtividade]
---

# I Had 15,000 Unorganized Photos. Claude Code Sorted Them While I Slept.

Thanh Pham, da Asian Efficiency, tinha um problema clássico: 15 mil fotos sem organização — Japão, eventos, headshots profissionais, celular, tudo junto. Tentou organizar manualmente e desistiu em 20 minutos. A tarefa era grande demais para ser feita à mão e irregular demais para automação baseada em regras simples.

A solução: apontou Claude Code para a pasta, deu três regras explícitas (fotos do Japão → pasta Japão; fotos com ele em contexto profissional → headshots; resto → organizar por ano), e soltou **uma única foto de referência do próprio rosto** como "registro facial". Fechou o notebook, foi viver o dia. Horas depois, estava pronto.

O mecanismo que torna isso possível é a combinação de duas camadas de informação: **EXIF metadata** (GPS, timestamps, modelo de câmera) e **raciocínio visual** sobre a imagem em si quando a metadata não basta. Claude Code olha a foto e decide: "isso é um headshot profissional? o Thanh está no centro? é um restaurante, evento, sessão de trabalho?". Estruturado + julgamento. É essa combinação que destrava o que scripts tradicionais não conseguem.

A lição maior: a maioria usa IA como mecanismo de busca — pergunta, resposta, fecha a aba. Claude Code rodando local é outra coisa. É uma "camada de execução autônoma". Você não pergunta, você **delega uma tarefa** e dá acesso aos seus arquivos. Ele roda até terminar. Pham cita o caso de um amigo que pediu ao Claude Code para reverter o engine de armazenamento local do Granola e construir integração com Google Drive do zero. A virada mental: de "IA como parceiro de conversa" para "IA como empreiteiro".

O framework prático fecha o artigo: (1) defina especificamente o que "organizado" significa, nada vago; (2) dê um ou dois exemplos quando houver julgamento visual; (3) aponte para a pasta e deixe rodar. Não fique olhando. Volte uma hora depois. O artigo termina com a pergunta provocativa: "qual é a sua pasta misc de 15 mil itens?".

## Por que importa

- Materializa o salto do "AI-as-tool" para **"AI-as-contractor"** — mudança de modelo mental que define quem ganha produtividade real com LLMs agênticos.
- A combinação de **metadata estruturada + raciocínio visual multimodal** é a fronteira concreta de utilidade: tarefas irregulares demais para regras, pequenas demais para contratar gente.
- Templates replicáveis para qualquer "pasta misc" pessoal ou profissional — Ramon pode mapear candidatos locais (screenshots, invoices, arquivos de obsidian) seguindo o mesmo protocolo de 3 passos.

## Frases notáveis

> "Most of us use AI like a search engine. We ask a question, get an answer, close the tab. … That's maybe 5% of what's actually available."

> "From AI as conversation partner to AI as contractor."
