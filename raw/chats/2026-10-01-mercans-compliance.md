# Extração de conhecimento: Projeto Mercans Compliance (Regulatory Affairs)

> **Fontes usadas:** os arquivos deste projeto (`Mercans_Compliance_Handoff_Primer.md`, `mercans_pipeline_v2_4.sh`, e as notas `Spain_IRPF_Annual_Projection_Defect`, `Spain_CCG_v1_6_Withholding_Logic`, `Spain_AFI_OUT_001_v1_2_DD_AFI_Alignment`, `GA_HRBS-14978`, `CI_HRBS-14996`) e a memória acumulada do projeto. As conversas individuais não foram reabertas uma a uma. O Primer é um snapshot de 2026-08-12, e as notas de setembro o substituem onde há conflito.
> Removi os dados pessoais de funcionários de clientes: nomes, IDs e valores individuais de folha. Contatos do lado do cliente aparecem só pelo papel.

---

## 1. Sobre este projeto

- **Propósito:** é o espaço de trabalho do time de Compliance Regulations (Regulatory Affairs) da Mercans, produto HRBLIZZ. Aqui se produzem e mantêm os artefatos estatutários de folha: CCG, WTC, DD, Report Specs, SIR, Payslip Generator, QA cross-checks e skill files por país. Também se respondem tickets de suporte de compliance (YouTrack HRBS-, CT-, SR-).
- **Etapas do serviço cobertas:**
  - **Research Pipeline:** builds de país via `mercans_pipeline_v2_4.sh` / `v2_6.sh` (10–11 estágios) e skill files.
  - **Suporte:** tickets HRBS-/CT-/SR- e queries de spec da BA (Lily Li).
  - **Design:** [INCERTO]. O que mais se aproxima é o BRD v1.2 de automação ticket→redline (n8n + Claude API).
- **Países com trabalho registrado:** Espanha (o mais ativo), Ucrânia, Holanda, Bélgica, França, Colômbia, Gabão, Côte d'Ivoire, Canadá (federal + Québec), Chile, Chade, Rep. do Congo, Bulgária. Há toques leves em Bahrein, Kuwait, Jordânia, Omã, Tunísia, Angola, Namíbia, Nigéria, Portugal e Irlanda.

---

## 2. Entregas

| País | Artefato | Versão | Data | Status |
|---|---|---|---|---|
| Espanha | CCG (`Spain_Payroll_Configuration_Guide_2026_v1_6.docx`) | v1.6 | 17-09-2026 | Aplicado como tracked insertions (autor "Claude"); linha 1.6 no VC |
| Espanha | Data Dictionary (campo SITUPER) | V4.1 | 18-09-2026 | VC linha 29 "Approved" |
| Espanha | Data Dictionary (AFI: 59+2 campos e mappers) | VC 4.6 | 23-09-2026 | Entregue |
| Espanha | Data Dictionary (remoção dos 58 campos AFI "not needed") | VC 28-Set-26 | 28-09-2026 | Entregue |
| Espanha | Data Dictionary (`Spain Data Dictionary V4.0.xlsx`) | VC linha 32 | 29-09-2026 | Draft (a renumeração do VC se perdeu no export do Google; todas as linhas B24–B31 leem 4.0) |
| Espanha | Data Dictionary | V4.5 | [INCERTO, data não registrada] | Entregue com campos duplicados deprecados |
| Espanha | ES-AFI-OUT-001 (SR-432) | v1.1 | 21-09-2026 | Entregue (passe de idioma + correção de dados) |
| Espanha | ES-AFI-OUT-001 | VC 1.2 | 23-09-2026 | 78 queries vermelhas da coluna V respondidas |
| Espanha | ES-AFI-OUT-001 | VC 1.3 | 25-09-2026 | Validação A3; escopo 12/7/58 |
| Espanha | ES-AFI-OUT-001 (arquivo `ES_AFI_OUT_001_v1.0.xlsx`) | VC 1.4 | 29-09-2026 | 76 células verde-escuras da coluna U respondidas |
| Espanha | Resposta ao defeito de projeção anual do IRPF (58163) | n/a | 16-09-2026 | Respondido à Lily Li |
| Espanha | Runbooks AEAT ES-AEAT-INT-OUT-001 / IN-001 | v1.3 | até 31-07-2026 | Entregue (prazo Marko Taylor) |
| Espanha | WTC / CCG | V3.10 / V1.3 | snapshot 12-08-2026 | Versões vigentes naquela data |
| Gabão | WTC (`GA-WTC-001-v3.1-DRAFT-HRBS-14978-2026-09-23.xlsx`) | v3.1 DRAFT | 23-09-2026 | Draft |
| Côte d'Ivoire | Parecer HRBS-14996 (ITS / regime único) | n/a | 22-09-2026, corrigido em 23-09-2026 | A correção substitui o parecer original |
| Côte d'Ivoire | 7 Report Specs (CI-CNPS-001/002/003, CI-DGI-001/002/003/004) | n/a | snapshot 12-08-2026 | Prontas para upload no Drive |
| Côte d'Ivoire | Skill file | n/a | n/a | Entregue, monolítico (refactor pendente) |
| Ucrânia | WTC | V4.1 | n/a | Entregue (correções de maternidade pendentes de input do cliente) |
| Ucrânia | DD | V3.10 | n/a | Entregue (chief_accountant_name, categoria D5 corrigida, No-Data Reason do 1-PV) |
| Ucrânia | Specs UA-1PV-001, UA-1PV-002, UA-INTREP-001 | n/a | snapshot 12-08-2026 | Prontas; nada postado no ticket ainda naquela data |
| Holanda (Mammoet) | Correção P13 | V6 | n/a | Passou em todas as checagens internas (14.226/14.226 cumulativos; gate 37 PASS/0 FAIL) |
| Holanda (Mammoet) | Test parts VTS | v3 | n/a | Prontas para a Manju submeter |
| Canadá | Pipeline completo até Stage 11 + skill `payroll-compliance-canada` | n/a | n/a | Entregue |
| Chile | Skill CL-SKILL-001 | n/a | n/a | Publicado (7 discrepâncias de taxa em aberto) |
| Chade | Skill file | n/a | n/a | Entregue e atualizado com esclarecimentos do Mohit |
| Rep. do Congo | Skill file | n/a | n/a | Entregue e atualizado |
| Bulgária | WTC | V2.2 | n/a | Códigos de renda Art.73 preenchidos |
| Global | Pipeline `mercans_pipeline_v2_4.sh` (v2.6 em uso) | v2.4 / v2.6 | n/a | Em uso |
| Global | BRD Compliance Research Automation | v1.2 | n/a | Finalizado (7 épicos, 15 user stories) |
| Global | 26 skills de país (batch) | n/a | n/a | Geradas; mais 30 atribuídas a Manju/Enaakshi [INCERTO, status não confirmado] |

---

## 3. Decisões tomadas

- **2026-05-23** | Global | Nunca editar as planilhas da Lily Li (Income Nature/Income Key, colunas de BA Mapping) | Claude editou sem pedido e a edição dela já estava correta | Regra do Team Lead (Wallisson)
- **Antes de 2026-08** | Ucrânia | 1-ПВ mensal e trimestral ficam como specs **separadas** | Não há base no Держстат para envio conjunto | Team Lead
- **Antes de 2026-08** | Espanha | M111 e M190 não são combinados | Mesmo princípio: não combinar sem base legal de envio conjunto | Team Lead
- **Antes de 2026-08** | Espanha | ES-AFI-001 fica **em escopo** | Ingerir o arquivo de resposta da TGSS é prática padrão do setor | Team Lead
- **Antes de 2026-08** | Bulgária | Apêndice 9 (е-болнични) e Apêndice 10 (УП-2) ficam **fora de escopo** | Benchmark com SAP SF, Workday, Papaya, Remote, Playroll, Leinonen: nenhum trata como output de folha | Team Lead
- **Antes de 2026-08** | Espanha / CI | Integração outbound-dominante: HRBLIZZ gera o arquivo e o cliente submete no portal | O e-filing é por portal | Team Lead
- **Antes de 2026-08** | Holanda | O mecanismo de leave-relief do 30% ruling é configuração manual controlada pelo cliente, sem proração automática | Ticket HRBS-10545 | Team Lead
- **Antes de 2026-08** | Holanda | Não implementar clieop03 | Substituído pelo SEPA em 2014 | Team Lead
- **Antes de 2026-08** | Canadá | Box 22 (imposto provincial não-Québec) é limitação conhecida, não defeito | n/a | Team Lead
- **Antes de 2026-08** | Global | Estrutura fixa de artefato: template de 10 abas e spec sheet de 22 colunas, modelo ES-M296-001 | Padronização entre países | Team Lead
- **2026-09-17** | Espanha | Na Art. 83.3.e, seguir o **algoritmo publicado pela AEAT** e não a leitura literal do RIRPF (pensionista com mais de 2 descendentes = €1.200) | É o que a calculadora da AEAT retorna | Team Lead / Claude
- **2026-09-18** | Espanha | Criar um campo novo `$hr.perceptor_situation` (SITUPER) em vez de reutilizar employment_status, unemployment_condition ou contract_or_relationship | A reutilização aplicaria os €600 duas vezes ou mistura conceitos diferentes | Team Lead
- **2026-09-18** | Espanha | SITUPER fica ACTIVO para toda a população | Clave B fora de escopo e clave C não listada (02-wtc.md §6) | Team Lead
- **2026-09-23** | Espanha | Estilo da coluna W nas specs: só inglês, veredito primeiro (Yes/No/Confirmed/Not confirmed/Field created/Done), uma linha curta, sem `$` paths, sem citação de manual | Padrão para respostas à BA | Team Lead
- **2026-09-25 / 28** | Espanha | AFI: 12 campos necessários, 7 constantes, 58 "not needed for now" (removidos do DD) | Escopo Phase 1 | Team Lead
- **2026-09-29** | Espanha | **Reversão:** Collective Agreement Code volta ao DD (13 campos AFI necessários, não 12) | TGSS Boletín Noticias RED 5/2018: obrigatório nas altas desde 5-11-2018 | Team Lead
- **2026-09-29** | Espanha | Segmentos OTD, DBA, DSC, DJD e PIT omitidos por enquanto (EXC/FCE/PES já omitidos) | Escopo atual | Team Lead
- **2026-09-29** | Espanha | Tabela T-12 mantida no DD | Converte nacionalidade ISO alpha-2 para código numérico TGSS | Team Lead
- **2026-09-23** | Gabão | Separar o CNSS ER em três elementos (PVID 11% / PF 5% / AT-MP 2%) | Para cada linha do cliente ter um elemento; os 18% combinados já estavam conformes | Team Lead (números de código são proposta do time, a confirmar na plataforma)
- **2026-09-23** | Gabão | 21640–21645 (pensão voluntária EE) tratados como pós-imposto | Não foi encontrado alívio de IRPP | Decisão **a confirmar**
- **Em aberto (OD-13)** | Global | Tickets HRBS- de Compliance Support editam direto ou escalam para CT-? | Não resolvido | Pendente (liderança)
- **n/a** | Global | Maestri descartado para pipeline não-assistido | n/a | Team Lead

---

## 4. Valores e regras estatutárias definidos

| País | Item | Valor | Vigência | Fonte citada |
|---|---|---|---|---|
| Espanha | MEI 2026 | 0,90% (0,75% ER / 0,15% EE) | 2026 | Orden PJC/297/2026 |
| Espanha | Projeção anual IRPF | Total esperado no ano civil, **pagas extra incluídas**, uma única vez | Vigente | RIRPF art. 83.2 |
| Espanha | Variável projetada | Ano anterior é **piso**, não adição: `Annual Var = MAX(prior year, YTD + still expected)` | Vigente | RIRPF art. 83.2 regra 1.ª |
| Espanha | Subtrações da base (lista fechada) | a) irregulares; b) SS do empregado; c) €2.000; d) red. Art. 20; e) €600/€1.200; f) pensión compensatoria. Pensão **não** consta | Vigente | RIRPF art. 83.3 |
| Espanha | Reduções 83.3.e (algoritmo AEAT) | PENSIONISTA €600; NUMDES>2 €600; DESEMPLEADO €1.200; máx. €1.800 | 2026 | Algoritmo AEAT 2026 (ambas as versões) |
| Espanha | Regra da metade | Mínimo por descendente a 50% salvo direito exclusivo (Modelo 145); acumulado 1→1.200 · 2→2.550 · 3→4.550 · 4→6.800 · +2.250 cada | Vigente | RIRPF art. 84 |
| Espanha | Teto da cuota | Se total < €35.200: cuota ≤ 43% × (total − limiar art. 81) | Vigente | RIRPF art. 85.3 |
| Espanha | Taxa inicial | cuota ÷ total × 100, 2 decimais; −2 pts se total < €33.007,20 com moradia DT 18.ª; mínimos 2% / 15% (0,8% / 6% Ceuta-Melilla) | Vigente | RIRPF art. 86 |
| Espanha | Taxa regularizada | (cuota − retenções já feitas) ÷ remuneração restante; **piso zero, sem devolução pelo pagador**; teto 47% (19% Ceuta-Melilla) | Vigente | RIRPF art. 87.3 / 87.5 |
| Espanha | Regime Ceuta/Melilla estendido a La Palma | Redução de 60% da taxa, mínimos 0,8%/6%, teto 19% | A partir de 10-09-2026 | RDL 23/2026 (BOE-A-2026-18828) |
| Espanha | Algoritmos AEAT 2026 | 1-jan a 9-set: ALGORITMO_2026.pdf / PRET-R200/R260; a partir de 10-set: Algoritmo Retenciones-2026_10sept.pdf / R261 | 2026 | sede.agenciatributaria.gob.es |
| Espanha | Prorrata de paga extra | Entra na base de cotização, **não** na base de IRPF | Vigente | LGSS art. 147.1; LIRPF 14.1.a; RIRPF 78.1 |
| Espanha | Limite previdência social | Menor entre 30% da renda líquida e €1.500, + até €8.500 pela tabela de coeficientes | Vigente | LIRPF art. 52.1 |
| Espanha | Ingreso a cuenta sobre contribuição de pensão ER | Nenhum dentro do limite art. 52; **sim** sobre o excedente (BIK art. 43) | Vigente | RIRPF art. 102.1 / 102.2 |
| Espanha | Prazo de baja AFI | 6 dias corridos (antes 3) | A partir de 01-08-2026 | RD 643/2026 |
| Espanha | Formato AFI | Numérico vazio = zeros, alfanumérico = espaços; datas AAAAMMDD | Vigente | Conceptos Comunes Ed. 12/2004 1.3/1.4; Tablas y formatos comunes Ed. 06/2016 |
| Espanha | Acúmulo do bônus L03 | Confirmado | Vigente | RD 2064/1995 Art. 16.2.b/c |
| Espanha | Presentación directa AEAT | HTTP POST JSON para PresBasicaDos (não SOAP); certificado na camada TLS; 190/296 via TGVI Online; pré-produção em `prewww1` | Vigente | Docs AEAT (runbooks v1.3) |
| Ucrânia | ESV maternidade (custeada pelo Fundo de Pensão) | ESV = Yes, 22% | Vigente | п.1 ч.1 ст.7 + ч.5 ст.8 Lei 2464 |
| Ucrânia | Per diem | Parcela dentro do teto não tributável (PIT/ML) | Vigente | пп.170.9.1 ПКУ |
| Ucrânia | Stock options com recharge | 4DF 101, ESV Yes, PIT gross-up 1,219512, ML sobre o nominal | Vigente | n/a |
| Ucrânia | Grant direto da matriz estrangeira | Não é agente fiscal | Vigente | п.171.1 ПКУ |
| Holanda | Norma salarial do 30% ruling | €48.013 (anual, sem a allowance) | 2026 | Belastingdienst (HRBS-10545) |
| Holanda | 30%-regeling | Redução para 27% no prazo cheio de 60 meses | A partir de 2027 | Belastingplan 2025 |
| Holanda | Samenvoegbepaling | Vigente | A partir de 01-01-2027 | n/a |
| Holanda | Betalingskenmerk | 16 dígitos, módulo 11, ainda obrigatório | 2026 | HRBS-9646 |
| Gabão | CNSS | PVID 16% (EE 5% / ER 11%), PF 5% ER, AT/MP 2% ER; teto XAF 1.500.000/mês; ER total 18% | A partir de 01-01-2026 | Décret n°0487/PR/MASI de 18-12-2025 |
| Gabão | CNAMGS | EE 2% / ER 4,1%; teto XAF 2.500.000/mês | Vigente | CLEISS 2026; decreto de 22-12-2016 |
| Gabão | TCS | 5% sobre a base após dedução de XAF 150.000 | Vigente | Business Consulting Gabon |
| Gabão | Base de IRPP | Bruto − CNSS − CNAMGS − TCS, abatimento de 20% com teto de XAF 10 m/ano | Vigente | PwC WWTS (06-08-2026) |
| Gabão | CFP (training levy) | 0,50% do bruto até XAF 1.500.000 (máx. XAF 7.500/mês); ônus do empregador | A partir de 01-01-2017 | Loi n°026/2016 (LF 2017) arts. 5–12 |
| Gabão | FNH | 2% ER (pré-LFR); LFR 2026: 3% sobre a remuneração CNSS até o teto, split e início dependem de texto regulamentar | LFR 2026: julho 2026 | Loi n°002/2026; CGI arts. 401–404 |
| Côte d'Ivoire | Regime simplificado de prestadores de serviços petrolíferos | Forfait sobre o faturamento (6% exploração / 2,17%), cobre impostos sobre salários: **sem ITS na folha**; CNPS e CMU continuam devidos | Desde LF 2019; taxas desde LF 2022 | CGI art. 1068 e ss.; Annexe fiscale 2019 art. 26, 2022 art. 9, 2025 art. 14 |
| Côte d'Ivoire | Teto CNPS (PF/AM/AT-MP) | XOF 70.000/mês; pensão com teto de 3.375.000 (45 × SMIG); 75.000 é o SMIG (piso, não teto) | Desde 01-01-2025 | CLEISS CI |
| Côte d'Ivoire | Prime de transport | Abidjan 30.000; Bouaké 24.000; demais 20.000; excluída do CNPS até 1× o valor isento; isenção uma vez por empregado por mês | Desde 2020 | Arrêté n° 2020-012/MEPS/CAB; CPS art. 23; NS n° 054/MFB/DGI-DLCD |
| Colômbia | Taxa máxima ARL Classe IV | 6,060% | Vigente | normograma.mintic.gov.co |
| Bulgária | Taxa fixa do Euro | 1,95583 BGN/EUR | A partir de 01-01-2026 | n/a |
| Bulgária | Parâmetros do orçamento 2026 | Transitórios (2025 convertidos); €2.352 máx. segurável e +2% pensão ainda **pendentes** | Snapshot 08-2026 | n/a |
| Canadá | CPP/EI/imposto federal no payslip | Método lesser-of por período (não máximo anual ÷ 12) | 2026 | n/a |
| Canadá | NR_RECIPIENT_TYPE_CODE | {1,3,4,5} | Vigente | CRA |

---

## 5. Erros e correções

| País | O que estava errado | O correto | Fonte | Onde aconteceu |
|---|---|---|---|---|
| Espanha | 58163 sem pagas extra (lia YTD fixo, não caixa; 64993 vazio em entidades com 64430) e com meses futuros subavaliados por 64440 | Projeção inclui extras uma única vez e o recorrente mensal real | RIRPF 83.2 | Produção HRBLIZZ (Elessent), 09/2026 |
| Espanha | 58118 negativo (reembolso de IRPF) | Piso zero, sem devolução pelo pagador | RIRPF 87.3.c | Produção HRBLIZZ, 09/2026 |
| Espanha | Leitura literal da 83.3.e (€600 único para pensionista com mais de 2 filhos) | €1.200, conforme o algoritmo AEAT | Algoritmo AEAT 2026 | Draft da CCG v1.6, corrigido em 17-09 |
| Espanha | CCG v1.5 dizia "never generate an ingreso a cuenta" sem qualificação | Ingreso a cuenta incide sobre o excedente ao limite art. 52 | RIRPF 102.2 | CCG 5.3.1, 7.3.2, corrigido em 18-09 |
| Espanha | Excel converteu ranges de posição em datas (58 células col H; 15 valores T-2) | Posições reconstruídas pelos comprimentos cumulativos | Layout AFI | ES-AFI-OUT-001, corrigido em 21-09 |
| Espanha | Coluna M dizia DDMMYYYY (27 linhas) | AAAAMMDD | Tablas y formatos comunes 06/2016 | ES-AFI-OUT-001, 29-09 |
| Espanha | W18/W285 "N" para ETI.160; W19–23 "leave blank" | ETI.160 vazio em produção (P teste, N só liquidações); ETI.180–220 preenchidos | Evidência A3 (A26S0003) | ES-AFI-OUT-001, 29-09 |
| Espanha | Population Rules linha 8 com ASA | MB | Evidência A3 | ES-AFI-OUT-001, 29-09 |
| Espanha | Prazo de baja 3 dias | 6 dias corridos | RD 643/2026 | Report Matrix / Population Rules, 29-09 |
| Espanha | Citação "Art. 23.1.b/c" | Art. 16.2.b/c RD 2064/1995 | RD 2064/1995 | Draft de ticket (L03) |
| Espanha | Rótulo "(peculiaridad 35)" afirmado sem fonte única | Não afirmar enquanto não for lido diretamente | n/a | Draft de ticket (PEC 35 / código 509) |
| Espanha | Taxa MEI 2026 errada | 0,90% | Orden PJC/297/2026 | WTC/CCG |
| Espanha | IRPF com dupla contagem de renda variável | Corrigido | RIRPF 82/87 + Ley 35/2006 art. 101 | CCG v1.1 (HRBS-10121) |
| Espanha | Pré-produção `prewww10` | `prewww1` | Docs AEAT | Runbooks AEAT |
| Ucrânia | Sample D6 validado contra J0510610 (v10) já superado | J0510611 (v11), em vigor desde 17-07-2026 | DPS | SR-163 |
| Ucrânia | Blogs concordavam numa resposta USC/ЄСВ errada | A lei primária revertia | Lei primária | Incidente USC (exemplo permanente) |
| Ucrânia | Stock options 4DF 101 + ESV=No | Inválido em qualquer cenário; tratamento depende do recharge | ПКУ / Lei 2464 | WTC Ucrânia |
| Ucrânia | Per diem com PIT/ML "Yes" fixo | Teto não aplicado; a correção é na coluna Formula (Desenvolvimento) | пп.170.9.1 ПКУ | WTC Ucrânia |
| Holanda | Resposta do 30% ruling com lente de consultoria fiscal | Lente de provedor de software de folha | n/a | HRBS-10545 |
| Holanda | Modelo BCCC/BCCP do próprio Team Lead | Corrigido por verificação independente | n/a | HRBS-10563 |
| Gabão | v3.0 sem o bloco de deduções Global 21100–21900 e de ER 23640–23673 (59 códigos) | Adicionados na v3.1 | Global WTC v1.0 | GA-WTC-001 |
| Gabão | Filtro salvo na coluna A mostrando só 8 códigos | Limpo | n/a | GA-WTC-001 v3.1 |
| Gabão | VC sem linhas 2.0/3.0 | Linha 3.1 adicionada | n/a | GA-WTC-001 v3.1 |
| Gabão | Cliente: "OPRAG/FNE Training Levy 1%" | Não existe no Gabão; a linha é o CFP 0,5% (OPRAG = autoridade portuária; FNE 1% é de Camarões) | Loi 026/2016; Loi 90/050 (CM) | HRBS-14943 |
| Côte d'Ivoire | Parecer de 22-09: "ITS é devido" (regime microentreprises) | Regime de prestadores petrolíferos: sem ITS na folha | CGI art. 1068 e ss. | HRBS-14996, corrigido em 23-09 |
| Côte d'Ivoire | Cliente usava 75.000 como teto CNPS | 70.000 (75.000 é o SMIG) | CLEISS CI | Arquivo do cliente |
| Côte d'Ivoire | Colunas "CNAMGS" e "FNH" no template do cliente | São órgãos do Gabão; equivalem a AT/MP 3% e PF+AM 5,75% | n/a | Arquivo do cliente |
| Côte d'Ivoire | GTN: pensão CNPS lançada e estornada (2517/2556; 2537/2566), cálculo errado acima do teto, wage types com rótulo errado (2531, 2538, 2560, 2569 "EIS") | Registrado como achado; não pedido pelo ticket | CLEISS; CGI | GTN REF-P201-861 |
| Bélgica | CCG Módulo 9 Step 7: 697,61 | 697,42 | n/a | CCG Bélgica (pendente) |
| Bélgica | WTC sem tax code box 360 no fiscal work bonus; bloco DmfA-Modification 90169 rotulado ORIGINAL | A corrigir | n/a | WTC / Report Specs Bélgica (pendente) |
| Colômbia | Taxa máxima ARL Classe IV errada | 6,060% | normograma.mintic.gov.co | Batch anterior |
| Canadá | Payslip com máximo anual ÷ 12; nome legal/endereço ausentes do DD | Lesser-of por período; campos adicionados | CRA | Pipeline Canadá |
| Global | C8 do audit acusava "todo" em espanhol/português | Regex `\bTODO\b` | n/a | Pipeline v2.4 |
| Global | C20 do audit dá FAIL | Falso positivo confirmado em todos os países | n/a | Pipeline |

---

## 6. Padrões e método

**Nomenclatura e versionamento**
- Formato: `{CC}-{TYPE}-{SEQ}-v{MAJOR}.{MINOR}[-DRAFT-{TICKET}-{YYYY-MM-DD}].ext`. A versão fica no nome do arquivo, não no timestamp do Drive.
- Na aprovação: remover o bloco DRAFT e arquivar a final anterior em `Archived/`. Deve existir exatamente uma final vigente por artefato.
- Toda edição atualiza o Version Control, com uma frase curta por edição. Nas specs AFI da Espanha o nome do arquivo ficou v1.0/V4.0 e a versão evolui só no VC.
- Drive "Compliance Team": pastas por país com subpastas 01–16. CCG em `05 - Payroll Regulation Guide`, WTC em `03 - WTC`, DD em `02 - DD`, Report Specs em `12 - Country Report Codes`.

**Modelos**
- CCG: 13 módulos fixos, perguntas do template viram H3 (cobertura ≥95%, check C11). Padrão-ouro: CCG Bulgária.
- Report Specs: padrão Espanha de 9 abas (modelo ES-M296-001), Sheet 4 com 21 colunas A–U, header azul FF4472C4 e cores de linha amber/blue/green/red/grey. O Primer cita "10 abas / 22 colunas" [INCERTO, divergência entre o Primer e o script v2.4].
- DD: formato CZ V2.0 com 8 abas. Só colunas azuis; as laranjas são do Dev. Só master data de input do usuário, só setor privado.
- WTC: CZ V2.0 + Global WTC baseline (~300 códigos obrigatórios) + abas Global WTC Coverage e Form Reference Guide.
- Payslip Generator: 5 abas (EN / local / Payslip Spec / Unit Rate Details / Population Range), base Moçambique, logo Mercans, paleta navy/cinza. "Mesmo modelo da Espanha" vale para o Payslip Spec 1.
- Skill files: `SKILL.md` fino como roteador + `references/` com um `.md` por artefato (padrão Chile/Canadá). Nome `payroll-compliance-{país}`, description de até 1.024 caracteres, validação por `package_skill.py`.

**Edição de arquivos**
- Arquivos .xlsx com desenhos embutidos: patch cirúrgico no XML, nunca round-trip completo pelo openpyxl. Validar byte-identidade das partes não tocadas.
- `delete_rows` corrompe esses arquivos; usar o esvaziamento de linha via XML.
- Índices de coluna sempre conferidos pelo header real.
- Depois de editar: checar well-formedness, desenhos byte-idênticos e diff célula a célula. Destaque de mudanças em azul-claro FFDDEBF7 (specs AFI).
- Verificação visual: soffice → pdf → pdftoppm. Antes de entregar, rodar `extract-text` no arquivo final.

**Pesquisa e confiança**
- Piso de 95% de precisão. Fonte primária alcançada diretamente; secundárias concordando entre si não bastam.
- Esquema, taxa ou template vindo de outro artefato não conta como fonte primária. Confirmar a versão em vigor.
- Só arquivos oficiais. Se for usada cópia de terceiros, dizer isso explicitamente.
- Declarar confiança e ressalvas antes do envio. "100%?" significa re-verificar do zero.
- Distinguir estruturas aditivas de subconjuntos antes de montar cross-checks (Свод da Ucrânia: Seção 2 é aditiva).
- Pesquisa no idioma local com termos técnicos rende mais (espanhol para AEAT, cirílico para Bulgária).

**Escopo e comunicação**
- Resolver só o que foi pedido. "Verificar" não é "corrigir". Achados próprios só são sinalizados se forem críticos de compliance, e fora do texto do ticket.
- Lente de provedor de software de folha, não de consultoria fiscal. Filtrar pedidos de escopo HR × Payroll.
- Respostas de ticket diretas e humanas, sem estrutura robótica, com corte de tamanho em todo draft.
- Se faltar um arquivo nomeado para fechar o ticket, pedi-lo explicitamente.
- Idioma: PT-BR com o Claude, inglês em todo entregável.

**Pipeline**
- Ambientes: Mac (zsh, Python 3.9, `--user`) e Windows Git Bash.
- Armadilhas conhecidas: `${CODE,,}` no bash 3.2; `tail -1` no Windows; path-mangling no `python3 -c` (gravar o script em arquivo).
- Agentes rodam com `claude -p --max-turns N --dangerously-skip-permissions`. O Stage 2 (scope lock-in) é bloqueante. O Stage 9 roda audit mecânico C1–C22 mais fixer com override justificado de falso positivo.

**Rastreio**
- YouTrack: CT- usa o campo Status (bundle 86-14). HRBS- usa State (86-28) com gate Support Group = "Compliance Support".
- Trello: lista MERCANS. Espanha = Prioridade ALTÍSSIMA, Ucrânia = Alta, demais países = Média.

---

## 7. Tickets e dúvidas de suporte

| Ticket | País | Pergunta | Resposta dada | Fonte | Mudou artefato? |
|---|---|---|---|---|---|
| CT-A-485 (thread Spain Migration) | Espanha | IRPF negativo / divergente do A3 em produção | Defeitos em 58163 (extras ausentes, meses futuros subavaliados) e 58118 sem piso zero; a divergência art. 86 × 87 é esperada | RIRPF 83.2, 87.3.c; LGSS 147.1 | Não; achado de fórmula para o Dev |
| (CCG v1.6, Lily) | Espanha | Lógica de retenção confirmada | Regras art. 83–87, previdência, paga extra | RD 439/2007; Ley 35/2006 | Sim: CCG v1.6 |
| (SITUPER) | Espanha | Input do algoritmo sem campo no DD | Campo novo `$hr.perceptor_situation` + mapper | Algoritmo AEAT 2026 | Sim: DD V4.1 |
| SR-432 | Espanha | Coluna A e Field Explanation em inglês | Passe completo de idioma + correção de datas corrompidas | Mensaje AFI (TGSS) | Sim: ES-AFI-OUT-001 v1.1 |
| SR-432 | Espanha | 78 queries da coluna V | Respondidas; DD com 59+2 campos | TGSS | Sim: VC 1.2 / DD 4.6 |
| SR-432 | Espanha | Coluna U verde-escura; campos e mappers deletados; zeros × vazio | 76 respostas; 26 mappers órfãos removidos; Collective Agreement Code restaurado | Conceptos Comunes 12/2004; RED 5/2018; RD 643/2026 | Sim: VC 1.4 / DD V4.0 |
| SR-83 | Espanha | Modelo 190 | [INCERTO, conteúdo não registrado] | n/a | n/a |
| HRBS-10121 | Espanha | Dupla contagem de variável no IRPF | Corrigido | RIRPF 82/87; Ley 35/2006 art. 101 | Sim: CCG v1.1 |
| HRBS-14978 | Gabão | Faltam códigos de dedução (normal/BIK), ajuste e "SS Company part 3" | Parts 1/2/3 = três ramos CNSS ER; deduções Global obrigatórias; BIK precisa de dedução não-caixa; ajustes são operacionais | Décret 0487/2025; CLEISS; PwC | Sim: WTC v3.1 DRAFT |
| HRBS-14943 | Gabão | "OPRAG/FNE Training Levy 1%" (blocker) | Não existe; a linha é o CFP 0,5% | Loi 026/2016; Loi 90/050 (CM) | Não |
| HRBS-14996 | Côte d'Ivoire | Regime único: sem ITS? | Corrigido em 23-09: regime petrolífero, sem ITS na folha se a entidade estiver inscrita; CNPS/CMU devidos | CGI 1068 e ss.; Annexes fiscales 2019/2022/2025 | Não |
| HRBS-14996 (22-09) | Côte d'Ivoire | Transporte 30.000 XOF | Valor estatutário de Abidjan; excluído do CNPS uma vez por mês; base CNPS do cliente correta | Arrêté 2020-012; CPS art. 23; NS 054 | Não |
| HRBS-14331 | Ucrânia | Maternidade, stock options, per diem (Altium) | Posição estatutária fechada; aplicação depende de input do cliente | Lei 2464; ПКУ | Parcial: WTC V4.1 |
| HRBS-12548 | Ucrânia | 1-ПВ, Свод, licença médica ПФУ, salário médio | 1-ПВ separado; Seção 2 aditiva; itens 3–4 bloqueados | Держстат; Постанова ПФУ №28-1 | Sim: specs UA-1PV / UA-INTREP |
| SR-163 | Ucrânia | Validação do sample D6 | Estava contra o formulário superado v10; correto é v11 | DPS | n/a |
| HRBS-10545 / HRBS-1534 | Holanda | 30% ruling (Omnicom / Excerpta Medica) | Teste anual de €48.013; leave-relief manual | Belastingdienst | Sim: NL-CCG reconstruída |
| HRBS-9646 | Holanda | Betalingskenmerk | Módulo 11 de 16 dígitos ainda obrigatório; não usar clieop03 | Belastingdienst | n/a |
| HRBS-10563 | Holanda | Modelo BCCC/BCCP | Corrigido por verificação independente | n/a | [INCERTO] |
| HRBS-8606 | Kuwait | PIFSS | [INCERTO, conteúdo não registrado] | n/a | n/a |
| HRBS-11078 | n/a | Exemplo real de HRBS que editou artefato sem virar CT- | Base do OD-13 | n/a | Sim |

---

## 8. Pendências em aberto

**Espanha**
- Defeito ODL: ref. 2420 tem length 4 × an6, e o deslocamento de 2 caracteres não fecha com o arquivo A3. Precisa reler a tabela ODL do manual TGSS antes do Dev (Regulatory Affairs).
- Tabelas T-79 e T-103 não estão fontadas. Textos das colunas G/M danificados pela extração do PDF.
- U13/U280 ainda dizem DDMMYYYY (respondido na coluna W).
- 58292 Tax Year End Date veio 20260930: verificar se é do relatório ou parâmetro real.
- Segundo modo de falha: 58117 negativo leva a 58118 ≈ 54,5%.
- Lacunas de input do algoritmo no DD: RESICEME/RENCEME (urgente, inclui La Palma), PRESVIV, CONYUGE, ANUALIDADES, AÑOADOP, CONVIVENCIA. Definir o que alimenta NUMDES com 5+ filhos. Descrição de `related_person_nif` está vaga.
- Itens pré-existentes na CCG: nome de cliente (7.3.2), referências HRBS e destaques amarelo/ciano. Decisão separada.
- Fora da CCG, ficam com outros times: ticket 13757, VUSA 1299 duplicados 58176/552, mapeamento 23640→64559, SOP de submissão, retro por período.
- AEAT: diseño de registro do 296; não há web service de verificação de NIF (limitação aceita).

**Ucrânia (aguardando contato do cliente / Altium)**
- Classificação dos códigos de maternidade.
- Recharge das stock options.
- 65805/65809 em 4DF 126 → 125 (levantado, não alterado).
- HRBS-12548 itens 3–4: certificado em papel × eletrônico; template de salário médio.

**Côte d'Ivoire**
- Confirmar se o forfait petrolífero cobre também os impostos do empregador (CN 1,2%, TA 0,4%, TFPC 1,2%, CE); o corpo do art. 1068 bis não estava legível.
- Confirmar a inscrição da entidade no regime.
- Baixar o Formulaire Unique da DGI.
- Refatorar o skill para thin-router.

**Gabão**
- Taxa e split do FNH quando sair o texto regulamentar da LFR 2026.
- 62890 Stock options com No/No/No (PwC trata como tributável).
- Confirmar na plataforma os números de código novos.
- Confirmar o tratamento pós-imposto de 21640–21645.
- O WTC do cliente (Google Sheet) não estava legível; Drive precisa de re-auth.

**Holanda**
- Sign-offs do cliente (Mammoet): decisão 2559, recuperação de €17,48, memo de systematiek.
- Reconciliação P09/P10.
- Tickets do Statutory Alert 2027 prontos para colar.

**Bélgica (ao fechar todos os estágios do pipeline)**
- Emitir alerta exaustivo de pendências.
- Corrigir: box 360 no WTC, 697,61 → 697,42 na CCG, 90169 rotulado ORIGINAL.
- Investigar: tabelas nr.53/58; check digit do número RSZ.
- Atualizar citações para incluir os decretos e a lei de julho de 2026.
- Cruzar a Form Reference Guide do WTC e o SIR com as 9 specs.

**Demais países**
- França: prioridade nº 1 (entrega em setembro, go-live em fevereiro).
- Colômbia: na fila depois da Bélgica.
- Chile: 7 discrepâncias de taxa (AFP Uno, Honorarios PPM, Ley 21.735).
- Chade: arquivos OLE2 criptografados da Baker Hughes; aguardando senha com Govind Thakur.
- Congo: roteamento do solidarity para a DGID × Décret 2024-131.
- Bulgária: orçamento 2026.

**Automação**
- OD-13 em aberto.
- Teste de write-back no YouTrack (bloqueia S21/S23).
- Setup do Hermes parado no `DESKTOP-TKRQLF7`, aguardando 3 arquivos de referência.
- Status das 30 skills atribuídas a Manju/Enaakshi.

---

## 9. Fronteiras

- **Desenvolvimento:** coluna Formula do WTC (ex.: teto de per diem na Ucrânia); defeitos de fórmula do engine (58163/58118 na Espanha); colunas laranjas do DD e do WTC.
- **Config/Product:** status de configuração S/C/M/N. Compliance só confirma a posição estatutária, não prescreve configuração.
- **BA (Lily Li):** planilhas Income Nature/Income Key e colunas de BA Mapping. Não editar sem aprovação explícita dela.
- **Cliente / empregador:** submissão em portal (AEAT, e-impots, e-CNPS); split tributável/não tributável de previdência (input do cliente); configuração do leave-relief no 30% ruling (NL); responsabilidade estatutária do empregador versus o que o engine calcula.
- **Infra/IT:** service account com acesso ao Shared Drive (Andre Voolaid aprova); chave da API Anthropic no Passbolt (Jasper Guevarra).
- **Implementação/Operações:** arquivos criptografados do cliente (Govind Thakur); itens de sistema, dados e SOP fora da CCG.
- **Fora do escopo de payroll (HR):** gestão de workforce, recrutamento, performance. Na Bulgária, е-болнични e УП-2.
- **Setor público:** o DD exclui servidores, militares, autônomos e cooperados sem contrato. A Mercans atende só o setor privado.
