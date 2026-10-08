# Revisão RESTO (2026-10-05)

Escopo: 38 hubs (todos em paises\ exceto os 12 hubs de outros grupos e README). Hubs só-skill (Alemanha, Bahrein, Belarus, Chipre, Costa-Rica, Dinamarca, Egito, Estonia, Filipinas, Finlandia, Indonesia, Libano, Malasia, Marrocos, Noruega, Portugal, Singapura, Suecia, Tchequia, Romenia, Tailandia, Australia): sem conflito de versão e sem divergência; os poucos "⚠️" (Costa-Rica, Filipinas) já trazem a ressalva correta. Sem alteração, exceto o que consta em A.

## A. Alterações feitas nos hubs
- Irlanda: [INCERTO] da pontuação do design (84% × 72%) resolvido (72% = ponto médio entre lógica 84% e contagem 60%; confirmado na tabela de correções do chat design-dev-kb); item marcado [x].
- Bulgaria: WTC BG "V2.2 (vigente: maior versão)"; "design usa V2.1" foi para Observação como histórico.
- Chile: Regulation Design "v1.1 (vigente: maior versão)", "arquivo nomeado v1.0" para Observação. Completadas fonte e vigência (2026) de Tetos 89,9/135,1 UF, comissões AFP e prazos Previred/F29/LRE (skill 01-ccg.md; valores idênticos aos do hub).
- Canada: completada a fonte de "lesser-of por período" (01-ccg.md Módulo 5) e de NR_RECIPIENT_TYPE_CODE {1,3,4,5} (04-reports-spec.md, T4A-NR rcpnt_tcd); vigência 2026.
- Franca: DD e Report Specs com "v1.1 (vigente: maior versão)" e a versão antiga em Observação. Diálogo social e prazo 2502-SD: [INCERTO] mantido, com a referência da skill acrescentada (CCG M5.1 e WTC FR-019 dizem 0,016% nos dois lados; 03-sir.md Q1 confirma prazo não resolvido).
- Holanda: removido o [INCERTO] do 30%-regeling 27% desde 2027 (confirmado: 01-ccg.md, Handboek §19.4.7; com a ressalva de que a coorte até 2023-12-31 mantém 30%). Completadas fonte e vigência de Zvw 6,10%, Aof laag/hoog, AWf, Wko (01-ccg.md). "Aof Uit 7,63%" continua sem fonte.
- Reino-Unido: completadas fonte/vigência de Levy, Auto-enrolment 5/3, Student loan (planos 1/2/4/5). Removido o [INCERTO] do tax code 1257L (confirmado como código 2026-27; a nota "2025/26" do DD é o defeito).
- Colombia: completadas fonte/vigência (2026) de IBC mín./máx., Saúde, Pensão, Parafiscales e SMMLV (skill: Ley 100 arts. 18/20/204, Ley 797/2003, Ley 1122/2007, Ley 21/1982, Ley 89/1988, Decreto 0159/2026). As 5 "Divergência hub × skill" ficaram intactas (ver B).
- Belgica: Observação dos Artefatos CCG e WTC ganhou a versão de registro da skill (v1.2 e v1.1). Divergências ficaram intactas (ver B).

## B. Propostas (precisam de aprovação)
| País | Item | Hub diz | Fonte diz (trecho curto + ref) | Proposta concreta | Risco |
|---|---|---|---|---|---|
| Irlanda | PRSI empregado | EE 4,1% | "Employee 4.20%" até 30/09/2026; "4.35%" desde 1/10/2026 (01-ccg.md §5.2 tabela A0/AX/AL/A1). 4,1% é só Class H (07-qa-report; 05-data-dictionary) | Fechar linha "PRSI EE 4,1%" com Até 2025-12-31 (⚠️ fonte do design) e acrescentar: EE 4,20% desde 2026-01-01 e 4,35% desde 2026-10-01 (SW 14 2026; 01-ccg.md §5.2) | Alto |
| Irlanda | PRSI empregador | ER 8,9% / 11,15% / 0,6% | "AX 4.20% / 9.00%; AL 4.20% / 9.00%; A1 4.20% / 11.25%" até 30/09; "A0 9.15%; AX/AL 4.35% / 9.15%; A1 4.35% / 11.40%" desde 1/10 (01-ccg.md §5.2) | Fechar linha antiga; acrescentar ER faixa baixa 9,00% e A1 11,25% desde 2026-01-01; 9,15% e 11,40% desde 2026-10-01 (SW 14 2026). NTFL 1% já embutido, não somar (01-ccg.md) | Alto |
| Irlanda | Limite A1 | A1 >527 | "The employer's lower-rate threshold for 2026 is €552 per week — not €527 (2025) and not €441" (01-ccg.md §5.2; SKILL.md item 3) | Corrigir para >552 (semanal; €1.104 quinzenal, €2.392 mensal) desde 2026-01-01; crédito PRSI e divisa AX/AL (€424) conferir no 01-ccg.md antes de reescrever a fórmula MAX(0; 12 − (sem − 352)/6) | Alto |
| Irlanda | USC | 0,5/2/3/8%, "8% acima de 42.662" | "€12,012 @ 0.5%; next €16,688 @ 2% (ceiling €28,700); next €41,344 @ 3% (ceiling €70,044); balance @ 8%" (01-ccg.md linhas ~295-304). 42.662 é a largura da faixa de 3% em 2025 (teto 70.044) | Fechar linha antiga; acrescentar USC 2026: 0,5% até 12.012; 2% até 28.700; 3% até 70.044; 8% acima de 70.044 (Revenue USC thresholds; 01-ccg.md). Obs.: a faixa de 2% em 2025 terminava em 27.382 | Alto |
| Reino-Unido | LEL | "LEL default 542" / "vs GBP 125 semanal" | "Lower earnings limit (LEL) £129 / £559 / £6,708" (01-ccg.md linha 340, 2026-27) | Fechar linha 542 (⚠️ sem fonte) com data de fim e acrescentar LEL £129/semana, £559/mês, £6.708/ano desde 2026-04-06 (HMRC rates page; 01-ccg.md §5.1). Atenção: 542 não parece valor de LEL em nenhum ano; verificar de onde o DD v3 tirou | Alto (DD GB é artefato de produção) |
| Reino-Unido | Letras de NI | "17 letras NI" | "all 16 category letters" (SKILL.md descrição; 07-qa-report: "all 16 category letters" 99%); tabela 01-ccg.md §5.2 lista A, B, C, D, E, F, H, I, J, K, L... | Trocar para 16 letras de categoria NIC em Valores-chave, e conferir no DD GB se existe uma 17ª opção (ex.: valor "sem letra"/Z) que explique o 17 antes de corrigir o DD | Médio |
| Belgica | box 360 no WTC | "falta tax code box 360 no fiscal work bonus" | "Wage type BE-003 'Fiscal work bonus' carries Tax Code '284; 360'" (02-wtc.md linha 50; WTC v1.1) | Marcar a pendência "box 360" como resolvida no WTC v1.1 (fonte: 02-wtc.md, linha de revalidação 284/360), mantendo a nota de que a v1.0 não tinha; nenhum arquivo a mudar | Baixo |
| Belgica | CCG 697,61 × 697,42 | CCG M9 Step 7 traz 697,61 (errado); correto 697,42 | CCG v1.2 linhas 2792/2801: "53.50% applied to 1,500.00 − 196.05 = 1,303.95 \| 697.61"; QA 07 linha ~114: "end-of-year premium line now reads 697.61 in both the detail and the summary". Conferência: 1.303,95 × 53,5% = 697,61 | Fechar a pendência "697,61 → 697,42": a skill (v1.2) mantém 697,61 e é coerente com a conta; 697,42 não reproduz com 53,5%. Perguntar de onde veio 697,42 (ver C) antes de mexer no CCG | Médio |
| Belgica | Social work bonus teto 1 jul | "3.594,36 (1 jul, conflito, ver Lacunas)"; Lacuna diz que design/QA §6.2 dizem NOT FOUND | CCG v1.2: "EUR 3,594.36 from 1 July 2026. CLOSED 16 September 2026 ... edition 2026/3 states 'het totaal van de vermindering per werknemer niet meer bedragen dan 3.594,36 EUR per kalenderjaar'" (01-ccg.md linha 1239; 02-wtc.md v1.1 linha 35). O 07-qa-report §6.2 "unresolved" é anterior ao refresh de 16/09 | Remover o "conflito" e a Lacuna: valor 3.594,36 desde 2026-07-01 confirmado (NSSO instructions 2026/3). O QA §6.2 está desatualizado, não a skill | Baixo |
| Colombia | Exoneração 10 SMMLV | "ER exonerado até 10 SMLMV" (saúde, SENA, ICBF) | "The test is strictly less than 10 SMMLV ... exactly $17.509.050 ... is lost"; exonera salud ER 8,5%, SENA 2%, ICBF 3%; nunca CCF (01-ccg.md linha 410; SKILL.md item 5; 05-DD EXONERACION_114_1) | Reescrever linhas Saúde/Parafiscales: "exoneração só com salário estritamente < 10 SMMLV (ET art. 114-1); CCF e pensão nunca exoneradas", desde 2026-01-01 | Alto |
| Colombia | Dependentes | "dependentes máx. 32 UVT" | "additional dependents deduction: 72 UVT per dependent per year, max 4" (01-ccg.md linhas 501/539; ET art. 336 num. 3, fora do limite 40%/1.340 UVT); 32 UVT/mês é o teto da dedução de 10% (art. 387) | Acrescentar linha: 72 UVT/dependente/ano, máx. 4 (ET art. 336 num. 3), mantendo 32 UVT/mês (art. 387, 10%) | Médio |
| Colombia | 1.340 UVT ÷ 12 | risco: validador do cliente divide por 12 | QA Q-2: "The engine convention of dividing by 12 (→ 111,6667 UVT ...) is a derivation ... prescribes no monthly conversion"; confiança ~75% (07-qa-report.md linha 156) | Reescrever a pendência: ÷12 é convenção derivada tanto no engine da skill quanto no validador; alternativa defensável é acumulado YTD (resultado diferente para rendas altas). Não afirmar sub-retenção até DIAN concepto | Médio |
| Colombia | IBC férias / embargo / bônus 95 UVT / cesantías | valores de HRBS-12492/12491/12487/13692 | Não aparecem na skill (embargo: só "inembargable", 01-ccg.md linha 1083) | Manter como "declarado pelo solicitante, sem fonte"; incluir no escopo da gap analysis CO. Sem alteração de valor | Baixo |
| Colombia | Situação da pesquisa | research-pipeline 🔄 "na fila depois da Bélgica" | Skill: pesquisa 2026-08-27, veredito READY WITH DOCUMENTED GAPS, 15 itens abertos (SKILL.md/07-qa-report.md); mas Mohit (~2026-08-29) pediu redesign/gap fixing | Atualizar Situação: "skill CO pronta (2026-08-27, READY WITH DOCUMENTED GAPS); gap analysis dos 5 tickets PMI pendente". Confirmar com o usuário (ver C) | Baixo |
| Irlanda / Colombia / Reino-Unido / Belgica | Regra 2 geral | linhas com ⚠️ sem fonte do design | idem acima | Ao aplicar as propostas, preservar a linha antiga com data de fim (não sobrescrever) | n/a |

## C. Perguntas para o Wallisson (respondíveis em 1 linha)
- [Belgica] De onde veio o 697,42 do Módulo 9 Step 7 (outro cálculo, outra alíquota)? A skill v1.2 e a conta 1.303,95 × 53,5% dão 697,61 (chat mercans-compliance).
- [Belgica] A pendência "box 360 no WTC" pode ser fechada, já que o WTC v1.1 traz "284; 360"? (02-wtc.md)
- [Reino-Unido] O "542" do LEL no DD GB v3 é erro de digitação ou outro campo (ex.: limite semanal de outra coisa)? (chat design-dev-kb)
- [Reino-Unido] O DD GB tem 17 opções de letra NI (talvez uma "sem letra")? A skill descreve 16 letras.
- [Irlanda] A HRBS-13860 (classes PRSI incorretas em Clavis e OMG) exige ação de Compliance ou fica só com o L2? O ticket só mostra acknowledgment do Romano (txt 34).
- [Irlanda] O design IE (Regulation Design v1.0) vai ser atualizado com PRSI 4,20/4,35%, A1 >552 e USC 2026 antes de usar como referência?
- [Colombia] Posso atualizar a Situação da pesquisa CO para "skill pronta 2026-08-27, gap analysis pendente"?
- [Lituania] O que a Manju atualizou na HRBS-15253 em 2026-09-28? O txt não mostra comentário dela, só o acknowledgment da Lavanya.
- [China] SR-316 (CN payslip): ficou pronto depois de 2026-08-10? O txt de 8/10 só mostra o pedido da Lily Li e o ping da Enaakshi; Due 2026-08-31.
- [Chile] A revisão dos campos amarelos da spec LRE (SR-221) foi concluída? O ticket tem comentários da Ruchi 13 dias e 5 horas antes do snapshot, sem fecho.
- [Kuwait] Tem acesso ao HRBS-8606 (PIFSS) no YouTrack? Não há PDF/txt na pasta; só o chat cita o ID.
- [Bulgaria] Alívio de deficiência por filho: 3.930 (design) ou 7.920/ano (660/mês)? Só os chats registram os dois números; não há skill BG.
- [Hungria] A SR-A-5 substitui a SR-A-1? E o family allowance correto é 133.340/266.660/440.000 (SR-A) ou 10.000/20.000/33.000 (transcrição)?
- [Hungria] A composição dos 18,5% é pensão 10 + saúde 8,5 (conferir) ou outra? Os chats dão duas versões.
- [Holanda] A redline §7.1.4 do NL-CCG-001 (HRBS-1534) foi aceita ou rejeitada?
- [Franca] Diálogo social 0,016%: vale ER e EE (CCG M5.1, WTC FR-019) ou só ER (CCG M3, Ex. 6)? E o prazo 2502-SD: 15 ou 31/jan (a skill deixa em aberto)?
- [Vietna/Tailandia/India/Romenia/Australia] Sem skill ou sem fonte além do chat; as perguntas existentes ("ICE", mapper restaurado, quem decidiu HRA/STSL, prazo do board) seguem abertas.

## D. Contagem
(contagem de linhas com [INCERTO], antes → depois)
- Irlanda: 2 → 1; 1 resolvida; 4 divergências hub × skill viraram propostas (PRSI EE, PRSI ER, limite A1, USC)
- Reino-Unido: 2 → 1; 1 resolvida (tax code 1257L); 2 divergências em proposta (LEL, 17 × 16 letras)
- Belgica: 2 → 2; 0 resolvidas; 3 divergências em proposta (box 360, 697,61/697,42, teto 3.594,36); 2 INCERTO mantidos (design BE sem registro; resíduos de BE na França: "FR-NSSO" e "Description (NL)" não aparecem mais na skill FR, o que sugere já corrigido; manter até o usuário confirmar)
- Holanda: 7 → 6; 1 resolvida (27% do 30% ruling); 5 mantidos (design sem registro, aceite do redline, aceite de rótulo HRBS-10563, prompt NL, variante do prompt)
- Franca: 7 → 7; 0 resolvidas; 2 com referência da skill acrescentada (diálogo social, 2502-SD)
- Colombia: 2 → 2; 0 resolvidas; 5 divergências em proposta (exoneração, dependentes, 1.340÷12, itens só do cliente, Situação); 9 linhas de valor com fonte/vigência completadas
- Chile: 2 → 2; 3 linhas ⚠️ completadas pela skill
- Canada: 2 → 2; 2 linhas ⚠️/vigência completadas
- Bulgaria: 4 → 4; regra de versões aplicada (WTC V2.2)
- Hungria 4, Lituania 3, China 4, India 2, Kuwait 4, Australia 3, Romenia 2, Tailandia 4, Vietna 4: sem alteração (sem skill ou fonte posterior ao snapshot de 29/09)
- Demais hubs só-skill: 0 [INCERTO], sem alteração
- Regra de versões (A): Bulgaria, Chile, Franca ajustados; Irlanda, Reino-Unido, Belgica (versão única), Holanda, Colombia sem conflito de numeração. Situação da Franca cita "Pacote v1.0" (nome do pacote, não de artefato); não alterei.
