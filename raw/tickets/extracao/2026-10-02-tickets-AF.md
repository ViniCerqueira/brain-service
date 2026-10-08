# Tickets YouTrack: África (Namíbia, Congo, Gabão, Côte d'Ivoire)

> Extraído de `raw/tickets/txt/` (grupo g-AF). Os arquivos 01 e 02 tinham texto vazio e foram lidos dos PDFs originais em `raw/tickets/youtrack_tickets/`.
> Datas absolutas foram **estimadas** a partir da data de impressão do snapshot menos o "X days ago" do YouTrack (precisão de ±1 dia).
> Dados pessoais de empregados (nomes, IDs de empregado, salários individuais) citados nos tickets foram **omitidos**.
> Observação: o arquivo `34 - Ticket - HRBS-13860 - Naersa file failing again this month` está na lista do grupo, mas é **Irlanda / Omnicom** (fora da África). Registrado no fim, em "Fora do grupo".

---

# NAMÍBIA

## HRBS-12072 — Mais códigos (pay elements) para Baker Hughes Namibia
- **País:** Namíbia / **Cliente:** Baker Hughes / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** SLA Exempt (First Reply e Resolution Time "Paused") / **Fase da entidade:** Implementation
- **Datas:** criado ~2026-07-20; última atualização ~2026-07-28 (Pradeep Duraisamy); snapshot de 2026-08-04. Sem resolução.
- **Arquivos-fonte:** `02 - Ticket HRBS-12072 - More codes for Baker Hughes Namibia` (.txt vazio; lido do .pdf)
- **Quem pediu:** Daniel Kelvin Balogun (implementação/consultor do lado Mercans/HRBlizz [INCERTO quanto ao papel exato]).
- **Pergunta / problema:** pedem pay elements adicionais para a Namíbia com duas combinações de flags: (1) Subject to Tax = Yes / SSNC = Yes / Pension = No (dizem que nenhum código da Compliance WTC tem essa combinação); (2) SSNC = No / ECF = Yes / Pension = No (exemplos: Overtime – Normal Workday 1.5x, Overtime). Pedem a lista completa de códigos aplicáveis. Link da WTC de compliance no ticket (Google Sheets).
- **Resposta / decisão:**
  - ~2026-07-28, Mohit Jain (Head of Compliance Product): a combinação SSNC=No / ECF=Yes / Pension=No **já existe na WTC**.
  - ~2026-07-28, Mohit Jain: duvida que a combinação Tax=Yes / SSNC=Yes / Pension=No exista; "se tiver certeza, confirme com Wallisson".
  - **Nenhuma resposta do Wallisson no snapshot.**
- **Valores estatutários:** nenhum citado.
- **Artefato afetado:** WTC (Compliance WTC Namíbia); ticket relacionado HRBS-12074 "Configure Entity using the WTC for Baker Hughes Namibia" (inward mention). Versão não citada.
- **Erros corrigidos:** nenhum.
- **Pendências:** confirmação (Wallisson) sobre a existência da combinação Tax=Yes / SSNC=Yes / Pension=No.
- **Fronteira:** configuração da entidade (HRBS-12074) é implementação.

## HRBS-12101 — Amostras (samples) dos relatórios estatutários da Namíbia
- **País:** Namíbia / **Cliente:** Baker Hughes / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Implementation
- **Datas:** criado ~2026-07-21; última atualização ~2026-07-26 (Manju Shetija); snapshot 2026-08-12. Sem resolução (First Reply −22d, Resolution −19d: SLA estourado).
- **Arquivos-fonte:** `16 - Ticket - HRBS-12101 - Provide samples for Namibia stat reports`
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** as duas pastas do Drive indicadas têm só os arquivos de spec, sem samples. Pedem samples (urgente) para: **SSC – Form Ten**, **PAYE 5 certificate**, **ETX**.
- **Resposta / decisão:** nenhuma resposta registrada no snapshot.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Report Specs da Namíbia (SSC Form Ten, PAYE 5, ETX) — falta de samples.
- **Erros corrigidos:** nenhum.
- **Pendências:** fornecer samples dos três relatórios — Compliance (assignee Wallisson).
- **Fronteira:** nenhuma explícita.

## HRBS-12111 — Revisão da Report Matrix da Namíbia
- **País:** Namíbia / **Cliente:** Baker Hughes (Baker Hughes Namibia) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Implementation
- **Datas:** criado ~2026-07-21; última atualização ~2026-07-21/22 (Ruchi Gupta); snapshots 2026-08-06 e 2026-08-10. Sem resolução (Resolution −13d → −16d).
- **Arquivos-fonte:** `06 - Ticket - HRBS-12111 - Please review this report matrix for Namibia`; `10 - Ticket - HRBS-12111 - Please review this report matrix for Namibia`
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** revisar a report matrix da Namíbia (anexo `Baker_Namibia_Report_Matr...xlsx`, 102 kB), "principalmente os relatórios estatutários".
- **Resposta / decisão:** só acknowledgement do suporte (Pradeep Duraisamy) e pedido a Manju Shetija para revisar. Nenhuma resposta de compliance nos snapshots.
- **Evolução entre snapshots:** nenhuma mudança de conteúdo entre 06/08 e 10/08 (só o SLA mais negativo).
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Report Matrix da Namíbia (cliente).
- **Pendências:** revisão da matrix — Compliance (assignee Wallisson; comentário pedia Manju).
- **Fronteira:** nenhuma explícita.

## HRBS-12483 — WTC Namíbia: confirmação de elementos pensionáveis
- **País:** Namíbia / **Cliente:** Baker Hughes Namibia / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Implementation
- **Datas:** criado ~2026-07-29; última atualização ~2026-07-30 (Ruchi Gupta); snapshot 2026-08-04.
- **Arquivos-fonte:** `01 - Ticket HRBS-12483 - Namibia WTC - Persionable element confirmation` (.txt vazio; lido do .pdf)
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** na Compliance WTC, o 62100 e outros códigos (62148, 62149, 62147, 62146, 62961) estão como **Pension = YES**; na WTC do cliente, pension está como **NO**. Pedem orientação. Link da WTC no ticket.
- **Resposta / decisão:** só "Kindly check this" de Ruchi Gupta para Wallisson. **Sem resposta no snapshot.**
- **Valores estatutários:** nenhum.
- **Artefato afetado:** WTC Namíbia (flag Subject to Pension dos códigos 62100, 62146–62149, 62961).
- **Pendências:** decidir se esses códigos são pensionáveis — Wallisson.
- **Fronteira:** nenhuma.

## HRBS-13602 — SS Employee Share (2551) não aplicado como dedução pré-imposto antes do Payroll Tax (2552)
- **País:** Namíbia / **Cliente:** Baker Hughes (BH Namibia, entidade REF-LE-03-060) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Implementation
- **Datas:** criado ~2026-08-21; última atualização 2026-08-24 (Mohit Jain); snapshot 2026-08-24.
- **Arquivos-fonte:** `32 - Ticket - HRBS-13602 - SS Employee Share (2551) not applied as pre-tax deduction before Payroll Tax calculation — Namibia`
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** o WT 2551 (SS Employee Share, "capped at NAD 99/month") reduz o Net Pay mas não reduz a base do Payroll Tax (WT 2552). Alegam que a WTC da Baker Hughes documenta "Taxable base = Basic + Housing ... − SS Ee Pension Add" e que é prática padrão do PAYE namibiano deduzir a SSC do empregado antes do imposto. Evidência: diferença sistemática de 99 × 30% = 29,70/mês em empregados com dados limpos (março/2026). Pedem: confirmar com o build se 2551 reduz a base de 2552, corrigir o cálculo e reprocessar. Notam que é independente de problemas já abertos sobre **metodologia de anualização** e **constante de faixas desatualizada (stale-bracket)**.
- **Resposta / decisão:**
  - 2026-08-24, Mohit Jain (Head of Compliance Product): "pela informação atual disponível, **não é dedução pré-imposto**"; 2551 = **MSD EE Contribution**; cita o CCG (link Google Docs) com screenshot. Reatribuiu a Wallisson para verificar e resolver.
  - **Sem resposta do Wallisson no snapshot.**
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Teto da contribuição SS do empregado (WT 2551) | NAD 99/mês | sem vigência no ticket | alegação do solicitante (WTC do cliente); sem fonte oficial no ticket |
| Taxa marginal usada no exemplo | 30% | sem vigência no ticket | sem fonte no ticket (cálculo do solicitante) |

- **Artefato afetado:** CCG Namíbia (posição de Mohit), WTC (WT 2551, 2552), GTN.
- **Erros corrigidos:** nenhum ainda; divergência aberta entre a alegação do cliente/implementação (pré-imposto) e o CCG (não pré-imposto).
- **Pendências:** decisão final de Wallisson sobre o tratamento fiscal do 2551; outros problemas abertos citados (anualização e faixas desatualizadas) [INCERTO: tickets não identificados].
- **Fronteira:** "build team" (Dev/configuração) para o flag do WT 2551.

## HRBS-14605 — Relatórios estatutários da Namíbia: confirmação de configuração
- **País:** Namíbia / **Cliente:** Baker Hughes (BH Namibia) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Implementation
- **Datas:** criado ~2026-09-15; última atualização ~2026-09-24 (Manju Shetija); snapshot 2026-09-25. Resolution −7d.
- **Arquivos-fonte:** `86 - Ticekt - HRBS-14605 - Namibia Statutory Reports - Configuration Confirmation`
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** confirmar o status de configuração de: (1) Monthly PAYE Return (NamRA, até 20 dias após o fim do mês; faixas progressivas; ano fiscal março–fevereiro); (2) SSC Contribution Return (pesquisa do cliente com informação conflitante: 0,9%/0,9% sobre ganhos seguráveis com teto ~NAD 11.000/mês vs. valor fixo); (3) VET Levy Return (1%, só empregador, Namibia Training Authority, acima de um limite de folha); (4) IT12E (certificados anuais) e IT14E (reconciliação anual), até 30 de junho.
- **Resposta / decisão:**
  - ~2026-09-15, Mohit Jain: "está em desenvolvimento".
  - ~2026-09-18, Katrin Rudi: em configuração: Monthly PAYE Return, Gross to Net, SSC Contribution Return. **Payslip já configurado e em revisão com Compliance.** Relatórios em configuração seriam desenvolvidos até **25/09** e depois vão para revisão de Compliance.
  - ~2026-09-18, Mohit Jain: "só temos esses relatórios; **não temos VET Levy Return nem IT12E**".
  - **Nenhuma resposta do Wallisson** sobre taxa/teto da SSC no snapshot.
- **Valores estatutários (todos citados pelo cliente como pesquisa própria, não confirmados):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Prazo do Monthly PAYE Return | 20 dias após fim do mês | sem vigência no ticket | sem fonte no ticket (alegação do cliente) |
| Ano fiscal Namíbia | março a fevereiro | sem vigência no ticket | sem fonte no ticket (alegação do cliente) |
| SSC empregado/empregador | 0,9% / 0,9% de insurable earnings, teto ~NAD 11.000/mês (cliente diz haver fontes conflitantes) | sem vigência no ticket | sem fonte no ticket — [INCERTO], não confirmado por Compliance |
| VET Levy | 1%, só empregador, acima de limite de folha | sem vigência no ticket | sem fonte no ticket (alegação do cliente) |
| Prazo IT12E / IT14E | 30 de junho após o fim do ano fiscal | sem vigência no ticket | sem fonte no ticket (alegação do cliente) |

- **Artefato afetado:** Report Specs/relatórios Namíbia (PAYE Return, SSC Return, G2N), Payslip (em revisão de Compliance).
- **Erros corrigidos:** nenhum.
- **Pendências:** confirmar taxa/teto SSC aplicados (Compliance); revisão de Compliance dos relatórios após 25/09 e do payslip; decisão sobre VET Levy Return, IT12E e IT14E (não existem hoje) — Mohit/Compliance.
- **Fronteira:** desenvolvimento/configuração dos relatórios por Katrin Rudi (time de configuração/Dev [INCERTO quanto ao time]).

---

# CONGO (Congo-Brazzaville)

## HRBS-12110 — Revisão da Report Matrix do Congo
- **País:** Congo (Brazzaville) / **Cliente:** Baker Hughes (Baker Hughes Congo) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Implementation
- **Datas:** criado ~2026-07-21; última atualização ~2026-07-21 (Pradeep Duraisamy); snapshot 2026-08-13. Resolution −20d.
- **Arquivos-fonte:** `20 - Ticket - HRBS-12110 - Plaese review this report matrix for Congo`
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** revisar a report matrix do Congo (anexo `Reporting Matrix - Congo`, 417 kB) e dizer se pode ir ao cliente para revisão.
- **Resposta / decisão:** só o repasse de Pradeep a Wallisson. **Sem resposta no snapshot.**
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Report Matrix Congo.
- **Pendências:** revisão — Wallisson.
- **Fronteira:** nenhuma.

## HRBS-12472 — Payslips Congo & Gabão: estado civil, nº de filhos, nº de partes
- **País:** Congo (Brazzaville) e Gabão / **Cliente:** Baker Hughes / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** SLA Exempt (Resolution "Paused") / **Fase:** Implementation
- **Datas:** criado ~2026-07-29; última atualização ~2026-08-10 (Manju Shetija); snapshot 2026-08-11.
- **Arquivos-fonte:** `13 - Ticket - HRBS-12472 - Payslips - Congo & Gabon`
- **Quem pediu:** Daniel Kelvin Balogun, repassando o cliente (o consultor fiscal do cliente diz que os campos devem constar no payslip "conforme recomendação do país").
- **Pergunta / problema:** incluir no payslip do Congo e do Gabão: **estado civil**, **número de filhos**, **número de partes (shares)**.
- **Resposta / decisão:**
  - ~2026-08-10, Manju Shetija — **Gabão:** serão exibidos estado civil e nº de partes; **nº de filhos não é mencionado e não é exigido**; pediu justificativa. **Congo:** atribuído a Wallisson para confirmação.
  - **Sem resposta do Wallisson para o Congo no snapshot.**
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Payslip Congo e Payslip Gabão.
- **Pendências:** confirmação para o Congo (Wallisson); justificativa do cliente para nº de filhos (Gabão).
- **Fronteira:** nenhuma.

## HRBS-13841 — CAMU não consta na WTC de compliance do Congo
- **País:** Congo (Brazzaville) / **Cliente:** Baker Hughes (Congo BH) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Pending on reporter / **Fase:** Implementation
- **Datas:** criado 2026-08-27; última atualização ~2026-08-31 (Daniel Kelvin Balogun); snapshots 2026-08-27 e 2026-08-31.
- **Arquivos-fonte:** `33 - Ticket - HRBS-13841 - We do not have CaMU on compliance WTC in CONGO`; `35 - Ticekt - HRBS-13841 - We do not have CaMU on compliance WTC in CONGO`
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** a WTC do cliente tem "CAMU Health Insurance (Employee)" com taxa efetiva observada ~0,5% dos ganhos regulares (excl. bônus extraordinários; ~0,46–0,47% em nov/25; varia mês a mês). Isso é o mesmo que o "CG Health Insurance EE" da WTC de compliance?
- **Resposta / decisão nossa:**
  - ~2026-08-27, **Wallisson:** confirmado — o item do cliente é a **CAMU solidarité (0,5% sobre a fração do salário acima de 500.000 XAF)**, **não** a CAMU empregado 2,27%. Segundo a autoridade CAMU Congo (camu-congo.fr), são **dois fluxos distintos**: contribuição 4,55% empregador / 2,27% empregado (6,82% combinado) e, separadamente, 0,5% de "contribution de solidarité nationale" sobre a fração acima de 500.000 XAF. A fórmula do cliente bate exatamente com esta última.
  - ~2026-08-31, Daniel (follow-up): pede confirmar se os 4,55%/2,27% são estatutários — o cliente **não tem** no G2N dele, mas o G2N do HRB tem.
- **Evolução entre snapshots:** 27/08 Open sem resposta → 31/08 resposta do Wallisson + nova pergunta; estado "Pending on reporter" apesar da pergunta em aberto.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| CAMU contribuição empregador | 4,55% | sem vigência no ticket | CAMU Congo (camu-congo.fr), citado por Wallisson |
| CAMU contribuição empregado | 2,27% | sem vigência no ticket | CAMU Congo (camu-congo.fr) |
| CAMU combinado | 6,82% | sem vigência no ticket | CAMU Congo (camu-congo.fr) |
| Contribution de solidarité nationale (CAMU) | 0,5% sobre a fração do salário acima de 500.000 XAF | sem vigência no ticket | CAMU Congo (camu-congo.fr) |

- **Artefato afetado:** WTC Congo (compliance vs. cliente); G2N.
- **Erros corrigidos:** o item "CAMU Health Insurance (Employee)" do cliente estava sendo comparado com a CAMU 2,27% → correto: corresponde à CAMU solidarité 0,5% acima de 500.000 XAF. A WTC de compliance, pelo ticket, não tem a linha de solidarité [INCERTO — o título diz "não temos CAMU", mas não fica explícito se a solidarité será adicionada].
- **Pendências:** responder se 4,55%/2,27% são estatutários e por que o cliente não aplica (Wallisson); possivelmente incluir a CAMU solidarité na WTC de compliance [INCERTO].
- **Fronteira:** nenhuma.

## HRBS-14055 — Occupancy tax e Region tax são regulatórios no Congo?
- **País:** Congo (Brazzaville) / **Cliente:** Baker Hughes (BH Congo) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Implementation
- **Datas:** criado ~2026-09-01; última atualização 2026-09-02 (Pradeep Duraisamy); snapshot 2026-09-02.
- **Arquivos-fonte:** `38 - Ticket - HRBS-14055 - Is occupancy tax & Region tax regulatory in Congo`
- **Quem pediu:** Daniel Kelvin Balogun.
- **Pergunta / problema:** "occupancy tax" e "Region tax" aparecem no G2N do cliente; são obrigatórios/regulatórios? Anexo: `Congo Payregister Jan'26` (3 MB) e link da WTC.
- **Resposta / decisão:** **sem resposta no snapshot.**
- **Valores estatutários:** nenhum.
- **Artefato afetado:** WTC Congo.
- **Pendências:** resposta de Compliance (Wallisson).
- **Fronteira:** nenhuma.

---

# GABÃO
- Só aparece em **HRBS-12472** (ver Congo acima): payslip do Gabão exibirá estado civil e nº de partes; nº de filhos não exigido (Manju Shetija, ~2026-08-10).
- Em **HRBS-14996** (Côte d'Ivoire), Wallisson observa que "CNAMGS" e "FNH" são **órgãos gaboneses** que não existem na CI (rótulos errados no registro do cliente CI).

---

# CÔTE D'IVOIRE

## CT-A-620 — CI: Specifications (artigo de Knowledge Base, projeto Compliance)
- **País:** Côte d'Ivoire / **Cliente:** nenhum (spec genérica do país) / **Tipo:** artigo de Knowledge Base (não é ticket) / **Prioridade/Estado:** n/a
- **Datas:** criado ~2026-08-05 por Mohit Jain; atualizado ~2026-08-07; snapshot 2026-08-14. Sub-artigos: CT-A-621 CI: Taxable Gross, CT-A-622 CI: Gross, CT-A-623 CI: Tax Table (atualizados em 05/08/2026).
- **Arquivos-fonte:** `21 - Tciket - CT-A-620 - CI; Specifications`
- **Quem escreveu:** Mohit Jain (Head of Compliance Product).
- **Conteúdo:** especificação de configuração das regulações CI no motor (IDs 9384011–9384181). O texto extraído da tabela está **muito fragmentado** (colunas quebradas); a leitura abaixo é a melhor reconstrução possível, e tudo que depende do alinhamento de colunas está marcado [INCERTO].
  - **Flags/HR fields:** 58238 CNPS Eligibility (bool); 58202 CNPS Work Injury Eligibility (bool); 58295 $actual_prorata_days; 58203 Exemption from DGI General and National Contribution; 58215 Worker Type (0 Local, 1 Foreign); 58216 Intern/Apprentice (1 Intern – primeiros 12 meses, 2 Apprentice); `number_of_dependent_child_not_disabled` / `_disabled`.
  - **58205 Family Situation Factor (nº de partes):** 1 + 1 (casado, ou viúvo com filhos) + 0,5 × filhos não deficientes + 1 × filhos deficientes + 0,5 (solteiro/divorciado com filhos); máximo 5.
  - **Regulações (ordem 11 a 181):** CI Gross Base; CI Gross Taxable Base; CI CNPS Pension Base; CI CNPS Pension Contribution (EE 6,30% / ER 7,70%; asserção CNPS Eligibility = 1 e prorata > 0); CI CNPS Universal Health Cover Contribution (asserção CNPS Eligibility = 1); CI CNPS (Family Benefits, Maternity, Injury) Base; CI CNPS (Family Benefits, Maternity, Injury) Contribution (ER 5,00%, ER 0,75%, e AT/MP via "Employer Rate Account 52560" quando Work Injury Eligibility = 1); CI DGI Capping for Interns – YTM; CI DGI Balance Capping for Interns (floor/ceiling 1.800.000 [INCERTO: anual]); CI DGI Base; CI DGI Contribution General and National (asserção NOT exemption 58203); CI DGI Contribution – Others; CI Private Pension Capping (EE 10%, MIN(base; 320.000)); CI Private Pension; CI Taxable Base; CI Monthly Tax Gross (tabela "CI: Tax Table", tipo differential); CI Family Tax Credits; CI Monthly Tax Net.
  - **RICF (Family Tax Credits):** MAX((partes − 1) × 11.000; 0).
- **Valores (como configurados na spec; sem fonte legal no artigo):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| CNPS pensão empregado / empregador | 6,30% / 7,70% | sem vigência no artigo | sem fonte no ticket (spec de configuração) |
| CNPS pensão base — local/intern (58216 ≤ 1): floor / ceiling | 900.000 / 40.500.000 [INCERTO: leitura de colunas quebradas; parecem valores anuais = 12 × 75.000 e 12 × 3.375.000] | sem vigência | sem fonte no ticket |
| CNPS pensão base — apprentice (58216 = 2): floor = ceiling | 450.000 [INCERTO] | sem vigência | sem fonte no ticket |
| CNPS PF/Maternidade/AT base — 58216 ≤ 1: floor/ceiling | 840.000 [INCERTO: parece anual = 12 × 70.000] | sem vigência | sem fonte no ticket |
| CNPS PF/Maternidade/AT base — apprentice | 450.000 [INCERTO] | sem vigência | sem fonte no ticket |
| CNPS Universal Health Cover (CMU) floor/ceiling | 6.000 [INCERTO: a qual linha pertence] | sem vigência | sem fonte no ticket |
| Prestações familiares (empregador) | 5,00% | sem vigência | sem fonte no ticket |
| Maternidade (empregador) | 0,75% | sem vigência | sem fonte no ticket |
| DGI – taxas empregador listadas | 9,20% (asserção Worker Type = 1, estrangeiro), 1,20%, 0,40%, 1,20% [INCERTO: distribuição entre "General and National" e "Others"] | sem vigência | sem fonte no ticket |
| Capping DGI para estagiários | 1.800.000 [INCERTO: período] | sem vigência | sem fonte no ticket |
| Previdência privada — teto | 10% limitado a 320.000 [INCERTO] | sem vigência | sem fonte no ticket |
| RICF por meia-parte acima de 1 | 11.000 por parte adicional | sem vigência | sem fonte no ticket |

- **Artefato afetado:** spec de configuração CI (equivalente a WTC/regulações do motor); sub-artigos Taxable Gross, Gross, Tax Table.
- **Erros corrigidos:** nenhum no artigo. Obs.: em HRBS-14996 Wallisson aponta que **não existe linha de CE** (contribuição de expatriados 9,2%) no GTN do cliente — mas a spec CT-A-620 parece ter um 9,20% com asserção Worker Type = 1 [INCERTO se é a mesma coisa].
- **Pendências:** nenhuma no artigo.
- **Fronteira:** é spec de configuração do produto (Mohit / Compliance Product).

## HRBS-14714 — Aplicabilidade do ITS na folha da Baker Hughes Côte d'Ivoire
- **País:** Côte d'Ivoire / **Cliente:** Baker Hughes / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / **Fase:** Live/BAU
- **Datas:** criado ~2026-09-16; última atualização 2026-09-16 (Mohit Jain, sem comentário visível); snapshot 2026-09-16. First Reply 6h.
- **Arquivos-fonte:** `75 - HRBS-14714 - Confirmation Required — Applicability of ITS (Income Tax) for Baker Hughes Ivory Coast Payroll`
- **Quem pediu:** Sivaranjani Subbarayula.
- **Pergunta / problema:** confirmar se o ITS é aplicável e deve ser retido para os empregados da CI no quadro estatutário atual; confirmar as faixas/alíquotas atuais do ITS e o tratamento do RICF para validar a WTC. Anexo: `BH Ivory Coast Payregister Ja...` (24 kB).
- **Resposta / decisão:** **sem resposta no snapshot.** Na prática foi tratada em **HRBS-14996** (mesmo assunto, aberto por Sivaranjani em ~22/09) [INCERTO: se os tickets foram vinculados].
- **Valores estatutários:** nenhum citado.
- **Artefato afetado:** WTC CI (ITS, RICF).
- **Pendências:** resposta formal neste ticket.
- **Fronteira:** nenhuma.

## HRBS-14996 — CI: "Single Tax Regime" (Impôt Synthétique / Régime Simplifié) e isenção de ITS dos empregados
- **País:** Côte d'Ivoire / **Cliente:** Baker Hughes (Baker Hughes EHO Ltd; entidade REF-LE-03-105; campo Client "No client" no ticket) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Pending on reporter (Resolution Paused) / **Fase:** não definida no ticket
- **Datas:** criado ~2026-09-22; última atualização 2026-09-28 (Sivaranjani Subbarayula); snapshots 2026-09-23, 2026-09-25, 2026-09-28. Sem resolução.
- **Arquivos-fonte:** `80 - Ticket - HRBS-14996 - Côte d'Ivoire Single Tax Regime ...`; `88 - Ticket - HRBS-14996 - ...`; `91 - Ticket - HRBS-14996 - ...`
- **Quem pediu:** Sivaranjani Subbarayula (com Govind Thakur anexando os registros do cliente).
- **Pergunta / problema:** o sistema calcula ITS, mas o cliente diz que a população está no "Single Tax Regime", sem retenção de PIT na folha. Pedem a lógica de flag para distinguir empregados STR dos do regime padrão. Ponto adicional: o sistema usa teto de **70.000** para "CNAMGS" e "FNH", o registro do cliente usa **75.000**.
- **Resposta / decisão nossa:**
  - **~2026-09-22 (Wallisson), resposta 1:**
    1. **Nenhum flag STR deve ser configurado; o ITS continua devido.** O impôt des microentreprises (e o régime de l'entreprenant) é "libératoire des autres impôts et taxes, à l'exclusion de l'ITS ... aussi bien à la charge des salariés que de l'employeur" (DGI, *Le Système Fiscal Ivoirien*). Substitui patente, BIC/BNC e TVA da entidade; nunca cobriu o ITS retido sobre salários. Também é inaplicável de fato: o regime tem teto de 200.000.000 XOF de faturamento anual, e só o registro de janeiro mostra 18 empregados e 46.100.070 XOF de remuneração no mês. Se o cliente insistir, pedir o instrumento específico (convention d'établissement, agrément ou ruling da DGI) — "nome de regime não é isenção".
    2. **Teto: 70.000 está correto.** PF (5%), maternidade (0,75%) e AT/MP (2–5%) têm teto de 70.000 XOF/mês; **75.000 é o SMIG = piso da assiette, não teto.** Pensão tem teto de 3.375.000 (45 × SMIG). Fonte: ficha CLEISS CI, atualizada em 1º/01/2025. O arquivo do cliente é inconsistente (17 empregados no 75.000, 1 no 70.000). "CNAMGS" e "FNH" são órgãos gaboneses que não existem na CI; os valores são AT/MP a 3% e PF+AM a 5,75%.
    3. **Defeitos no GTN** (REF-P201-861, janeiro) — precisam de tickets separados: ver "Erros corrigidos".
    - Conferido: a aritmética do ITS está correta (faixas pós-2024 menos RICF de 11.000 para 2 partes).
  - **~2026-09-23 (Wallisson), resposta 2** (após o cliente enviar uma "confirmação de ITS"): pede ao cliente (1) a "Déclaration du Prestataire de service" trimestral (Impôt BIC Pétrole/Gaz, e-impots.gouv.ci) e (2) prova de "nationalité étrangère" (Annexe fiscale 2019 art. 26), para confirmar se a entidade se enquadra no **régime des prestataires de services pétroliers** — e não no impôt synthétique (que exclui ITS por lei). Confirmado isso, configura-se a lógica de flag pedida.
  - ~2026-09-25: Sivaranjani anexa 3 PDFs (tax declaration of existence; resolução de 24/11/2023; "Réponse demande de remb...") e pede para habilitar o flag. Govind: um dos documentos ainda está pendente no cliente.
  - **~2026-09-25 (Wallisson), resposta 3:** **nacionalidade estrangeira confirmada** — a entidade é succursale (D1020) de empresa estrangeira (sede em Bermudas; resolução do board de 24/11/2023: Baker Hughes EHO FZE, Jebel Ali Free Zone, EAU). **Regime confirmado para 2025:** carta DGI nº 0984/MFB/DGI/DGE de 19/08/2025 aceita o IFPGAZ declarado e pago pela Baker Hughes EHO Ltd (NCC 0211442C) sob o régime des prestataires de services pétroliers. **A confirmação do flag virá com a declaração IFPGAZ de 2026.**
  - ~2026-09-28, Sivaranjani: pede versão detalhada em inglês, diz "não precisamos da resposta de IA", pergunta se é necessário obter esses documentos todo ano; o cliente está firme no processo de isenção e **escalou para Marko**.
- **Evolução entre snapshots:** 23/09 (Pending on reporter, só resposta 1) → 25/09 (In Progress; resposta 2, docs anexados, um pendente) → 28/09 (Pending on reporter; resposta 3 e cobrança/escalonamento).
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Teto de faturamento do impôt des microentreprises | 200.000.000 XOF/ano | sem vigência no ticket | DGI, Le Système Fiscal Ivoirien [INCERTO se a fonte cobre o teto ou só a exclusão do ITS] |
| Teto CNPS PF / maternidade / AT-MP | 70.000 XOF/mês | ficha atualizada em 2025-01-01 | CLEISS — ficha de contribuições CI |
| SMIG (piso da assiette) | 75.000 XOF/mês | ficha atualizada em 2025-01-01 | CLEISS |
| Teto CNPS pensão | 3.375.000 XOF/mês (45 × SMIG) | ficha atualizada em 2025-01-01 | CLEISS |
| Prestações familiares (empregador) | 5% | ficha atualizada em 2025-01-01 | CLEISS |
| Maternidade (empregador) | 0,75% | ficha atualizada em 2025-01-01 | CLEISS |
| AT/MP (empregador) | 2–5% (cliente aplica 3%) | ficha atualizada em 2025-01-01 | CLEISS |
| CN employeur | 1,2% | sem vigência no ticket | sem fonte no ticket (citado por Wallisson) |
| CE expatriados | 9,2% | sem vigência no ticket | sem fonte no ticket |
| Contribuições máximas no teto (EE pensão / ER pensão / PF / AM / AT-MP 3%) | 212.625 / 259.875 / 3.500 / 525 / 2.100 XOF | derivado dos tetos acima | cálculo de Wallisson |
| Prime de transport isenta (Abidjan) | 30.000 XOF | arrêté de 30/01/2020 | arrêté 30/01/2020 (citado por Wallisson) |
| RICF | 11.000 para 2 partes | sem vigência no ticket | sem fonte no ticket |
| Faixas ITS | "pós-2024" (não detalhadas) | pós-reforma 2024 | sem fonte no ticket |

- **Artefato afetado:** WTC/GTN CI (wage types 2517, 2537, 2556, 2566, 2531, 2538, 2560, 2569; falta linha CE); configuração de flag de isenção ITS (não criado).
- **Erros corrigidos (apontados por nós):**
  - Cliente/solicitante: "Single Tax Regime isenta ITS dos empregados" → **errado**: impôt synthétique/microentreprises exclui expressamente o ITS; o enquadramento possível é o régime des prestataires de services pétroliers (em verificação).
  - Cliente: teto de 75.000 → **errado**: 75.000 é o piso (SMIG); o teto é 70.000.
  - Rótulos do cliente "CNAMGS"/"FNH" → órgãos gaboneses; na CI são AT/MP 3% e PF+AM 5,75%.
  - GTN: pensão CNPS lançada e estornada (2517 +/2556 −; 2537 +/2566 −) → nenhuma pensão CNPS sendo cobrada de nenhum lado.
  - GTN: empregado acima do teto de pensão com contribuições erradas → corretas são as máximas no teto (tabela acima).
  - Rótulos de wage types: 2531 diz 5,75% mas paga PF 5%; 2538 diz "Work Accident 0,75%" mas paga maternidade; 2560 paga o AT/MP real; 2569 rotulado "EIS" (não existe na CI) paga CN employeur 1,2%; falta linha CE (expatriados 9,2% subcobrados).
  - Bases: o cliente exclui 30.000 de transporte das bases ITS e CNPS (Abidjan) e exclui a ajuda de moradia da base ITS; o motor não aplica nenhum dos dois. Transporte deve ser parametrizado por localidade; exclusão de moradia exige base legal do cliente (indenização de moradia em dinheiro é normalmente tributável).
- **Pendências:**
  - Cliente: documento que ainda falta + declaração IFPGAZ 2026 para confirmar o flag de 2026.
  - Nós (Wallisson): versão detalhada em inglês, sem "cara de IA"; responder se os documentos são exigidos todo ano.
  - Abrir tickets separados para os defeitos do GTN (pensão estornada, rótulos, CE, bases) [INCERTO se já foram abertos].
  - Escalonamento ao Marko (cliente).
- **Fronteira:** correção do GTN/wage types e configuração do flag = configuração/Dev (tickets separados); posição fiscal do cliente = cliente (documentos).

---

# Fora do grupo (incluído na lista g-AF por engano)

## HRBS-13860 — Arquivo NAERSA falhando de novo (Irlanda / Omnicom)
- **País:** Irlanda / **Cliente:** Omnicom (entidades Clavis Technologies Ltd e OMG) / **Tipo:** Incident / **Prioridade:** Medium / **Estado final:** In Progress / **Support Group:** L2 / **Assignee:** Romano Fusana (não Compliance) / **Fase:** Live/BAU
- **Datas:** criado 2026-08-27; snapshot 2026-08-27.
- **Arquivos-fonte:** `34 - Ticket - HRBS-13860 - Naersa file failing again this month`
- **Quem pediu:** Philippa O'Reilly (lado cliente [INCERTO]).
- **Problema:** submissão NAERSA de agosto falhou para todas as entidades; Clavis e OMG por **classes PRSI incorretas**. Pedem corrigir as classes e submeter no mesmo dia. Processos 8211/8212 "errored" (NAERSA Contribution Submission with Reconciliation Details; Irish Tax Payroll Submission).
- **Resposta:** só acknowledgement e dados de processo (Romano Fusana, Support Engineer). Sem envolvimento de Compliance.
- **Fronteira:** suporte L2 / integração — fora do escopo de Compliance no snapshot. **Mover para o grupo Irlanda.**

---

## Síntese do grupo

### (a) Decisões recorrentes / padrões
1. **Cliente quase único: Baker Hughes** (Namíbia, Congo, Gabão, CI). O solicitante típico é Daniel Kelvin Balogun (implementação) ou Sivaranjani Subbarayula/Govind Thakur (CI, BAU); a triagem passa por Pradeep Duraisamy → Mohit Jain/Manju Shetija → Wallisson.
2. **Padrão "WTC do cliente vs. WTC de compliance":** a maioria dos tickets compara a WTC/G2N legado do cliente com a nossa (pension flags na Namíbia, CAMU e occupancy/region tax no Congo, tetos na CI). A regra que aparece nas respostas do Wallisson: **identificar exatamente qual contribuição estatutária o item do cliente representa** (ex.: CAMU solidarité 0,5% ≠ CAMU 2,27%; "CNAMGS/FNH" na CI = AT/MP e PF+AM) antes de aceitar ou rejeitar.
3. **Nome de regime não é isenção:** pedido de isenção fiscal só com instrumento específico (convention d'établissement, agrément, ruling DGI, declaração IFPGAZ) e confirmado **por ano** (2025 confirmado; 2026 aguarda a declaração).
4. **Piso ≠ teto:** SMIG CI (75.000) é piso da assiette; teto de PF/AM/AT é 70.000 (CLEISS, 01/01/2025).
5. **Defeitos de GTN achados durante a revisão vão para tickets separados** (não se resolvem dentro do ticket de pergunta).
6. **Muitos tickets da Namíbia/Congo de jul–ago/2026 sem resposta nos snapshots** (12072, 12101, 12110, 12111, 12483, 14055) com SLA negativo — fila de pendências do Wallisson.
7. Relatórios Namíbia: só existem PAYE Return, G2N, SSC Return (+ Payslip); **não existem VET Levy Return nem IT12E** (Mohit, ~18/09/2026).
8. Feedback do solicitante (28/09): respostas devem ser **mais detalhadas, em inglês, sem aparência de IA**.

### (b) Lista de [INCERTO]
- Papel exato de Daniel Kelvin Balogun (implementação?) e de Katrin Rudi (configuração/Dev?).
- Datas absolutas: todas estimadas a partir de "X days ago" (±1 dia).
- HRBS-13602: identificação dos tickets "annualization-methodology" e "stale-bracket-constant" citados.
- HRBS-13841: se a CAMU solidarité 0,5% será adicionada à WTC de compliance; a pergunta sobre 4,55%/2,27% segue sem resposta.
- HRBS-14605: taxa/teto SSC Namíbia (0,9%/0,9%, ~NAD 11.000) — só alegação do cliente.
- HRBS-14714: se foi vinculado/fechado em favor do HRBS-14996.
- HRBS-14996: se a fonte DGI cobre o teto de 200 M XOF; se os tickets separados de defeito do GTN foram abertos; qual documento ainda falta no cliente.
- CT-A-620: quase todos os floors/ceilings e a distribuição das taxas DGI (9,20 / 1,20 / 0,40 / 1,20) entre linhas — texto da tabela quebrado; valores parecem anuais (12 × 75.000; 12 × 3.375.000; 12 × 70.000). Conferir no original do YouTrack. Também se o 9,20% (Worker Type = 1) da spec é o CE que Wallisson diz faltar no GTN.
- HRBS-13860: está no grupo errado (Irlanda).

### (c) Artefatos e últimas versões citadas por país
| País | Artefato | Versão / estado citado |
|---|---|---|
| Namíbia | Compliance WTC | sem versão; pension flags 62100/62146–62149/62961 = Yes (em questão, HRBS-12483); combinação SSNC=No/ECF=Yes/Pension=No existe (HRBS-12072) |
| Namíbia | CCG | sem versão; 2551 = MSD EE Contribution, não pré-imposto (Mohit, 24/08/2026) |
| Namíbia | Report Specs (SSC Form Ten, PAYE 5, ETX) | sem samples (HRBS-12101) |
| Namíbia | Report Matrix (cliente) | em revisão (HRBS-12111) |
| Namíbia | Relatórios: Monthly PAYE Return, G2N, SSC Contribution Return | em configuração, desenvolvimento previsto até 25/09/2026, depois revisão de Compliance |
| Namíbia | Payslip | configurado, em revisão de Compliance (~18/09/2026) |
| Namíbia | VET Levy Return, IT12E (IT14E) | não existem |
| Congo | Compliance WTC | sem versão; sem CAMU solidarité [INCERTO]; occupancy/region tax em questão |
| Congo | Report Matrix | em revisão (HRBS-12110) |
| Congo | Payslip | campos estado civil / nº filhos / nº partes pendentes de confirmação |
| Gabão | Payslip | exibirá estado civil e nº de partes; nº de filhos não |
| Côte d'Ivoire | Spec CT-A-620 (+ CT-A-621 Taxable Gross, CT-A-622 Gross, CT-A-623 Tax Table) | atualizada ~07/08/2026 (sub-artigos 05/08/2026) |
| Côte d'Ivoire | WTC/GTN (REF-P201-861) | defeitos apontados em 22/09/2026 (pensão estornada, rótulos 2531/2538/2560/2569, falta CE, bases transporte/moradia) |
| Côte d'Ivoire | Flag de isenção ITS (prestataires pétroliers) | não criado; 2025 confirmado por carta DGI 0984/MFB/DGI/DGE de 19/08/2025; 2026 aguarda IFPGAZ |
