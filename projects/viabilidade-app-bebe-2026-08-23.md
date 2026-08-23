# Viabilidade — App bebé (white noise / rotina) — 2026-08-23

**Status:** validado com números de mercado · **Decisão pendente:** GO / NO-GO do Boss
**Fontes:** Sensor Tower, Playwire AdMob benchmarks, market.us, Deloitte 2025 (via pesquisa 23/08)

## A tese
Portfólio de apps utilitários de nicho com AdMob + IAP, codificados pelo pipeline de agentes (OpenCode + foreman), supervisão do Boss. Primeiro app: white noise / sons de sono para bebé — o Boss É o usuário-alvo (2º filho a caminho). Validar com o próprio bebé antes de escalar.

## Números de mercado (referência)
- **Slumber "White Noise Deep Sleep"** (iOS, 2016): US$200k/mês, 50k downloads/mês. Um app de 2016 ainda imprime isso.
- **Huckleberry** (baby tracker): US$800k/mês — mas US$12,5M de VC atrás. Não é o nosso jogo.
- **Mercado baby trackers:** US$515M (2024) → US$1,45B (2033), CAGR 13,2%.
- **Praça:** PT ~85k nascimentos/ano; BR ~2,6M/ano. App em PT-BR + EN ataca as duas.

## Projeção honesta (freemium, unlock €4,99, ads nos grátis)
| Cenário | Installs/mês | Receita líquida/mês |
|---|---|---|
| Pessimista (30/dia) | 900 | **~€100** |
| Base (150/dia) | 4.500 | **~€650** |
| Otimista (500/dia) | 15.000 | **~€2.600** |

Premissas: conversão IAP 2-3%, eCPM interstitial tier-1 €5-8 / global €2,5-5, DAU ~35% da base mensal. Break-even rápido porque infra custa ~€0 (homelab + pipeline existente).

## Vantagens competitivas nossas
1. Custo marginal por tentativa ≈ €0 (agentes codificam, CI pronto, Play Console pronto)
2. Usuário-teste interno: o bebé chega em meses — feedback loop perfeito
3. PT-BR nativo + inglês; concorrência direta é fraca em PT

## Riscos e bloqueios reais
- **Play (conta pessoal):** closed testing com 12 testers por 14 dias antes de produção — planejar o gate no cronograma (aprendido no pack).
- **iOS gated** no enrollment Apple (bloqueio do Boss, não meu).
- **Sons:** usar CC0 / gerados (synth) — NADA de música licenciada. Lullabies PT-BR originais são diferencial defensável.
- Retenção é o jogo: app de som vive de DAU; ASO (ícones, screenshots, keywords) vale mais que features.
- "Passivo" = ~2 fins de semana de build + ~2h/semana de manutenção e ASO. Sem marketing pago.

## Rota B (fogo lento, em paralelo)
Ferramentas PT para freelancers (calculadora recibo verde etc.). Concorrência real: Doutor Financas, Unipeople, gov.pt — fracos em UX mas com domínio. SEO 12-24 meses. Só se o Boss quiser o second bet.

## Próximos passos (se GO)
1. Definir nome + pacote mínimo: 8-12 sons CC0/synth, timer, fade, favoritos, AdMob banner+interstitial, unlock único €4,99
2. Dispatch OpenCode (worktree própria) para MVP Android-first
3. Recrutar os 12 testers (igreja A Ponte + família BR) — o gate de 14 dias
4. Dogfood com o bebé; iterar sons

## Veredicto
**Vale o shot.** Custo quase zero, upside real, janela pessoal perfeita. Expectativa honesta: €100-650/mês em 6-12 meses no cenário base — rendimento semi-passivo, não salário.
