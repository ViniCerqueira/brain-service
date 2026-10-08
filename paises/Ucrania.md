# Ucrânia

> Hub do país. Índice: [[00-INDEX]] · Skill: não há

Clientes ligados: Altium Ukraine (principal), GSK Ukraine (implementação), SDL Ukraine (citado no campo Company Name). Quem abre quase todos os tickets HRBS é Nataliia Hahan (especialista local de payroll UA do lado Mercans) [INCERTO: papel/time exato não declarado]. BA: Lily Li. Dev: Michael Mukosi John. Product: Mohit Jain. Datas de ticket são aproximadas (~).

## Situação
| Etapa | Status | Data | Observação |
|---|---|---|---|
| [[research-pipeline]] | ✅ | 2026-09 | WTC, CCG, DD e Report Specs entregues; versões vigentes (regra 8: maior versão citada): WTC V4.1, CCG V1.5, DD V3.10. Nos tickets, WTC V3.9 e CCG V1.5 estavam em draft em ~2026-09-21 (HRBS-14331); o chat de 2026-10-01 cita WTC V4.1 e DD V3.10. |
| [[design]] | 🔄 | 2026-09-28 | Specs D1, 4DF, D5, D6 em "In Review" (BA/Dev), faltando XML de amostra real; 1-PV (SR-414/415) em Open com perguntas da BA; Payslip (SR-340) In Progress com Dev. Advance Payroll sem especificação de desenvolvimento (HRBS-14255). |
| Produção (outro time) | — | | Ver [[fronteiras]] |
| [[suporte]] | 🔄 | 2026-09-29 | 18 tickets nos snapshots; vários sem resposta nossa (ver Pendências). |

## Artefatos entregues
| Artefato | Versão | Data | Arquivo/local | Observação |
|---|---|---|---|---|
| WTC master | V4.1 (vigente: maior versão) | V4.1 sem data; V3.9 ~2026-09-21 | Ukraine_Wage_Type_Catalogue_Mercans | Histórico: V3.2 (WT 62964, D1 accrual 13) → v3.4 → v3.5 (79417 Mobilization) → v3.6 (79414 Donor leave, 79415 Business trip) → v3.7 → v3.8 (20 PEs de gross-up) → V3.9. Lily publicou o "Finalized WTC" em Google Sheets (~2026-09-21). V3.9 (draft nos tickets) → V4.1 (chat: mercans-compliance) com "correções de maternidade pendentes de input do cliente". |
| CCG | V1.5 (vigente: maior versão; draft nos tickets) | ~2026-09-21 | Ukraine_Country_Configuration_Guide_FY2026 | Histórico: Module 8 v1.1 (~08-05) → v1.2 (~08-11) → V1.3 (~09-08, Advance Payroll) → V1.5 (V1.4 não citada). |
| Data Dictionary | V3.10 (vigente: maior versão) | ~2026-09-25 (V3.10); ~2026-08-19 (V3.8) | Ukraine_Data_Dictionary | Histórico: V3.3 (part_time_indicator) → V3.4 → V3.5 (HRBS-12368) → v3.7 → V3.8 (+ incremento chief_accountant_name; tickets) → V3.10 (chat), com chief_accountant_name, categoria D5 corrigida, No-Data Reason do 1-PV. |
| Report Spec D1 (UA-D1-001_UnifiedSocialContribution) | atualizada ~2026-08-20 | | SR-160 | In Review; falta XML de amostra real. |
| Report Spec 4DF (UA-4DF-001_PersonalTax) | atualizada ~2026-08-20 | | SR-161 | In Review; QC da Lily (09-28) com correções para o Dev. |
| Report Spec D5 (UA-D5-001_LabourRelations) | v3 | ~2026-08-20 | SR-162 | In Review. |
| Report Spec D6 (UA-D6-001_SpecialSeniority) | v3 | ~2026-08-20 | SR-163 | In Review; validação contra formulário J0510611 (v11), não v10 (chat). |
| Report Spec 1-PV mensal (UA-1PV-001, template Derzhstat S0301016) | sem número | | SR-414 | Open; perguntas da BA de 09-29. Chat: "pronta" em 12-08. |
| Report Spec 1-PV trimestral (UA-1PV-002, template S0301121) | sem número | | SR-415 | Open. |
| Report Spec UA-INTREP-001 (relatório interno) | sem número | snapshot 12-08-2026 | (chat: mercans-compliance) | "Pronta; nada postado no ticket" naquela data. [INCERTO: situação atual; liga-se ao HRBS-12548] |
| Payslip (Payslip Spec 1; templates Ukraine EN/UK) | sem número | | SR-340 | In Progress (Dev); template × spec inconsistentes. |
| WTC do cliente Altium (WTC_Altium_Ukraine_2026_2) | — | | HRBS-14331 | Mantido pela Nataliia/cliente. Fora do nosso escopo. |

## Valores-chave (com vigência)
Conteúdo estatutário geral: não há skill de país. Abaixo, só o discutido em ticket/chat. Salário mínimo, base máxima do ESV e tetos de per diem foram afirmados pela solicitante, não confirmados por nós.

| Item | Valor | A partir de | Até | Fonte |
|---|---|---|---|---|
| Coeficiente de gross-up de benefício não monetário | 1.219512, só na base do PIT | 2026 (ticket: "applicable for 2026") | | Art. 164.5 PKU; pp. 164.2.17 PKU (HRBS-12181) |
| Base do Military Levy e do USC sobre BIK | valor bruto, sem coeficiente | ⚠️ vigência? (posição DPS 2025-2026) | | §16-1, pidrozd. 10, rozd. XX PKU (HRBS-12181/14331) |
| Divisor do 62209 (Monthly bonus compensation) | 0.82 | ⚠️ vigência? | 0.77 (pedido, rejeitado) | Raciocínio sobre Art. 164.5 (HRBS-14331) |
| PIT | 18% | ⚠️ vigência? | | ⚠️ sem fonte (exemplo do HRBS-12181) |
| Military Levy | 5% | ⚠️ vigência? | | ⚠️ sem fonte (exemplo do HRBS-12181) |
| PIT Diia City | 5% | ⚠️ vigência? | | ⚠️ sem fonte (HRBS-14324, proposto pela solicitante) |
| ESV (USC) padrão do empregador | 22% | ⚠️ vigência? | | ⚠️ sem fonte (HRBS-12368/14331); chat: Lei 2464 ch.1 art.7 |
| ESV com deficiência | 8.41% sobre a base real, sem complemento até a base mínima | ⚠️ vigência? | | Instruction 449 s.III; DPS 04.02.2026 (HRBS-12631) |
| ESV do empregado | 0,00 (abolido) | 2016-01-01 | | Law 77-VIII (SR-160) |
| ESV: base mínima no mês de admissão/desligamento | não se aplica (incide sobre o salário real) | ⚠️ vigência? | | Instruction 449 s.III (HRBS-12631) |
| ESV sobre seguro de vida | Sim (só seguro médico e previdenciário são isentos) | ⚠️ vigência? | | Poryadok/Resolution 1170, p. 2, rozd. II (HRBS-14331) |
| ESV sobre maternidade (custeada pelo Pension Fund) | Sim, 22%; isenta de PDFO e Military Levy | ⚠️ vigência? | | p.1 ch.1 art.7 + ch.5 art.8 Lei 2464; p. 165.1.1 PKU (chat: mercans-compliance; HRBS-14331) |
| Salário mínimo | UAH 8.647 | 2026-01-01 | | ⚠️ sem fonte (Nataliia, HRBS-14331) |
| Base máxima do ESV | UAH 172.940/mês (20 × salário mínimo) | 2026 | | Lei 2464-VI, art. 7 parte 1 (Nataliia, HRBS-14331) |
| Per diem doméstico: teto | UAH 864,70/dia (0,1 × salário mínimo) | 2026 | | p. 170.9.1 PKU (Nataliia) |
| Per diem exterior: teto | EUR 80/dia, taxa NBU do dia | 2026 | | p. 170.9.1 PKU (Nataliia; confirmado: HRBS-14331 PDF, "For 2026 ... EUR 80 per calendar day") |
| Presente: parte não tributável | 25% do salário mínimo de 1º de janeiro (HRBS-14324); "25%" sem base (HRBS-12181) | ⚠️ vigência? | | subpar. 165.1.39 PKU (confirmado: HRBS-14324 txt, base = salário mínimo de 1º de janeiro; HRBS-12181 txt cita só "25% threshold", sem conflito) |
| Presentes de aniversário não tributáveis | PIT/Military = Não, 4DF 160 | ⚠️ vigência? | | p. 165.1.39 PKU (HRBS-14331) |
| Pagamento a FOP com comprovante de registro | PIT/Military/USC = Não, 4DF 157 (WT 62942) | ⚠️ vigência? | | p. 177.8 PKU (HRBS-14331) |
| Despesas de representação documentadas e publicitárias | isentas de PIT | ⚠️ vigência? | | Art. 170.9 PKU (HRBS-12181) |
| Prazo de PDFO/Military Levy | no momento da transferência (salário por banco); 3 dias bancários só para dinheiro/não monetário | ⚠️ vigência? | | TCU Art. 168.1, confirmado pela DPS (HRBS-12631) |
| Frequência do 4DF/D1 (pessoa jurídica) | mensal (só FOP: trimestral) | 2026-01-01 | | Law 4536-IX; MinFin Orders 4/243/284 (HRBS-12631) |
| Média de férias | 12 meses | ⚠️ vigência? | | Poryadok 100 p.2 |
| Média de donor leave e viagem | 2 meses; viagem paga o maior entre média e diária do mês | ⚠️ vigência? | | Poryadok 100 §8; LC Art. 121 §4; LC Art. 124 (donor) |
| Média de sick leave/maternidade | 12 meses (HRBS-12631/13392) × 6 meses (HRBS-14331) [INCERTO: contradição nossa] | ⚠️ vigência? | | Poryadok 1266 p.4 |
| Indexação | base month + índice acumulado (não é média) | ⚠️ vigência? | | Procedure 1078 |
| Compensação de férias não gozadas (79401) | média nova de 12 meses no desligamento | ⚠️ vigência? | | Poryadok 100, p. 2, segundo parágrafo |
| Proração de salário | dias úteis do horário | ⚠️ vigência? | | cartas de 27.05.2019 nº 4340 e 15.04.2019 nº 553 (emissores: Держпраці nº 4340 e Мінсоцполітики nº 553; confirmado: HRBS-12631 PDF, UTF-8) |
| Adiantamento (Advance Payroll): piso de cálculo | dias trabalhados × oklad puro, sem bônus; pagamento ao menos 2× por mês | ⚠️ vigência? | | Law 108/95-VR Art. 24; LC Art. 115 (HRBS-14255) |
| Fusão do Social Insurance Fund no Pension Fund | — | 2023-01-01 | | ⚠️ sem fonte (HRBS-14331) |
| Sick leave: quem paga | empregador dias 1-5; Pension Fund do 6º dia; PF desde o 1º dia para maternidade e cuidado de familiar | ⚠️ vigência? | | ⚠️ sem fonte (regras da Nataliia aceitas, HRBS-14331) |
| Sick leave: % por tempo de seguro | faixas divergentes (HRBS-13389 × HRBS-14331; ver Pendências) | ⚠️ vigência? | | ⚠️ sem fonte |
| Tributação de sick leave comum | 18% PDFO + 5% ML + 22% ESV (8.41% deficiência) | ⚠️ vigência? | | ⚠️ sem fonte (HRBS-14331) |
| Código de acréscimo do D1 para top-up ao salário mínimo (WT 62964) | 13 | ⚠️ vigência? | | MFU ordem 4 §IV (SR-160) |
| Envio do 1-PV trimestral | XML S0301121, assinado com KEP, só eletrônico | ⚠️ vigência? | | Law 2524-IX art. 10(4) (SR-415); portal: Кабінет респондента (Respondent's Cabinet; confirmado: SR-415 PDF) |
| Formulário D6 vigente | J0510611 (v11) | 2026-07-17 | J0510610 (v10) | DPS (chat: mercans-compliance, SR-163) |
| Per diem: parcela dentro do teto | não tributável (PIT/ML) | ⚠️ vigência? | | pp. 170.9.1 PKU (chat: mercans-compliance) |
| Grant direto da matriz estrangeira | entidade UA não é agente fiscal | ⚠️ vigência? | | p. 171.1 PKU (chat: mercans-compliance) |
| Stock options com recharge | 4DF 101, ESV Sim, gross-up 1,219512 no PIT, ML sobre o nominal | ⚠️ vigência? | | ⚠️ sem fonte (chat: mercans-compliance) |

## Decisões
- ~2026-04/05: a coluna de categoria de segurado do WTC não mapeia para o XML do D1; renomeada "Insured Person Type for ESV Engine" (20 = trabalho; 21 = contrato civil), filtro de motor; D1 Graf 8 vem de $hr.esv_category_code — nós, validado pela BA (SR-160).
- ~2026-05/06: part_time_indicator (0/1) no DD V3.3, obrigatoriedade M, sem default; WT 62964 com D1 accrual 13 — Lily corrigiu CM→M e concordamos (SR-160).
- ~2026-06/07: relatórios D1, D5, D6 e 4DF desenvolvidos em ucraniano (requisito estatutário) (SR-160).
- Antes de 2026-08: 1-PV mensal e trimestral ficam como specs separadas — não há base no Derzhstat para envio conjunto — Team Lead (chat: mercans-compliance).
- ~2026-08-03: não criar a série BIK "PIT sem Military Tax" — sem base legal; é diferença de base, não de incidência; WT 79417 Mobilization criado — nós (HRBS-12181).
- ~2026-08-05: donor leave (79414) e business trip (79415) novos; sick leave por outro regulamento (1266), não pela fórmula de férias — nós (HRBS-12631).
- ~2026-08-11: gross-up 1.219512 só na base do PIT; separação PIT/Military é regra de motor, não coluna Formula — nós (HRBS-12181). Mesmo dia: correções do CCG v1.2 (ver Correções).
- ~2026-08-12/13: gross-up só para benefício não monetário, limitado a 20 PEs (restrição do produto), em vez dos 109 códigos 4DF=126 — correção da Nataliia aceita; Lily/Dev desenvolvem (HRBS-12181, WTC v3.8).
- ~2026-08-13: DD V3.5 com 15 campos novos; salário em USD não entra no DD (é lógica de WTC) — nós (HRBS-12368).
- ~2026-08-19: dados históricos pré-go-live em grupo próprio do DD ("Historical Payroll Data (Pre-Go-Live Migration)"); indexação usa só o base month (Effective Date of Current Salary) — nós (HRBS-13392).
- ~2026-08-20: D1, D6, 4DF e D5 são anexos do formulário J05; 011/012/013 → HZ/HZN/HZU com C_DOC_STAN 1/2/3; HBOS/HBUH adicionados; D5 orientado a eventos (7 tipos); D6 com gatilho de 2 camadas — nós, com a BA (SR-160/161/162/163).
- ~2026-09-08: requisitos do Advance Payroll estão no CCG (Module 4 §4.2, Module 1 §1.2, Module 13); Mohit: não basta, falta especificação de desenvolvimento — nós; Product (HRBS-14255).
- ~2026-09-09/10: seguro de vida com USC=Sim; contractor FOP 4DF 157 no 62942; feriado/fim de semana trabalhado conta como dia inteiro na proração de bônus; catálogo do cliente Altium fora do escopo (mantemos só o master) — nós (HRBS-14331).
- ~2026-09-21: 65894 não existe e não será criado; PEs novos entram no WTC sem código e a Lily atribui — Lily/nós (HRBS-14331).
- ~2026-09-24: "staff" do 1-PV mensal = Labour Registry Person Category (D5) 1-2; categoria 3 (CPC) excluída; 1-PV trimestral: XML S0301121, KEP, só eletrônico — nós (SR-414/415).
- ~2026-09-25: campo chief_accountant_name no DD (alimenta o HBUH) — nós, pedido da Lily (SR-160).
- Mantido contra a objeção da Nataliia: ressalva "(if main place of work)" do contrato civil (CPC) na base mínima do ESV — nós (HRBS-12631) [INCERTO: sem tréplica].

## Suporte (tickets)
| Data | Ticket | Assunto | Resolução | Mudou artefato? |
|---|---|---|---|---|
| ~2026-09-01 | HRBS-12181 | WTC update: BIK sem Military Tax e gross-up (Altium) | Resolved. Série "PIT only" recusada; gross-up só na base do PIT, não monetário, 20 PEs; WTC v3.8 finalizado. Pendente: 65806/65808 (Art. 170.9), uso do 4DF 169. | Sim: WTC v3.4→v3.8, 79417 |
| ~2026-08-17 | HRBS-12368 | Data Dictionary e master data dos EEs (Altium) | Paused/SLA Exempt. DD V3.5 entregue. Pendente: pedido de apagar option mapper de Region, sem resposta. | Sim: DD V3.5 |
| ~2026-08-07 | HRBS-12548 | Relatórios estatísticos (1-PV, sick leave do Pension Fund, internos) | Paused; sem resposta no ticket. Gerou SR-414/415 e UA-INTREP-001. Itens 3-4 (Tab. 2 do PF, template de salário médio) bloqueados por input do cliente (chat). | Sim: specs 1-PV |
| ~2026-09-28 | HRBS-12631 | Reserva de férias, salário médio, revisão do CCG (Altium) | Pending on reporter. WTC v3.6 (79414/79415), CCG v1.1→v1.2. Pergunta da Nataliia sobre relatório de reserva de férias sem resposta. | Sim: WTC v3.6, CCG v1.2 |
| 2026-08-18 | HRBS-13389 | Insurance Record (tempo de seguro) | Open; sem resposta nossa | Não |
| ~2026-08-20 | HRBS-13392 | 12 meses de histórico de payroll (média) | Open (L2). Respondido: 3 elementos num grupo novo do DD. Duas réplicas da Nataliia sem resposta. | Sim: DD (grupo novo) |
| ~2026-08-24 | HRBS-13499 | Data Dictionary GSK Ukraine | Open; sem resposta nossa | Não |
| ~2026-09-11 | HRBS-14255 | Advance Payroll no nível país | Pending on reporter. Requisitos no CCG V1.3; Product pede especificação de desenvolvimento. | Sim: CCG V1.3 |
| 2026-09-08 | HRBS-14324 | Fórmulas de salário médio e benefício adicional | Open; sem resposta nossa | Não |
| ~2026-09-23 | HRBS-14331 | Checagem do catálogo WTC do cliente Altium | Resolved, com 6 perguntas novas da Nataliia sem resposta | Sim: WTC V3.9 (draft), CCG V1.5 (draft) |
| 2026-09-25 | HRBS-15216 | Data Dictionary check (obrigatoriedade, SSC Rate) | New, Unassigned; sem resposta nossa | Não |
| 2026-09-28 | SR-160 | Report Spec D1 (ESV) | In Review; HBOS/HBUH, chief_accountant_name; falta XML real | Sim: spec D1, DD |
| 2026-09-28 | SR-161 | Report Spec 4DF (PIT) | In Review; QC da Lily com 8 achados para o Dev | Sim: spec 4DF |
| 2026-09-28 | SR-162 | Report Spec D5 | In Review; spec v3; QC da Lily para o Dev | Sim: spec D5 v3 |
| 2026-09-28 | SR-163 | Report Spec D6 | In Review; spec v3; sample validado contra v11 (não v10) | Sim: spec D6 v3, DD (d6_duration_unit) |
| 2026-08-10 | SR-340 | Payslip UA | In Progress (Dev); template × Payslip Spec 1 inconsistentes | Não |
| 2026-09-29 | SR-414 | 1-PV mensal, SPEC | Open, prazo 2026-09-30; novas perguntas da BA de 09-29 | Sim: UA-1PV-001 |
| 2026-09-29 | SR-415 | 1-PV trimestral, SPEC | Open, prazo 2026-09-30; 2 perguntas da BA | Sim: UA-1PV-002 |

## Pendências
- [ ] Resolver nossa contradição sobre o período-base do sick leave: 6 meses (HRBS-14331, colunas K/X) × 12 meses (HRBS-12631 e 13392) — nós (HRBS-14331 × HRBS-12631/13392)
- [ ] Confirmar as faixas de % do sick leave por tempo de seguro (HRBS-13389: <5 anos 60%, 5-8 80%, 8+ 100% × HRBS-14331: <3 50%, 3-5 60%, 5-8 70%, >8 100%); não sabemos quais valores entraram no CCG V1.5 — nós/Nataliia (HRBS-13389, 14331)
- [ ] Código 4DF 128 para maternidade: Nataliia diz que 128 vale só para licença 126 + 14 dias e que 65700-65712 seriam 101 ou 126; contradiz o CCG — nós (HRBS-14331, pós-Resolved)
- [ ] Perguntas pós-Resolved do HRBS-14331: Severance 62180/62181 fora da base de ESV; per diem dentro/fora do teto (62570, 65570-65572, 65580-65582, 62965; risco de dupla tributação); stock options (cenário A/B, input do cliente/global team); códigos "102" e "sem imposto" (imagens não capturadas) — nós/cliente (HRBS-14331)
- [ ] Decidir o desenho final do gross-up de BIK: regra de motor × PE agregado 58134 (nunca construído) — Compliance/BA/Dev (HRBS-14331, HRBS-12181)
- [ ] Responder HRBS-13389 (Insurance Record: tipo, estático ou acumulado, ligação ao WTC de sick pay) — nós
- [ ] Responder HRBS-13499 (campos GSK; decidir se Grade 2, City of Work, Manager entram no DD de país) — nós
- [ ] Responder HRBS-14324 (fórmulas: base horária do Art. 107, paralisação Art. 113, variante de gross-up, presentes) — nós
- [ ] Responder HRBS-15216 (obrigatoriedade, remoção do 1C Personnel Number, SSC Rate, ESV Category Code, tradução); checar impacto em D5/D1 antes de tirar obrigatoriedade — nós (SR-160/162)
- [ ] SR-414 (1-PV mensal), perguntas da BA de 29/09, prazo 30/09 vencendo: categoria de "external part-time", formato de arquivo na Report Matrix, "No-Data Indicator", "average FTE headcount", exclusões do staff (maternidade, cuidado, mobilizados, suspensos; licença sem vencimento da lei marcial → 79410?), campos de deviation flag (25%/10%), option mapper inexistente na coluna O — nós (SR-414)
- [ ] SR-415 (1-PV trimestral), prazo 30/09: colunas E/F da Wage Fund Classification após mudança dos 4DF; coluna V em vermelho — nós (SR-415)
- [ ] XML de amostra real (não schema) para D1, 4DF, D5, D6; confirmar duplicatas PERIOD_MONTH/YEAR/D_FILL; HDDGV/HNDGV fora da spec — nós (SR-160/161/162/163)
- [ ] HRBS-13392: responder às duas réplicas da Nataliia (rótulo do denominador de dias úteis do horário; dois conjuntos de exclusão 1266/100 e onde moram) e ao mecanismo de carga — nós/L2 (HRBS-13392)
- [ ] HRBS-12631: relatório de reserva de férias no HRBlizz (leave module/Vaishnavi); código de acréscimo do D1 para 79414/79415 TBC; rótulo "theoretical" da semana 53; discordância da Nataliia sobre CPC — nós (HRBS-12631)
- [ ] HRBS-12368: pedido de apagar o option mapper de Region; confirmar salário USD no WTC — nós (HRBS-12368)
- [ ] HRBS-12181: confirmar com a Altium 65806/65808 (Art. 170.9: PIT=Não?) e uso do 4DF 169; resolver conflito de nomes do 65808 (HRBS-12181 e WTC v3.8: 65808 = Representation expenses (financial), 65810 = Life insurance; Nataliia no HRBS-14331 chamou 65808 de "Life Insurance (BIK)" e nossa resposta repetiu o rótulo; ver proposta em rev-UA) — nós/cliente (HRBS-12181, 14331)
- [ ] HRBS-12548: relatório do Pension Fund de sick leave (Tab. 2) e relatórios internos de cruzamento/salário médio sem tratamento registrado — nós (HRBS-12548; chat: itens 3-4 bloqueados por certificado em papel × eletrônico)
- [ ] Classificação de maternidade, recharge das stock options e 65805/65809 em 4DF 126 → 125 aguardam contato do cliente (Altium) (chat: mercans-compliance)
- [ ] SR-340: alinhar templates Payslip EN/UK com a Payslip Spec 1 (ESV Payer Number, division); confirmar [VERIFY WITH RA] sobre EDRPOU = ESV payer number — nós (SR-340)
- [ ] SR-163: possível erro do Dev ("Chief Accountant RNOCPP" → director_signatory_rnocpp) — Dev/nós [INCERTO] (SR-163)
- [x] Versões vigentes decididas pela regra 8 (2026-10-05): WTC V4.1, DD V3.10, CCG V1.5. Resta apenas confirmar o paradeiro da V1.4 do CCG (não citada) — nós (chat × tickets)
- [ ] HRBS-14255: confirmar se Compliance precisa entregar algo além do CCG V1.3 — Lily/Mohit (HRBS-14255)
- [ ] Valores sem fonte (PIT 18%, Military 5%, ESV 22%/8.41%, salário mínimo, base máxima do ESV, per diem) a confirmar com fonte oficial — nós (várias)

## Correções ligadas
Registradas em [[correcoes]] (via consolidação do grupo UA):
- Seguro de vida: USC Não → Sim (Poryadok 1170); contradizia nossa resposta do HRBS-12181 (HRBS-14331).
- 65894: changelog dizia que a linha foi criada; não existe e foi retirado (HRBS-14331).
- Divisor do 62209: 0.77 → 0.82 (HRBS-14331).
- CCG v1.2: prazo PDFO/ML, base mínima do ESV na admissão/desligamento, deficiência 8.41%, proração por dias úteis, 4DF mensal (HRBS-12631).
- CCG 8.2: lista de exclusão do 1266 aplicada às férias; citação do Social Insurance Fund (HRBS-14331).
- Gross-up: escopo de 109 códigos → só não monetários, 20 PEs; exemplo com base errada (2.360 → 2.439,02) (HRBS-12181).
- SR-163: sample D6 validado contra o formulário v10 superado → v11 (chat).
- Outras: ver lista completa em `correcoes-UA` do scratchpad.

## Fontes
- raw/tickets/extracao/2026-10-02-tickets-UA.md
- raw/chats/2026-10-01-mercans-compliance.md (trechos sobre Ucrânia)
- raw/chats/2026-10-01-compliance-research.md e raw/chats/2026-10-01-mercans-design-dev-kb.md (sem trechos sobre a Ucrânia)
