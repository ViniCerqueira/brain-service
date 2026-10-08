# Tickets YouTrack: Espanha A — specs de Seguridad Social (SR-79, SR-80, SR-81, SR-144, SR-432)

> Fonte: snapshots impressos do YouTrack em `raw/tickets/txt/` (texto via pdftotext). Datas de comentário são **aproximadas**: o YouTrack mostra datas relativas ("3 months ago") e elas foram convertidas a partir da data de impressão de cada snapshot. Dados pessoais (NAF de trabalhador citado em comentário, códigos de empregado de teste, IDs de payroll) foram omitidos de propósito.
>
> Pessoas (papel): **Wallisson dos Santos Gomes** = Research Analyst (RA, compliance, nós); **Lily Li** = Business Analyst (BA); **Drew** (sobrenome ilegível no texto extraído: "Drew �ispuu") = Developer (Brenet); **Illya Virchenko** = time de Integration [INCERTO: papel inferido pelo pedido de Lily "must be assigned to integration team"]; **Katrin Rudi** = a quem Lily/Illya escalam a alocação [INCERTO: papel não dito]; **Gulnaaz** = quem fornece amostras A3 e pede validações [INCERTO: papel não dito]; **Raul** = "Spanish consultant".

---

## SR-79 — ES: Fichero de Bases – Sistema de Liquidación Directa (Social Security) – SPEC (ES-BASES-001)

- **País:** ES (Espanha) / **Cliente:** nenhum citado (testes na entidade "Spain Reports Testing") / **Tipo:** Statutory Report spec (projeto SR) / **Prioridade:** Major
- **Estado final:** In Review; Phase **Deployed To Production** (snapshot de 2026-09-25). Assignee: Wallisson. Due date 31 Jan 2026.
- **Datas:** criado ≈ dez/2025–jan/2026 ("9 months ago" em 25/09/2026); última atualização 2026-09-25 (Lily Li); deploy em produção ≈ 2026-09-17. Não resolvido.
- **Arquivos-fonte:** `18 - Ticket - SR-79 - ES; Fichero de Bases … SPEC.txt` (12/08/2026), `30 - … SR-79 …` (21/08), `39 - … SR-79 …` (02/09), `44 - … SR-79 …` (04/09), `54 - … SR-79 …` (09/09), `61 - SR-79 ES - Fichero de Bases … SPEC.txt` (11/09), `87 - Ticket - SR-79 - ES Fichero de Bases … SPEC.txt` (25/09, estado final).
- **Evolução entre snapshots:** 18→61: Phase "Final Review" o tempo todo; comentários só acumulam (snapshots antigos são subconjunto do mais recente, sem edição de conteúdo relevante). 61→87: entram a resposta de Wallisson sobre os gatilhos de settlement type (≈11/09), o pedido de Lily ao Dev, a implementação de Drew (≈14/09), testes L13, aceite (≈16/09), deploy em produção (≈17/09) e a Phase passa para "Deployed To Production". Anexos: 5 → 21.
- **Ligações:** CT-A-485 (SPAIN – Regulation Specifications); inward: HRBS-12113 (Bonificación Formación Continua), HRBS-13757 (Statutory report issues and testing feedback), SR-80.
- **Quem pediu:** Lily Li (BA) com queries de mapeamento; Drew (Dev) com dúvidas de implementação; Illya Virchenko (requisito de unicidade); Gulnaaz (amostras A3).

**Pergunta / problema**
Mapeamento de produto do Fichero de Bases (XML enviado à TGSS via SILTRA): quais base codes gerar e quando, regras de settlement type (L00/L02/L03/L13/L9x/V0x), ReferenciaExterna, FechaControl, códigos de horas (H) e indicadores (I), e alinhamento com AFI (SR-80) e CRA (SR-81). Dezenas de queries na planilha da spec ("Fichero de Bases (SSC) Spec" e "Field Options").

**Respostas / decisões nossas (agrupadas por tema)**

1. *Fluxo de queries iniciais (≈mar/2026):* várias rodadas de queries em roxo nas sheets "Fichero de Bases (SSC) Spec" e "Field Options", respondidas ("queries reverted"). Lily pediu que o desalinhamento de campos/cabeçalhos seja corrigido pelo RA, não pelo BA (mesmo problema existe na spec M190).
2. *Indenização (severance) — ≈mar–abr/2026:* 58197 Prorated Severance Taxable → **base code 701** apenas (desemprego geral); **não** entra em 500 (contingências comuns) nem 601 (AT/EP). 58198 Prorated Severance Exempt → não reportado (excluído da base de SS). Ver correção em SR-81 sobre a parte CRA.
3. *Gatilho de base codes:* gerar o registro do base code só se o valor calculado > 0; **sem registros com valor zero** (código omitido se não há valor).
4. *Unicidade (Illya, ≈abr/2026):* nome do arquivo e `referenciaExterna` devem ser únicos e não se repetir em nenhuma outra Legal Entity (crítico para rastrear status da submissão). Lily adicionou à spec.
5. *Revisão v2.1 (≈jul/2026):* coluna "AFI Field(s) Referenced" confirmada; mesmo campo em AFI e Bases = mesma lógica de mapeamento. `IndicadorObligatoriedad (B/P)` é campo só do AFI; é um **gate por Codigo sobre o registro inteiro** (Type + Code + Amount saem juntos: B = obrigatório, P = pode omitir os três juntos). Seções vazias (Datos Liquidación / Datos Mes / Dato del Tramo) foram reorganizadas fisicamente na ordem do schema oficial; ~40 referências "same as row X" atualizadas (2 já apontavam errado).
6. *Settlement types (≈jul/2026):* CURRENT period só L00/L02; RETRO (mecanismo MesLiquidativo, como L03) cobre L13, L90, L91, L92, L93, V03, V90 (manual TGSS rotula L90–L93 "Fuera de plazo"). C02/C03/C90/C91 (colegios concertados) **fora de escopo**. Tabela de 14 códigos na Field Options (L01 não existe, removido). Rectification Indicator: omitir para os 14 tipos.
7. *500 × 509 × 563 × 663 (≈ago–set/2026):* ver "Erros corrigidos". Versão final: 509 = trigger por 79418, 79419, 79420, 79421, 79423, 79424, 79429, 79430, 79432 (excluídos de 500); 500 = SUM(58151) quando não part-time e sem os gatilhos do 509; **563** (Pago Delegado IT, origem contingência comum) adicionado, gatilho 79415/79416; **663** = 58151 quando SUM(79412) > 0 (79411, dia 1, excluído — custo puro do empregador). Confirmado (≈04/09) que 58151 é o valor reportado e a SUM só funciona como gate (pareamento oficial IDC 21).
8. *ReferenciaExterna:* usar a versão do Dev — **últimos 4 dígitos do número do CCC + MMyy** (8 caracteres, único por entidade e período). O padrão antigo `'BAS' + MMyyyy` tem 9 caracteres e nunca foi válido (campo é 1–8 caracteres).
9. *L03 com vários meses (≈ago/2026):* **uma única Liquidacion com vários blocos LiquidacionMes, um por mês corrigido** (não várias Liquidacion nem vários arquivos). Base: manual TGSS — erro R9532 bloqueia repetir o mesmo mês dentro de uma Liquidacion; R9622/R9693 tratam "liquidaciones que abarquen más de un mes" como caso normal. Instrução ao Dev: loop no nível LiquidacionMes.
10. *Comparação com amostras A3 (≈02/09/2026), 10 tipos em escopo:* L00, L02, L03, L13, L90, L91, L92, L93, V03, V90 (C02/C03/C90/C91 fora). Tipo e Código são independentes. TipoDato C/H/I = Concepto/Horas/Indicador. Mudanças: (1) removido o hardcode "SolicitudRecepcionRNT = S" (ausente nos arquivos reais); (2) adicionados 497/498/499 = tramos 1/2/3 do **solidarity surcharge**, só no primeiro tramo; (3) adicionado indicador 51; (4) 603 reetiquetado com tabela completa de pareamentos (500+601 normal; 500+603 IT com prestação paga pela empresa; 500+603+563 IT contingência comum pago delegado; 500+603+663 IT acidente pago delegado; 509+603 IT pago directo / sem direito / maternidade-paternidade integral / ERE integral / risco gravidez-lactação); (5) gatilho do 509 validado contra WTC; (6) lógica L03 de datas confirmada sem mudança; (7) "501/502 corrigidos (estavam trocados)" — texto no ticket: "50158554, 50258558 fixed (were swapped)" [INCERTO: leitura provável 501→58554 e 502→58558].
11. *Queries de ≈04/09/2026:* 601 cobre full-time e part-time (H01 acompanha o 601 para part-time; não é outro base code). Condição de 500/509 não inclui 79415/79416/79417. Type I completo; Type H: 4 códigos faltantes adicionados, mapeamento aberto (`part_time_hours_per_week` falta no DD apesar de registrado como adicionado). **604 marcado como provável código fantasma** (não apagado).
12. *Consolidação (≈08/09):* Lily reclamou de versões paralelas (v2.4 sem as mudanças); Wallisson consolidou tudo **num único arquivo — o linkado na descrição do ticket** ("ES-BASES-001_FicheroBases_Spec", sem sufixo de versão).
13. *Hours e Indicadores (≈09–10/09):* H01 aplicável → `$63958.amount` (usado nas fórmulas Social Security Floor Part-Time). H02 aplicável, sem wage type no WTC; sempre junto com novo base code **537**, nunca sozinho. H03/H04/H06 sem wage type no WTC (gap de produto, não do cliente). H05 sem campo no WTC para ERE/jornada reduzida. Código de horas = **"01"**, não "1" (Bases.xsd: Codigo minLength 2 / maxLength 3). 537 → 58151 (BCCC), não 58153 (BCCP): horas complementarias (art. 12.5 ET) são horas ordinárias, mesmo grupo do 500; wage type ainda não construído no WTC. Indicadores: 51 = Modalidad Salario (M, só grupos diários 08–11); 52 = Opción Epígrafe 126 (só período 2006 — código morto); 54 = Motivo de presentación L03 (obrigatório quando Tipo = L03; 5 valores).
14. *Novos campos DD (Spain DD v3.12, ≈10/09):* `$hr.number_of_additional_hours_contract_part_time` (H02), `$hr.number_of_hours_of_face_to_face_theoretical_training` (H03), `$hr.number_of_hours_of_distance_theoretical_training` (H04), `$hr.coefficient_part_time_in_situation_of_ere` (H05), `$hr.number_of_tutoring_hours_training_contracts` (H06), `$legal_entity_hr.software_vendor_code_registered_with_tgss` (ETI campo 50, an..4, pos. 9, padrão W0xx), `$legal_entity_hr.process_syntax_version_number` (ETI campo 60, n1, pos. 13), `$legal_entity_hr.reason_for_l03_submission` (option mapper de 5 valores = indicador 54). Fonte dos campos ETI: "Sistema RED – Mensaje de Afiliación (AFI)", Ed. 05/2025 (header ETI comum a AFI/CRA/Bases).
15. *Settlement type por gatilho (≈10–11/09):* **não** depende de seleção única de `$legal_entity_hr.tgss_bases_settlement_type`; um arquivo BASES pode ter vários tipos (amostra L00+L13 confirma); cada tipo dispara por bloco/tramo conforme a circunstância. Confirmado que `tgss_bases_settlement_type` **não** é campo de legal entity. **L13** = exclusivo de trabalhador desligado com pagamento de férias não gozadas; base diária pelo período equivalente, com os base codes que normalmente se aplicam (500, 601/603), não só 500; bloco próprio junto ao do mês de desligamento, mesmo mês de liquidação. Gatilhos exatos reescritos com a "Tabla de Tipos de Liquidación" do Manual de Usuario SLD – Especificaciones Técnicas (ago/2025): L93 ok (citação adicionada); L02 com nuance en-plazo/fuera-de-plazo; L90/L91 reescritos com redação oficial; L92 = contrapartida ex-officio do L02; V03 = "(L03 de L13)"; V90 = dois gatilhos alternativos. Regras transversais confirmadas: MarcaBorrado só para C00/C02/C03/C13/C90/C91/L03/L90; FechaControl obrigatório só para L03/C03.
16. *Implementação (Drew, ≈14/09):* tipo por gatilho por bloco (L00 sempre; L03 para retro com um LiquidacionMes por mês corrigido + FechaControl + indicador 54; L13 para desligados com férias pagas), elemento RNT removido, TipoDato C/H/I, mudanças da Field Options (501/502/509/563/663/601/603, solidarity 497–499, 537 + H02, H01–H06, I51). L00 testado ok; L13 passou após gerar a partir do ciclo principal de fevereiro; aceite ≈16/09; produção ≈17/09.

**Valores estatutários / regras técnicas citadas**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| ReferenciaExterna | 1–8 caracteres; único entre legal entities | sem vigência no ticket | spec ES-BASES-001 / requisito Illya (sem fonte oficial no ticket) |
| Código de horas (Codigo) | minLength 2 / maxLength 3 → "01" | Bases.xsd v2.0.2, mar/2024 | seg-social.es "SLD: Fichero de Bases – Manual de Usuario" v2.0.2 |
| Indicador 54 (motivo L03) | 1 Atrasos de convenio; 2 Normativa/disposición legal; 3 Acto de conciliación; 4 Sentencia judicial; 5 Cualquier otro título legítimo | sem vigência no ticket | Codigos_Fichero_de_bases (TGSS) / spec |
| Indicador 51 | "M" modalidade mensal, só grupos de cotização diários 08–11 | sem vigência no ticket | Codigos_Fichero_de_bases (TGSS) |
| Indicador 52 | Opción Epígrafe 126, só período 2006 | sem vigência no ticket | Codigos_Fichero_de_bases (TGSS) |
| 497/498/499 | Solidarity surcharge tramos 1/2/3, só primeiro tramo | sem vigência no ticket | sem fonte no ticket (amostras A3) |
| Settlement types fora de prazo | L90–L93 "Fuera de plazo" | Manual ago/2025 | TGSS Manual de Usuario SLD – Especificaciones Técnicas (ago/2025) |
| Liquidacion multi-mês | um mês não pode repetir (R9532); multi-mês normal (R9622/R9693) | sem vigência no ticket | Manual oficial TGSS |
| Horas complementarias | horas ordinárias, grupo CC | sem vigência no ticket | art. 12.5 ET |
| Licenças pago directo (509) | 79417–79424 (aborto, menstruação incapacitante, interrupção de gravidez) | sem vigência no ticket | WTC citando art. 26bis/26ter ET, RD-ley 1/2023 (lista depois refinada — ver erros) |

**Artefatos afetados:** Report Spec ES-BASES-001 (v2.1 → v2.3 → v2.4 → arquivo único consolidado, sem número), Field Options; Spain DD v3.12; WTC V4.3/V4.4 (consultado); Regulation Specifications (CT-A-485).

**Erros corrigidos**
- Control Date (linhas 53–54): era tratado como flag de "late filing" → é a **data de pagamento do salário**, obrigatória só no L03; L02 nunca usa. 5 fórmulas de Ano (31/33/39/46/49) e 1 de Mês (48) apontavam para o campo-fonte errado → corrigidas (v2.1).
- 509 usava flag genérico 58235 (qualquer licença, inclusive pago delegado) → sobreposição com 500 → substituído por wage types específicos (v2.3). Depois (v2.4, cruzando WTC V4.4): 79006/79007/79029/79030/79032 eram códigos "Unit" (contagem de dias) → trocados pelos Payout 79429/79430/79432; 79417 (aborto dia 1) é pago pelo empregador, não INSS pago directo → removido; 79406/79407 (maternidade/paternidade payout) BCCC=Yes → tratamento padrão no 500, fora do 509.
- C-563 faltava (obrigatório junto ao 500 em todo pago delegado) → adicionado.
- `'BAS' + MMyyyy` (9 caracteres) → últimos 4 do CCC + MMyy.
- SolicitudRecepcionRNT "obrigatório, hardcode S" → removido (ausente em arquivos reais).
- 603 descrito como "AT/EP part-time" → reetiquetado com pareamentos de IT.
- 501/502 trocados → corrigidos [INCERTO quanto ao mapeamento exato]. Também havia conflito: referência oficial 502 = "Other Overtime" × spec 502 = "Common contingencies – Part-time".
- L02 documentado como "Error correction settlement" → é "Complementaria por salarios de tramitación" (readmissão/salários de tramitação em contexto judicial).
- `tgss_bases_settlement_type` como seleção única de legal entity (inclusive a BA chegou a dizer que os tipos retro ficavam nesse campo) → tipo por gatilho por bloco; não é campo de LE.
- Bug de Dev (não de spec): CCC saindo como zeros no XML → relatório lia snapshot de masterdata vazio; corrigido por Drew.

**Pendências em aberto**
- (Wallisson, 25/09) Lily pergunta se os tipos além de L00, L03, L13 estão em escopo e devem ser gerados pela HRB; segundo o consultor espanhol Raul, não são usados. Se em escopo, dar gatilho claro. **Sem resposta no snapshot.**
- (Dev/Drew, ≈24/09) adicionar 2 pay elements ao gatilho do L13 (acceptance e produção) — elementos não nomeados no texto [INCERTO].
- 563: Drew (≈14/09) pediu confirmação se o valor é SUM(79415;79416) (como na célula E145) ou 58151 gated; Wallisson tinha dito 58151 gated em ≈04/09, mas em ≈ago escreveu "Formula unchanged: SUM(79415, 79416)". Sem resposta registrada [INCERTO].
- Drew pediu confirmação de que 501 e 602 leem 58554 (horas extras em CC e AT/EP) — sem resposta registrada.
- Mapeamento de horas H02–H06: wage types inexistentes no WTC (gap de produto); 537 sem wage type construído.
- `part_time_hours_per_week` ausente no DD.
- 604 "provável fantasma" a confirmar.
- Teste real de L03 (sem payroll retro calculado na entidade de teste no momento do pedido).

**Fronteira:** Desenvolvimento/configuração do relatório = Dev (Drew/Brenet); bugs de geração (CCC zerado) = Dev, não spec; criação de wage types novos (537, H02–H06) = produto/WTC.

---

## SR-80 — ES: AFI – Affiliation Message (Social Security) – SPEC (ES-AFI-001 / TrabajadoresTramos)

- **País:** ES / **Cliente:** nenhum citado / **Tipo:** Statutory Report spec (na prática: arquivo **inbound** da TGSS) / **Prioridade:** Major
- **Estado final:** Open; Phase "Development Phase – Developer"; Assignee **Lily Li** (snapshot 14/09/2026). Due date 31 Jan 2026.
- **Datas:** criado ≈ jan/2026 ("8 months ago"); última atualização 2026-09-14 (Wallisson). Não resolvido.
- **Arquivos-fonte:** `45 - Ticket - SR-80 ES - AFI … SPEC.txt` (04/09/2026), `56 - … SR-80 …` (09/09), `65 - … SR-80 …` (14/09, estado final).
- **Evolução:** Assignee: Drew (04/09) → Wallisson (09/09) → Lily Li (14/09). Em 04/09 Drew dizia que SR-370 "passou no teste de aceite em 12 Aug"; depois editou para "already built in acceptance". 09/09: entra o pedido de comparar com amostra A3. 14/09: Wallisson responde "inbound" e depois reconfirma com nomes completos.
- **Ligações:** menciona SR-79 e SR-370 (SOLTRT SolicitudTrabajadoresTramos); inward HRBS-9178 (Updating Spain DD and Country fields), HRBS-12839 (Spain Regulation_AFI Report confirmation).
- **Quem pediu:** Lily Li (BA); time de payroll operation (requisitos MA/MB/MC/MG); Illya Virchenko (Integration); Drew (Dev).

**Pergunta / problema**
O que é o "AFI" desta spec, quem gera e para quem, se é necessário para product mapping, quais campos viram HR fields, quais se ligam ao Fichero de Bases, e se é inbound ou outbound. Payroll operation pediu também quatro "relatórios" AFI (MA/MB/MC/MG).

**Respostas / decisões nossas**
- *(≈mar/2026)* Authorized User ID / `Autorizado` → `$legal_entity_hr.red_authorization_code` (número de autorização RED do operador do SILTRA; não é API key).
- *(≈mai/2026) MA/MB/MC/MG:* não são 4 relatórios novos; são tipos de transação de afiliação (Alta, Baja, Cambio de Contrato, Cambio de Grupo de Cotización), eventos em tempo real de HR/onboarding, normalmente **não gerados pelo motor de payroll**. **Ficam fora desta spec**; se em escopo, ticket próprio.
- *(≈mai/2026) Fluxo:* sem API HRB↔TGSS. SILTRA é aplicação Java desktop, autenticada com certificado SILCON; processo manual do operador: (1) solicita TrabajadoresTramos à TGSS (opcional/informativo), (2) baixa o XML e importa na HRB, (3) HRB lê e gera ES-BASES-001, (4) operador sobe o Bases via SILTRA, (5) TGSS valida; se não confere, devolve arquivo de erro; sem arquivo de confirmação, TGSS fecha a liquidação de ofício. ES-AFI-001 é "Fichero de Respuesta de la TGSS" — **não é gerado pela HRB**.
- *(≈mai/2026) Spec continua necessária para product mapping:* product mapping vale para arquivos gerados **e** recebidos; a HRB precisa ler DatosTramo/DatoSolicitado (base codes 500, 501, 502, 601, 602, 701, 702, 703 e indicadores B/P) para saber quais registros gerar no Bases. Rebatido o documento do Gemini trazido pela BA (que dizia não haver parsing): ele está certo que o arquivo não dirige o gross-to-net, errado ao concluir que não há parsing.
- *(≈mai/2026) Check competitivo:* ingestão do TrabajadoresTramos é padrão de mercado — SAP HCM (RPC_PAYES_CRETA_FILES, SAP Note 2223843), a3innuva/a3nom, Sage Despachos Connected ("Comparador Trabajadores y Tramos"), miNomina, wincreta, JMD, Logicsoftware. Decisão: **ES-AFI-001 fica em escopo**.
- *(≈mai/2026) Campos:* já no DD (NAF, documento, grupo de cotização, tipo de contrato, CNO, província/CCC/Autorizado, coeficiente part-time derivado). READ-ONLY da TGSS, **não** criar como HR field: CAF, DiasCotizados, todo DatoSolicitado, Peculiaridades. Novos campos propostos: CNAE (LE), TRL, ColectivoEspecial (condicional). Ligação com Bases: Autorizado, CCC, períodos, Tipo, LiquidacionMes, NAF, datas de tramo; ligação crítica = DatoSolicitado/Codigo diz quais Codigo gerar no Bases.
- *(≈jul/2026) v1.1 → v2.0 (auditoria fechada, aba "Audit Closure Memo"):* coluna U "READ-ONLY from TGSS Response" estava majoritariamente errada. Final: ficam **N** (lado da solicitação, ecoados de volta, sem mapeamento no download): Autorizado, ReferenciaExterna, Ccc, CccConcertado, Periodo, Tipo, Control Date. Viram **Y** (dado da TGSS, HRB só lê): Naf, Ipf, CAF, Settlement Month, datas de tramo, bloco InformacionAfiliacion inteiro, Peculiaridades, DatosTramo, Contribution Base Amount. Settlement Type sincronizado com a lista de 14 códigos (L01 não existe).
- *(≈jul/2026)* DD atualizado para **v3.9** para alinhar opções de settlement type spec × DD.
- *(≈ago/2026)* Referência da interface inbound para Integration: **ES-TGSS-INT-IN-001** (acesso concedido a Illya).
- *(≈04/09/2026)* Confirmado: **SR-80/TrabajadoresTramos = inbound (TGSS→usuário)**; **SR-370/SolicitudTrabajadoresTramos = outbound (usuário→TGSS)**. Fonte: Manual de Usuario TGSS, Sistema Liquidación Directa, agosto/2025.
- *(≈09/09/2026)* Amostra A3 `A26S0003.AFI` confere com TrabajadoresTramos; nenhuma mudança na spec.
- *(≈10/09 e 14/09/2026)* Resposta curta "inbound" gerou confusão; reconfirmado com nomes completos: "inbound" referia-se ao TrabajadoresTramos especificamente, não a "AFI" como categoria geral.

**Valores estatutários:** nenhum valor estatutário (alíquota/teto/prazo) no ticket.

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Base codes pedidos via DatoSolicitado | 500, 501, 502, 601, 602, 701, 702, 703 | sem vigência no ticket | spec ES-AFI-001 / documentação SILTRA (sem citação precisa) |
| CausaBaseAdicional | 001 / 901 / 902 / 903 (part-time concentrado / relevista / aposentadoria parcial) | sem vigência no ticket | schema oficial (citado genericamente) |

**Artefatos afetados:** Report Spec ES-AFI-001 TrabajadoresTramos (v1.1 → **v2.0**); Spain DD **v3.9**; referência de integração ES-TGSS-INT-IN-001.

**Erros corrigidos (incluindo respostas nossas anteriores)**
- **TRL**: nossa resposta de ≈mai/2026 dizia "Work Risk Type, determina a taxa AT/EP" → correto: **"Tipo de Relación Laboral"**; a escala de risco 000/500/800 "foi inventada".
- **Epígrafe** (54): não é RETA/autônomo → predecessor pré-2007 do campo Ocupación.
- **CatProfesional** (57): só regime de mineração de carvão, não código CNO geral.
- **CausaBaseAdicional** (60): códigos reais 001/901/902/903; nada a ver com maternidade ou IT.
- Coluna U (read-only): Control Date Y→N; Collection Date/Time N→Y; bloco InformacionAfiliacion N→Y; Contribution Base Amount N→Y; depois Naf, Ipf, CAF, Settlement Month, datas de tramo, Peculiaridades, DatosTramo → Y.
- Settlement Type: L01 removido (não existe).

**Pendências em aberto:** ticket assignado a Lily Li; sem pergunta aberta a Wallisson no último snapshot. Alocação ao time correto (Integration × report config) continuava em discussão: Lily diz que é inbound e deve ir para Integration; Illya diz que "aparece como Outbound report e requer report config" (≈02/09); Drew esclareceu a diferença SR-80 × SR-370.

**Fronteira:** MA/MB/MC/MG = eventos de HR/onboarding, fora desta spec (ticket separado, que depois virou SR-432 [INCERTO: ligação não explícita no texto]). Interface inbound = time de **Integration** (Illya/Katrin). Operação no SILTRA = operador/cliente (manual).

---

## SR-81 — ES: CRA – Communication of Paid Remuneration Concepts (Social Security) – SPEC (ES-CRA-001)

- **País:** ES / **Cliente:** nenhum citado (testes "Spain Reports Testing") / **Tipo:** Statutory Report spec / **Prioridade:** Major
- **Estado final:** In Review; Phase **Final Review**; Assignee Wallisson (snapshot 04/09/2026). Due 31 Jan 2026. Spent time 1d 2h 17m.
- **Datas:** criado ≈ jan/2026 ("8 months ago"); última atualização 2026-09-04 (Drew). Aceite passado ≈ 2026-08-18. Não resolvido.
- **Arquivos-fonte:** `42 - Ticket - SR-81 ES - CRA – Communication of Paid Remuneration Concepts (Social Security) - SPEC.txt` (único snapshot).
- **Ligações:** inward CT-4406 (Spain Regulation_Retribution Flexible), CT-4433 (ES: Spain Regulation Support).
- **Quem pediu:** Lily Li (BA); Drew (Dev).

**Pergunta / problema**
Mapeamento dos pay elements para códigos CRA (sheet "Pay Elements with CRA Code"), indicador I/E, campos de legal entity (Settlement Type, Action Type), tratamento de severance (rateado vs. pago) e posição/comprimento dos campos no arquivo.

**Respostas / decisões nossas**
- *(≈mar/2026)* Várias rodadas de queries respondidas. Linhas 58100, 58105, 58111, 58129 removidas da sheet (sem indicador marcado).
- *(≈abr/2026)* Novo campo LE **"TGSS CRA Action Type"**: opções do DD confirmadas contra a aba Field Options da spec; "blank" é só o comportamento default (TGSS trata como Alta), não é opção selecionável — não entra no mapper. Default **A** (todas as submissões mensais padrão). **TGSS CRA Settlement Type** default **00** (folha mensal padrão). Label, descrição e referência ao mapper completados no DD.
- *(≈abr/2026)* Settlement Month/Year = período em que a remuneração foi efetivamente paga (CRA reporta no mês de pagamento).
- *(≈abr–mai/2026) Severance — ver erro corrigido abaixo.* Estado final: no mês de desligamento o CRA tem **58184, 58186, 58188, todos 0054/E** (não sujeitos a SS). **58197 e 58198 não aparecem no CRA**; são wage types só do BASES (construções de cálculo para a prorrata L03): 58197 distribui a base de SS do excesso tributável (código 701) nos 12 meses anteriores; 58198 (isento) não é reportado no BASES.
- *(≈ago/2026)* Indicador do código CRA **0001 é sempre I**. Remuneration Amount = soma do valor do pay element por código CRA no período, **agrupada por código + indicador I/E** (Dev: chave `CONCAT('CRE_'; código; '_'; I/E)`; 10 códigos misturam I e E: 0033, 0042, 0043, 0044, 0045, 0046, 0050, 0054, 0055, 0062). Spec **V2.3** (mudanças em rosa).
- Implementação Dev (≈jun/2026): arquivo fixed-width de 70 caracteres `.CRA` (SILTRA/RED), registros ETI/DDE/TRB/CRE, mapeamento de 548 WTs para códigos CRA (spec v2.2), valores em centavos. Nome do relatório: "Spain CRA - Conceptos Retributivos Abonados".
- Bugs de teste (≈ago/2026, Dev): valor mantido no sistema saindo como zeros; posições 19–22 (Settlement Year) e 23–24 (Settlement Month) trocadas → corrigidos; aceite passou.
- *(04/09/2026, Dev)* External Reference vazio **por design** (linha 9 da spec sem mapeamento; ID interno opcional) — Drew sugere `$payroll.reference_code` se quiserem preencher. Remuneration Amount vem do **resultado da folha**, não do salary card (coincidência no caso testado: salário-base prorrateado + férias pagas na rescisão, ambos mapeados para 0001).

**Valores estatutários / regras técnicas**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Formato CRA | linhas fixas de 70 caracteres, registros ETI/DDE/TRB/CRE | sem vigência no ticket | spec ES-CRA-001 v2.2 (sem fonte oficial no ticket) |
| Settlement Type default | 00 (folha mensal) | sem vigência no ticket | spec / Field Options (sem fonte oficial no ticket) |
| Action Type default | A (blank = Alta por default da TGSS) | sem vigência no ticket | spec Field Options (sem fonte oficial no ticket) |
| Severance no CRA | 58184/58186/58188 → 0054/E | sem vigência no ticket | sem fonte no ticket |

**Artefatos afetados:** Report Spec ES-CRA-001 (v2.2 → **V2.3**); Spain DD (campos TGSS CRA Action Type, TGSS CRA Settlement Type; em SR-79 também `software_vendor_code_registered_with_tgss` e `process_syntax_version_number`).

**Erros corrigidos**
- **Nossa resposta de ≈abr/2026 estava errada:** dissemos "CRA: reportar 58197 (0054/I) e 58198 (0054/E) no mês de desligamento" e que a tabela de mapeamento devia ficar. A BA apontou e corrigimos (≈mai/2026): no CRA entram **58184, 58186, 58188 (0054/E)**; 58197/58198 são **só BASES**. (Obs.: em SR-79 ≈mar/2026 a tabela mostrava 58197 → CRA 0054/I e 58198 → 0054/E; superada por esta correção.)
- Dev: zeros no lugar do valor mantido; ano/mês trocados nas posições 19–24.

**Pendências em aberto**
- **(Wallisson, 04/09/2026)** Lily pede revisão de **posição e comprimento dos campos do registro ETI** comparando amostra A3 (`tc260704.cra`) com o arquivo gerado. Sem resposta no snapshot.
- (BA/negócio) decidir se External Reference deve ser preenchido com `$payroll.reference_code`.

**Fronteira:** geração do arquivo e bugs = Dev (Drew/Brenet).

---

## SR-144 — ES: SEPE LLAMAMIENTO (callback) – SPEC

- **País:** ES / **Cliente:** nenhum citado / **Tipo:** Statutory Report spec / **Prioridade:** Major
- **Estado final:** Open; Phase **Deployed To Production**; Assignee Wallisson (snapshot 09/09/2026). Due 28 Feb 2026.
- **Datas:** criado ≈ fev/2026 ("7 months ago"); última atualização 2026-09-09 (Lily Li); deploy em produção ≈ 2026-09-08.
- **Arquivos-fonte:** `55 - Ticket - SR-144 ES - SEPE LLAMAMIENTO (callback) - SPEC.txt` (único snapshot).
- **Quem pediu:** Lily Li (BA).

**Pergunta / problema**
Relatório pronto para teste (≈jun/2026); download vinha vazio; depois aceite e produção. Após a produção, a BA comparou com amostra A3 (`L26S0001.XML`) e perguntou sobre o bloco `DATOS_USOLIBRE_EMPRESA`.

**Respostas / decisões**
- Dev (≈jul/2026): pasta vazia é comportamento esperado — relatório **orientado a evento**, só gera arquivo quando há `sepe_callback_start_date` no período (llamamiento só quando trabalhador **fijo discontinuo** é efetivamente chamado de volta).
- Aceite ≈ago/2026; produção ≈08/09/2026. Sem mudança de mapeamento.
- Nenhuma resposta nossa registrada no ticket.

**Valores estatutários:** nenhum no ticket.

**Artefato afetado:** Report Spec SEPE LLAMAMIENTO (versão não citada).

**Erros corrigidos:** nenhum.

**Pendências em aberto**
- **(Wallisson, 09/09/2026)** bloco `DATOS_USOLIBRE_EMPRESA`: na amostra A3 vem preenchido (conteúdo com códigos tipo "E3|T…|C…|F…"); no arquivo gerado é omitido porque a explicação do campo na spec não é clara. Pergunta: o bloco é opcional? O que mapear exatamente? Sem resposta.

**Fronteira:** desenvolvimento e deploy = Dev (Drew).

---

## SR-432 — ES: AFI Outbound (Mensaje de Afiliación) – SPEC

- **País:** ES / **Cliente:** nenhum citado / **Tipo:** Statutory Report spec (outbound) / **Prioridade:** Major
- **Estado final:** Open; Phase "Product Mapping Phase – Business Analyst"; Assignee Wallisson (snapshot 28/09/2026). Due **29 Jan 2027**.
- **Datas:** criado ≈ 2026-09-14; última atualização 2026-09-28 (Lily Li).
- **Arquivos-fonte:** `79 - Ticket - SR-432 ES - AFI Outbound (Mensaje de Afiliación) - SPEC.txt` (22/09/2026), `85 - Ticket - SR-432 - ES AFI Outbound (Mensaje de Afiliación) - SPEC.txt` (28/09/2026, estado final).
- **Evolução:** 22/09: Phase "Development Phase – Developer", 2 pedidos (tradução e queries coluna V). 28/09: Phase "Product Mapping Phase – Business Analyst"; queries respondidas, DD 4.6, validação A3, nova pergunta sobre 77 campos.
- **Quem pediu:** Lily Li (BA); Gulnaaz (validação contra amostra A3).

**Pergunta / problema**
Spec do AFI outbound (Mensaje de Afiliación) com nomes de campo e explicações em espanhol; queries de mapeamento na coluna V; validação contra amostra A3; confirmação de criação de campos novos no DD.

**Respostas / decisões nossas**
- *(≈20–21/09)* Coluna A e "Field Explanation" da sheet "AFI Spec" traduzidas para inglês.
- *(≈22–23/09)* Queries da coluna V respondidas na coluna W (atualizações em verde). **DD atualizado — Version Control 4.6** — com novos campos e option mappers. Algumas respostas anteriores mudaram (listadas na **Version Control 1.2** da spec); principal: linhas 173–174, **DAM.2150–2170 só se aplica ao Special System 32**, portanto **não** é o coeficiente de part-time discutido em reunião.
- *(≈25/09)* Validado contra amostra A3 `A26S0003.AFI`: campo de entidade de pensão (pos. 40–44) confirmado em 43/43 registros. Campo reservado (2420): posição corrigida — texto "18-21/len4 18-23/len6 (TGSS manual typo)" [INCERTO: provável de 18–21/len 4 para 18–23/len 6, por erro de digitação no manual TGSS]. Spec atualizada.

**Valores estatutários:** nenhum no ticket.

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| DAM.2150–2170 | aplica-se só ao Special System 32 | sem vigência no ticket | sem fonte no ticket |
| Campo reservado 2420 | posição 18–23, len 6 [INCERTO] | sem vigência no ticket | manual TGSS (com erro de digitação) + amostra A3 |

**Artefatos afetados:** Report Spec "Spain AFI – Outbound (Mensaje de Afiliación)" (Version Control **1.2**); Spain DD (**Version Control 4.6**).

**Erros corrigidos:** resposta anterior (reunião) tratava DAM.2150–2170 como coeficiente de part-time → só Special System 32. Posição do campo reservado 2420 (erro no manual TGSS).

**Pendências em aberto**
- **(Wallisson, 28/09/2026)** Lily: "no DD há 77 campos novos no total; esses 77 devem mesmo ser criados?" Sem resposta.

**Fronteira:** nada explícito. Contexto: em SR-80 os eventos MA/MB/MC/MG (Alta/Baja/Cambios) foram declarados fora daquela spec e "eventos de HR/onboarding, normalmente não gerados pelo payroll"; SR-432 parece ser a spec separada desse outbound [INCERTO].

---

## Síntese do grupo

### (a) Decisões recorrentes / padrões
1. **Sem registros zerados no Fichero de Bases:** base code só sai se valor > 0; senão é omitido.
2. **Inbound × outbound bem separados:** SR-80 TrabajadoresTramos = inbound (TGSS→usuário), SR-370 SolicitudTrabajadoresTramos = outbound; AFI outbound (Mensaje de Afiliación) = SR-432. Respostas curtas ("inbound") geraram confusão → responder sempre com nome completo do arquivo.
3. **Mesmo campo em specs diferentes = mesma lógica de mapeamento** (AFI ↔ Bases ↔ CRA; header ETI é comum a AFI/CRA/Bases). `Autorizado` = `$legal_entity_hr.red_authorization_code` em todas.
4. **Spec inbound também precisa de product mapping** (a HRB precisa ler/parsear o arquivo recebido).
5. **Settlement type por gatilho, por bloco**, não por seleção única de legal entity; vários tipos no mesmo arquivo; retro (L03 etc.) = uma Liquidacion com vários LiquidacionMes; C02/C03/C90/C91 (concertados) fora de escopo.
6. **Severance:** CRA reporta o pagamento real (58184/58186/58188, 0054/E) no mês de desligamento; BASES usa 58197 (código 701, L03 nos 12 meses anteriores); 58198 não vai para nenhum dos dois.
7. **Gap de produto declarado, não "inventado":** quando não há wage type no WTC (H02–H06, 537, inicialmente 663), marcar como gap/aberto em vez de chutar mapeamento.
8. **Uma só versão de spec:** atualizar sempre o arquivo linkado na descrição do ticket (BA reclamou de versões paralelas).
9. **Validação contra amostras A3** (Gulnaaz) virou etapa padrão antes/depois do deploy (SR-79, SR-80, SR-81, SR-144, SR-432).
10. Destaques por cor na planilha: laranja = corrigido; verde = novo/atualizado; rosa/magenta/roxo = queries/mudanças da BA.
11. Unicidade de nome de arquivo e ReferenciaExterna entre legal entities (requisito de Integration).

### (b) Lista de [INCERTO]
- Papéis de Illya Virchenko, Katrin Rudi e Gulnaaz (inferidos, não ditos).
- SR-79: "50158554, 50258558 fixed (were swapped)" — leitura provável 501→58554, 502→58558.
- SR-79: valor do 563 — SUM(79415;79416) ou 58151 gated pela soma (respostas nossas divergentes; pergunta do Dev sem resposta).
- SR-79: os 2 pay elements adicionados ao gatilho do L13 (≈24/09) não estão nomeados no texto.
- SR-79: datas exatas (convertidas de datas relativas).
- SR-432: correção do campo reservado 2420 ("18-21/len4 18-23/len6") — direção provável 18–21/4 → 18–23/6.
- SR-432 × SR-80: a mesma amostra A3 `A26S0003.AFI` foi dita em SR-80 (≈09/09) como correspondente ao **TrabajadoresTramos (inbound)** e em SR-432 (≈25/09) usada para validar o **AFI outbound** (entidade de pensão pos. 40–44, 43/43 registros). Possível contradição ou arquivo com conteúdo misto — verificar.
- SR-432 como o "ticket separado" para MA/MB/MC/MG previsto em SR-80: não explícito.
- SR-80: TRL e ColectivoEspecial — após a correção de TRL, não está claro se TRL/CNAE/ColectivoEspecial seguiram como campos novos no DD.

### (c) Artefatos e últimas versões citadas
| Artefato | Última versão citada | Ticket |
|---|---|---|
| ES-BASES-001 Fichero de Bases Spec | arquivo único consolidado (após v2.4), linkado na descrição; em produção ≈17/09/2026 | SR-79 |
| ES-AFI-001 TrabajadoresTramos Spec | v2.0 (com "Audit Closure Memo") | SR-80 |
| ES-CRA-001 CRA Spec | V2.3 | SR-81 |
| Spain AFI Outbound (Mensaje de Afiliación) Spec | Version Control 1.2 | SR-432 |
| SEPE LLAMAMIENTO Spec | sem versão; em produção ≈08/09/2026 | SR-144 |
| Spain Data Dictionary | v3.9 (SR-80) → v3.12 (SR-79) → Version Control 4.6 (SR-432) | SR-79/80/432 |
| Spain WTC | V4.3 / V4.4 (consultado) | SR-79 |
| SR-370 SolicitudTrabajadoresTramos (outbound) | construído em acceptance | citado em SR-80 |
| Referência de integração inbound | ES-TGSS-INT-IN-001 | SR-80 |
| Fontes oficiais citadas | TGSS Manual de Usuario SLD – Especificaciones Técnicas (ago/2025); Bases.xsd / "SLD: Fichero de Bases – Manual de Usuario" v2.0.2 (mar/2024); "Sistema RED – Mensaje de Afiliación (AFI)" Ed. 05/2025; Codigos_Fichero_de_bases (TGSS); art. 12.5, 26bis/26ter ET; RD-ley 1/2023 | — |
