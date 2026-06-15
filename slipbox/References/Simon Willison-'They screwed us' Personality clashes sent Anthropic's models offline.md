---
title: "\"They screwed us\": Personality clashes sent Anthropic's models offline"
source: Simon Willison
date: 2026-06-15
url: https://simonwillison.net/2026/Jun/15/axios-clashes-anthropics/
category: Link Blog
tags: [anthropic, claude, export-controls, ai-policy, jailbreaking]
ingested: 2026-06-15
---

# "They screwed us": Personality clashes sent Anthropic's models offline

## Resumo

Link blog de Simon Willison comentando uma matéria da Axios sobre os bastidores da decisão do Departamento de Comércio dos EUA de suspender o acesso aos modelos Mythos 5 e Fable 5 da Anthropic. A peça traz "fontes familiares" e "fontes próximas à Anthropic" — Simon destaca que é a melhor coleção de fofocas que ele viu sobre o imbróglio. Reunião com o Commerce Department está marcada para o dia em D.C. com Logan Graham (Frontier Red Team), Dave Orr (Head of Safeguards, ex-Google DeepMind) e Nicholas Carlini.

## Pontos-chave

- **Contexto**: o governo dos EUA (via Commerce Department) emitiu diretiva que submete Mythos 5 e Fable 5 a controles de exportação, restringindo uso fora dos EUA. Anthropic cortou acesso totalmente até a questão ser resolvida. Outros modelos da Anthropic não foram afetados.
- **As pessoas-chave no lado Anthropic**: Logan Graham (lidera a Frontier Red Team, ex-Special Adviser to the Prime Minister no governo Boris Johnson cobrindo AI/science/tech policy), Dave Orr (Head of Safeguards, ex-Director of Engineering no Google DeepMind), Nicholas Carlini (pesquisador de segurança frequentemente citado por Simon).
- **A opção "jailbreak-proof"**: uma alternativa em discussão seria tornar os modelos da Anthropic inquebráveis — mas a própria Anthropic admite que jailbreak resistance perfeita "pode ser impossível".
- **A opção "atitude fix"**: a outra alternativa descrita pela fonte é um ajuste de atitude onde, em vez de alguém se sentir desconsiderado, "todo mundo se sente seguro, protegido e feliz". Simon não está otimista de que isso devolva o Fable logo.
- **Constitutional Classifiers**: a defesa técnica da Anthropic é seu trabalho com Constitutional Classifiers (post de janeiro 2026). Eles classificam o jailbreak que disparou a reação do governo como "potencial narrow, non-universal jailbreak" — não um jailbreak universal.
- **Antecedente**: link para o paper de 2023 "Universal and Transferable Adversarial Attacks on Aligned Language Models" (llm-attacks.org) — Simon se pergunta se a Anthropic de fato resolveu aquela classe de ataques. Resposta implícita: não completamente.

## Notas e Conexões

- Conecta com [[Anthropic Safety Superpower]] (Stratechery, 15 jun 2026) — leitura complementar: a análise da Stratechery sobre por que a segurança da Anthropic é diferencial estratégico.
- Conecta com [[TLDR AI 2026-06-15]] — a edição de hoje também cobre o desligamento do Fable/Mythos como headline.
- [[AI Policy]] e [[Export Controls]] como tema em ascensão — o caso Anthropic é provavelmente o primeiro de muitos.
- [[Jailbreaking]] como categoria técnica — vale ler o paper llm-attacks.org como base conceitual.
