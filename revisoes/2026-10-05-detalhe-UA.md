# Revisão UA (2026-10-05)

Método: o `pdftotext` sem `-enc UTF-8` perdia o cirílico; com `-enc UTF-8 -layout` o cirílico sai. A ferramenta Read não renderiza PDF neste PC (falta poppler). Extrações UTF-8 em `scratchpad\ua\`.

## A. Alterações feitas nos hubs
- Ucrânia: regra 8. WTC V4.1, CCG V1.5, DD V3.10 viraram "(vigente: maior versão)". Histórico foi para Observação, e a linha "Situação" foi ajustada. Saíram 3 [INCERTO] de numeração (WTC, DD x2).
- Ucrânia: cartas nº 4340 e nº 553 agora têm emissor (4340 = Держпраці; 553 = Мінсоцполітики). Confirmado no PDF do HRBS-12631 (UTF-8).
- Ucrânia: portal do 1-PV trimestral = Кабінет респондента (Respondent's Cabinet). Confirmado no PDF do SR-415.
- Ucrânia: per diem exterior EUR 80, removido [INCERTO] de vigência. Confirmado: HRBS-14331 PDF diz "For 2026 ... EUR 80 per calendar day".
- Ucrânia: presente (25% do salário mínimo de 1º de janeiro), removido [INCERTO] de "conflito de descrição". O HRBS-14324 dá a base e o HRBS-12181 cita só "25% threshold"; os dois não se contradizem.
- Ucrânia: Pendência de versões marcada como feita pela regra 8. Resta só a V1.4 do CCG, que não é citada.
- Ucrânia: Pendência do 65808 recebeu o contexto de rótulos (ver B1). O conflito continua aberto.
- Criado `scratchpad\pacote-skill-UA.md`: 25 correções e as "Open items".

## B. Propostas (precisam de aprovação)
| País | Item | Hub diz | Fonte diz (trecho curto + ref) | Proposta concreta | Risco |
|---|---|---|---|---|---|
| UA | B1. Rótulo do 65808 | Conflito de nomes (representação x seguro de vida) | HRBS-12181: "65808 Representation expenses (financial, no military tax)"; WTC v3.8 renomeou 65810 = Life insurance. HRBS-14331: Nataliia escreve "65808 Life Insurance (BIK)", e nossa resposta repetiu "65808 base + 65894". | Tratar o 65808 como Representation (financial) e o seguro de vida como 65810. Corrigir a resposta do HRBS-14331 (o pedido de "mais um código" vale para o 65810) e acrescentar linha em `correcoes.md`. | Médio |
| UA | B2. Período-base do sick leave | 6 meses (HRBS-14331 K/X) x 12 meses (12631/13392) | O mesmo HRBS-14331 se contradiz. O texto de regras de Lily diz "Last 12 calendar months before the month of illness". As colunas K/X dizem "6-month base ... Postanova 1266, п. 4". | Decidir um valor com a Nataliia, pela Postanova 1266 p. 4, antes de publicar. Se mudar, fechar a linha antiga com "Até" e acrescentar a nova. | Alto |
| UA | B3. Faixas de % do sick leave | Divergência 13389 x 14331 | HRBS-13389: <5 anos 60%, 5-8 80%, 8+ 100%. HRBS-14331 (regras de Lily): <3 anos 50%, 3-5 60%, 5-8 70%, >8 100%. Maternidade sempre 100%. | Usar a tabela do HRBS-14331 (mais recente) só depois de confirmar com a Nataliia; encerrar com "Até" as faixas do 13389 se forem substituídas. | Alto |
| UA | B4. Código 4DF 128 | Contradiz o CCG | HRBS-14331, Nataliia: "code 128 - is only for the maternity sick leave for 126 +14 days"; outras licenças 101 (férias) ou 126 (benefício). | Ajustar WTC e CCG para 128 só em maternidade sick (126 + 14 dias) e revisar 65700-65712. Confirmar com a Nataliia primeiro. | Alto |
| UA | B5. Códigos "102" e "sem imposto" (HRBS-14331) | Pendência "imagens não capturadas" | O texto do PDF traz só: "Here should be code 102? please update WT" e "Here is No all taxes, maybe its Mean that this is maternity vacation for the care of the children till 3 or 6 Years?". O WT em questão está nas imagens, que não consegui ler. | Abrir o PDF original no Chrome e identificar o WT (pergunta C1). Hipótese: licença-cuidado tratada como benefício (126) com tributos. | Médio |

## C. Perguntas para o Wallisson (respondíveis em 1 linha)
- [Ucrânia] Qual WT aparece nas imagens do HRBS-14331 (comentários "Here should be code 102?" e "No all taxes ... children till 3 or 6 years")? As imagens não vêm no texto e o Read não renderiza PDF aqui. Se você abrir o PDF "81 - Ticekt - HRBS-14331..." (págs. 14-15), me diga o código e o nome.
- [Ucrânia] A Nataliia respondeu algo depois do HRBS-12631 sobre a ressalva "(if main place of work)" do contrato civil? Se sim, o [INCERTO] sai. (origem: HRBS-12631)
- [Ucrânia] Qual é o papel/time da Nataliia Hahan (especialista local da Mercans, cliente ou parceiro)? (origem: cabeçalho do hub)
- [Ucrânia] O UA-INTREP-001 (relatório interno) já foi postado em algum ticket depois de 12-08? (origem: chat de 2026-10-01)
- [Ucrânia] O SR-163 "Chief Accountant RNOCPP -> director_signatory_rnocpp" é erro do Dev? A spec traz exatamente esse mapeamento, então ou o rótulo ou o campo está errado.

## D. Contagem
- Ucrânia: [INCERTO] 10 linhas antes -> 5 depois (restam: papel da Nataliia, UA-INTREP-001, sick leave 6 x 12 meses, ressalva CPC, SR-163). 7 itens resolvidos (WTC, DD, per diem, presente, emissores das cartas, portal do 1-PV, numeração do DD). 5 propostas. Os itens B2-B5 são divergências dentro do próprio ticket, não resolvíveis só pela fonte. Não há skill; as fontes foram os tickets e o chat.
- Outros itens não tocados: vários valores "⚠️ sem fonte" (PIT 18%, ML 5%, ESV 22%, salário mínimo etc.). Não há skill para completar a fonte, e os tickets só repetem os valores. Para o salário mínimo UAH 8.647, o HRBS-14331 confirma o valor (8,647 x 0.1 = 864.70) mas sem lei citada, então a marcação "sem fonte" fica.
