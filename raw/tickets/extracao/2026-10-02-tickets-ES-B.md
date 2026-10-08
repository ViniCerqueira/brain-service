# Tickets YouTrack: Espanha B — Modelos 190/111/296, certificado, finiquito, regulação, handover, SILTRA, AFI report

> Fonte: `raw/tickets/txt/` (pdftotext). Datas absolutas foram **estimadas** a partir das datas relativas ("N days ago") e da data de impressão de cada snapshot; podem variar ±1 dia. Nomes de empregados, NIF/DNI, datas de nascimento e códigos de empregados de teste que aparecem em anexos/exemplos foram omitidos de propósito.
> Pessoas (lado Mercans/HRBlizz): **Lily Li** (Business Analyst), **Drew Ðispuu** (Developer), **Brenet** (Business Analyst/QA citado), **Gulnaaz Parveen** (Implementation/operação Espanha, reporta testes contra o A3), **Katrin Rudi** (configuração/coordenação), **Mohit Jain** (autor da KB de regulação), **Manju Shetija** (líder de compliance), **stripathi** / **Afrin Fathima** / **Mohamed Nabil** (Support), **Wallisson** (nós: Research/Compliance).

---

## CT-4321 — ES: Regulation Handover Checklist
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / — (projeto Compliance) / Research task / Normal / **Ready for Design** / criado ~jan/2026 ("8 months ago" em 14/09/26), start date 12 Jan 2026, design due 31 Dec 2025, Sprint 42; última atualização ~jun/2026 (por Wallisson).
- **Arquivos-fonte:** `64 - Ticket - CT-4321 ES - Regulation Handover Checklist.txt` (snapshot único, 14/09/2026).
- **Quem pediu:** criado por Wallisson; assignees Lily Li (Regulation Designer / Build), QA Mohit Jain e Ruchi Gupta.
- **Pergunta / problema:** checklist de handover dos artefatos de regulação da Espanha para Design/Build: CCG 2026 (Spain Payroll Configuration Guide 2026), WTC, DD e Specs de Modelo 296, 216, 190, 111, Fichero de Bases (SLD), AFI e CRA. Critérios de aceite: inputs do ICE, da Advisory, verificação contra pesquisa própria e simulação em software terceiro ("Above list is confirmed"). Depois (~abr/2026) Lily perguntou se só precisava mapear a aba "ES - Statutory Research" da spec de payslip, já que os campos de master data não aparecem nela.
- **Resposta / decisão nossa (~abr/2026, "5 months ago"):** a aba **ES - Statutory Research** é só para **pay elements** (earnings, deductions, bases de contribuição, contribuições do empregador): é ali que o BA mapeia seção do payslip e flags BCCC/BCCP/IRPF. Os campos de cabeçalho (nome da empresa, NIF, CCC, nome do empregado, NAF, Grupo de Cotización, tipo de contrato, % IRPF etc.) aparecem na aba **España (EN)** (a nómina) só como referência; a origem deles já está no **DD** (ex.: `$legal_entity_hr.tax_id_number_nif`, `$hr.social_security_affiliation_number`, `$hr.contribution_group`, `$legal_entity_hr.social_security_contribution_account_code`). Não há mapeamento separado.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Payslip Spec (Google Sheet enviada por Manju ~mar/2026), CCG 2026, WTC, DD, Specs M296/M216/M190/M111/Fichero de Bases/AFI/CRA (sem versão citada).
- **Erros corrigidos:** nenhum.
- **Pendências:** nenhuma explícita (um comentário de Lily foi apagado).
- **Fronteira:** Build/Design (Lily Li) e QA (Mohit Jain, Ruchi Gupta) fazem o mapeamento e a configuração; nós entregamos os artefatos.

---

## CT-A-485 — SPAIN - Regulation Specifications (artigo da Knowledge Base)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / — / artigo de Knowledge Base (projeto Compliance), não é ticket / — / — / criado por Mohit Jain ~jan/2026; atualizado por Lily Li em ~14/09/2026. Sub-artigos atualizados entre 03/02/2026 e 07/09/2026.
- **Arquivos-fonte:** `66 - Ticket - CT-A-485 - SPAIN - Regulation Specifications.txt` (snapshot único, 15/09/2026; 43 páginas, tabela muito embaralhada pelo pdftotext).
- **Quem pediu:** Mohit Jain (autor) e Lily Li (mantém). Não há comentários nem respostas nossas.
- **Conteúdo:** é a **especificação de configuração** (lado Build) do motor de payroll da Espanha, derivada do CCG/WTC: (1) tabela de **flags** (58xxx/639xx) com fórmulas sobre campos do DD (`$hr.tax_regime`, `$hr.contract_type_key`, `$hr.family_situation`, `$hr.tax_residency_status`, `$hr.child_count_*`, `$hr.disability_code`, `$hr.extra_pay_month_1..3`, `$legal_entity_hr.company_turnover_100000` etc.); (2) lista de "Regulation IDs" 9724001–9724621 (pay elements de regulação: bases e isenções de benefícios, plano de pensão, indenização/severance, bases e contribuições BCCC/BCCP mensal/diária/tempo parcial/afastamento, cota de solidariedade, horas extras, cálculo anual de IRPF, regularização, não residente, regime Beckham, conselheiros); (3) 21 sub-artigos (CT-A-486 a CT-A-501), incluindo "ES: Retro Design Concept" (27/07/2026), "ES BCCC Taxability Matrix" (07/09/2026), "ES IRPF General Tax Table 2026", "ES Zero Tax Floor", "ES Low Income Reduction", "ES Solidarity Quota", "ES Pension Plans Contribution Limit" e três sub-artigos **"Not in Scope - ES Garnishments and Court Orders..."** (02/06/2026).
- **Resposta / decisão nossa:** nenhuma no artigo.
- **Valores estatutários (como escritos na KB; nenhum traz fonte nem vigência explícita, exceto o rótulo "2026" da tabela de IRPF):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Base máx. de cotização mensal (SS ceiling employee / part-time) | 5.101,20 | [INCERTO] presumido 2026 | sem fonte no ticket |
| Base mín. mensal Grupo 1 / 2 / 3 / 4-7 | 1.929 / 1.599,60 / 1.391,70 / 1.424,50 | [INCERTO] presumido 2026 | sem fonte no ticket ([INCERTO] associação grupo↔valor pela tabela embaralhada; G3 < G4-7 parece estranho) |
| Base mín. tempo parcial por hora G1 / G2 / G3 / G4-11 | 11,98 / 9,94 / 8,65 / 8,58 | [INCERTO] | sem fonte no ticket |
| Base máx. / mín. diária (grupos 8-11) | 170,04 / 47,48 por dia | [INCERTO] | sem fonte no ticket |
| Base mín. estagiário (Floor for Intern) | 1.424,50 [INCERTO] | [INCERTO] | sem fonte no ticket |
| Contingências comuns EE / ER | 4,7% / 23,6% | — | sem fonte no ticket |
| MEI EE / ER | 0,15% / 0,75% | — | sem fonte no ticket |
| Desemprego contrato indefinido (contract key < 401) EE / ER | 1,55% / 5,5% | — | sem fonte no ticket |
| Desemprego contrato temporário (contract key > 389) EE / ER | 1,6% / 6,7% | — | sem fonte no ticket |
| FOGASA ER | 0,2% | — | sem fonte no ticket |
| Formação profissional EE / ER | 0,1% / 0,6% | — | sem fonte no ticket |
| Linha "58208 = 4" EE / ER | 2% / 7% ([INCERTO] qual categoria é o valor 4) | — | sem fonte no ticket |
| Horas extras força maior EE / ER | 2% / 12% | — | sem fonte no ticket |
| Horas extras normais EE / ER | 4,7% / 23,6% | — | sem fonte no ticket |
| Acidente de trabalho | conta de taxa 52560 (por entidade) | — | sem fonte no ticket |
| Estagiários (58208 = 2/3): valores fixos 57,72 / 7,95 / 11,51 e 2,88×dias (máx. 65,42), 0,35×dias (máx. 7,95) | [INCERTO] o que cada um representa | — | sem fonte no ticket |
| Vale-refeição isento | 11,00 / dia | — | sem fonte no ticket |
| Seguro saúde isento | 500 / pessoa; 1.500 se com deficiência | — | sem fonte no ticket |
| Cheque transporte isento | 1.500 / ano | — | sem fonte no ticket |
| Quilometragem isenta | 0,26 / km | — | sem fonte no ticket |
| Diárias isentas: com pernoite / sem pernoite / exterior com pernoite / exterior sem pernoite | 53,34 / 26,67 / 91,35 / 48,08 (a KB escreve "per km" nas três últimas: [INCERTO], parece erro de rótulo para "per day") | — | sem fonte no ticket |
| Stock options isentas | 12.000 | — | sem fonte no ticket |
| Mínimo pessoal | 5.550; +1.150 se idade > 65; 2.550 se idade > 75 (fórmula aninhada, como escrita) | — | sem fonte no ticket |
| Mínimo por deficiência do empregado | 3.000 / 6.000 / 9.000 / 12.000 (códigos 1/2/3/3+assistência ou mobilidade reduzida) | — | sem fonte no ticket |
| Mínimo por descendentes | 2.400 / 2.700 / 4.000 / 4.500 (4º em diante); metade se não houver cômputo integral; +2.800 por filho < 3 anos | — | sem fonte no ticket |
| Mínimos por ascendentes e deficiência de ascendentes | "Check WTC" | — | sem fonte no ticket |
| Indenização isenta por demissão objetiva | 20 dias/ano, máx. 12 meses | — | sem fonte no ticket |
| Indenização isenta por demissão improcedente | 45 dias/ano antes de 12/02/2012, 33 dias/ano depois; tetos 24 e 42 mensalidades; isenção total máx. 180.000 | — | sem fonte no ticket |
| Redução de rendimento irregular | 30% sobre até 300.000 (condições: antiguidade > 2 anos e 62181 < 0,1) | — | sem fonte no ticket |
| Low Income Reduction | limite de rendimento líquido 19.747,50; fórmula "SUBTRACT(band; 2000)" ([INCERTO] leitura) | — | sem fonte no ticket |
| Retenção mínima contrato < 1 ano | 2% (MAX(...; 0,02)) | — | sem fonte no ticket |
| Não residente UE/EEE / resto do mundo | 19% / 24% | — | sem fonte no ticket |
| Regime de expatriados (Beckham) | 24% até 600.000; 47% sobre o excesso | — | sem fonte no ticket |
| Conselheiros (Board of Directors) | 35%; 19% quando 58203 > 0 (faturamento da empresa < 100.000) | — | sem fonte no ticket |
| Tabela de IRPF | "ES IRPF General Tax Table 2026" (sub-artigo, valores não impressos) | 2026 | sem fonte no ticket |

- **Artefato afetado:** é o espelho de configuração do CCG/WTC (Regulation IDs 9724xxx, pay elements 58xxx/62xxx/63xxx/64xxx). Sem versão.
- **Erros corrigidos:** nenhum registrado no artigo.
- **Pendências:** nenhuma registrada.
- **Fronteira:** artigo do time de Build/Configuração (Mohit/Lily). Penhoras/ordens judiciais marcadas como **Not in Scope**.

---

## HRBS-12839 — Spain Regulation_AFI Report confirmation
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / Mercans ("Spain all clients"; amostra do cliente KGS) / Service Request / Medium / **Open** / criado ~06/08/2026; atualizado ~07/08/2026 (Afrin Fathima). Ambiente Production, fase Live/BAU, Tier 3, SLA "Violation".
- **Arquivos-fonte:** `09 - Ticket - HRBS-12839 - Spain Regulation_AFI Report confirmation.txt` (snapshot único, 08/08/2026).
- **Quem pediu:** Gulnaaz Parveen (operação/Implementation Espanha).
- **Pergunta / problema:** a Espanha tem um "AFI report" com a contribuição de pensão enviada à Seguridad Social via **SILTRA**. Ela vê "ES: AFI - Affiliation Message (Social Security) - SPEC" em desenvolvimento e pergunta se é o mesmo relatório; anexou amostra AFI do cliente KGS (arquivo A26G0002).
- **Resposta / decisão nossa:** **nenhuma resposta registrada** no snapshot.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Spec "ES: AFI - Affiliation Message (Social Security)" (sem versão).
- **Erros corrigidos:** nenhum.
- **Pendências:** confirmar se a AFI Spec corresponde ao arquivo AFI de pensão do A3/KGS: **nós (Wallisson)**. [INCERTO] se foi respondido depois.
- **Fronteira:** nenhuma explícita.

---

## HRBS-13757 — Spain Regulation_Statutory report issues and testing feedback
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / Mercans ("SPAIN all clients"; entidades de teste citadas: REF-04-261 e Hermes Fund Managers Ireland Limited) / Incident / Medium / **Pending on reporter** (Paused) / criado ~25/08/2026; última atualização ~17/09/2026 (Lily Li). Production, "Not legal entity related ticket", Tier 3.
- **Arquivos-fonte:** `59 - Ticekt - HRBS-13757 - ...txt` (10/09/2026), `77 - Ticekt - HRBS-13757 - ...txt` (18/09/2026).
- **Evolução entre snapshots:** em 10/09 o assignee era **Lily Li**; em 18/09 passou a **Wallisson**. Entraram depois de 10/09: resposta de Wallisson (11/09), novo erro de M190 (15/09), atribuição a Wallisson e pedido de campos obrigatórios no payslip (17/09).
- **Quem pediu:** Gulnaaz Parveen (testes de relatórios contra o A3 e portais oficiais).
- **Pergunta / problema:** feedback de testes dos relatórios estatutários da Espanha: SEPE CERTIFICA (schema XML não bate com o SEPE; dados de representante legal não saem), SEPE CONTRATA (upload ok), SEPE LLAMAMIENTO (não gera arquivo), SEPE PRORROGA (formato ok); M216 ok; M111, M190 e M296 rejeitados no portal da AEAT; M190 trazendo não residentes; Fichero de Bases com muitos códigos sem mapeamento; códigos CNO no CERTIFICA; formato do Certificado de Retenciones diferente das amostras; payslip sem campos obrigatórios.
- **Resposta / decisão nossa:**
  - **~01/09/2026 (Fichero de Bases, contra `Codigoes_Fichero_de_bases.xlsx`):** **L00 e L13 são independentes e podem coexistir** no mesmo período (por isso o A3 mostra L00+L13); **L03 cobre sempre períodos anteriores ao L00 atual**, então é sempre separado. **L01** na tabela de tipos de liquidação **não é código TGSS real**: sinalizado, não apagado. Descrições de **L02 e L03 estavam erradas**, corrigidas pelo manual oficial do SLD da TGSS. L13 (linha 135) já estava correto.
  - **~01/09/2026 (CERTIFICA / CNO):** o DD está **correto com 4 dígitos** (CNO-11 / tabela T90 da Seg-Social); o campo **CodProfesion exige 7 dígitos**, e o mapeamento passava o valor sem preenchimento (por isso 3123, código válido, foi rejeitado). Correção: **completar à direita com zeros até 7 dígitos**. Specs atualizadas: **Fichero de Bases v2.5** e **CERTIFICA v1.1**.
  - **~01/09/2026 (2ª resposta):** Lily não achou mudanças; Wallisson reaplicou nas versões mais recentes do Drive: no CERTIFICA o fix já estava (linha 30), acrescentou aba de **Version Control**; no Fichero de Bases reaplicou as correções L01/L02/L03 e preencheu as entradas v2.3/v2.4 que faltavam no controle de versão.
  - **~11/09/2026:** M111: spec confirmada (posição, tamanho, checksum) e já testada, o erro de portal da entidade precisa de análise do **Dev**. M296: spec correta e atual, mesmo encaminhamento ao **Dev**. **Certificado anual: formato confirmado correto, verificado contra 5 certificados reais emitidos/aceitos pela AEAT.**
  - Lily (BA, ~31/08): rejeição de M190/M296 no portal porque o arquivo declara **Ejercicio = 2026**, ano ainda não encerrado (regra de negócio da AEAT, não bug de formato); no arquivo dela, não residentes não aparecem no M190. Em ~04/09: padding de CNO resolvido; posições do M111 ajustadas; problema de exibição da taxa de imposto no payslip resolvido e deploy em produção no mesmo dia.
- **Valores estatutários:** nenhum valor de alíquota/teto. Regras de formato: CodProfesion = 7 dígitos (CNO de 4 dígitos + zeros à direita), fonte: tabela T90 CNO (seg-social.es) e spec; tipos de liquidação L00/L13/L03 conforme manual SLD TGSS.
- **Artefato afetado:** Spec Fichero de Bases (SR-79) **v2.5**; Spec SEPE CERTIFICA (SR-145) **v1.1**; Specs M111/M190/M296; Certificado de Retenciones (SR-342); Payslip.
- **Erros corrigidos:** descrições L02/L03 erradas → corrigidas pelo manual TGSS; L01 marcado como código inexistente; CodProfesion sem padding → padding a 7 dígitos; Version Control do Fichero de Bases sem v2.3/v2.4 → preenchido.
- **Pendências:**
  - **M190 ainda com erro no portal** (Hermes / REF-04-261, ~15/09): atribuído a **Wallisson** (ligado a SR-83).
  - **Payslip sem campos obrigatórios por lei** segundo o cliente (~17/09): **código de contrato (ex.: 100)** e **data de antiguidade**: **nós (Wallisson)** avaliar.
  - SEPE CERTIFICA (schema XML) e SEPE LLAMAMIENTO (não gera arquivo): [INCERTO] se foram resolvidos; só o representante legal e o CNO aparecem como resolvidos.
  - Fichero de Bases: pedido de Gulnaaz para nomear relatórios com "L" no início e conferir de onde vêm as bases do L13: [INCERTO] se foi atendido.
- **Fronteira:** erros de portal com spec já confirmada (M111, M296) → **Dev**. Testes no A3/portais → Gulnaaz (operação).

---

## HRBS-14528 — SILTRA Notifications Integration to HRB
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / **KGS - Kidde Global Solutions** / Question / Inquiry / Medium / **Open** / criado ~12/09/2026; atualizado ~24/09/2026 (Manju Shetija). Production, Live/BAU, Tier 3.
- **Arquivos-fonte:** `92 - Ticket - HRBS-14528 - SILTRA Notifications Integration to HRB.txt` (snapshot único, 28/09/2026).
- **Quem pediu:** Mohamed Nabil (Support/cliente KGS).
- **Pergunta / problema:** integrar ao HRB as **notificações recebidas no SILTRA** (mensagens que a Seguridad Social envia sem que tenhamos mandado arquivo, avisando de ações pendentes). Vem uma resposta e um PDF com link para a notificação no portal; pasta de recepção `C:\SILTRA\SVA\Msjrec`; amostras `.msj`.
- **Resposta / decisão nossa:** **nenhuma registrada.** Katrin Rudi (~16/09): precisa de pesquisa do time de Manju antes da configuração; stripathi (~17/09) mudou o support group para **Compliance** e pediu devolução à configuração depois da pesquisa.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** nenhum ainda (possível nova integração/spec).
- **Erros corrigidos:** nenhum.
- **Pendências:** pesquisa de compliance sobre o formato/uso das notificações SILTRA (.msj): **nós (Wallisson)**; depois volta para Configuração.
- **Fronteira:** a integração em si é de **Configuração/Integration**; nossa parte é só a pesquisa.

---

## SR-82 — ES: Modelo 111 (Personal Income Tax IRPF) - SPEC
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / — (projeto Statutory Reports) / Statutory report spec / Major / **In Review** (fase Final Review) / criado ~jan/2026; due 31 Jan 2026; última atualização 03/09/2026 (Lily Li). Spent time 1d 5h 17m.
- **Arquivos-fonte:** `40 - Ticket - SR-82 ES - Modelo 111 (Personal Income Tax IRPF) - SPEC.txt` (snapshot único, 03/09/2026).
- **Quem pediu:** Lily Li (BA) e Drew Ðispuu (Dev); erros de portal trazidos por Gulnaaz (amostra A3 "111 (4).TXT").
- **Pergunta / problema:** desenvolvimento e teste do M111. Pontos: troca de código 57176 → 58176 nas linhas 24/27; linhas 29–31 para clave G; filers mensais × trimestrais; arquivo rejeitado no portal da AEAT (nome da empresa com tamanho diferente do A3).
- **Resposta / decisão nossa:**
  - **~jul/2026:** Wallisson acrescentou as linhas 29, 30 e 31 para cobrir **clave G** (citado por Lily).
  - **~02/09/2026 (causa raiz do erro de portal):** o campo **Company Legal Name (12-51, 40 caracteres) eram dois campos da AEAT fundidos**: *Denominación o Apellidos* (23-82, 60) + *Nombre* (83-102, 20) = 80 caracteres. Os 40 que faltavam deslocavam todas as posições seguintes, inclusive 6 campos de contagem de perceptores (98 caracteres) e o IBAN (2434 caracteres). **Tabela de campos inteira reconstruída** contra o desenho técnico oficial da AEAT (**dr111e16v18.xls**), conferida byte a byte contra a amostra A3 e a saída do HRB.
  - **Amendment Type:** no M111 são dois campos: **Declaración Complementaria (pos. 538, "X"/branco)** e **Número de Justificante de la Declaración Anterior (539-551, 13 dígitos)**, preenchidos só em complementar/substitutiva. M190 (Complementary Flag 121 + Substitutive Flag 122 + Prior Declaration ID 123-135) e M216 (Complementary 432 + Prior Justificante 433-445) já estavam certos. **Spec v4** atualizada.
  - Lado Dev (Drew, ~14–19/08): período mensal = só o mês; trimestral = 1T–4T; uma configuração `es-modelo-111` com dois custom reports (`es-modelo-111-monthly`, 1 período; `es-modelo-111-quarterly`, 3 períodos), variante lida por `$report.label`. Regra de uso: o trimestral é retrospectivo a partir da folha usada, então deve ser gerado a partir do último mês do trimestre. Mensal aprovado ~20/08, trimestral ~21/08 (após corrigir NIF em branco).
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Periodicidade M111 | mensal (01–12) ou trimestral (1T–4T), conforme `company.filer_type` | — | spec (citada pelo Dev); sem fonte legal no ticket |
| Denominación o Apellidos / Nombre | pos. 23-82 (60) / 83-102 (20) | desenho vigente | AEAT dr111e16v18.xls |
| Declaración Complementaria / Justificante anterior | pos. 538 / 539-551 | desenho vigente | AEAT dr111e16v18.xls |

- **Artefato afetado:** **M111 Spec v4** (02/09/2026); DD (novo campo pedido).
- **Erros corrigidos:** nome da empresa como um campo de 40 caracteres → dois campos AEAT (60 + 20), com deslocamento de todas as posições seguintes corrigido; código 57176 → 58176 (linhas 24/27).
- **Pendências (pedido de Lily, 03/09, sem resposta no snapshot): nós (Wallisson):**
  1. Campos em branco nas colunas B–S: Tax Year, [05] In-Kind Value, [11] In-Kind Value to Professionals, [17] In-Kind Prize Value, [23] Forestry In-Kind Value, [26] Payments to Non-Resident Entities, [29] Previous Declaration Result (só complementar), Reserved for Colegio Concertado.
  2. Acrescentar ao DD `$legal_entity_hr.previous_m111_justificante_number`.
  3. Lily vai remover do DD as opções além de original e substitutiva, porque o sistema só suporta essas duas. [INCERTO] impacto na regra do campo 538 (complementar).
  - Em HRBS-13757 (~10/09) persistia erro de IBAN no portal para a entidade de teste; em 11/09 Wallisson disse que a spec está correta e encaminhou ao Dev.
- **Fronteira:** desenho da solução mensal/trimestral e erros de portal com spec correta → **Dev (Drew)**.

---

## SR-83 — ES: Modelo 190 (Personal Income Tax IRPF) - SPEC
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / — (testes nas entidades "Spain Reports Testing" e Hermes / REF-04-261) / Statutory report spec / Major / **In Review** (Final Review) / criado ~jan/2026; due 31 Jan 2026; última atualização 16/09/2026 (Lily Li). Spent 2d 3h. Ligado a SR-342, CT-4406 (Retribución Flexible), CT-4433 (Spain Regulation Support).
- **Arquivos-fonte (7 snapshots):** `17 - ...SR-83...` (12/08), `26 - ...` (19/08), `43 - ...` (04/09), `57 - ...` (10/09), `67 - ...` (15/09), `73 - ...` (16/09 13:54), `74 - ...` (16/09 18:53, final; idêntico ao 73 no conteúdo).
- **Evolução entre snapshots:** 12/08 → até a resposta sobre posições/clave B (10/08) e o pedido de Lily a Drew (12/08). 19/08 → + WTC V4.4, Declaration ID corrigido, pergunta sobre posições que "não batem" (Brenet). 04/09 → + correção de posições (19/08), implementado (20/08), erro de portal (03/09). 10/09 → + causa raiz Type 2 (04/09), 5 campos novos, registros B/03 e L/27 extras. 15/09 → + confirmação dos 5 campos, remoção dos registros vazios, aceite, deploy em produção e novo erro de portal. 16/09 → + correção de Family Situation/Contract Type/Descendants e nova pergunta de Lily.
- **Quem pediu:** Lily Li (BA), Drew Ðispuu (Dev), Brenet (conferência de posições); erros de portal vindos de Gulnaaz (amostras A3).
- **Pergunta / problema:** fechar a spec do M190 (resumo anual de retenções do trabalho): escopo de claves, mapeamento de pay elements, posições do registro de tamanho fixo e rejeições no portal da AEAT.
- **Resposta / decisão nossa (por tema):**
  - **Escopo de claves (21/07):** **Clave B entra no escopo** (não remover). Riscos durante gravidez/lactação e parte da licença parental paga pela SS são "pago directo" pelo INSS/mútua, não pago delegado pelo empregador: é o gatilho da Clave B. Fontes: WTC (campo AEAT Key), Ibermutua, Umivale Activa. Spec **v2.7** (ES-M190-001_Modelo190_Spec_v2.7). Lily pediu para editar o arquivo do enunciado da tarefa e não remover os destaques rosa dela.
  - **Incapacidade (21/07):** 79416 (Sickness leave payment 16-20 days) faltava e foi incluído em *Incapacity Gross Amount* e *Incapacity Withholdings*, com 79414 e 79415.
  - **BIK para Clave G (22/07):** zero na prática, mas mapear como **zero derivado, não fixo**. Espécie é válida para clave G ("percepciones, dinerarias o en especie"; pos. 108-147 sem restrição de clave); o zero vem da falta de pay elements BIK para profissionais. Fixar zero subdeclararia se um cliente pagar profissional em espécie. Os dois campos de incapacidade em espécie (pos. 282-321) são **só Clave A**.
  - **Campos aplicáveis à Clave B (22/07, coluna X em roxo):** identificação, Clave/Subclave (subclave obrigatória para B), os quatro campos de valor, bloco pessoal/familiar ("solo claves A, B, C"), redução de rendimento irregular e despesas dedutíveis; **só B.01:** Incapacity Gross/Withholdings; **não se aplica a B:** Contract Type, Contract End Date, Geographic Mobility, dois campos de incapacidade em espécie.
  - **Rendimento irregular (23/07):** coluna nova no WTC para marcar rendimento irregular → **WTC v4.2**.
  - **Posições e linhas TBC (10/08):** linha 57 = 171-183; linha 58 = 184-196; linha 107 (Ejercicio de Devengo) = 148-151. Linhas 55/56 (contribuição do empregador a pensão/PPSE/Mutualidad; seguro de dependência) não são campos AEAT próprios: o excedente tributável vai para a linha 26 (82-94). **Linha 107 fica**: obrigatória quando houver atrasos/reintegros de exercício anterior (as referências às linhas 59/60 estavam desatualizadas). **Linha 27, Clave B = zeros** (pago directo, empregador não retém).
  - **Subclaves (10/08 e 13/08, WTC V4.4, destaque laranja):** 79429 (risco lactação) e 79430 (risco gravidez): **B.01 → B.03** (01 é só pensões/haberes pasivos; 03 é a residual da B). 79432 (Parental Leave Payout, Paid Weeks): **B.01 → L.27** ("prestaciones públicas por maternidad o paternidad exentas del IRPF"). Fonte: AEAT Diseños Lógicos 190 / FAQ AEAT. Linhas 55/56 → instância **Clave A** da linha 26.
  - **Posições corrigidas (19/08, contra Diseños Lógicos 190, ejercicio 2025, PDF anexado):** a saída do Dev estava certa, a spec errada. **Birth Year** acrescentado (153-156); **Family Situation Key 265 → 157**; **Disability Percentage 333 → 167**; **Contract Type 351-352 → 168**.
  - **Rejeição no portal (04/09):** causa raiz: posições Type 2 ausentes na spec saíam em branco onde a AEAT exige zeros. Acrescentados: titular da unidade de convivência (169); mobilidade geográfica corrigida **328 → 170**; espécie/incapacidade/repercutido (309-321); complemento de ajuda à infância (322); retenções Estado/Navarra/Álava/Guipúzcoa/Vizcaya (323-387); excesso de ações de start-ups (388); rendimentos de gestão de fundos de empreendimento (389); tipos de prestação B.01 (390-394). **Removido campo inventado "White Type 2" em 471-483**, dentro da zona 395-500 que a AEAT exige em branco.
  - **5 campos novos (10/09):** todos confirmados contra Diseños Lógicos 190 (Ejercicio 2025), texto do BOE (**Orden HAC/1431/2025**) e cópia v3.3 do Compliance. *Incapacity In-Kind Withholding Passed-On* (309-321) = parte do ingreso a cuenta (296-308) repercutido ao empregado; como 296-308 é zero, este também é zero.
  - **Erros de portal persistentes (15/09, destaque amarelo):** Year of Birth correto. **Family Situation Key:** a spec listava 6 códigos; a AEAT define **3**, e o **código 1 estava invertido** (exige filho dependente); escopo corrigido para claves A, B (01/03/04/99), C. **Contract Type:** a spec tinha 2 dígitos com códigos 01-05 (outra classificação); a AEAT usa **1 dígito, códigos 1-4, só Clave A**. **Descendants** (antes "Number of Children") mapeado em 266-267, dentro de outro campo; posição real **223-228**, composto de 4 partes: **causa direta do erro 21902B no Registro 3**.
  - Lado Dev: 65816-65819 e 65830-65839 → Clave L / Subclave 24 (espécie isenta); 65820-65829 e 65840-65849 excluídos (~jun/2026); Declaration ID corrigido para `1902026000001` (~14/08); registros vazios B/03 e L/27 removidos (~14/09); campos de contato mapeados por Lily por urgência e corrigidos; **deploy em produção ~15/09/2026**.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Clave B – riscos gravidez/lactação (79429/79430) | B.03 | Ejercicio 2025 (desenho) | AEAT Diseños Lógicos 190 / FAQ AEAT |
| Licença parental paga (79432) | L.27 (isenta) | Ejercicio 2025 | AEAT Diseños Lógicos 190 |
| Clave B – retenções | zero (pago directo INSS/mútua) | — | Ibermutua, Umivale Activa, regras AEAT (citadas) |
| Campos de incapacidade em espécie (282-321) | só Clave A | Ejercicio 2025 | AEAT Diseños Lógicos 190 |
| Family Situation Key | 3 códigos; escopo claves A, B, C | Ejercicio 2025 | AEAT Diseños Lógicos 190 |
| Contract Type | 1 dígito, códigos 1-4, só Clave A, pos. 168 | Ejercicio 2025 | AEAT Diseños Lógicos 190 |
| Descendants | pos. 223-228 (4 partes) | Ejercicio 2025 | AEAT Diseños Lógicos 190 |
| Zona reservada | 395-500 em branco | Ejercicio 2025 | AEAT Diseños Lógicos 190 / Orden HAC/1431/2025 |

- **Artefato afetado:** **ES-M190-001_Modelo190_Spec** (v2.7 em 21/07; edições posteriores sem número; "cópia v3.3 do Compliance" citada em 10/09), **WTC v4.2** (23/07) e **WTC V4.4** (~13/08), DD (4 campos novos de descendentes).
- **Erros corrigidos:**
  - Clave B fora do escopo → incluída.
  - 79416 ausente da incapacidade → incluído.
  - **Nossa própria afirmação de 21/07 de que 79432 era Clave B → corrigida em 10/08 para L.27**; 79429/79430 B.01 → B.03 (WTC V4.4).
  - Posições da spec erradas (Family Situation, Disability, Contract Type; Birth Year ausente) → corrigidas em 19/08.
  - Posições Type 2 ausentes (branco em vez de zero) e campo inventado em 471-483 → corrigidos em 04/09.
  - Mobilidade geográfica 328 → 170.
  - Family Situation com 6 códigos e código 1 invertido → 3 códigos AEAT; Contract Type 2 dígitos/01-05 → 1 dígito/1-4; Descendants 266-267 → 223-228 (15/09).
- **Pendências:**
  - **Nós (Wallisson):** explicar a lógica de mapeamento de *Descendants (Mínimo por Descendientes)* e remover da spec os campos duplicados que já existem no DD (pedido de Lily, 16/09).
  - **Dev:** mapear os 4 novos campos de DD para Descendants (col. V, linha 32); investigar por que Year of Birth ainda falha nos Registros 2/4 (não é defeito de spec).
  - **Dev / dados:** linha 107 (Accrual Year) bloqueada: `wage_type.accrual_period_year` não existe no modelo de dados (mesma lacuna do SR-342); campo sai 0000. Linhas 55/56 precisam dos códigos de wage type da Mercans; pay element de quota sindical (linha 58) não existia no WTC (~04/08).
  - [INCERTO] **Possível regressão:** em ~14/09 o Dev **removeu os grupos de registro B/03 e L/27** por "não terem wage type mapeado na spec", mas em ~14/08 ele tinha dito que 79429/79430 geram B/03 e 79432 gera L/27. Conferir se esses wage types continuam sendo declarados.
- **Fronteira:** configuração, modelo de dados e testes de portal → **Dev (Drew)** / BA (Lily); campos de contato mapeados no sistema por Lily.

---

## SR-85 — ES: Modelo 296 (Personal Income Tax IRPF) - SPEC
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / — (entidades de teste) / Statutory report spec / Major / **In Review** (Final Review) / criado ~jan/2026; due 31 Jan 2026; última atualização 04/09/2026 (Lily Li). Spent 3h 30m. Ligado a CT-4406 e CT-4433.
- **Arquivos-fonte:** `41 - Ticket - SR-85 ES - Modelo 296 (Personal Income Tax IRPF) - SPEC.txt` (snapshot único, 04/09/2026).
- **Quem pediu:** Lily Li (BA), Drew Ðispuu (Dev); erro de portal com amostra A3 ("296 (2).TXT").
- **Pergunta / problema:** spec do M296 (resumo anual de retenções de não residentes / M216): conteúdo da aba "Income Nature and Income Key", 65815, separação dinheiro/espécie, campos obrigatórios e rejeição no portal.
- **Resposta / decisão nossa:**
  - **~mar/2026:** queries respondidas (sem detalhe no ticket).
  - **~mai/2026:** Wallisson disse que a remoção de 65815 (v2.1) estava **errada**, citando WTC v3.3 (Key 20 / Subkey 01, sujeito ao 216).
  - **~jun/2026 (autocorreção):** ele trabalhava numa cópia de referência de 30/04. Na **WTC V3.5** (mudança V3.4 de 07/05), **65815 passou a Flexible Remuneration - Non-Taxable SS Subject**: sem mapeamento 296, então fica **fora** da aba. A remoção estava certa.
  - **~06/08/2026:** confirmou a mudança estrutural: **um registro Type 2 por natureza**: **D (dinheiro) se houver renda em dinheiro, E (espécie) se houver renda em espécie**; quem só tem espécie gera só E, quem só tem dinheiro gera só D; totais do Type 1 = soma dos Type 2. Base e retenção (2582) repartidas proporcionalmente entre dinheiro (58176) e espécie (58177).
  - Confirmado na spec (citado por Lily, ~18/08): **Total Recipients Count = total de registros Type 2**; flag 58218 = 1 e `$hr.tax_residency_status` devem sempre coincidir (Lily: YES).
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| % de retenção não residente com 58205 = 3 | 19% (saída correta "1900", não "2400") | — | spec/BA; sem fonte legal no ticket |
| 65815 (Flexible Remuneration - Non-Taxable SS Subject) | sem chave 296 | a partir da WTC V3.4 (07/05/2026) | WTC V3.5 |

- **Artefato afetado:** **M296 Spec** (v2.1 ~mai; **V2.3** revisada pelo Dev ~ago); WTC v3.3 → V3.5.
- **Erros corrigidos:** nossa contestação da remoção de 65815 (baseada em cópia antiga do WTC) → retirada; linha 41: 57176 → 58176; aba "Income Nature and Income Key" sem 62149, 6298%, 79417-79424, 79429, 79430, 79432 (mudança de Lily); Tax Residence Country (T2-040) em branco → mapeado para país de residência ISO2 (Dev); % de retenção 2400 → 1900; registro indevido para empregado só com dinheiro e contagem de perceptores errada → corrigidos (aceite ~20/08).
- **Pendências (04/09, sem resposta no snapshot): nós (Wallisson):** (1) confirmar se a lista de campos que passaram de branco para zero cobre tudo (Recipient Mediator Flag 134, Issuer Code Type 135, Declarant Payment Type 148, Accrual Tax Year 171-174, Loan Start/Maturity 175-190, Lender Remuneration/Compensations/Guarantees 191-226; erros AEAT E020180–E020300); (2) formato correto de *Record ID / Sequential Number* (77-84): o sistema gera zero-padded alinhado à direita, o A3 gera "1" + espaços. Em HRBS-13757 (~11/09) Wallisson declarou a spec do M296 "correta e atual" e encaminhou o erro de portal ao Dev. [INCERTO] se os zero-fills foram incorporados à spec antes disso.
  - Lily (HRBS-13757): parte das rejeições do M296 vinha de **Ejercicio = 2026** (ano não encerrado).
  - Campos condicionais (endereço T2-031, data/local de nascimento T2-038/039, NIF no país de residência T2-037): Lily disse que são obrigatórios conforme a spec; [INCERTO] mapeamento HR final.
- **Fronteira:** estrutura D/E, população e mapeamento HR → **Dev**.

---

## SR-342 — ES: Employee Tax Certificate - SPEC (Certificado de Retenciones)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / — / Statutory report spec (ES-CERT-001_CertificadoRetenciones_Spec) / Major / **In Review** (Final Review) / criado ~jul/2026; due 31 Aug 2026; última atualização 11/09/2026 (Lily Li). Ligado a HRBS-11736 (certificado faltando na lista) e SR-83.
- **Arquivos-fonte:** `60 - Ticket - SR-342 ES - Employee Tax Certificate - SPEC.txt` (snapshot único, 11/09/2026).
- **Quem pediu:** Lily Li (BA; "urgente"); Dev Drew Ðispuu.
- **Pergunta / problema:** várias rodadas de queries na coluna V da spec; criação de pay elements; desenvolvimento e teste; formato do PDF gerado diferente da amostra do A3.
- **Resposta / decisão nossa:** ~jul/2026: queries respondidas em 3 rodadas (detalhes só na planilha). Como combinado, criados no WTC um **novo pay element de overpayment** e um **novo de "original amount"** → **WTC v4.2** (Lily atribui os códigos).
- Lado Dev/BA: relatório "Spain Employee Tax Certificate" em acceptance (~02/09); Lily pediu trocar códigos antigos **58176 → 58552** e **58177 → 58572** (~04/09); **aceite aprovado ~10/09**. Lily (11/09): a amostra do A3 e o arquivo gerado têm formatos diferentes, pediu para destacar mudanças na spec se for o caso.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** ES-CERT-001_CertificadoRetenciones_Spec (sem versão); WTC v4.2.
- **Erros corrigidos:** códigos antigos 58176/58177 → 58552/58572 (troca de Lily/Dev).
- **Pendências:** nós avaliarmos se a spec deve mudar por causa da diferença de formato com o A3 (11/09). Em HRBS-13757 (~11/09) Wallisson já respondeu que o **formato está correto, verificado contra 5 certificados reais da AEAT**. [INCERTO] se isso foi replicado no SR-342. Lacuna de modelo de dados `wage_type.accrual_period_year` (citada pelo Dev no SR-83 como "mesma lacuna levantada no SR-342").
- **Fronteira:** desenvolvimento → Dev (Drew); atribuição ao dev → Katrin Rudi.

---

## SR-365 — ES: FINIQ-001_Finiquito_Spec
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** ES / — (validação pendente nas entidades de Gulnaaz) / Statutory report spec / Major / **In Review** (Final Review) / criado ~19/07/2026; due 31 Aug 2026; última atualização ~07/08/2026 (Lily Li). Ligado a HRBS-11970 (carta de finiquito faltando no sistema).
- **Arquivos-fonte:** `07 - Ticket - SR-365 - ES FINIQ-001_Finiquito_Spec.txt` (snapshot único, 07/08/2026).
- **Quem pediu:** Lily Li (BA); Dev Drew Ðispuu.
- **Pergunta / problema:** queries da spec (coluna W); depois, no teste, o IRPF de um empregado desligado em fevereiro saiu 0% porque o rendimento anual ficou abaixo do zero tax floor. Lily perguntou o alcance do zero floor, já que no desligamento não há renda futura projetada.
- **Resposta / decisão nossa:**
  - **~21–22/07:** queries respondidas; referência ao **DD v3.9** ("Spain Data Dictionary V3.9").
  - **~04/08 (zero floor no desligamento): comportamento esperado, não defeito.** A cessação da relação (qualquer motivo, inclusive baixa voluntária) é gatilho de **regularização (Art. 87.2.3º RIRPF)**; no finiquito, o valor anual comparado ao zero floor é recalculado para o **total real acumulado no ano**, não a projeção anual original. Se essa base menos o mínimo pessoal for ≤ 0, a alíquota é zero (**Art. 86.1 / 87.3**); quanto mais cedo no ano, mais provável. **Sem correção retroativa** de holerites anteriores (Art. 87.3 impede restituição). **Não se aplica o piso de 2% do Art. 86.2**, que vale só para contratos pactuados com duração inferior a um ano, não para indefinido encerrado antes.
  - Lado Dev (~31/07): população = um documento por empregado com data de término no período; data = `$hr.sepe_last_day_worked`, com fallback para `$employee.last_working_date` (mesma fonte do SEPE CERTIFICA, para os dois relatórios concordarem). Aceite aprovado ~06/08; falta Gulnaaz confirmar nas entidades dela.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Regularização por cessação | obrigatória em qualquer cessação | sem vigência no ticket | Art. 87.2.3º RIRPF |
| Alíquota zero se base regularizada − mínimo pessoal ≤ 0 | 0% | sem vigência no ticket | Art. 86.1 / 87.3 RIRPF |
| Sem restituição de retenções anteriores | — | sem vigência no ticket | Art. 87.3 RIRPF |
| Piso de 2% | só para contratos < 1 ano | sem vigência no ticket | Art. 86.2 RIRPF |

- **Artefato afetado:** ES-FINIQ-001_Finiquito_Spec (sem versão); DD v3.9; CCG (regra do zero floor; Lily cita que o CCG compara com rendimento anual).
- **Erros corrigidos:** nenhum (a dúvida não era defeito).
- **Pendências:** **nós (Wallisson):** responder se o **Finiquito é só para residentes ou também para não residentes** (não está na spec; pergunta de ~07/08 sem resposta no snapshot). **Gulnaaz:** confirmar nas entidades dela.
- **Fronteira:** configuração da população/fonte de data → Dev.

---

## Síntese do grupo

### (a) Decisões recorrentes / padrões
1. **Desenho oficial da AEAT manda, não a spec antiga nem o A3.** Em M190 e M111 a causa dos erros de portal estava na spec (campos fundidos, posições erradas, campos inventados, códigos de outra classificação). Correção sempre contra o desenho oficial (Diseños Lógicos 190 ejercicio 2025 + Orden HAC/1431/2025; dr111e16v18.xls) e conferência byte a byte com amostra A3 + saída HRB.
2. **Campos numéricos AEAT sem valor são preenchidos com zeros, nunca com espaços**; zonas reservadas (ex.: 395-500 do M190) ficam em branco. Vale para M190 (04/09) e M296 (pendente).
3. **Zero derivado, não fixo:** quando um valor é zero só por falta de pay element (BIK para clave G), mapear pela fórmula, não fixar 0.
4. **Clave/subclave pela forma de pagamento:** pago directo INSS/mútua → Clave B (sem retenção, zeros); riscos gravidez/lactação = B.03; licença parental isenta = L.27; incapacidade em espécie só Clave A.
5. **Um registro por natureza** (M296: D para dinheiro, E para espécie; Type 1 = soma; contagem de perceptores = nº de registros Type 2). Não gerar registros de clave com valor zero.
6. **Rejeição por Ejercicio = ano corrente** é regra da AEAT (não se declara ano não encerrado), não bug.
7. **Spec confirmada + erro persistente → Dev.** Quando a spec já foi verificada, o erro de portal da entidade vai para o Dev (M111, M296 em 11/09).
8. **Sempre checar a versão mais recente do WTC/arquivo do enunciado antes de contestar** (caso 65815: contestação baseada em cópia de 30/04, retirada; Lily exige editar o arquivo do enunciado e preservar os destaques dela).
9. **Finiquito/zero floor:** cessação = regularização com base real acumulada; 0% é esperado; sem retroativo; 2% só para contratos < 1 ano.
10. **Payslip spec:** aba Statutory Research só para pay elements; cabeçalho vem do DD.
11. **Códigos de ocupação:** DD guarda CNO de 4 dígitos; o relatório (CERTIFICA CodProfesion) completa até 7 com zeros à direita.
12. **Fichero de Bases:** L00 e L13 coexistem; L03 sempre separado (períodos anteriores); L01 não existe na TGSS.

### (b) Lista de [INCERTO]
- CT-A-485: associação grupo↔valor das bases mínimas (tabela embaralhada; G3 1.391,70 < G4-7 1.424,50 parece inconsistente); vigência dos valores (presumida 2026); significado de 58208 = 2/3/4 (estagiários / 2% e 7%) e dos valores 57,72 / 7,95 / 11,51 / 65,42; rótulo "per km" nas diárias 26,67 / 91,35 / 48,08; leitura da fórmula da Low Income Reduction; base de estagiário 1.424,50.
- HRBS-12839: se a AFI Spec foi confirmada depois (sem resposta no snapshot).
- HRBS-13757: status final de SEPE CERTIFICA (schema XML) e SEPE LLAMAMIENTO (não gera); se os relatórios do Fichero de Bases foram renomeados com "L" e a origem das bases L13 conferida.
- SR-82: impacto de o sistema só suportar declaração original/substitutiva sobre o campo 538 (complementar); resposta aos campos em branco e ao novo campo de DD.
- SR-83: possível regressão. O Dev removeu os registros B/03 e L/27 (~14/09), que antes geravam 79429/79430 (B.03) e 79432 (L.27). Conferir se esses wage types continuam no M190.
- SR-85: se a lista de zero-fill (E020180–E020300) e o formato do Record ID foram incorporados à spec; mapeamento final de T2-031/037/038/039.
- SR-342: se a resposta "formato correto, verificado contra 5 certificados AEAT" foi registrada também no SR-342.
- Todas as datas absolutas são estimadas a partir de datas relativas.

### (c) Artefatos e últimas versões citadas
| Artefato | Última versão citada | Onde / quando |
|---|---|---|
| Spain Wage Type Catalogue (WTC) | **V4.4** (79429/79430 → B.03; 79432 → L.27) | SR-83, ~13/08/2026 (v4.2 em ~23/07: coluna de rendimento irregular + PEs de overpayment/original amount; V3.5 com mudança V3.4 de 07/05 sobre 65815) |
| Spain Data Dictionary (DD) | **V3.9** | SR-365, ~21/07/2026 (+ 4 campos de Descendants e `previous_m111_justificante_number` pendentes) |
| ES-M190-001_Modelo190_Spec | v2.7 (21/07); edições posteriores sem número até 15/09; "cópia v3.3 do Compliance" citada | SR-83 |
| M111 Spec | **v4** | SR-82, 02/09/2026 |
| M296 Spec | **V2.3** (Dev revisou ~ago; v2.1 em ~mai) | SR-85 |
| Fichero de Bases Spec (SR-79) | **v2.5** | HRBS-13757, ~01/09/2026 |
| SEPE CERTIFICA Spec (SR-145) | **v1.1** | HRBS-13757, ~01/09/2026 |
| ES-CERT-001_CertificadoRetenciones_Spec | sem versão | SR-342 |
| ES-FINIQ-001_Finiquito_Spec | sem versão | SR-365 |
| Spain Payroll Configuration Guide (CCG) | "2026" | CT-4321 |
| Payslip Spec (Google Sheet) | sem versão | CT-4321 |
| KB SPAIN - Regulation Specifications (CT-A-485) | atualizada 14/09/2026; sub-artigo BCCC Taxability Matrix 07/09/2026 | CT-A-485 |
| Fontes oficiais citadas | AEAT Diseños Lógicos 190 (ejercicio 2025); Orden HAC/1431/2025; AEAT dr111e16v18.xls; manual SLD TGSS; tabela T90 CNO (seg-social.es); RIRPF arts. 86.1, 86.2, 87.2.3º, 87.3; Ibermutua; Umivale Activa | vários |
