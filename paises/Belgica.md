# Bélgica

> Hub do país. Índice: [[00-INDEX]] · Skill: `payroll-compliance-belgium`

## Situação
| Etapa | Status | Data | Observação |
|---|---|---|---|
| [[research-pipeline]] | 🔄 | snapshot 2026-08 | CCG, WTC, SIR e 9 Report Specs existem; correções pendentes "ao fechar todos os estágios do pipeline". Colômbia entra na fila depois da Bélgica. |
| [[design]] | ⏳ | | [INCERTO] sem design BE registrado; BE serve de precedente de formato (colunas laranja do WTC, navy do net pay) |
| Produção (outro time) | — | | |
| [[suporte]] | ⏳ | | sem tickets nas fontes |

## Ficha do país (da skill)
> Resumo do que mais importa para o serviço. Fonte: skill `payroll-compliance-belgium`, lida em 2026-10-02. Valores exatos e tabelas: ler a skill. Se divergir, vale a skill.

- **Escopo:** ano de renda 2026, setor privado, federal, EUR. Fora: diretores de empresa, autônomos, setor público, sobretaxas regionais/municipais, tributação em nível de assessment, Limosa (entregue pelo empregador estrangeiro). Holandês construído; francês (obrigatório, nulidade do documento se faltar) e alemão não construídos. Escalas setoriais (joint committees) são configuração por cliente.
- **Órgãos:** NSSO/RSZ-ONSS, FPS Finance, Fedris, Febelfin.
- **Relatórios principais (9 specs):** Dimona, DmfA, DmfA modification, DRS/ASR, FinProf 274, Belcotax 281.10, Fedris work accident, Febelfin SEPA pain.001 (Limosa descartado, só referência). Nenhum foi submetido a portal.
- **Versões de registro (skill, refresh 2026-09-16):** CCG v1.2, WTC v1.1 (359 linhas), DD v1.4 (92 blocos de mapper / 2.018 códigos), SIR v1.0, QA de 2026-08-17.
- **Confiança da skill:** não existe veredito de tier para a Bélgica (anterior à convenção; não citar). QA por artefato: SIR 93%, CCG 86%, WTC 85%, Report Specs 86%, DD 87%, Payslip 86%, scope_manifest 78%. 6 blockers e 11 majors abertos (QA anterior ao refresh de 16/09; vários itens fechados depois, ver `PROPAGATION-LEDGER.md`).

**Armadilhas confirmadas** (SKILL.md "Design clarifications"; todas `(engine)` salvo indicação)
1. Social work bonus = duas componentes R_B + R_A, cada uma com limite, máximo e coeficiente próprios; exemplos 2, 4 e 6 do corpus usaram só o máximo da A → `01-ccg.md` Mod 5.1.1
2. Isenção básica na retenção = 11.170 (Annex III nr. 32), não 11.180 (contrafactual) nem 11.550 (assessment) → `01-ccg.md` Mod 6
3. Tetos de faixa Annex III 16.710 / 29.500 / 51.050, não os do assessment 16.720 / 29.510 / 51.070 → `01-ccg.md` Mod 6
4. Retenção de notice indemnity usa Annex III nr. 58 (via nr. 62), não nr. 53 (53,50% vs 38,96% no exemplo: 5.766,20 a mais) → `01-ccg.md` Mod 9.1
5. Coeficiente de idade do carro da empresa: 100% 12 meses, depois -6 pp por ano decorrido (piso 70%); contar pela data, não pelo ano de registro → `01-ccg.md` Mod 7
6. Multiplicador CO2 = 4,00 desde 2026-01-01 e multiplica só a contribuição calculada, nunca o mínimo (25,99 não indexado / 42,34 indexado) → `01-ccg.md`
7. Special SS contribution: três tabelas por situação do domicílio fiscal (a situação escolhe a tabela, não o teto); EUR 15,45 só na Tabela 2 → `01-ccg.md` Mod 5
8. Essa contribuição é por faixa trimestral: meses 1 e 2 provisórios, corrigir no último pagamento do trimestre → `01-ccg.md` Mod 5
9. Fator de remuneração de referência para pagamentos excepcionais: padrão Mercans x 13,92 (disputado na prática belga; declarar como padronização) → `01-ccg.md` Mod 6/9
10. Calendário do GMMI (1 jan, 1 abr, 1 ago) difere do work bonus (1 jan, 1 mar, 1 abr, 1 jul, 1 set; sem linha de 1 ago) → `01-ccg.md` Mod 5.1.1
11. Fiscal work bonus: 33,14% da componente A e 52,54% da B (não um percentual misto); teto anual EUR 765 → `01-ccg.md` Mod 7.1
12. CBA 90: dois tetos, social EUR 4.255 e fiscal EUR 3.701 (entre os dois: isento de SS, tributável) → `01-ccg.md`
13. Impatriados: tributário (35%, sem teto de 90.000, mínimo 70.000) difere do NSSO (mínimo 75.000, teto 90.000 mantidos) → `01-ccg.md` Mod 11
14. Base legal do work bonus: Lei 20/12/1999 art. 2 → RD 17/01/2000 → RD 27/03/2023 → RD 05/03/2024; não o art. 353bis → `01-ccg.md`
15. Teto anual do social work bonus após 2026-07-01: ver Lacunas (não extrapolar)
16. Idioma do documento de pessoal é ditado pela sede de operação (exploitatiezetel); payslip bilíngue não é permitido → `06-payslip.md`
17. Sobretaxa fixa de 7% do não-residente (Chefquet, C-119/24, 2026-03-12) é de assessment, não modelar em payroll → `01-ccg.md`
18. Specs unem wage types por `Mercans Code`, não pelo nome em inglês; `contract_type` (tempo integral/parcial) e `contract_duration_type` são mappers diferentes e a colisão persiste no payslip (BE-X10-005) → `04-reports-spec.md`, `05-data-dictionary.md`

**O que mais dá errado** (do QA)
- Manifesto outbound sem crosswalk: faltam 7 fluxos SIR (OUT-03, 07, 08, 16, 17, 18, 19) (BE-X10-001); fluxos de outbound em dois blocos do manifest discordam (BE-X10-001).
- 52,54% do fiscal work bonus não é reportado no 281.10 (dois tax codes num wage type ou dois wage types; decisão, não pesquisa) (BE-X10-002).
- WTC dizia que dois artefatos entregues não existiam (BE-X10-003); DD certifica registro que não contém (BE-X10-004).
- Multiplicador CO2 repousava em 4 fontes tier-B (BE-X10-022); a skill diz que a citação legal foi incorporada depois (ler a célula F59 do WTC, não o relatório).

**Lacunas abertas / não confirmado** (candidatos a ticket ou nova pesquisa)
- Check digit do número RSZ/NSSO de 9 dígitos (não resolvido).
- Teto anual do social work bonus após 2026-07-01: o design item 16 e o QA §6.2 dizem NOT FOUND, enquanto o SKILL.md (refresh) cita EUR 3.594,36 desde 2026-07-01 (NSSO instructions 2026/3). Skill internamente inconsistente: confirmar.
- Reforço do fiscal work bonus (componente B a 63%) não confirmado como promulgado; indexação do EUR 765 não resolvida.
- Registro único de limitações do país (união de G1–G27 do SIR, DD, specs) não existe (BE-X10-004/006).
- Relatório de QA predata o refresh de 16/09 e ainda cita `BE-WTC-001-v1.0`.

**Valores-âncora**
| Item | Valor | A partir de | Fonte |
|---|---|---|---|
| Contribuição SS do empregado | 13,07% | 2026 | skill (descrição); `01-ccg.md` Mod 5 |
| Isenção básica na retenção | 11.170 (redução 2.987,98) | 2026 | Annex III nr. 32 |
| Alíquotas de retenção | 26,75 / 42,80 / 48,15 / 53,50% | 2026 | Annex III nr. 31 |
| Multiplicador CO2 | 4,00 (5,50 em 2027-01-01) | 2026-01-01 | Lei 25/11/2021 art. 34, 1º |
| Teto social work bonus anual | 3.466,44 (1 jan); 3.523,92 (1 abr); 3.594,36 (1 jul, conflito, ver Lacunas) | 2026-01-01 | NSSO instructions 2026/1, /2, /3 |
| CBA 90 | teto social 4.255; teto fiscal 3.701 | 2026 | `01-ccg.md` |

## Artefatos entregues
| Artefato | Versão | Data | Arquivo/local | Observação |
|---|---|---|---|---|
| CCG Bélgica | sem versão citada | — | — | Módulo 9 Step 7 com valor a corrigir (697,61 para 697,42). Skill (SKILL.md, versão de registro 2026-09-16): v1.2 |
| WTC Bélgica | sem versão citada | — | — | Falta tax code box 360 no fiscal work bonus. Skill (versão de registro): v1.1 |
| Report Specs Bélgica (9 specs) | — | — | — | Bloco DmfA-Modification 90169 rotulado ORIGINAL (a corrigir) |
| SIR Bélgica | — | — | — | Cruzar com a Form Reference Guide do WTC e as 9 specs |
| Skill `payroll-compliance-belgium` | n/a | n/a | skill Mercans | Existe (Dutch built; French/German não) |

## Valores-chave (com vigência)
| Item | Valor | A partir de | Até | Fonte |
|---|---|---|---|---|
| CCG Módulo 9 Step 7 | 697,42 (o CCG traz 697,61, errado) | ⚠️ vigência? | | ⚠️ sem fonte (chat: mercans-compliance) |

## Decisões
- sem data: BE é precedente de formato para a França (colunas laranja do WTC vazias para o dev; justificativa Yes-No na col. F) (chat: design-dev-kb; ver [[Franca]])
- sem data: BE/TN usam navy no net pay; o verde (m-3) da França vai para o standard owner (chat: design-dev-kb)

## Suporte (tickets)
| Data | Ticket | Assunto | Resolução | Mudou artefato? |
|---|---|---|---|---|
| — | _(nenhum ticket BE nas fontes)_ | | | |

## Pendências
- [ ] Divergência hub × skill: o hub lista "falta box 360 no WTC", mas o WTC v1.1 da skill já traz o fiscal work bonus com tax codes duplos 284 e 360 — verificar (skill lida em 2026-10-02)
- [ ] Divergência hub × skill: o hub diz que o CCG traz 697,61 (errado) no Módulo 9 Step 7 e deveria ser 697,42; o CCG v1.2 da skill ainda mostra 697.61 nos exemplos (linhas ~2792/2801) — verificar (skill lida em 2026-10-02)
- [ ] Corrigir: box 360 no WTC; 697,61 para 697,42 no CCG; 90169 rotulado ORIGINAL — Wallisson — (chat: mercans-compliance)
- [ ] Emitir alerta exaustivo de pendências ao fechar todos os estágios — Wallisson — (chat: mercans-compliance)
- [ ] Investigar tabelas nr.53/58 e check digit do número RSZ — Wallisson — (chat: mercans-compliance)
- [ ] Atualizar citações para incluir os decretos e a lei de julho de 2026 — Wallisson — (chat: mercans-compliance)
- [ ] Cruzar a Form Reference Guide do WTC e o SIR com as 9 specs — Wallisson — (chat: mercans-compliance)
- [ ] [INCERTO] resíduos de BE na França: "Description (NL)" e "FR-NSSO / FR-FIN series" no CCG M10 — ver [[Franca]]

## Correções ligadas
- _(nenhuma correção concluída; as três correções acima estão pendentes)_

## Fontes
- raw/chats/2026-10-01-mercans-compliance.md
- raw/chats/2026-10-01-mercans-design-dev-kb.md
- skill payroll-compliance-belgium (lida em 2026-10-02)
