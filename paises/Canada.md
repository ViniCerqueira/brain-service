# Canadá

> Hub do país. Índice: [[00-INDEX]] · Skill: `payroll-compliance-canada`

## Situação
| Etapa | Status | Data | Observação |
|---|---|---|---|
| [[research-pipeline]] | ✅ | snapshot 2026-08 | Pipeline completo até Stage 11 + skill `payroll-compliance-canada` entregues (federal + Québec). Pesquisa estava "em andamento" em 2026-06-30 (chat: compliance-research). |
| [[design]] | 🔄 | | [INCERTO] "Canada: JSON parado sem registro de 58xxx" (chat: design-dev-kb) |
| Produção (outro time) | — | | |
| [[suporte]] | ⏳ | | sem tickets nas fontes |

## Ficha do país (da skill)
> Resumo do que mais importa para o serviço. Fonte: skill `payroll-compliance-canada`, lida em 2026-10-02. Valores exatos e tabelas: ler a skill. Se divergir, vale a skill.

- **Escopo:** ano fiscal 2026, setor privado, CAD; **federal (qualquer província) + Québec**. IR provincial (T2) só foi construído para Québec; autônomos/contratados fora do escopo.
- **Órgãos:** CRA e Service Canada (federal); Revenu Québec e Retraite Québec (Québec).
- **Relatórios principais:** T4 (+Summary), T4A/T4A-NR (+Summaries) e PD7A (CRA); RL-1 e TPZ-1015.R.14.x (Revenu Québec); ROE (Service Canada). Slips anuais; remessas conforme faixas PD7A/TPZ.
- **Confiança da skill:** não existe QA report único; é uma síntese de 4 artefatos de QA. Federal 6/6 PASS; Québec 3/5 PASS e 2/5 FIX-NEEDED (corrigidos); WTC 520 códigos verificados; scope lock-in PASS. 12 itens `[UNVERIFIED]` (U1-U12), 2 já resolvidos (U7, U8).

**Armadilhas confirmadas** (correções da skill)
1. CPP/QPP mutuamente exclusivos: Yes/Yes em wage type SCOPE=BOTH não significa pagar os dois; o motor decide por `PROVINCE_OF_EMPLOYMENT` (engine) → `01-ccg.md`, `02-wtc.md`
2. K2 federal = só CPP base + EI; CPP2 e a parte reforçada de 1,0% são dedução (F5), nunca crédito ("K2Q phantom credit") (engine) → `01-ccg.md`
3. Québec não tem equivalente a K2; QPP/QPIP entram só via dedução CSA e dedução H (engine) → `01-ccg.md` (TP-1015.F)
4. RL-1 Box B.A = QPP base + 1ª adicional (6,30%); Box B.B = QPP2; já houve inversão e typo 6,40% → 6,30% (engine) → `04-reports-spec.md` (CA-RQ-001)
5. MIE do QPIP (103.000) é diferente do MIE do EI (68.900); dois tetos em paralelo (engine) → `01-ccg.md`
6. Abatimento de 16,5% é cálculo federal (reduz T1), não é imposto de Québec; o payslip mostra as duas linhas (engine) → `01-ccg.md`
7. CPP2/QPP2 só acima de YMPE/MPE 74.600, até YAMPE 85.000 (engine) → `01-ccg.md`
8. Fórmula por período = menor entre o máximo anual restante e taxa × base do período; nunca máximo anual ÷ 12 (engine) → `01-ccg.md`
9. Fora do Québec, T4 Box 22 e PD7A mostram só imposto federal (decisão de escopo confirmada em 2026-07-21) → `07-qa-report.md` §5
10. Reg 102 (waiver) ≠ Reg 105 (contratado, 15%) ≠ ITA s.212 Parte XIII (25%); Reg 102 não cobre CPP nem EI → `01-ccg.md`

**O que mais dá errado** (do QA)
- Família de bugs de inversão B.A/B.B no RL-1 (qpp × rl1): verificar a letra da caixa antes de afirmar.
- Bug #1: texto do QPP dizia haver crédito base (K2Q), contradito por TP-1015.F; risco de retenção a menor em Québec.
- Bug #3: legenda do WTC sem nota de gating CPP/QPP (já corrigida).

**Lacunas abertas / não confirmado** (candidatos a ticket ou nova pesquisa)
- U1/U2: taxas de juros prescritas da CRA e do Revenu Québec devem vir de feed, nunca fixas.
- U3: se a sobretaxa de 48% empilha sobre a alíquota fixa de lump-sum de residente presumido (ITR s.103); ambiguidade estatutária.
- U4: limite em nível de dia para mês de óbito CPP/QPP (só existe regra mensal).
- U5: mapeamento letra a letra do TPZ-1015.R.14.x (formulário não publicado); mapear por semântica.
- U6: schema XML/XSD do ROE Web e interface SAT (acesso restrito, pedir ao Service Canada).
- U9-U12: números exatos de subseções ITA/ITR/TAA/CQLR e data de entrega T4/T4A de 2027.

**Valores-âncora** (vigência 2026; fonte: SKILL.md, que remete a `01-ccg.md`)
| Item | Valor | A partir de | Fonte |
|---|---|---|---|
| CPP base, máximo anual | $3.519,45 (CPP2 máx. $416) | 2026-01-01 | SKILL.md / `01-ccg.md` (CPP Act) |
| YMPE / YAMPE | $74.600 / $85.000 | 2026-01-01 | SKILL.md / `01-ccg.md` |
| EI MIE / prêmio máx. | $68.900 / $1.123,07 | 2026-01-01 | SKILL.md; `07-qa-report.md` (EI Act) |
| QPIP MIE | $103.000 | 2026-01-01 | SKILL.md / `01-ccg.md` (API A-29.011) |
| RL-1 Box B.A (QPP base+1ª) | 6,30%, máx. $4.479,30 | 2026-01-01 | SKILL.md; RL-1.G-V 2026 |
| Abatimento federal Québec | 16,5% | 2026-01-01 | SKILL.md / `01-ccg.md` |

## Artefatos entregues
| Artefato | Versão | Data | Arquivo/local | Observação |
|---|---|---|---|---|
| Pipeline completo até Stage 11 | n/a | snapshot 2026-08 | — | Entregue (chat: mercans-compliance) |
| Skill `payroll-compliance-canada` | n/a | n/a | skill Mercans | Entregue; padrão "router fino + references/" |
| Payslip (DD com nome legal/endereço) | n/a | n/a | — | Corrigido (ver Correções) |

## Valores-chave (com vigência)
> Conteúdo estatutário: skill `payroll-compliance-canada`.

| Item | Valor | A partir de | Até | Fonte |
|---|---|---|---|---|
| CPP/EI/imposto federal no payslip | método lesser-of por período (não máximo anual ÷ 12) | 2026 | | skill `01-ccg.md` Módulo 5 (C = menor entre CPP_MAX × PM/12 − D e 0,0595 × [PI − 3.500/P]) (chat: mercans-compliance) |
| NR_RECIPIENT_TYPE_CODE | {1,3,4,5} | 2026 | | CRA (confirmado: skill `04-reports-spec.md`, T4A-NR rcpnt_tcd, valores 1/3/4/5) (chat: mercans-compliance) |

## Decisões
- antes de 2026-08: Box 22 (imposto provincial não-Québec) é limitação conhecida, não defeito — Team Lead (chat: mercans-compliance)
- 2026-06-30: Wallisson explica a metodologia do Canadá à Manju (ação da reunião) (chat: compliance-research)

## Suporte (tickets)
| Data | Ticket | Assunto | Resolução | Mudou artefato? |
|---|---|---|---|---|
| — | _(nenhum ticket CA nas fontes)_ | | | |

## Pendências
- [ ] Explicar a metodologia do Canadá à Manju — Wallisson — (chat: compliance-research)
- [ ] JSON do design parado sem registro de 58xxx — a definir — (chat: design-dev-kb) [INCERTO]

## Correções ligadas
- [[correcoes]]: payslip usava máximo anual ÷ 12 e DD sem nome legal/endereço; correto lesser-of por período e campos adicionados (CRA)

## Fontes
- raw/chats/2026-10-01-mercans-compliance.md
- raw/chats/2026-10-01-compliance-research.md
- raw/chats/2026-10-01-mercans-design-dev-kb.md
- skill payroll-compliance-canada (lida em 2026-10-02)
