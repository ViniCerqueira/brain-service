# Tickets YouTrack: Colômbia, Chile, China, Holanda, Lituânia + sem país no título (Congo, Espanha)

> Fonte: `raw/tickets/txt/` (12 arquivos, 12 tickets distintos, um snapshot cada). Datas relativas ("há 3 meses") foram convertidas a partir da data do snapshot (cabeçalho do PDF) e são **aproximadas**.
> Nomes e IDs de empregados presentes nos tickets (HRBS-14054, HRBS-10563, HRBS-12487, HRBS-12491) foram **omitidos** de propósito.

---

# Chile

## SR-221 — CL-DT-001-LRE-LibroRemuneracionesElectronico-Spec
- **País:** Chile (CL) / **Cliente:** nenhum (projeto Statutory Reports) / **Tipo:** Issue de especificação de report / **Prioridade:** Major / **Estado final:** In Progress / **Fase:** Product Mapping (Phase – Business Analyst)
- **Datas:** criado ~2026-04/05 ("5 months ago" em 2026-09-28) por Wallisson; última atualização 2026-09-28 (Ruchi Gupta); Due Date 31 Jul 2026 (vencido); sem resolução.
- **Arquivos-fonte:** `94 - Ticekt - SR-221 - CL-DT-001-LRE-LibroRemuneracionesElectronico-Spec.txt`
- **Quem pediu:** criado por Wallisson (Research Analyst); revisão por Ruchi Gupta (Business Analyst).
- **Pergunta / problema:** Report Spec do LRE (Libro de Remuneraciones Electrónico, DT). Ruchi pediu revisão dos campos destacados em amarelo (~2026-05/06). Wallisson apagou a versão anterior e subiu uma versão melhorada; Ruchi reclamou que já tinha trabalhado no arquivo. Em ~2026-09-15 o link não abria; Wallisson atualizou. Em 2026-09-28 Ruchi pediu **uma coluna no WTC indicando o código de report aplicável**.
- **Resposta / decisão nossa:**
  - ~2026-05/06: "previous version was deleted, this is now an improved one, please review".
  - ~2026-09-15: "link updated".
- **Valores estatutários:** nenhum citado.
- **Artefato afetado:** Report Spec CL-DT-001 (LRE); WTC Chile (nova coluna de report code pedida). Versões não citadas.
- **Erros corrigidos:** erro de processo: **apagar a versão anterior de um artefato em que o BA já tinha trabalhado** ("This is not the way to update the documents" — Ruchi). Correto: não apagar, versionar.
- **Pendências:** adicionar coluna de report code no WTC CL (Wallisson); revisão dos campos amarelos [INCERTO se concluída].
- **Fronteira:** Business Analyst (Ruchi Gupta) faz o product mapping a partir da nossa spec.

## SR-232 — CL-PRV-001-Previred-PlanillaMensual-Spec
- **País:** Chile (CL) / **Cliente:** nenhum / **Tipo:** Issue de especificação de report / **Prioridade:** Major / **Estado final:** Open / **Fase:** Product Mapping (Phase – Business Analyst)
- **Datas:** criado ~2026-04/05 por Wallisson; última atualização 2026-09-28 (Ruchi Gupta); Due Date 31 Jul 2026 (vencido).
- **Arquivos-fonte:** `90 - Ticket - SR-232 CL-PRV-001-Previred-PlanillaMensual-Spec.txt`
- **Quem pediu:** criado por Wallisson; BA Ruchi Gupta; Manju Shetija citada.
- **Pergunta / problema:** Report Spec da Planilla Mensual Previred. ~2026-09-15 o link não abria; Ruchi compartilhou link de Google Sheets e pediu atualizar a descrição. 2026-09-28: pediu **coluna no WTC com o report code aplicável** (mesmo pedido do SR-221).
- **Resposta / decisão nossa:** ~2026-09-15: "link updated".
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Report Spec CL-PRV-001 (Previred); WTC Chile.
- **Erros corrigidos:** nenhum.
- **Pendências:** coluna de report code no WTC CL (Wallisson).
- **Fronteira:** BA (Ruchi) / Manju Shetija.

---

# China

## SR-316 — CN_Payslip
- **País:** China (CN) / **Cliente:** nenhum / **Tipo:** Issue (Statutory Reports) / **Prioridade:** Normal / **Estado final:** Open / **Fase:** Specification (Phase – Research Analyst)
- **Datas:** criado ~2026-07-10 ("about 1 month ago" em 2026-08-10) por Enaakshi Vats; última atualização ~2026-08-09; Due Date 31 Aug 2026.
- **Arquivos-fonte:** `12 - Ticket - SR-316 - CN_Payslip.txt`
- **Quem pediu:** Lily Li (~2026-08-04) pediu converter o payslip CN para o formato Compliance; Enaakshi Vats (Research Analyst) pediu ajuda a Wallisson.
- **Pergunta / problema:** converter o "China CN Payslip generator v1.0" (Google Sheets) para o formato padrão Compliance. Subtarefa de CT-4457 (CN_China_Compliance Artifacts for development).
- **Resposta / decisão nossa:** nenhuma resposta registrada no snapshot.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Payslip Generator CN v1.0.
- **Erros corrigidos:** nenhum.
- **Pendências:** conversão para o formato Compliance (Wallisson/Enaakshi). Estado posterior a 2026-08-10 [INCERTO].
- **Fronteira:** nenhuma explícita.

---

# Colômbia (cliente Philip Morris International — Compañía Colombiana de Tabaco SAS, entidade REF-LE-00-505)

> Contexto comum aos 5 tickets: são itens que a PMI precisa resolver **antes da transição para o Instaroll** (lista "PMI Instaroll Transition Tracker", discutida em ELT). Em ~2026-08-29 Mohit Jain (Head of Compliance Product) disse que **"Colombia requires a redesign or at least a major gap fixing work"** e, ~2026-09-03, após conversa com Manju, atribuiu todos a Wallisson **"for gap analysis during Colombia research"**. Nenhuma resposta nossa no snapshot (2026-09-16). Os valores abaixo foram **declarados pelo solicitante (time de payroll/cliente)**, não validados por nós.

## HRBS-12487 — Automação do cálculo de vacation bonus (offcycle) acima de 95 UVT
- **País / Cliente:** Colômbia / PMI (1764 – Compañía Colombiana de Tabaco SAS) / **Tipo:** Incident (Tier 1, New Development Item) / **Prioridade:** Medium / **Estado final:** Pending on reporter / Live/BAU / Production
- **Datas:** criado ~2026-07-16 ("about 2 months ago" em 2026-09-16) por Jose Quiroga; última atualização ~2026-09-03 (Mohit Jain).
- **Arquivos-fonte:** `68 - Ticekt - HRBS-12487 - Automation of Vacation Pay Calculation - Offcycle.txt`
- **Quem pediu:** Jose Quiroga (payroll, lado Mercans/cliente); Support Engineer Romano Fusana; Sohail Ahmad (Support).
- **Pergunta / problema:** com o Instaroll, passos manuais do vacation bonus precisam ser automatizados: quando o bônus de férias excede **95 UVT**, devem ser deduzidos seguridade social e retenção na fonte. Dias de férias em WT **63123**; bônus calculado em WT **62837** (aparece no G2N). Jose enviou `95UVT_Automation_Spec.xlsx` (abas Parameters, Art383, Example, Validation) com exemplo real do offcycle da semana 31/2026.
- **Regras declaradas pelo solicitante:**
  - Fórmula do bônus (já correta no HRBlizz): `ROUND(Total Días × 2.8 × (salário base mensal / 30), 0)`.
  - Total Días = Days Taken + Cash Out Amount (usar só Days Taken é fonte de erro conhecida).
  - Salario Integral sempre excluído deste offcycle; só Personnel Area CO = Ordinario.
  - Procedimento de retenção já no cadastro (opção 6 do employee card); Procedimento 2: % fixo no WT **52552**.
- **Resposta / decisão nossa:** nenhuma ainda. Sohail: precisa de suporte de compliance para automatizar SS e imposto sobre esses bônus.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Limite para SS + retenção sobre vacation bonus | 95 UVT | 2026 (offcycle sem. 31/2026) | sem fonte no ticket |
| Fator do bônus | 2.8 × dias × salário/30 | — | regra do cliente/sistema, sem fonte legal no ticket |

- **Artefato afetado:** WTs 63123, 62837, 52552 (WTC CO); versão não citada.
- **Erros corrigidos:** nenhum.
- **Pendências:** gap analysis (Wallisson) dentro da pesquisa Colômbia.
- **Fronteira:** automação/configuração = Dev/Support; nós = regra legal.

## HRBS-12491 — Explicação do cálculo de embargo (garnishment)
- **País / Cliente:** Colômbia / PMI / **Tipo:** Incident (Tier 1, Instaroll) / **Prioridade:** Medium / **Estado final:** Pending on reporter
- **Datas:** criado ~2026-07-16 por Heidy Ballesteros Puyo; última atualização ~2026-09-03 (Mohit Jain).
- **Arquivos-fonte:** `69 - Ticket - HRBS-12491 - Explanation of Garnishment Calculation.txt`
- **Quem pediu:** Heidy Ballesteros Puyo (Support Engineer/payroll); Cintia Torres (Senior Payroll Consultant); Romano Fusana (Support Engineer).
- **Pergunta / problema:** o sistema gera um valor preliminar de embargo que não reflete a metodologia da ordem judicial; o time ajusta manualmente a cada período. Com o Instaroll, não haverá acesso para ajustar antes da geração da folha.
- **Regra pedida pelo solicitante (Heidy):**
  1. Base = ganhos salariais conforme a ordem judicial (todos os salariais **ou** só salário básico, conforme a ordem).
  2. Deduzir 2552 Income Tax, 2553 Fondo de Solidaridad Pensional, 2554 EPS empregado, 2556 AFP empregado.
  3. Subtrair o SMMLV vigente.
  4. Aplicar 1/5 do excedente.
  - Valor fixo determinado pelo juiz: sem cálculo, aplicar o valor fixo do registro de embargo.
  - Base ≤ SMMLV → embargo = 0 (nunca negativo).
  - Itens citados: 21125 (dedução de embargo), 64993 (item de cálculo).
- **Resposta / decisão nossa:** nenhuma ainda.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| SMMLV | COP 1.750.905 | 2026 | sem fonte legal no ticket (declarado por Heidy) |
| Fração embargável | 1/5 do excedente sobre o SMMLV | — | sem fonte legal no ticket |

- **Artefato afetado:** itens 21125, 64993, 2552–2556 (WTC CO).
- **Erros corrigidos:** nenhum.
- **Pendências:** Romano perguntou quantos embargos ativos por período e a lista completa de itens; sem resposta. Gap analysis (Wallisson).
- **Fronteira:** configuração/Dev; dados da ordem judicial = cliente.

## HRBS-12492 — Regras de contribuição à seguridade social (empregado e empregador)
- **País / Cliente:** Colômbia / PMI (REF-LE-00-505) / **Tipo:** Incident (Tier 1, Instaroll) / **Prioridade:** Medium / **Estado final:** Pending on reporter
- **Datas:** criado ~2026-07-16 por Cintia Torres; última atualização ~2026-09-03 (Mohit Jain).
- **Arquivos-fonte:** `70 - Ticekt - HRBS-12492 - SSecurity Contribution Rules (Employee & Employer) – Colombia.txt`
- **Quem pediu:** Cintia Torres (Senior Payroll Consultant); Heidy Ballesteros Puyo enviou o "Validador Seguridad Social julio Monthly.xlsx".
- **Pergunta / problema:** confirmar se o sistema pode ser parametrizado para: (1) regra dos 40% da Lei 1393/2010 (excesso de pagamentos não salariais volta para o IBC); (2) alíquotas e exonerações por nível de IBC (acima/abaixo de 10 SMLMV); (3) regra do IBC nas férias (salário do mês anterior, não o pagamento de férias). Romano observou um caso com 4 dias de férias em que a contribuição foi calculada sobre o bruto do mês inteiro.
- **Resposta / decisão nossa:** nenhuma ainda.
- **Valores estatutários (declarados pelo solicitante):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| IBC mínimo / máximo | 1 SMLMV / 25 SMLMV | sem vigência no ticket | sem fonte no ticket |
| Pagamentos não salariais | máx. 40% da remuneração total; excesso entra no IBC | — | Lei 1393 de 2010 (citada) |
| Saúde | 12,5% (empregado 4% / empregador 8,5%); 8,5% exonerado até 10 SMLMV | sem vigência | sem fonte no ticket |
| Pensão | 16% (empregado 4% / empregador 12%) | sem vigência | sem fonte no ticket |
| ARL | só empregador, conforme classe de risco | — | sem fonte no ticket |
| Fondo de Solidaridad Pensional | só empregado, a partir de 4 SMLMV, progressivo | — | sem fonte no ticket |
| Parafiscales (só sobre salário) | Caja 4%, ICBF 3%, SENA 2%; ICBF/SENA/Saúde exonerados até 10 SMLMV | — | sem fonte no ticket |
| IBC durante férias | salário do mês imediatamente anterior ao início das férias (gozadas e antecipadas) | — | Art. 3, Decreto 1072 de 2015 e guias PILA (citados) |
| IBC salário integral | 70% (mencionado por Romano) | — | sem fonte no ticket |

- **Artefato afetado:** regras de SS na regulação CO; versão não citada.
- **Erros corrigidos:** nenhum confirmado (possível erro do sistema: IBC de férias sobre o bruto do mês [INCERTO]).
- **Pendências:** gap analysis (Wallisson); lista de conceitos não salariais pedida por Romano (sem resposta explícita além do validador).
- **Fronteira:** parametrização = Dev/Config.

## HRBS-13627 — Explicação do cálculo de retención en la fuente
- **País / Cliente:** Colômbia / PMI / **Tipo:** Question/Inquiry (Tier 1) / **Prioridade:** Medium / **Estado final:** Open (Resolution Time −20d, ou seja, estourado)
- **Datas:** criado ~2026-08-23 ("24 days ago" em 2026-09-16) por Heidy Ballesteros Puyo; última atualização ~2026-09-03 (Mohit Jain).
- **Arquivos-fonte:** `71 - Ticket - HRBS-13627 - Explanation of Income Tax Withholding Calculation.txt`
- **Quem pediu:** Heidy Ballesteros Puyo.
- **Pergunta / problema:** o sistema deve calcular automaticamente a retenção (Procedimento 1 ou 2 com % fixo). Hoje: cálculo padrão para todos e ajuste manual dos "Expat Home"; reclassificação para o conceito certo (2552 geral; 21330 Personal Income Tax Withholding (Theoretical) para Expat Home). Validador Excel de julho/2026 anexo (abas Tax Report, Gross to Net PMI, Contingente, ReteFuente PRIMA, Tax Table, Tax Ded, Recaculo Retencio).
- **Lógica descrita pelo solicitante:** Base 1 = renda − SS obrigatória; deduções Art. 387 limitadas; AFC/VFP limitado a 30%; 25% isento limitado a 65,83 UVT/mês; limite global 40% de Base 1 e 111,67 UVT/mês; tabela Art. 383 em UVT. Procedimento 2: % recalculado em junho e dezembro, média dos 12 meses anteriores. Prima de servicios (Proc. 1): sem dedução de SS, Art. 387 e limite 40%; só 25% isento; aplica-se a alíquota marginal. Proc. 2: prima somada à renda do mês. Expatriados/não residentes: 20% sobre total tributável, sem benefícios; cliente responsável por indicar os empregados, mudança só por escrito. Retenção contingente: cálculo paralelo com pagamentos não recorrentes, usa a diferença positiva.
- **Ponto de atenção levantado pelo próprio solicitante:** o validador aplica 1.340 UVT ÷ 12 por mês, sem acumulado anual; para quem já atingiu 1.340 UVT no ano (ex.: IC bonuses), há controle manual. Risco de sub-retenção.
- **Resposta / decisão nossa:** nenhuma ainda.
- **Valores estatutários (declarados pelo solicitante):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| UVT | COP 52.374 | ano fiscal 2026 | DIAN Resolução 000238 de 15/12/2025 (citada) |
| Auxílio alimentação isento (salário ≤ 310 UVT) | 41 UVT/mês (COP 2.147.334) | 2026 | Art. 387-1 E.T. |
| Juros moradia / leasing | 100 UVT/mês (COP 5.237.400) | 2026 | Art. 387 E.T. |
| Medicina pré-paga / seguro saúde | 16 UVT/mês (COP 837.984) | 2026 | Art. 387 E.T. |
| Dependentes (10% da renda bruta) | máx. 32 UVT/mês (COP 1.675.968) | 2026 | Art. 387 E.T. |
| AFC + VFP | 30% da renda do trabalho | — | Art. 126-1 E.T. |
| Renda isenta 25% | 790 UVT/ano ≈ 65,83 UVT/mês (COP 3.446.732) | 2026 | Art. 206 num. 10 E.T. |
| Limite global isenções + deduções | 40% da Base 1, máx. 1.340 UVT/ano ≈ 111,67 UVT/mês (COP 5.847.117) | 2026 | Art. 388 E.T. |
| Tabela Art. 383 | 0–95 UVT 0%; 95–150 19%; 150–360 28% + 10 UVT; 360–640 33% + 69; 640–945 35% + 162; 945–2.300 37% + 268; >2.300 39% + 770 | 2026 | Art. 383 E.T. |
| Procedimento 2 | % fixo semestral, recalculado em junho e dezembro | — | Art. 386 E.T. |
| Expat / não residente (configuração do cliente) | 20% sobre total tributável | — | sem fonte legal no ticket |

- **Artefato afetado:** conceitos 2552, 21330 (WTC CO).
- **Erros corrigidos:** nenhum.
- **Pendências:** gap analysis (Wallisson); acumulado anual do limite de 1.340 UVT.
- **Fronteira:** classificação de expat/não residente = cliente.

## HRBS-13692 — Provisões de cesantías e intereses sobre cesantías
- **País / Cliente:** Colômbia / PMI / **Tipo:** Question/Inquiry (Tier 1) / **Prioridade:** Medium / **Estado final:** Open (Resolution Time −19d)
- **Datas:** criado ~2026-08-25 ("22 days ago" em 2026-09-16) por Heidy Ballesteros Puyo; última atualização ~2026-09-03 (Mohit Jain).
- **Arquivos-fonte:** `72 - Ticekt - HRBS-13692 - Accruals Severance Pay and Severance Interest Calculation.txt`
- **Quem pediu:** Heidy Ballesteros Puyo.
- **Pergunta / problema:** o sistema não gera automaticamente as provisões de cesantías (conceito **22110** Provision Severance – Social Benefits Provision Accrual 1) e de intereses (**22112** Provision Interest Severance Pay – Social Benefits), nem o relatório de consolidação (fechamento e entrega ao cliente). Hoje é calculado fora e carregado via Excel. Pede automação + relatório (lista de campos mínimos no ticket).
- **Resposta / decisão nossa:** nenhuma ainda.
- **Valores estatutários (declarados pelo solicitante):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Cesantías | 1 mês de salário por ano de serviço, proporcional | — | sem fonte específica no ticket ("Colombian labor regulations") |
| Base variável | média do último ano (ou do tempo trabalhado) se o salário variou nos últimos 3 meses | — | Art. 253 Código Sustantivo del Trabajo (citado) |
| Intereses sobre cesantías | 12% a.a. = cesantías × 12% × dias / 360; pagamento em janeiro do ano seguinte ou na rescisão | — | sem fonte específica no ticket |

- **Artefato afetado:** conceitos 22110, 22112; novo report de consolidação (sem Report Spec ainda).
- **Erros corrigidos:** nenhum.
- **Pendências:** gap analysis (Wallisson).
- **Fronteira:** relatório/automação = Dev/Reports.

---

# Holanda

## HRBS-14675 — Netherlands standard report (netherland-ssc-pdf): atualizar % de SSI para 2026
- **País / Cliente:** Holanda / Omnicom (entidades: Omnicom Public Relations Group B.V., Excerpta Medica B.V., VIDIBOKO, TBWA Nederland B.V, ARA Groep B.V) / **Tipo:** Question/Inquiry (Tier 1) / **Prioridade:** Medium / **Estado final:** Pending on reporter / Live/BAU / Production
- **Datas:** criado ~2026-09-15 por Suresh Jalihal; última atualização 2026-09-21 (Mohit Jain).
- **Arquivos-fonte:** `78 - Ticket - HRBS-14675 - Netherlands standard reports- Need to update SSI percentage as per 2026.txt`
- **Quem pediu:** Suresh Jalihal (payroll/implementação); Abarna Khaliq (Senior Specialist-Configurations) disse que não trata reports; Shaik Jani Sharif (Senior Specialist – Reports); Mohit Jain (Head of Compliance Product).
- **Pergunta / problema:** o report `netherland-ssc-pdf` mostra percentuais de SSI antigos. Suresh pede atualizar para 2026. Reports Team: o report está configurado como **Custom Report**, não Statutory, e pediu a spec. Suresh diz que deveria ser standard por país (consta no BPQ e na report matrix), sem spec. Mohit pediu a Wallisson (2026-09-21) para verificar **se é um statutory report de compliance**.
- **Resposta / decisão nossa:** nenhuma ainda.
- **Valores estatutários (pedidos pelo solicitante, não validados):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| ZVW | 6,10% | 2026 | sem fonte no ticket |
| AOF Laag | 6,27% | 2026 | sem fonte no ticket |
| AOF Hoog | 7,63% | 2026 | sem fonte no ticket |
| AOF Uit | 7,63% | 2026 | sem fonte no ticket |
| AWF Laag | 2,74% | 2026 | sem fonte no ticket |
| AWF Hoog (escrito "Haag") | 7,74% | 2026 | sem fonte no ticket |
| WKO | 0,50% | 2026 | sem fonte no ticket |
| ZW Flex / WGA | conforme campo "company details" da Legal Entity | — | — |

- **Artefato afetado:** report `netherland-ssc-pdf` (Custom Report); sem spec.
- **Erros corrigidos:** % antigos no report (valores antigos não transcritos no texto; só no PDF anexo).
- **Pendências:** Wallisson decidir se o report é de compliance/statutory e, se for, fornecer spec atualizada; senão, devolver para Reports (Shaik).
- **Fronteira:** Reports Team (Shaik Jani Sharif) mantém Custom Reports; Configurations (Abarna) não trata reports.

---

# Lituânia

## HRBS-15253 — ACCENTURE LITHUANIA | Compliance (Calculation & Reporting) Check
- **País / Cliente:** Lituânia / Accenture (Accenture Lithuania, REF-LE-04-359) / **Tipo:** Question/Inquiry (Tier 1) / **Prioridade:** Medium / **Estado final:** Open / Live/BAU / Production
- **Datas:** criado 2026-09-28 por Kevin Gunawan; última atualização 2026-09-28 (Manju Shetija).
- **Arquivos-fonte:** `99 - Ticket - HRBS-15253 - ACCENTURE LITHUANIA  Compliance (Calculation & Reporting) Check.txt`
- **Quem pediu:** Kevin Gunawan (alocado ao engagement Lituânia, montando o escopo de configuração).
- **Pergunta / problema:** cliente novo na Lituânia. Pede marcar cada item como S (suportado e configurado) / C (suportado, precisa configurar) / M (workaround manual) / N (não suportado), com dono e roadmap para M/N. Cobertura sem validar números. Partes: (1) cálculo: bases GPM vs Sodra, flags por wage type, BIK, contribuições Sodra empregado (pensão, doença, maternidade, PSD, Pilar II) e empregador (desemprego, Guarantee Fund, Long-Term Employment Benefit Fund, acidentes por grupo de risco, switch por tipo de contrato), GPM (faixas incl. mudança de 1/1/2026, NPD), teto anual Sodra, piso MMA, ausências, arredondamento, multi-contrato, retro, A1; (2) mensal: SAM + SAM3SD/SAM3SDP (.ffdata, EDAS), GPM313 (.ffdata, EDS), payslip, banco, GL, reconciliação; (3) eventos: 1-SD, 2-SD, 9-SD, 12-SD, 13-SD, NP-SD, PT; (4) anual: GPM312 + GPM312L/GPM312U, provisão de férias, virada de parâmetros; (5) perguntas: quem mantém .ffdata, ambiente de teste, correções, **existe parameter sheet de LT assinado e quem é o dono**, a Mercans já entregou LT antes.
- **Resposta / decisão nossa:** nenhuma; só o acknowledgment do Product Support (Lavanya Balamurugan).
- **Valores estatutários (como escritos no ticket):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| SAM (Sodra) | até o dia 15 do mês seguinte, com pagamento | — | sem fonte no ticket |
| GPM313 (VMI) | até o dia 15 do mês seguinte | — | sem fonte no ticket |
| Pagamento do GPM | pago até dia 15 → imposto até dia 15 do mesmo mês; pago após dia 15 → até o último dia do mês | — | sem fonte no ticket |
| GPM312 anual | 15 de fevereiro | — | sem fonte no ticket |
| 1-SD | antes do primeiro dia de trabalho | — | sem fonte no ticket |
| Faixas GPM | mudança de estrutura | a partir de 2026-01-01 | sem fonte no ticket (sem valores) |

- **Artefato afetado:** nenhum citado (pergunta implícita sobre existência de CCG/parâmetros LT).
- **Erros corrigidos:** nenhum.
- **Pendências:** resposta de cobertura item a item (Compliance/Wallisson, assignee). [INCERTO] o que Manju atualizou em 2026-09-28 (sem comentário visível).
- **Fronteira:** itens de HR vs payroll (eventos SD) e formatos de banco/GL = Implementation/Integration; o ticket pede explicitamente o dono de cada item.

---

# Sem país no título

## HRBS-10563 — Espanha: wage types, matriz de tributação e lacunas na lógica de licenças estatutárias
- **País / Cliente:** Espanha / "All Spain" (sem cliente) / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open, SLA **Breached** / Assignee: Lily Li
- **Datas:** criado ~2026-06 ("3 months ago" em 2026-09-08) por Gulnaaz Parveen; respostas de Wallisson ~2026-06/07; última atualização 2026-09-08 (Gulnaaz). Inward mention: CT-4433 ES: Spain Regulation Support.
- **Arquivos-fonte:** `52 - Ticket - HRBS-10563 - Update Required Wage Type Configurations, Taxability Matrix, and Statutory Leave Logic Gaps.txt` (o texto tem trechos cortados em "Show more").
- **Quem pediu:** Gulnaaz Parveen (Implementation/Support); Lily Li (regulation design / dona do WTC).
- **Pergunta / problema:** 7 pontos: (1) série 6296 (62960–62969) tributável e não sujeita a SS; (2) série 6298 (62980–62989) não tributável e não sujeita a SS; (3) severance informado pelo cliente (62180 tributável/não SS; 62983 não tributável) prevalece sobre o calculado; (4) licenças estatutárias faltantes (aborto, menstruação incapacitante, interrupção da gravidez etc.) com base do mês anterior (BCCC/BCCP); (5) acidente de trabalho dia 1 vs dia 2 (79411/79412); (6) período de acúmulo da 15ª paga (paga em março); (7) lógica da base de cotização em meses com licença.
- **Resposta / decisão nossa (Wallisson):**
  - **~2026-06 (1ª resposta, WTC V3.9, mudanças em laranja):**
    - P1: confirmado (N=Yes, BCCC/BCCP=No). Ressalva: pelo Art. 147 LGSS a regra é que toda remuneração cotiza; "tributável mas não SS" só vale para exclusões do Art. 147.2 (locomoção/dietas dentro dos limites IRPF, estudos etc.). Só mapear conceitos realmente não SS na série. Colunas T–AC sem mudança (clave A).
    - P2: flags confirmados; **corrigido** o metadado AEAT/190: 62983 → clave L / subclave L05 (indenização por despido isenta, Art. 7.e LIRPF), Exempt_InfoOnly, fora de 111/216; 62980–62982 e 62984–62989 → clave L / L01, Exempt_InfoOnly. Precedente: 62873.
    - P3: tratado nos regulation steps (Lily); sem mudança no WTC.
    - P4: adicionados 79022 Termination of Pregnancy Leave Unit, 79024 Disabling Menstruation Leave Unit, 79028 Abortion Leave Unit (espelhando 79008). Não renomeou os payouts genéricos 79420–79428 sem aval da Lily.
    - P5: 79411 = dia do acidente, salário integral pago pelo empregador (Art. 173.1 LGSS); 79412 = 75% da base reguladora a partir do dia seguinte, pagamento delegado (mútua/INSS); BR = BCCP do mês anterior ÷ dias (30 para mensal). Aborto e interrupção da gravidez seguem o padrão "dia 1 empregador"; menstruação incapacitante é paga pela SS desde o dia 1.
  - **~2026-06/07 (2ª resposta):**
    - 62983: CRA **0054** (Indemnizaciones por despido o cese), indicador **E** na TGSS/SILTRA + clave L/L05 na AEAT/190; os dois coexistem. Mesmo critério já aprovado em ES-CRA-001 (58184, 58186, 62180).
    - P4: adicionados Leave Units Risk During Pregnancy, Risk During Lactation, Parental Leave; payouts 79416/79417/79418 (BCCC/BCCP=No; AEAT B.01 — depois corrigido, ver abaixo). **Não adicionados:** parciais de maternidade/paternidade/parental (tratados pelo coeficiente de % de jornada) e ERE parcial/total (suspensão/ERTE, SEPE paga; tratar como status, não como licença no WTC).
    - P7: "100% BR" é só payout e não entra na base de cotização; nascimento/cuidado cota sobre BCCC do M-2 (Orden PJC/297/2026). **Corrigiu a Lily:** o mecanismo por dia e por contingência vale também para a base de cotização (base diária = base do mês anterior ÷ 30; base na situação = base diária × dias). A Seção 5 do documento "BCCC/BCCP Base Logic" está errada (só vale para mês inteiro de licença).
  - **~2026-07 (3ª resposta):** ÷30 só para grupo mensal; grupo diário ÷ dias reais do mês anterior (28/30/31); tempo parcial: soma dos últimos 3 meses ÷ dias do período (RDL 11/2024). Vários tipos de licença no mesmo mês: segmentar o mês, cada licença com sua base. Dias trabalhados: ganhos reais do mês, com piso/teto. Exemplos A–C (depois corrigidos).
  - **~2026-07 (4ª resposta, autocorreção):** as duas bases (BCCC e BCCP) **continuam durante qualquer licença** (Orden PJC/297/2026 Art. 6.1, 6.3, 6.5); nenhuma é zero enquanto o trabalhador está de alta. Ganhos dos dias trabalhados entram em BCCC **e** BCCP. Piso/teto aplicam-se à BCCC e à BCCP mensais (não só à base dos dias trabalhados) e não são proporcionais aos dias trabalhados; proporcionalidade por dias é só regra de alta/baixa no mês.
  - **~2026-07 (5ª resposta):** payouts novos 79417–79424: colunas N–S OK; **corrigido** AEAT/190 de clave B/pago directo/"Not in 111" para clave A / subclave em branco / Work_Cash_Gross / Work-Cash (111 01-03) (empregado ativo = pago delegado; B só quando o INSS paga diretamente). 216 Scope: N/A nas 6 linhas de subsídio; "Subject to withholding (216)" em 79417 (aborto dia 1) e 79422 (ToP First Day). Limpou campos 296 indevidos (296 Key=20, Subkey=01) em 79422. Renomeou 79419 para "Abortion Leave 75% day 21+ Payout".
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Novas IT (aborto, menstruação incapacitante, interrupção da gravidez): subsídio | 60% BR dias 1–20; 75% a partir do dia 21 | sem vigência explícita | LO 1/2023 (arts. 169.1.a e 173 LGSS) |
| Bandas aborto | salário dia 1 + 60% dias 2–20 + 75% dia 21+ | — | Art. 173 LGSS |
| Bandas menstruação incapacitante | 60% dias 1–20 + 75% dia 21+ (sem dia 1 do empregador) | — | Art. 173 LGSS |
| Bandas interrupção da gravidez | First Day + 60% dias 2–20 + 75% dia 21+ | — | Art. 173 LGSS |
| Acidente de trabalho dia 1 | 100% salário, pago pelo empregador | — | Art. 173.1 LGSS |
| Acidente de trabalho a partir do dia 2 | 75% da BR (BCCP mês anterior ÷ 30) | — | Art. 173.1 LGSS (citado) |
| Risco na gravidez / lactação | 100% BR, INSS/mútua desde o dia 1 | — | Arts. 186–187 LGSS |
| Licença parental | 2 de 8 semanas pagas a 100% pela SS; 6 sem remuneração | nascimentos a partir de 2024-08-02 | RDL 9/2025 |
| Base de cotização em nascimento/cuidado | BCCC do M-2 | 2026 | Orden PJC/297/2026 (BOE-A-2026-7296) |
| Base diária durante IT/risco/nascimento | base do mês anterior ÷ 30 (grupo mensal); ÷ dias reais (grupo diário) | 2026 | Orden PJC/297/2026 |
| Tempo parcial (BR) | soma dos últimos 3 meses ÷ dias do período | — | RDL 11/2024 |
| Tope máximo de cotização | EUR 5.101,20/mês | 2026 | Orden PJC/297/2026 (citada no contexto) |
| Teto diário | [INCERTO] texto truncado ("170 04/d"); consistente com 5.101,20 ÷ 30 = 170,04/dia | 2026 | Orden PJC/297/2026 [INCERTO] |
| 62983 SILTRA | CRA 0054, indicador E | — | ES-CRA-001 Table 84 |
| 62983 Modelo 190 | clave L / L05 (Art. 7.e LIRPF) | — | Modelo 190 |

- **Artefato afetado:** WTC Espanha **V3.9** (In Progress) e DD **V3.7** (In Progress) — Lily mandou editar nessas versões; Wallisson marcou mudanças em laranja (Lily em roxo). Documento "BCCC/BCCP Base Logic" (Seção 5 errada). ES-CRA-001.
- **Erros corrigidos:**
  - Série 6298: AEAT clave A "subject to withholding" → clave L/L05 (62983) e L/L01 (demais).
  - Payouts 79417–79424 (e 79416–79418 de risco/parental): AEAT clave B/pago directo → clave A/Work_Cash_Gross (pago delegado).
  - 79422: campos 296 indevidos removidos.
  - 79419: nome "75% day 21" → "75% day 21+".
  - Entendimento da Lily (per-day só no payout) → per-day também na base de cotização.
  - Seção 5 do documento BCCC/BCCP Base Logic ("full monthly base always") → incorreta em mês parcial.
  - **Autocorreção de Wallisson:** exemplos A–C que zeravam BCCP durante licença por contingência comum (e BCCC durante AT) → errado; as duas bases continuam (Art. 6 Orden PJC/297/2026). Também o worked-day base entra em BCCC e BCCP, não só em BCCC.
- **Pendências:**
  - 2026-09-08: Gulnaaz reporta que a lógica de licença médica **ainda não funciona** em produção (entidade REF-03-069; licença médica de abril a maio de 2026 deveria usar a base de SS de março, último mês trabalhado inteiro). Anexou G2N de mar/abr/mai 2026 e payslip correto do A3. Para Lily + Wallisson.
  - Lily: análise completa, regulation design, reports mapping e desenvolvimento ("major change to Spain regulations"). ETA com Mohit.
  - Ponto 6 (15ª paga): Lily criou o campo "Extra Pay Month N (Accrual Month)"; sem resposta nossa sobre CBA [INCERTO se precisa de ação nossa].
  - Further query 4 (gatilho do cálculo segmentado): resposta truncada no PDF [INCERTO].
- **Fronteira:** regulation steps/desenvolvimento = Lily Li / Dev; severance override (P3) = regulation steps; implementação = Gulnaaz.

## HRBS-14054 — Congo: TUS subestimado por falta de gross-up do car allowance no G2N do cliente
- **País / Cliente:** Congo (Brazzaville) / BH Congo / **Tipo:** Service Request / **Prioridade:** Medium / **Estado final:** Open / Support Group: Compliance Support
- **Datas:** criado ~2026-09-01 por Daniel Kelvin Balogun; última atualização ~2026-09-02 (Mohit Jain).
- **Arquivos-fonte:** `37 - Ticket - HRBS-14054 - TUS Understated for Multiple Employees — Root Cause is Missing Car Allowance Gross-Up from client g2n.txt`
- **Quem pediu:** Daniel Kelvin Balogun (validação de payroll).
- **Pergunta / problema:** o TUS sai menor que o esperado para empregados com car allowance. Alguns têm car allowance líquido garantido (500.000 / 625.000 / 750.000 conforme grade); o HRB faz o gross-up corretamente. O cliente registra o gross-up em coluna separada "Gross up", o que é só outra estrutura. Para dois empregados a coluna está vazia, e isso reduz o Taxable Total e o TUS. Outros casos (taxa de produtividade; "SS Employee Arrears" em três empregados) são tratados como dado do cliente e ficam fora do ticket. **Pergunta: o gross-up deve entrar na base do TUS (Unique tax) no Congo?** Anexo TUS_Discrepancies_6Employees.xlsx.
- **Resposta / decisão nossa:** nenhuma no snapshot.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| TUS | 7,5% do Taxable Total | sem vigência no ticket | sem fonte no ticket |
| Car allowance líquido garantido | 500.000 / 625.000 / 750.000 (por grade; moeda não citada, provavelmente XAF [INCERTO]) | — | política do cliente |

- **Artefato afetado:** base do TUS (regulação CG); versão não citada.
- **Erros corrigidos:** nenhum confirmado (o erro é do G2N do cliente, não do HRB, segundo o autor).
- **Pendências:** resposta de compliance sobre o gross-up na base do TUS (Wallisson).
- **Fronteira:** inconsistências de dados (arrears, produtividade) = cliente.

---

## Síntese do grupo

### (a) Decisões recorrentes / padrões
1. **Espanha, base de cotização em licenças (HRBS-10563):** por dia e por contingência; BCCC e BCCP **nunca zeram** enquanto o trabalhador está de alta; worked-days entram nas duas bases; piso/teto sobre a base mensal (não proporcional a dias trabalhados); nascimento/cuidado usa BCCC M-2; base: Orden PJC/297/2026 Art. 6.
2. **Espanha, AEAT/190 de subsídios de IT com empregado ativo = clave A (pago delegado)**, não B; clave B só quando o INSS paga diretamente. Severance isento = clave L/L05 + CRA 0054 indicador E.
3. **Não renomear/criar estrutura no WTC alheio sem aval**: Wallisson não renomeou payouts da Lily; variantes parciais e ERTE não viram WT (tratados por coeficiente/status).
4. **Versionamento de artefato:** não apagar versão anterior em que outro time já trabalhou (SR-221, reclamação da Ruchi); editar em versão In Progress (WTC V3.9 / DD V3.7 na Espanha) com cor própria de destaque.
5. **Colômbia (PMI):** 5 tickets de gap para a transição Instaroll; Mohit classificou CO como precisando de **redesign ou grande correção de gaps**; todos ficam para a gap analysis na pesquisa de CO (Wallisson). Nenhuma resposta nossa ainda.
6. **Pedido recorrente de BA (Chile):** coluna no WTC com o **report code** aplicável a cada WT (SR-221 e SR-232).
7. **Fronteira com Reports (Holanda):** Reports só mexe em Custom Reports com spec; perguntam a Compliance se o report é statutory.

### (b) [INCERTO]
- SR-221: se a revisão dos campos amarelos foi concluída.
- SR-316: estado após 2026-08-10.
- HRBS-12492: se o sistema realmente calcula o IBC de férias sobre o bruto do mês (só uma observação do Support).
- HRBS-10563: teto diário 2026 truncado no texto ("170 04/d", provavelmente EUR 170,04/dia); resposta ao "further query 4" (gatilho) truncada; se o ponto 6 (15ª paga / CBA) exige ação nossa; correção depois da reclamação de 2026-09-08.
- HRBS-14054: moeda do car allowance (provavelmente XAF).
- HRBS-15253: o que Manju Shetija atualizou em 2026-09-28.
- Todas as datas são aproximadas (convertidas de "há N dias/meses").
- Valores de CO e NL são **declarados por quem pediu** e não foram validados por nós; não devem entrar como valor confirmado sem checar a skill/fonte oficial.

### (c) Artefatos e últimas versões citadas por país
| País | Artefato | Versão / estado |
|---|---|---|
| Chile | Report Spec CL-DT-001 (LRE) | sem versão; In Progress; pedido de coluna de report code no WTC |
| Chile | Report Spec CL-PRV-001 (Previred Planilla Mensual) | sem versão; Open |
| Chile | WTC CL | sem versão; nova coluna "report code" pedida |
| China | Payslip Generator CN | v1.0 (a converter para o formato Compliance); pai CT-4457 |
| Colômbia | WTC CO (WTs 63123, 62837, 52552, 21125, 64993, 2552–2556, 21330, 22110, 22112) | sem versão; gap analysis/redesign pendente |
| Holanda | report `netherland-ssc-pdf` | Custom Report, sem spec |
| Lituânia | nenhum citado | pergunta se existe parameter sheet LT assinado |
| Espanha | WTC ES | **V3.9** (In Progress) |
| Espanha | DD ES | **V3.7** (In Progress) |
| Espanha | ES-CRA-001 (Table 84); documento "BCCC/BCCP Base Logic" | sem versão; Seção 5 incorreta |
| Congo | regulação TUS | sem versão |
