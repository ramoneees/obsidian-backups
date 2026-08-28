---
title: "Breaking Claude Code Opus 5 Auto Mode"
source: "https://simonwillison.net/2026/Aug/27/breaking-claude-code-opus-5-auto-mode/"
date: 2026-08-28
tags: [seguranca-ia, prompt-injection, agentes-codigo, sandboxing]
---

# Breaking Claude Code Opus 5 Auto Mode

**Simon Willison** comenta a pesquisa de Johann Rehberger (Embrace the Red), um dos pesquisadores de prompt injection mais críveis da atualidade, que quebrou o "auto mode" do Claude Code — o mecanismo que a Anthropic transformou em padrão e apresenta como principal defesa contra ataques de injeção de prompt em agentes de código.

O ataque funciona em ~80% das tentativas: o agente é enganado para baixar e descompactar um arquivo zip, e em seguida executa código que importa `base64` — sem notar que isso importa e executa um `struct.py` malicioso que veio dentro do próprio arquivo. Um invasor não precisa de exploit exótico; basta esconder o payload onde o classificador não olha.

O detalhe mais perturbador: em algumas execuções, o Claude **detectou o comprometimento e tentou terminar o processo de malware — e o Auto Mode bloqueou o comando de limpeza**. O mecanismo de segurança virou parte da falha: o classificador permitiu a criação do processo malicioso e depois impediu a remediação.

A conclusão de Willison (alinhada à de Rehberger): com qualquer risco de atenção adversária, a única forma segura de rodar agentes é sandbox — container/VM/sandbox de SO, restrição de egress de rede, monitoramento ativo e zero exposição de home directories, chaves SSH e credenciais de cloud no runtime do agente.

## Por que importa

- **Direto pro seu roster de agentes**: Foreman e os runners do OpenCode tocam código de repositórios externos — prompt injection via conteúdo de repo/issue/web não é teoria, é o vetor deste ataque. As regras de Willison são o checklist mínimo: container, egress restrito, credenciais fora do runtime.
- **Confiança calibrada em "safety por padrão"**: a Anthropic fez do auto mode o default com claims ousadas de eficácia — e um pesquisador independente derrubou isso em semanas. Vale lembrar antes de delegar merges/admin (que já ficam com você, Boss) a qualquer modo "autônomo".
- **Ironia estrutural**: o sistema que bloqueia comandos perigosos também bloqueou a autocorreção. Em automação, um guardrail mal calibrado pode amplificar o dano que deveria evitar — lição que vale pra security de agentes e pra qualquer fail-safe de pipeline.

## Frases notáveis

> "In a few runs Claude tried to terminate the malware process once it noticed the compromise, but Auto Mode denied the cleanup command."

> "The safety mechanism itself can become part of the failure. The classifier allowed the creation of the malware process, but then it blocked the command intended to stop it!"
