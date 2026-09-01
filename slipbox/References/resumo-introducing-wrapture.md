---
title: "Introducing wrapture"
source: "https://simonwillison.net/2026/Aug/31/introducing-wrapture/"
date: 2026-09-01
tags: [python, testes, agentes-ia, observabilidade]
---

Graham Dumpleton (criador do wrapt, mod_wsgi e do agente Python da New Relic) lançou o **wrapture**, uma biblioteca que estende as ideias de monkey-patching do wrapt para unificar duas disciplinas que vivem separadas: *testing* e *tracing*. Com ela, qualquer função ou método pode ser embrulhado para ter todo acesso rastreado ou sobrescrito — uma alternativa ao `unittest.mock` e, ao mesmo tempo, uma ferramenta de observabilidade para projetos existentes, com suporte a OpenTelemetry incluído.

O que chama atenção é o mecanismo declarativo: um arquivo de configuração TOML define o que observar (`domain:Calculator`), o que capturar (`summary`) e onde despejar (`trace.jsonl`). Tracing adicionado a projeto legado sem tocar em uma linha de código — o tipo de coisa que faz um devops sorrir. Nos exemplos de teste, padrões como `binding(Gateway, "charge").on_call.returns(...)` e `transforms_result(...)` substituem mocks frágeis por contratos explícitos.

Mas o detalhe mais provocativo é a origem: é o primeiro projeto grande do Dumpleton *inteiramente escrito por agente de IA* — e ele faz questão de distinguir isso de "vibe coding". O design era dele, completo e anterior; a IA foi o meio de produção, não a fonte das decisões. Engenharia dirigida por quem sabe exatamente o que quer, com o agente como multiplicador de throughput.

Projeto novo (poucas semanas), mas com pedigree e uma tese interessante: observabilidade e testes são o mesmo problema — interceptar código que você não controla sem perturbá-lo.

## Por que importa

- **Padrão ouro para delegação a agentes**: o contraste "vibe coding vs. engenharia dirigida por IA" é exatamente o modelo do Boss — agentes executando, humano arquitetando. Dumpleton provou que funciona até para biblioteca de infraestrutura delicada (monkey-patching é territorio de armadilhas).
- **Tracing declarativo via config** é ouro para o playbook de automação: instrumentar código legado sem alterá-lo reduz o custo de adotar observabilidade em projetos como o precisase.
- **Mock + tracing unificados** elimina uma duplicação clássica de ferramental em Python — vale monitorar antes de adotar, mas é candidato forte ao stack.

## Frases notáveis

> "Every line of code and documentation in wrapture was written by an AI assistant working under my direction. [...] I engineered wrapture carefully from the start. I have spent a long time in this particular corner of Python and knew exactly what the result needed to be, and the AI was the means of producing it rather than the source of the design."

> "Attaching observation to code you do not control, recording what flows through it, and doing so without disturbing the program being watched, is a problem I have never really stopped thinking about."
