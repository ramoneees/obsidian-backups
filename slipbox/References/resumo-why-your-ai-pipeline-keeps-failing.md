---
title: "Why Your AI Pipeline Keeps Failing (It's Not the Model)"
source: https://www.asianefficiency.com/technology/chain-step-quality/
date: 2026-06-13
tags: [ia, devops, pipelines, asian-efficiency, automacao]
---

# Why Your AI Pipeline Keeps Failing (It's Not the Model)

Asian Efficiency destrincha um diagnóstico que se repete em todo projeto de IA que escala: o output final é ruim, o dev culpa o modelo, troca de provider, ajusta prompt — e o problema persiste. A tese central é que a falha raramente está no LLM; está na **arquitetura da chain**. Cada passo do pipeline herda a qualidade (ou a mediocridade) do passo anterior, e degrada um pouco mais. Quando você chega no passo 5 olhando para o output final, o erro original no passo 2 já foi processado três vezes e se tornou irreconhecível.

O caso prático é devastador: Blake Eastman tinha um pipeline de análise comportamental que custava $9 por query e ainda errava. A correção não foi prompt melhor nem modelo mais inteligente — foi **decompor o trabalho**. Quebrar o monolito em componentes de responsabilidade única, processar uma unidade de dados por vez na granularidade certa, e **verificar o output de cada passo antes de passar adiante**. Resultado: $0.07 por query, mesma qualidade, e outputs previsíveis em vez de aleatórios. Redução de custo >99%, só por rearranjo.

O princípio que emerge é direto: **cada passo da chain deve produzir output que você usaria sozinho**. Não perfeito, mas claro, completo, utilizável como input do próximo passo. A regra vale para qualquer sistema sequencial, mas em IA ela é especialmente traiçoeira porque outputs ruins de IA parecem bons — são gramaticalmente corretos, bem escritos, estruturalmente sólidos. O erro mora na *substância*: detalhe perdido, ênfase errada, contexto evaporado. É o oposto de uma planilha, que cospe números obviamente errados quando você alimenta dado podre. A superfície polida mascara o subsídio podre.

A implicação operacional é clara: debug de pipeline de IA exige caminhar pra trás passo a passo, não mexer no prompt final. Construir incrementalmente, validar a cada elo, avançar só quando o elo está sólido. Se um passo produz algo que te envergonharia usar, pare ali — não passe adiante esperando que o próximo passo compense. Não compensa. **Garbage in, garbage out sempre foi verdade em computação; em IA o lixo vem com verniz.**

## Por que importa

- Diagnóstico aplicável direto aos seus workflows com agentes Hermes/OpenClaw: a falha raramente é o modelo, é o encadeamento.
- O caso $9 → $0.07 é um argumento fortíssimo contra monolítos de prompt e a favor de decomposição + validação por etapa.
- Vale como princípio de design de qualquer sistema em chain — não só IA.

## Frases notáveis

- "Most of the time, the AI isn't the problem. The architecture is."
- "Garbage in, garbage out has always been true in computing. But it hits differently with AI because the outputs look polished even when they're wrong."
