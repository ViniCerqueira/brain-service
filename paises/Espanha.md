# Espanha

> Hub do país. Índice: [[00-INDEX]] · Skill: `payroll-compliance-spain`

Espanha é o país mais ativo do serviço (chat: mercans-compliance). Contexto: Research (CCG/WTC/DD) entregue em 2026; o grosso do trabalho atual é Design/Report Specs (SR-xx, com Lily Li como BA e Drew/Brenet como Dev) e Suporte. Datas de tickets são aproximadas (±1 dia). Detalhe estatutário geral: ver a skill, não copiado aqui. Serviços: [[research-pipeline]] · [[design]] · [[suporte]] · [[fronteiras]].

## Situação
| Etapa | Status | Data | Observação |
|---|---|---|---|
| [[research-pipeline]] | ✅ | CCG v1.6 em 2026-09-17 | CCG v1.0 (jan/2026) → v1.1 (HRBS-10121) → v1.2 (HRBS-10272) → v1.3 → v1.6 (17/09, tracked insertions). WTC e DD em evolução contínua por tickets (ver Artefatos). Pesquisa ainda pedida em tickets (HRBS-14528 SILTRA, HRBS-13757 payslip). |
| [[design]] | 🔄 | atualizado 2026-09-29 | Regulation Design v2 (CT-A-507) em produção desde jun/2026 com redesign de ~40% (reteste pendente). Specs: SR-79 em produção (~17/09); SR-144 em produção (~08/09); SR-83 deploy ~15/09 (portal ainda com erro); SR-81/82/85/342/365 em Final Review; SR-80 Open (Dev); SR-432 em Product Mapping (BA). |
| Produção (outro time) | — | | Dev/deploy = Drew/Brenet; ver [[fronteiras]]. |
| [[suporte]] | 🔄 | 2026-09-28 | HRBS-10563, HRBS-12839, HRBS-13757, HRBS-14528 abertos. SLA de HRBS-10563 estourado, de HRBS-12839 em violação. |

## Ficha do país (da skill)
> Resumo do que mais importa para o serviço. Fonte: skill `payroll-compliance-spain`, lida em 2026-10-02. Valores exatos e tabelas: ler a skill. Se divergir, vale a skill.

- **Escopo:** ano fiscal 2026, setor privado, Régimen General da Seguridad Social, EUR. Fora: territórios forais (tributação), RETA/autónomos, regimes especiais, funcionários públicos, IRNR e art. 93 LIRPF (Beckham), bonificaciones/reducciones (só tarifas cheias).
- **Órgãos:** TGSS, AEAT, SEPE, Ministerio de Trabajo y Economía Social.
- **Relatórios principais:** RNT/RLC (mensal), Modelo 111 (mensal/trimestral), Modelo 190 (anual), CRA, Contrat@, Certific@2, Delt@, eventos de afiliação (altas/bajas), Modelos 216/296, recibo individual de salarios.
- **Confiança da skill:** build do zero; veredito PASS WITH NOTES, 0 defeitos críticos, 8 itens abertos (Q1–Q8), 4 abaixo de 95%. Abaixo do piso: RNT/RLC e CRA layouts (~55–60%), Modelo 190 layout/subclaves (~65%), prazo do certificado de empresa (~70%), Modelos 216/296 (~50%). Seções estatutárias do CCG em 93–98%.

**Armadilhas confirmadas** (SKILL.md "Design clarifications" e `07-qa-report.md` §4)
1. Dois motores sobre o mesmo bruto (SS mensal com teto e prorrata das pagas; IRPF projeção anual com tipo único); base IRPF reduz SS, base SS nunca reduz IRPF (engine) → `01-ccg.md`
2. Pagas extraordinárias: prorrata na base de cotização, tributadas no pagamento (engine) → `01-ccg.md`
3. Horas extras fora da base de contingencias comunes, dentro da base AT/EP (que também serve a desempleo/FOGASA/FP); um único campo "base SS" não representa a Espanha (engine) → `01-ccg.md`
4. MEI incide sobre a base CC, não AT/EP (engine) → `01-ccg.md`
5. Quota de solidariedade: art. 19 bis imprime as taxas de 2045 (5,5/6/7%); 2026 = 1,15/1,25/1,46% (DT 42.ª); base é a remuneração sem teto (engine) → `01-ccg.md` §2.3
6. Base mínima = 1.424,40 (diário arredondado 47,48 × 30), não 1.424,50 (engine) → `01-ccg.md`
7. Km: 0,26 (Orden HFP/792/2023); o texto do RIRPF art. 9.A.2.b) ainda diz 0,19 (engine) → `01-ccg.md` §8
8. SMI integral está sujeito a retenção de IRPF em 2026 (piso do art. 81 ainda 15.876) (engine) → `01-ccg.md`
9. Retenção IRPF usa escala nacional única, sem variação por comunidade; forais fora; Ceuta/Melilla com redução de 60% (engine) → `01-ccg.md`
10. Tarifa AT/EP atribuída pela TGSS por CNAE-2025 (LGSS DA 61.ª); ocupação pode sobrepor; empregador não escolhe (engine) → `01-ccg.md` §2.4
11. Prazo de baja passou de 3 para 6 dias corridos em 2026-08-01 (RD 643/2026); reporte do CNO de toda a força de trabalho até 2027-02-01 → `04-reports-spec.md`
12. Modelo 111 de julho (grandes empresas): agosto inteiro + 20 dias de setembro → `04-reports-spec.md` ES-RPT-002
13. Todos os valores de 2026 repousam em prorrogação orçamentária; RDL 16/2025 e RDL 2/2026 foram revogados, nunca citar como vigentes (cadeia: RDL 3/2026 → Orden PJC/297/2026) → `07-qa-report.md` U1
14. Anexo do recibo: "II. DEDUCCIONES" (corrección de errores BOE-A-2014-11988); templates antigos trazem "I." → `06-payslip.md`

**O que mais dá errado** (do QA)
- Tarifa AT/EP: reverificar as taxas por CNAE contra BOE antes de calcular prêmio real (Q1, 93%).
- Percentuais de IT 60% (dias 4–20)/75%: cadeia de citação, RD 53/1980 não lido (Q2, 88%).
- Incerteza jurídica viva: sem Ley de Presupuestos 2026 (U1); SMI × retenção (U2); Directiva de transparência salarial 2023/970 não transposta (U3); semana de 37,5h rejeitada, ET art. 34.1 segue 40h (U4); formato do reporte CNO da RD 643/2026 não especificado (U5).
- Sempre pedir o convenio colectivo para estrutura salarial, antiguidade, pagas, horas extras, jornada < 40h, complemento de IT.

**Lacunas abertas / não confirmado** (candidatos a ticket ou nova pesquisa)
- Layouts de campo RNT/RLC e CRA (Q3, maior lacuna do pack); Modelo 190 registro/subclaves (Q4); prazo do certificado de empresa (Q7); Modelos 216/296 e Beckham não pesquisados (Q8).
- Limite de elegibilidade RED Directo (<25 vs 15 trabalhadores) (Q5); Contrat@ em lote (Q1/Q6, 60%); Modelo 111 caixas 13–27 derivadas (~70%).
- Algoritmos de validação de NIF/NIE/NAF/CCC/IBAN tratados como conhecimento comum, não lei citada.

**Valores-âncora**
| Item | Valor | A partir de | Fonte |
|---|---|---|---|
| Tope máximo de cotização | 5.101,20 €/mês | 2026 | Orden PJC/297/2026 |
| Contingencias comunes | 28,30 % | 2026 | Orden PJC/297/2026 |
| MEI | 0,90 % (0,75 ER / 0,15 EE) | 2026 | Orden PJC/297/2026 art. 16 |
| Solidariedade | 1,15 / 1,25 / 1,46 % (acima de 5.101,20 / 5.611,32 / 7.651,80) | 2026 | LGSS DT 42.ª; Orden art. 17 |
| SMI | 1.221,00 €/mês (17.094/ano) | 2026 | RD 126/2026 |
| Base mínima | 1.424,40 €/mês | 2026 | Orden PJC/297/2026 |

## Artefatos entregues
| Artefato | Versão | Data | Arquivo/local | Observação |
|---|---|---|---|---|
| CCG (Spain Payroll Configuration Guide 2026) | v1.6 (vigente: maior versão) | 2026-09-17 | `Spain_Payroll_Configuration_Guide_2026_v1_6.docx` | Tracked insertions (autor "Claude"). Observação: tickets citam só "2026" (CT-4321) e chat de 12/08 citava V1.3; prevaleceu o chat mais recente. Versões anteriores: v1.1 (HRBS-10121), v1.2 (HRBS-10272), v1.3 (queries da Lily). (chat: mercans-compliance, chat: design-dev-kb) |
| WTC (Spain Wage Type Catalogue) | V4.4 (vigente: maior versão, regra de 2026-10-05) | ~2026-08-13 | Drive (arquivo da Lily) | V4.4 (SR-83, 79429/79430→B.03; 79432→L.27). Observação: chat de 12/08 cita WTC V3.10 como vigente e design-dev-kb cita V3.9 final; HRBS-10563 editou V3.9 In Progress. Os tickets SR-83/SR-342 já falam V4.2 (~23/07) e V4.4, o que conflita com V3.10 em 12/08. Resolvido em 2026-10-05: vale a maior versão (V4.4). Marco: V3.4 (07/05) / V3.5 tirou 65815 do 296 (SR-85). |
| DD (Spain Data Dictionary) | VC 4.6 (vigente: maior versão, regra de 2026-10-05) | 2026-09-29 | Drive | Observação: VC 4.6 em 2026-09-23, com remoção de 58 campos AFI em 2026-09-28 e arquivo V4.0 Draft em 2026-09-29 (histórico); renumeração do VC se perdeu no export; todas as linhas B24–B31 leem 4.0. V4.1 (SITUPER, 18/09, Approved) e V4.5 (data não registrada) também citados. Tickets antigos: v3.9 (SR-80/SR-365), v3.12 (SR-79, ~10/09). Anteriores: v3.7 (design v2). |
| ES-BASES-001 Fichero de Bases Spec (SR-79) | v2.5 (vigente: maior versão; arquivo único consolidado em produção ~2026-09-17) | 2026-09-17 | arquivo linkado na descrição do SR-79 | Observação: histórico: SR-79 cita v2.1 → v2.3 → v2.4 → consolidado (08/09); HRBS-13757 cita v2.5 (~01/09). |
| ES-AFI-001 TrabajadoresTramos Spec (SR-80, inbound) | v2.0 (Audit Closure Memo) | ~2026-07 | Drive | Observação: DD v3.9 alinhado. Ticket Open com Lily (14/09). |
| ES-AFI-OUT-001 AFI Outbound (SR-432) | VC 1.4 (vigente: maior versão; arquivo `ES_AFI_OUT_001_v1.0.xlsx`) | 2026-09-29 | Drive | Observação: ticket SR-432 (28/09) cita VC 1.2; chat registra 1.1 (21/09), 1.2 (23/09), 1.3 (25/09, validação A3, escopo 12/7/58), 1.4 (29/09). |
| ES-CRA-001 CRA Spec (SR-81) | V2.3 (vigente: maior versão) | ~2026-08 | Drive | Observação: v2.2 em jun/2026 (Dev, 548 WTs). |
| SEPE LLAMAMIENTO Spec (SR-144) | sem versão | produção ~2026-09-08 | Drive | Orientado a evento (só gera com `sepe_callback_start_date`). |
| SEPE CERTIFICA Spec (SR-145) | v1.1 | ~2026-09-01 | Drive | CodProfesion com padding a 7 dígitos (HRBS-13757). |
| M111 Spec (SR-82) | v4 | 2026-09-02 | Drive | Tabela de campos reconstruída contra dr111e16v18.xls. |
| ES-M190-001 Modelo 190 Spec (SR-83) | v3.3 (vigente: maior versão; "cópia do Compliance", citada em 10/09) | 2026-09-16 | Drive | Histórico: v2.7 (21/07); edições posteriores sem número até 15/09. Deploy ~15/09. |
| M296 Spec (SR-85) | V2.3 (vigente: maior versão; Dev ~ago) | 2026-09-04 | Drive | Histórico: v2.1 em ~mai. |
| ES-CERT-001 Certificado de Retenciones (SR-342) | sem versão | aceite ~2026-09-10 | Drive | Formato verificado contra 5 certificados reais da AEAT (HRBS-13757). |
| ES-FINIQ-001 Finiquito Spec (SR-365) | sem versão | ~2026-08-07 | Drive | Aceite do Dev ~06/08; validação de Gulnaaz pendente. |
| Runbooks AEAT ES-AEAT-INT-OUT-001 / IN-001 | v1.3 | até 2026-07-31 | Drive | Presentación directa por HTTP POST JSON (chat: mercans-compliance). |
| Regulation Design v2 (CT-A-507) | v2 | 2026-06 | Drive/KB | ~90+ passos, ordinais 5–621; substituiu v1 (19 PDFs CT-A-485..505). |
| KB SPAIN - Regulation Specifications (CT-A-485) | atualizada 2026-09-14 | 2026-09-14 | KB Compliance | Espelho de configuração do CCG/WTC (Mohit/Lily). Sub-artigo BCCC Taxability Matrix: 2026-09-07. |

## Valores-chave (com vigência)
Só o que foi decidido/discutido em ticket ou chat. Valores estatutários gerais: skill `payroll-compliance-spain`.

| Item | Valor | A partir de | Até | Fonte |
|---|---|---|---|---|
| Tope máximo de cotização mensal | EUR 5.101,20 (diário 170,04, grupos 8–11) | 2026-01-01 | | Orden PJC/297/2026 (BOE-A-2026-7296) citada em HRBS-10563; confirmado: skill 01-ccg.md §2.2 (arts. 2–3, "from 1 January 2026") |
| Bases mínimas mensais G1 / G2 / G3 / G4-7 | 1.929,00 / 1.599,60 / 1.391,70 / ~1.424,50 (provisório) | 2026 (⚠️ vigência?) | | CT-A-485 (⚠️ sem fonte); chat: design-dev-kb cita CCG. Associação grupo-valor confirmada no PDF de CT-A-485 (leitura pdftotext -layout, 2026-10-05). ATENÇÃO: a skill (01-ccg.md §2.2) traz outros valores: G1 1.989,30 / G2 1.649,70 / G3 1.435,20 / G4-7 1.424,40; ver Pendências |
| Bases mínimas part-time por hora G1 / G2 / G3 / G4-11 | 11,98 / 9,94 / 8,65 / 8,58 | 2026 (CCG v1.3) | 11,62 / 9,64 / 8,38 / 8,32 (CCG v1.0) | Orden PJC/297/2026 (chat: design-dev-kb) |
| MEI 2026 | 0,90% (ER 0,75% + EE 0,15%) | 2026 | | Orden PJC/297/2026 (chat: mercans-compliance) |
| Contingências comuns EE / ER | 4,7% / 23,6% | 2026-01-01 | | CT-A-485; CCG; confirmado: Orden PJC/297/2026 art. 4.a) (skill 01-ccg.md §2.3) |
| Desemprego indefinido / temporário (EE/ER) | 1,55/5,5 e 1,6/6,7 | 2026-01-01 | | CT-A-485; CCG; confirmado: Orden art. 33.2.a).1.º e 2.º (skill 01-ccg.md §2.3) |
| FOGASA ER / Formação profissional EE/ER | 0,2% / 0,1% e 0,6% | 2026-01-01 | | CT-A-485; confirmado: Orden art. 33.2.b) e c) (skill 01-ccg.md §2.3) |
| Quota de solidariedade | 0,19/0,96; 0,21/1,04; 0,24/1,22 (excesso 0–10%, 10–50%, >50%); base codes 497/498/499 só no 1º tramo do Bases | 2026-01-01 | | CT-A-492 / CCG; SR-79; taxas confirmadas: Orden art. 17 / LGSS DT 42.ª (skill 01-ccg.md §2.3) |
| Base de cotização em nascimento/cuidado | BCCC do M-2 | 2026 | | Orden PJC/297/2026 (HRBS-10563) |
| Base diária durante IT/risco/nascimento | base do mês anterior ÷ 30 (grupo mensal); ÷ dias reais do mês anterior (grupo diário) | 2026 | | Orden PJC/297/2026 (HRBS-10563) |
| Tempo parcial, base reguladora | soma dos últimos 3 meses ÷ dias do período | ⚠️ vigência? | | RDL 11/2024 (HRBS-10563) |
| BCCC e BCCP durante licença | continuam as duas (nunca zero com trabalhador de alta); worked-days entram nas duas; piso/teto sobre a base mensal | 2026 | | Orden PJC/297/2026 Art. 6.1, 6.3, 6.5 (HRBS-10563) |
| Novas IT (aborto, menstruação incapacitante, interrupção da gravidez) | 60% BR dias 1–20; 75% do dia 21 | ⚠️ vigência? | | LO 1/2023; arts. 169.1.a e 173 LGSS (HRBS-10563) |
| Acidente de trabalho | dia 1 = 100% salário pelo empregador; dia 2+ = 75% da BR (BCCP mês anterior ÷ 30) | 2026 | | Art. 173.1 LGSS (HRBS-10563); confirmado: skill 01-ccg.md (tabela de IT, art. 173.1) |
| Risco na gravidez/lactação | 100% BR, INSS/mútua desde o dia 1 | ⚠️ vigência? | | Arts. 186–187 LGSS (HRBS-10563) |
| Licença parental | 2 de 8 semanas pagas a 100% pela SS | nascimentos a partir de 2024-08-02 | | RDL 9/2025 (HRBS-10563) |
| Prazo de baja AFI | 6 dias corridos | 2026-08-01 | 3 dias | RD 643/2026 (chat: mercans-compliance) |
| Settlement types do Bases em escopo | L00, L02 (corrente); L03, L13, L90–L93, V03, V90 (retro); C02/C03/C90/C91 fora | ⚠️ vigência? | | Manual TGSS SLD Especificaciones Técnicas (ago/2025) (SR-79) |
| ReferenciaExterna do Bases | 8 caracteres: últimos 4 do CCC + MMyy | ⚠️ vigência? | `'BAS'+MMyyyy` (9 caracteres, nunca válido) | Bases.xsd v2.0.2 / spec (SR-79) |
| Código de horas no Bases | "01" (minLength 2, maxLength 3) | mar/2024 | | "SLD: Fichero de Bases – Manual de Usuario" v2.0.2 (SR-79) |
| Severance no CRA | 58184/58186/58188, 0054/E; 62983 também 0054/E | ⚠️ vigência? | 58197 0054/I e 58198 0054/E (errado, abr/2026) | ES-CRA-001 Table 84 (SR-81, HRBS-10563) |
| Severance no Bases | 58197 → base code 701 (nunca 500/601), L03 nos 12 meses anteriores; 58198 não reportado | ⚠️ vigência? | | spec ES-BASES-001 (SR-79); acúmulo L03: RD 2064/1995 Art. 16.2.b/c |
| M190, riscos gravidez/lactação (79429/79430) | Clave B / subclave B.03 | Ejercicio 2025 | B.01 | AEAT Diseños Lógicos 190 / FAQ AEAT (SR-83) |
| M190, licença parental paga (79432) | Clave L / L.27 (isenta) | Ejercicio 2025 | Clave B (21/07) | AEAT Diseños Lógicos 190 (SR-83) |
| M190, subsídios de IT com empregado ativo (79417–79424) | Clave A (pago delegado); B só quando INSS paga direto | ⚠️ vigência? | clave B/pago directo | HRBS-10563 |
| M190, série 6298 (62983 / demais) | Clave L/L05 (despido isento, Art. 7.e LIRPF) / L/L01 | ⚠️ vigência? | clave A subject to withholding | HRBS-10563 |
| M190, Family Situation / Contract Type / Descendants | 3 códigos (claves A, B, C); 1 dígito 1–4, só Clave A, pos. 168; Descendants pos. 223–228 | Ejercicio 2025 | 6 códigos; 2 dígitos 01–05; pos. 266–267 | AEAT Diseños Lógicos 190; Orden HAC/1431/2025 (SR-83) |
| M111, nome da empresa | Denominación (23-82, 60) + Nombre (83-102, 20); complementar pos. 538; justificante anterior 539-551 | desenho vigente | campo único de 40 caracteres | AEAT dr111e16v18.xls (SR-82) |
| M296, retenção não residente com 58205=3 | 19% (saída "1900") | ⚠️ vigência? | 2400 (errado) | spec/BA (⚠️ sem fonte legal) (SR-85) |
| Finiquito / zero floor | regularização por cessação (Art. 87.2.3º RIRPF); base real acumulada; 0% se base − mínimo pessoal ≤ 0 (Art. 86.1/87.3); sem restituição; piso 2% só contratos < 1 ano (Art. 86.2) | ⚠️ vigência? | | RIRPF (SR-365) |
| Projeção anual do IRPF | total esperado no ano civil, pagas extra incluídas uma vez; `MAX(ano anterior; YTD + ainda esperado)` | vigente | | RIRPF art. 83.2 (chat: mercans-compliance); HRBS-10121 usa `MAX(0; var ano anterior − var YTD)` |
| Reduções art. 83.3.e | pensionista 600; NUMDES>2 600; desempregado 1.200; máx. 1.800 | 2026 | pensionista com mais de 2 descendentes = 1.200 só pela leitura literal (descartada) | Algoritmo AEAT 2026 (chat: mercans-compliance) |
| Regra da metade (art. 84) | descendente a 50% salvo direito exclusivo; acumulado 1→1.200 · 2→2.550 · 3→4.550 · 4→6.800 · +2.250 cada | vigente | | RIRPF art. 84 (chat: mercans-compliance) |
| Taxa regularizada | (cuota − retenções feitas) ÷ remuneração restante; piso zero; teto 47% (19% Ceuta/Melilla) | vigente | | RIRPF 87.3/87.5 (chat: mercans-compliance) |
| Regime Ceuta/Melilla estendido a La Palma | redução de 60% da taxa; mínimos 0,8%/6%; teto 19% | 2026-09-10 | | RDL 23/2026 (BOE-A-2026-18828) |
| Algoritmos AEAT 2026 | 1-jan a 9-set: ALGORITMO_2026.pdf / PRET-R200/R260; a partir de 10-set: Algoritmo Retenciones-2026_10sept.pdf / R261 | 2026-09-10 | até 2026-09-09 (versão anterior) | sede.agenciatributaria.gob.es |
| Prorrata de paga extra | entra na base de cotização, não na base de IRPF | vigente | | LGSS art. 147.1; LIRPF 14.1.a; RIRPF 78.1 |
| Limite previdência social | menor entre 30% da renda líquida e 1.500 (+ até 8.500 pela tabela de coeficientes); ingreso a cuenta só sobre o excedente | vigente | | LIRPF art. 52.1; RIRPF 102.1/102.2 |
| Escala IRPF, mínimos, isenções, Beckham, não residente, penhora | ver CCG v1.6 e CT-A-485 (ex.: não residente UE/EEE 19% / resto 24%; Beckham 24% até 600.000 e 47% acima; vale-refeição 11/dia; km 0,26) | 2026 | | CT-A-485 / CCG (⚠️ sem fonte nos tickets; não copiado) |

## Decisões
- ~2026-03: Authorized User ID/`Autorizado` → `$legal_entity_hr.red_authorization_code` (número de autorização RED do operador SILTRA, não é API key) — vale em AFI, CRA e Bases — Wallisson (SR-80)
- ~2026-03/04: 58197 (severance tributável rateado) → base code 701 apenas; 58198 não reportado — Wallisson (SR-79)
- ~2026-04: gerar base code só se valor > 0; sem registros zerados no Fichero de Bases — Wallisson (SR-79)
- ~2026-04: nome do arquivo e `referenciaExterna` únicos entre Legal Entities (rastrear status) — requisito de Illya (Integration), incluído por Lily (SR-79)
- ~2026-04: CRA: "TGSS CRA Action Type" default A; "TGSS CRA Settlement Type" default 00; "blank" não entra no mapper — Wallisson (SR-81)
- ~2026-05: MA/MB/MC/MG (Alta/Baja/Cambio de Contrato/Cambio de Grupo) não são 4 relatórios; são eventos de HR/onboarding fora da SR-80; se em escopo, ticket próprio — Wallisson (SR-80)
- ~2026-05: ES-AFI-001 fica em escopo; spec inbound também precisa de product mapping (HRB lê DatosTramo/DatoSolicitado para saber o que gerar no Bases). Check competitivo (SAP HCM, a3, Sage, etc.). Rebatido parecer do Gemini — Wallisson / Team Lead (SR-80; chat: mercans-compliance)
- ~2026-05: severance no CRA: 58184/58186/58188 (0054/E); 58197/58198 só BASES — Wallisson, após apontamento da BA (SR-81)
- ~2026-06: 65815 sem chave 296 (WTC V3.5) — Wallisson (autocorreção) (SR-85)
- ~2026-06: 62983 → CRA 0054/E + AEAT clave L/L05; 62980–62989 → L/L01 Exempt_InfoOnly — Wallisson (HRBS-10563)
- ~2026-06: 79411 = dia do acidente (empregador); 79412 = 75% BR pago delegado — Wallisson (HRBS-10563)
- 2026-06-18: redesign de ~40% da Regulation Design (`52560` combina IT+IMS por CNAE; floor/ceiling SS anuais) — gaps do implementation expert — Mohit (chat: design-dev-kb)
- ~2026-06/07: não renomear/criar estrutura no WTC da Lily sem aval; parciais de maternidade/paternidade/parental e ERE parcial/total não viram WT (coeficiente/status) — Wallisson (HRBS-10563)
- ~2026-07: as duas bases (BCCC e BCCP) continuam durante qualquer licença (Orden PJC/297/2026 Art. 6) — Wallisson (HRBS-10563, autocorreção)
- ~2026-07: retro (L13, L90–L93, V03, V90) por MesLiquidativo; C02/C03/C90/C91 fora de escopo; Rectification Indicator omitido — Wallisson (SR-79)
- 2026-07-21: Clave B entra no escopo do M190 (pago directo INSS/mútua; 79429/79430 → B.03; 79432 → L.27 após correção de 10/08) — Wallisson (SR-83)
- 2026-07-22: BIK clave G = zero derivado, não fixo — Wallisson (SR-83)
- ~2026-07: M111 clave G (linhas 29–31) acrescentadas — Wallisson (SR-82)
- ~2026-08-04: zero floor no finiquito é comportamento esperado (regularização, Art. 87.2.3º/86.1/87.3 RIRPF), sem correção retroativa, sem piso 2% — Wallisson (SR-365)
- ~2026-08-06: M296 = um registro Type 2 por natureza (D dinheiro, E espécie); Type 1 = soma; contagem de perceptores = nº de Type 2 — Wallisson (SR-85)
- ~2026-08: Bases L03 multi-mês = uma Liquidacion com vários LiquidacionMes (um por mês corrigido) — Wallisson (SR-79)
- ~2026-08: ReferenciaExterna = últimos 4 do CCC + MMyy (versão do Dev) — Wallisson (SR-79)
- ~2026-08-04: SR-80/TrabajadoresTramos = inbound (TGSS→usuário); SR-370/SolicitudTrabajadoresTramos = outbound; responder sempre com nome completo do arquivo — Wallisson/Drew (SR-80)
- Antes de 2026-08: M111 e M190 não são combinados (sem base legal de envio conjunto); integração outbound-dominante (HRBLIZZ gera, cliente submete no portal) — Team Lead (chat: mercans-compliance)
- ~2026-09-01: L00 e L13 coexistem; L03 sempre separado (períodos anteriores); L01 não existe na TGSS; CodProfesion completa até 7 dígitos com zeros à direita — Wallisson (HRBS-13757)
- ~2026-09-08: consolidar a spec do Bases num único arquivo (o linkado no ticket), sem versões paralelas — Wallisson, após reclamação da Lily (SR-79)
- ~2026-09-10/11: settlement type do Bases por gatilho por bloco, não por seleção única de legal entity; `tgss_bases_settlement_type` não é campo de LE — Wallisson (SR-79)
- ~2026-09-11: spec M111/M296 confirmadas; erro persistente de portal vai para o Dev; certificado anual verificado contra 5 certificados da AEAT — Wallisson (HRBS-13757)
- 2026-09-17: art. 83.3.e segue o algoritmo publicado pela AEAT, não a leitura literal do RIRPF — Team Lead / Claude (chat: mercans-compliance)
- 2026-09-18: novo campo `$hr.perceptor_situation` (SITUPER), ACTIVO para toda a população; clave B fora de escopo no CCG e clave C não listada — Team Lead (chat: mercans-compliance)
- 2026-09-23: estilo da coluna W nas specs: só inglês, veredito primeiro, uma linha curta, sem `$` paths — Team Lead (chat: mercans-compliance)
- 2026-09-25/28: AFI outbound Phase 1: 12 campos necessários, 7 constantes, 58 "not needed for now" removidos do DD — Team Lead (chat: mercans-compliance)
- 2026-09-29: reversão: Collective Agreement Code volta ao DD (13 campos AFI necessários) por Boletín Noticias RED 5/2018; segmentos OTD, DBA, DSC, DJD, PIT omitidos; tabela T-12 mantida — Team Lead (chat: mercans-compliance)

## Suporte (tickets)
| Data | Ticket | Assunto | Resolução | Mudou artefato? |
|---|---|---|---|---|
| 2026-09-25 | SR-79 | Fichero de Bases (ES-BASES-001), spec e testes | Em produção ~17/09; Phase Deployed To Production, ainda In Review; Lily pergunta sobre tipos além de L00/L03/L13 | Sim: spec consolidada, DD v3.12 |
| 2026-09-14 | SR-80 | AFI/TrabajadoresTramos (inbound) | Spec v2.0; ticket Open com Lily (alocação Integration × report config) | Sim: spec v2.0, DD v3.9 |
| 2026-09-04 | SR-81 | CRA (ES-CRA-001) | V2.3; aceite ~18/08; Final Review; revisão do registro ETI pendente | Sim |
| 2026-09-03 | SR-82 | Modelo 111 | Spec v4 com campos reconstruídos; Final Review | Sim |
| 2026-09-16 | SR-83 | Modelo 190 | Deploy ~15/09; novo erro de portal; posições e campos corrigidos; Final Review | Sim: spec, WTC V4.4, DD |
| 2026-09-04 | SR-85 | Modelo 296 | Estrutura D/E; spec V2.3; Final Review | Sim |
| 2026-09-09 | SR-144 | SEPE LLAMAMIENTO | Em produção ~08/09; evento-driven; pergunta sobre DATOS_USOLIBRE_EMPRESA | Não |
| 2026-09-11 | SR-342 | Employee Tax Certificate | Aceite ~10/09; pay elements novos no WTC | Sim: WTC v4.2 |
| ~2026-08-07 | SR-365 | Finiquito | Zero floor explicado (esperado); aceite Dev ~06/08 | Não |
| 2026-09-28 | SR-432 | AFI Outbound (Mensaje de Afiliación) | Product Mapping; DD VC 4.6 → ajustes até VC 1.4; 77 campos novos em dúvida | Sim: spec + DD |
| ~2026-06 | CT-4321 | Regulation Handover Checklist | Ready for Design; aba "Statutory Research" só para pay elements | Não |
| 2026-09-14 | CT-A-485 | KB SPAIN Regulation Specifications | Artigo da KB (Mohit/Lily), sem resposta nossa | Não |
| 2026-09-08 | HRBS-10563 | WTC, taxability matrix e lógica de licenças | 5 respostas + autocorreção; lógica ainda não funciona em produção (REF-03-069) | Sim: WTC V3.9, DD V3.7 |
| 2026-08-08 | HRBS-12839 | Confirmar se AFI Spec = AFI de pensão (KGS) | Sem resposta no snapshot; SLA violado | Não |
| 2026-09-18 | HRBS-13757 | Feedback de testes dos relatórios (SEPE, M111/M190/M296, Bases, payslip) | Pending on reporter; correções de Bases v2.5 e CERTIFICA v1.1 | Sim |
| 2026-09-28 | HRBS-14528 | SILTRA Notifications Integration (cliente KGS) | Sem resposta; pesquisa de compliance pedida | Não |
| ~2026 (sem data) | HRBS-10121 | Projeção de variável conta em dobro no IRPF | Corrigido para `MAX(0; prev − YTD)` | Sim: CCG v1.1 |
| ~2026 (sem data) | HRBS-10272 | AT/EP por CNAE, recaída IT, data de incapacidade | Seções 5.1.3, 8.2.1, 7.1.2; 10 campos novos | Sim: CCG v1.2, DD v3.7 |
| 2026-09-16 | (CT-A-485, thread Spain Migration) | IRPF negativo/divergente do A3 em produção (Elessent) | Defeitos em 58163 e 58118: achado de fórmula entregue ao Dev | Não (CCG v1.6 depois) |

## Pendências
- [ ] Divergência hub × skill: Valores-chave registra base mínima G4-7 "~1.424,50 (provisório)" (é o que CT-A-485 diz); a skill diz 1.424,40 (01-ccg.md §2.2, diário 47,48 × 30; 1.424,50 é erro conhecido) — confirmado em 2026-10-05; aguarda aprovação da proposta (ver rev-ES.md)
- [ ] M190: possível regressão — em ~14/09 o Dev removeu os grupos B/03 e L/27 "por não terem wage type mapeado na spec", mas em ~14/08 dissera que 79429/79430 geram B/03 e 79432 gera L/27; conferir se continuam declarados — Wallisson / Dev (SR-83) [INCERTO]
- [ ] Amostra A3 `A26S0003.AFI`: dita em SR-80 (~09/09) como conferindo com TrabajadoresTramos (inbound) e em SR-432 (~25/09) usada para validar o AFI outbound (entidade de pensão pos. 40–44, 43/43). Esclarecer — Wallisson (SR-80 × SR-432) [INCERTO]
- [ ] SR-81: Lily pede revisão de posição/comprimento dos campos do registro ETI comparando A3 `tc260704.cra` com o gerado; sem resposta — Wallisson (SR-81)
- [ ] SR-81: decidir se External Reference é preenchido com `$payroll.reference_code` — BA/negócio (SR-81)
- [ ] SR-82: preencher campos em branco colunas B–S (Tax Year, [05], [11], [17], [23], [26], [29], Reserved), acrescentar `$legal_entity_hr.previous_m111_justificante_number` ao DD; impacto de só haver original/substitutiva no campo 538 — Wallisson / Lily (SR-82)
- [ ] SR-83: explicar lógica de Descendants e remover campos duplicados do DD (pedido de Lily, 16/09) — Wallisson (SR-83)
- [ ] SR-83: Year of Birth ainda falha nos Registros 2/4 e linha 107 (Accrual Year) bloqueada por `wage_type.accrual_period_year` inexistente (mesma lacuna do SR-342); linhas 55/56 e quota sindical (linha 58) sem wage type — Dev (SR-83)
- [ ] M190 no portal ainda com erro (Hermes / REF-04-261, ~15/09) e Ejercicio = 2026 gera rejeição por regra da AEAT — Wallisson (HRBS-13757, SR-83)
- [ ] SR-85: confirmar lista de campos que passaram de branco para zero (Recipient Mediator Flag 134 ... Lender 191-226; erros E020180–E020300) e formato do Record ID (77-84: sistema zero-padded × A3 "1"+espaços); campos condicionais T2-031/037/038/039 — Wallisson (SR-85) [INCERTO se incorporado à spec]
- [ ] SR-365: Finiquito é só para residentes ou também para não residentes? Sem resposta (~07/08); Gulnaaz confirmar nas entidades — Wallisson / Gulnaaz (SR-365)
- [ ] SR-144: bloco `DATOS_USOLIBRE_EMPRESA` (opcional? o que mapear?) — Wallisson (SR-144)
- [ ] SR-79: Lily pergunta se tipos além de L00, L03, L13 estão em escopo (consultor Raul diz que não são usados); sem resposta — Wallisson (SR-79)
- [ ] SR-79: 563 = SUM(79415;79416) ou 58151 gated (respostas nossas divergentes); 501/602 leem 58554?; 2 pay elements no gatilho do L13 (não nomeados); 604 provável fantasma; H02–H06 e 537 sem wage type no WTC; `part_time_hours_per_week` ausente no DD; teste real de L03 — Wallisson / Produto-WTC (SR-79) [INCERTO]
- [ ] SR-432: Lily pergunta se os 77 campos novos no DD devem mesmo ser criados (28/09); chat registra 58 campos removidos e 13 necessários — Wallisson (SR-432) [INCERTO: reconciliar contagens]
- [ ] SR-432/chat: defeito ODL ref. 2420 (length 4 × an6, deslocamento de 2 caracteres não fecha com A3); reler tabela ODL do manual TGSS; tabelas T-79 e T-103 sem fonte — Wallisson / Regulatory Affairs (SR-432; chat: mercans-compliance)
- [ ] HRBS-12839: confirmar se a AFI Spec corresponde ao arquivo AFI de pensão (A26G0002, KGS); sem resposta, SLA violado — Wallisson (HRBS-12839)
- [ ] HRBS-14528: pesquisa de compliance sobre formato/uso das notificações SILTRA (.msj, pasta `C:\SILTRA\SVA\Msjrec`), depois volta à Configuração — Wallisson (HRBS-14528)
- [ ] HRBS-13757: payslip sem código de contrato e data de antiguidade segundo o cliente — avaliar — Wallisson; SEPE CERTIFICA (schema XML) e LLAMAMIENTO: status [INCERTO]; renomear relatórios do Bases com "L" e conferir bases do L13: [INCERTO]
- [ ] HRBS-10563: lógica de licença médica ainda não funciona em produção (REF-03-069, licença abr-mai 2026 deveria usar base de março) — Lily + Wallisson; "further query 4" (gatilho do cálculo segmentado) truncada; ponto 6 (15ª paga, campo "Extra Pay Month N (Accrual Month)") sem resposta nossa — [INCERTO se precisa de ação nossa]
- [ ] SR-342: replicar a resposta "formato correto, verificado contra 5 certificados AEAT" e avaliar se a spec muda — Wallisson (SR-342) [INCERTO]
- [ ] CCG: defeitos de fórmula em 58163 (extras) e 58118 (piso zero; 58117 negativo → 58118 ≈ 54,5%); lacunas de input no DD (RESICEME/RENCEME urgente incl. La Palma, PRESVIV, CONYUGE, ANUALIDADES, AÑOADOP, CONVIVENCIA; NUMDES com 5+ filhos); 58292 Tax Year End Date veio 20260930; U13/U280 ainda DDMMYYYY — Wallisson / Dev (chat: mercans-compliance)
- [ ] Ordinais 456/461 do design v2 ainda usam `ADD($58901;MULTIPLY($59009;12))`; confirmar correção em produção; ordinais 161/211 [TBD]; reteste do redesign de 40% — Dev / Compliance (chat: design-dev-kb) [INCERTO]
- [x] Conflito de versão do WTC e do DD — resolvido em 2026-10-05 pela regra 8: WTC V4.4, DD VC 4.6 (maior versão)
- [ ] CT-A-485: significado de 58208 = 2/3/4 (não consta na skill; 2/3 aparecem em linhas de estagiário) — Wallisson [INCERTO]. Resolvido em 2026-10-05: associação grupo-valor confirmada no PDF (G1 1929 / G2 1599,60 / G3 1391,70 / G4-7 1424,50; G3 < G4-7 é fato da fonte, que diverge da skill); rótulo "per km" nas diárias 26,67 / 91,35 / 48,08 é erro de rótulo da fonte: são valores por dia (skill 01-ccg.md §8: 53,34/91,35 com pernoite, 26,67/48,08 sem)
- [ ] Fora da CCG, com outros times: VUSA 1299 duplicados 58176/552, mapeamento 23640→64559, SOP de submissão, retro por período — outros times (chat: mercans-compliance)
- [ ] Itens pré-existentes na CCG (nome de cliente em 7.3.2, referências HRBS e destaques amarelo/ciano) — decisão separada (chat: mercans-compliance)

## Correções ligadas
- _(entradas a serem consolidadas em [[correcoes]]; rascunho em scratchpad `correcoes-ES.md`)_
- BCCC/BCCP zerados durante licença → as duas bases continuam (Orden PJC/297/2026 Art. 6) (HRBS-10563)
- Per-day só no payout / Seção 5 do doc "BCCC/BCCP Base Logic" → per-day também na base de cotização (HRBS-10563)
- Severance no CRA: 58197/58198 → 58184/58186/58188 (0054/E); 58197/58198 só BASES (SR-81)
- TRL = Tipo de Relación Laboral (não Work Risk Type) (SR-80)
- 79432 = L.27 e não Clave B; 79429/79430 = B.03 e não B.01 (SR-83, WTC V4.4)
- Dupla contagem de renda variável no IRPF corrigida (HRBS-10121, CCG v1.1)
- Série 6298 e payouts 79417–79424: AEAT clave L/L05 e clave A, não clave A/withholding nem clave B (HRBS-10563)
- M190 posições/campos da spec (Family Situation, Contract Type, Descendants, Type 2, campo inventado) (SR-83)
- M111 nome da empresa com 40 caracteres → 60 + 20 (SR-82)
- Fichero de Bases: Control Date, 509/563/603/501-502, ReferenciaExterna, L02/L03, settlement type por LE (SR-79, HRBS-13757)
- CCG v1.6: 58163/58118, art. 83.3.e, ingreso a cuenta; AFI-OUT: datas Excel, DDMMYYYY, prazo de baja, ETI.160 (chat: mercans-compliance)

## Fontes
- skill payroll-compliance-spain (lida em 2026-10-02)
- raw/tickets/extracao/2026-10-02-tickets-ES-A.md
- raw/tickets/extracao/2026-10-02-tickets-ES-B.md
- raw/tickets/extracao/2026-10-02-tickets-OUT.md (seção HRBS-10563)
- raw/chats/2026-10-01-mercans-compliance.md
- raw/chats/2026-10-01-mercans-design-dev-kb.md
- raw/chats/2026-10-01-compliance-research.md (apenas menções de contexto: Ilia Virchenko/Integration, AEAT no SI)
