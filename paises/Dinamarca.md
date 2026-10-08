# Dinamarca

> Hub do país. Índice: [[00-INDEX]] · Skill: `payroll-compliance-denmark`

## Situação
| Etapa | Status | Data | Observação |
|---|---|---|---|
| [[research-pipeline]] | ✅ | 2026-08-22 | skill compilada (build do zero em 2026-08-22) |
| [[design]] | ⏳ | | |
| Produção (outro time) | — | | |
| [[suporte]] | ⏳ | | |

## Ficha do país (da skill)
> Resumo do que mais importa para o serviço. Fonte: skill `payroll-compliance-denmark`, lida em 2026-10-02. Valores exatos e tabelas: ler a skill. Se divergir, vale a skill.

- **Escopo:** ano de renda 2026, setor privado, DKK. Fora: setor público/tjenestemænd, Groenlândia e Ilhas Faroé, DIS/sømandsbeskatning, autônomos/virksomhedsordning, tetos de pensão (PBL), LL § 7 P, imposto corporativo/IVA.
- **Órgãos:** Skattestyrelsen (eIndkomst), ATP / Samlet Betaling, FerieKonto, Udbetaling Danmark, Erhvervsstyrelsen.
- **Relatórios principais:** eIndkomst mensal (DK-RPT-001); pagamento de A-skat e AM-bidrag (RPT-002); relatórios FerieKonto (RPT-003/004) e avisos de transição de férias (RPT-008/009, 31 dez e 31 jan); Samlet Betaling (RPT-005, trimestral); notificação de ausência/refusion (RPT-006); declaração de lønsumsafgift (RPT-007).
- **Confiança da skill:** "PASS WITH NOTES", 0 defeitos críticos, 12 itens abertos. Única seção abaixo do piso de 95%: `06-payslip.md` (~65%, não há lei de conteúdo do payslip). Seções em 80–90%: `04-reports-spec.md` 85% (lista de campos eIndkomst ~70% completa), lønsumsafgift 80%, salário mínimo/jornada 85%, documentação de emprego 80%, `02-wtc.md` 90% (13 células `[VERIFY]`), `03-sir.md` 90%.

**Armadilhas confirmadas**
1. Denmark é por skattekort: o engine nunca calcula imposto por faixas; trækprocent + fradrag do eSkattekort já incluem tudo; recalcular personfradrag/beskæftigelsesfradrag/jobfradrag duplica (engine) → `01-ccg.md` §2, §4
2. Skatteloft 2026 é 44,57% e cobre só §§ 6 e 7 (bundskat + mellemskat + kommuneskat); topskat e top-topskat ficam fora e empilham (tetos efetivos 52,07% e 57,07%); 52,07% era o teto de 2025 (engine) → `01-ccg.md` §4.3
3. Três faixas empilhadas: mellemskat 7,5% acima de 641.200; topskat 7,5% acima de 777.900; top-topskat 5% acima de 2.592.700, medidas após AM-bidrag (engine) → `01-ccg.md` §4
4. Base do AM-bidrag não é o bruto: felt 0013 = bruto menos ATP do empregado menos pensão administrada pelo empregador; felt 0016 = 0,08 × felt 0013 (engine) → `01-ccg.md` §3, `04-reports-spec.md`
5. AM-bidrag sobre contribuição de pensão é retido pela instituição de pensão (doméstica; KSL § 49 D stk. 1), não pelo empregador; estrangeira inverte (stk. 4); não "corrigir" uma regra contra a outra (engine) → `01-ccg.md` §5.3
6. Beskæftigelsesfradrag e jobfradrag são ligningsmæssige: reduzem só a base municipal/igreja, nunca a personlig indkomst nem movem limiares (engine) → `01-ccg.md` §4
7. ATP é kroner fixos por faixa de HORAS, em três tabelas (mensal ≥117h = 99,00 empregado / 198,00 empregador / 297,00 total; 14 dias ≥54h = 156,60; semanal ≥27h = 78,30); nunca percentual nem anual÷12 (engine) → `01-ccg.md` §5.1
8. Sem seguridade social percentual e sem teto; encargos do empregador são kroner por FTE por trimestre via Samlet Betaling; AES depende do branchekode (284 a 10.892 kr/FTE/ano, 16 grupos); branchegruppe errado é o maior erro de custo; só lønsumsafgift é percentual (engine) → `01-ccg.md` §5.2
9. Aviso prévio indenizado ≠ severance: løn i opsigelsesperiode vai no felt 0013; fratrædelsesgodtgørelse/gratiale são tributáveis mas isentos de AM (felt 0014 e 0069), uma fatia isenta de 8.000 kr/ano (LL § 7 U); funktionærloven § 2 a: 12 anos = 1 mês, 17 anos = 3 meses, só dispensa pelo empregador (engine) → `01-ccg.md` §10
10. Base da feriegodtgørelse não é felt 0013 (ferieloven § 19 stk. 2 soma de volta pensão do empregado e o próprio AM); acúmulo 2,08 dias/mês; dia de férias não pago = −4,8% do salário mensal (engine) → `01-ccg.md` §7
11. FerieKonto: empregador que paga no FerieKonto reporta feriegodtgørelse líquida de A-skat e AM; os demais, bruta; prazos dependem do fim do período; desligados reportados e pagos até o último dia do mês; avisos de transição com prazos distintos (31 dez / 31 jan) (engine) → `04-reports-spec.md` RPT-003/004/008/009
12. Sem skattekort = 55% do bruto sem dedução (AM 8% continua); 40% para pagadores de pensão (KSL § 48 stk. 11); ordem da retenção: lønindeholdelse, restskat indregnet, AM, A-skat; o feed traz também a lønindeholdelsesprocent (engine) → `01-ccg.md` §2, §6
13. Forskerskat: teste salarial por safra de contratação (65.400 kr/mês para contratos desde 1 jan 2026; 78.000 para 2025); 27% + 8% AM = 32,84% efetivo; 84 meses acumulados entre empregadores; citar só o valor 2026 em kroner (engine) → `01-ccg.md` §13
14. Bagatelgrænser são limiares, não franquias (1.400 kr benefícios pequenos; 7.600 kr relacionados ao trabalho): estourar tributa o valor todo; idem diária/km acima da taxa do Skatterådet (3,94 kr/km até 20.000 km, depois 2,28) (engine) → `01-ccg.md` §11
15. Denmark é M2M (eIndkomst via MQ ou Sterling File Gateway; eSkattekort por subscription push + SOAP síncrono); portais reais: Samlet Betaling e lønsumsafgift → `03-sir.md`

**O que mais dá errado** (do QA)
- Citar pré-reforma (teto 52,07%, topskat única de 15%) em 2026.
- Citar 37% (trækprocent do exemplo, construído) como "a taxa de retenção dinamarquesa" (O-1).
- Afirmar que ferieloven exige férias acumuladas no payslip (não sustentado pelo texto; "lønseddel" tem zero ocorrências).
- Erro de citação já ocorrido: ansættelsesbevisloven é LOV nr 501 de 16/05/2023, em vigor desde 1 jul 2023 (não "LOV nr 700 de 24/05/2022") (O-9).
- Rejeitado: barselsdagpenge de 4.695 kr/semana; correto 5.085 kr/semana (O-7).

**Lacunas abertas / não confirmado** (candidatos a ticket ou nova pesquisa)
- O-10: status da transparência salarial (Diretiva 2023/970, prazo 7 jun 2026; projeto ligelønsloven talvez caducado com a eleição): NÃO afirmar que está em vigor.
- O-8: grundbeløb 2010-niveau da forskerskat não resolvido (só o valor 2026 é citável).
- O-4: mecânica/prazos da lønsumsafgift (~60%).
- O-12: lista de campos eIndkomst ~70% completa (faltam 0023, 0042, 0201).
- O-11: rota do eSkattekort para o setor privado (Serviceplatformen vs MQ/SFG) e tipo de certificado; NemRefusion.
- O-3: escopo exato de KSL § 49 A stk. 3 nr. 1–4; O-2: LG sem linha própria; O-5: regra do meio-dia é prática, não lei; O-6: registro de jornada e descanso de 11h; O-7: divisão das semanas de licença parental (fonte secundária).
- 13 células `[VERIFY]` no `02-wtc.md`; `06-payslip.md` ~65%.

**Valores-âncora**
| Item | Valor | A partir de | Fonte |
|---|---|---|---|
| Bundskat / mellemskat | 12,01% / 7,5% acima de 641.200 kr | 2026-01-01 | L 138 (2023-24) |
| Topskat / top-topskat | 7,5% acima de 777.900 kr / 5% acima de 2.592.700 kr | 2026-01-01 | L 138 (2023-24) |
| Skatteloft (§ 19) | 44,57% (só §§ 6 e 7) | 2026-01-01 | PSL § 19, L 138 (2023-24) |
| AM-bidrag | 8% | 2026-01-01 | AMBL |
| ATP mensal (≥117 h) | 99,00 / 198,00 / 297,00 (empregado / empregador / total) | 2026-01-01 | virk.dk (ATP) |
| Feriegodtgørelse / ferietillæg | 12,5% / 1%; 2,08 dias/mês | 2026-01-01 | ferieloven (LBK nr 152 de 20/02/2024) |

## Artefatos entregues
| Artefato | Versão | Data | Arquivo/local | Observação |
|---|---|---|---|---|
| | | | | |

## Valores-chave (com vigência)
| Item | Valor | A partir de | Até | Fonte |
|---|---|---|---|---|
| | | | | |

## Decisões
- 

## Suporte (tickets)
| Data | Ticket | Assunto | Resolução | Mudou artefato? |
|---|---|---|---|---|
| | | | | |

## Pendências
- [ ]

## Correções ligadas
- _(links para entradas de [[correcoes]])_

## Fontes
- skill payroll-compliance-denmark (lida em 2026-10-02)
