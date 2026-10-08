# Extração: projeto "Mercans Design & Development Knowledge Base"

> Extraído em 2026-10-01. Cobertura: 69 docs + 8 planilhas do projeto, lidos na íntegra.
> Regra: só o que está registrado no projeto. `[INCERTO]` marca dúvida ou conflito entre fontes. Cada linha cita o doc de origem entre colchetes.
> Sem PII de funcionários de clientes. Nomes de clientes substituídos por [cliente].
> Abreviações de fonte: **FR-pack** = FR_Design_CarryOver_Pack.md; **T-AAAA-MM-DD** = KB_Transcript_AAAA-MM-DD_*.md; **T-08-25** = Cross Training - Design Creation - 2026_08_25 (Gemini).docx; **DevKB** = KB_DevTeam_AI_Prompts_And_TaxRuleGroups.md; **FormulaPrompt** = Mercans Formula Prompt.md (idêntico ao .docx "# Mercans Payroll Formula — Global AI Prompt").

---

## 1. Sobre este projeto

- **Propósito:** base canônica de design e desenvolvimento da folha Mercans. Dono: Compliance Regulations Team (Wallisson Gomes). Uso compartilhado com os times de Design/Dev. Objetivo: design autônomo de regulações para países novos, a partir de padrões de países já em produção. [00_INDEX.md; instruções do projeto]
- **Etapas cobertas:**
  - **Design:** a maior parte. Regulation Design (flags, regulations, bands, taxability matrices, contas), transcrições de cross-training com o dev team, comparações Claude vs Dev, prompts de IA, padrões do engine.
  - **Research Pipeline:** pacote FR completo (CCG, WTC, DD, SIR, Payslip, QA); artefatos de ES, CL, BW, BG, IE e TD; crítica pré-submissão de TD; pesquisa estatutária TD.
  - **Suporte:** pouco. Escalações citadas em transcrições (VN, TH, NL, AU, RO) e as queries da Lily Li sobre ES.
- **Países:**
  - Com pacote ou design próprio: FR, ES, CL, BW, BG, IE, TD, HU, CI, CG, IN (WTC Display), GB (DD), NL (prompt de Client Manual).
  - Citados: EG, TR, MY, LB, RO, TH, ID, VN, AU, PH, CY, IQ/KRI, Gabon, Yemen, Canada.
- **Tipos de fonte** (conforme as instruções do projeto):
  - Pesquisa de compliance = verdade legal.
  - Docs do dev team e prompts = verdade de implementação.
  - Transcrições = histórico de decisões.
  - Os KB_Transcript_* são resumos feitos a partir de notas Otter/Gemini, não transcrições literais.
  - O T-2026-07-16 foi reconstruído de um auto-transcript ruim e não tem nada ratificado. [T-2026-06-16_18; T-2026-07-16]
- **Arquivo duplicado:** `KB_Transcript_2026-06-25_Design_Creation_CrossTraining.md` aparece duas vezes no projeto (criado em 25/06 e em 11/07). Nos trechos comparados, o conteúdo é igual. [INCERTO: só uma das versões foi lida por inteiro]

## 2. Entregas

### França (FR): pacote de pesquisa (Research Pipeline v2.4) e design

| Artefato | Versão | Data | Status | Fonte |
|---|---|---|---|---|
| CCG FR-CCG-001 (13 módulos; 136/136 perguntas) | v1.0 | ~2026-08-26 | Entregue; QA PASS no formato | [01-ccg.md; 07-qa-report.md] |
| WTC FR-WTC-001 (374 WTs = 300 globais + 74 FR-0xx; 6 abas) | v1.0 | 2026-08-27 | "Draft" no Version Control | [02-wtc.md] |
| DD FR-DD-001 (25 ID + 164 campos de país; 54 mappers / 303 códigos) | arquivo v1.0, conteúdo v1.1 | 2026-08-27 | Released | [05-data-dictionary.md] |
| Report Specs (15 workbooks: 10 outbound, 5 inbound) | v1.0 → v1.1 | 2026-08-27 | 15/15 no formato; anotação F-1 a corrigir | [SKILL.md; 07-qa-report.md] |
| SIR FR-SIR-INDEX-001 + integration landscape (5 autoridades, 3 M2M) | v1.0 | 2026-08-27 | HAS_INTEGRATIONS | [03-sir.md] |
| Runbooks NETENT-DSN, URSSAF-DPAE, DGFIP-EDI (7 fases) | — | 2026-08-27 | BUILD-READY, com itens bloqueados ou não verificados | [03-sir.md] |
| Payslip FR-PSL-001 (8 abas; versão FR legal + EN cortesia) | v1.0 | — | Entregue (m-3 em aberto) | [06-payslip.md] |
| QA cross-check | — | 2026-08-28 | **87/100, NEEDS PATCHES** (0 críticos, 3 maiores, 3 menores) | [07-qa-report.md] |
| Alignment patch DD × Specs | — | 2026-08-27 | 26/26 asserções OK | [07-qa-report.md] |
| scope_manifest.json (lock em 2026-08-26) | 1.1 | 2026-08-27 | Validação PASS (W-01..W-03) | [07-qa-report.md] |
| Skill roteadora `fr-compliance` | — | upload 2026-09-06 | Ativa | [SKILL.md] |
| Design Method v3 (substitui a v2 de 25/08) | v3 | 2026-08-28 | Autoritativo | [FR-pack] |
| Regulation Design FR, Bloco 1 (prefixo 9250; 7 regs, 21 flags, 13 bases, 18 contas) | v0.1 | ~2026-08-28 | Validado contra o Ex. 1 do CCG; próximo é o Bloco 2 | [FR-pack] |

### Demais países

| País | Artefato | Versão | Data | Status | Fonte |
|---|---|---|---|---|---|
| ES | WTC | v3.6 → v3.9 (final) | — | Aprovado (Lily Li, Mohit Jain) | [KB_Spain_Research_Artifacts(_v2).md] |
| ES | CCG (autor Wallisson) | v1.0 (jan/2026) → v1.1 (HRBS-10121) → v1.2 (HRBS-10272) → v1.3 (final) | — | Final v1.3 | idem |
| ES | DD | v3.1 → v3.7 (final) | — | Final v3.7 | idem |
| ES | Regulation Design v1 (19 PDFs CT-A-485..505) | v1 | — | Substituído | [KB_Spain_Regulation_Design.md] |
| ES | Regulation Design CT-A-507 (~90+ passos, ordinais 5–621, com o "40% redesign") | v2 | jun/2026 | Produção | [KB_Spain_Regulation_Design_v2.md] |
| ES | Report specs: SR-79 Bases, SR-80 AFI, SR-83 M190, SR-224 Payslip | — | — | Open | [KB_Spain_DevTeam_Questions_And_Reports.md] |
| ES | Report specs: SR-81 CRA, SR-82 M111, SR-84/85 M216/M296, SR-142..145 SEPE, SR-130 G2N | — | — | In Review | idem |
| ES | Report specs: CT-1057 Finiquito, CT-1059 L00-L13 | — | — | On Hold | idem |
| ES | CT-4357 Retro | — | — | Ready for Dev | idem |
| CL | CCG CL-CCG-001 / WTC CL-WTC-001 / DD CL-DD-001 | v1.1 / v1.0 / v1.0 | mai/2026 | Base do design | [KB_Chile_Research_Artifacts.md] |
| CL | Design Decisions (respostas da Ruchi por GChat) | — | 2026-06-03 | 5 bloqueios resolvidos | [KB_Chile_Design_Decisions.md] |
| CL | Regulation Design (9152xxx, 36 regs) | v1.1 (arquivo chamado v1.0) | jun/2026 | Q1 e Q5 abertas | [CL_Regulation_Design_v1.0.md] |
| BW | CCG (autor Wallisson) / WTC / DD | v1.0 (fev/2026) / v3.0 / v3.1 | — | Base | [KB_Botswana_Full_Package.md] |
| BW | Design CT-A-507 + tabela CT-A-508 (Mohit; 12 regs, 9072xxx) | — | — | Produção | idem |
| BG | BG_Design.xlsx + bg.json (28 regs, 9100xxx); base BG-CCG-001, WTC/DD V2.1 | — | — | Produção; país de referência para o formato artigo + JSON | [KB_Bulgaria_Design_*.md] |
| IE | Regulation Design do Claude (31 regs, 9372xxx); base CCG 2025, WTC v3.6, DD v3.4 | v1.0 | — | 6 open items | [IE_Regulation_Design_v1.0.md] |
| IE | Comparação Claude vs Dev (CT-A-192, 52 regs) | — | 2026-06-24 | ~72% | [IE_Design_Comparison_Claude_vs_DevTeam.md] |
| TD | CCG / WTC / DD / 7 report specs | v1.2 / v1.1 / v1.1 | — | Base do design | [TD_Regulation_Design_v1_0.md] |
| TD | Crítica pré-submissão + lista de problemas (14 itens) | — | 2026-06-25 | Concluída | [TD_DevTeam_Critique_PreSubmission.md; TD_Lista_Problemas_Pesquisa.md] |
| TD | Regulation Design clean-room do Claude (24 artigos: 23 ativos + 1 retirado) | v1.0 | 2026-07-07 | Concluído | [TD_Regulation_Design_v1_0.md] |
| TD | Statutory Research CCG Positions (Q1–Q7) | — | 2026-07-07 | Posições para a reunião | [TD_Statutory_Research_CCG_Positions.md] |
| TD | Comparação Claude vs Dev (CT-A-580, 31 regs; Mohit fez em ~2 dias com IA) | — | 2026-07-07 | Lógica ~89%, geral ~83% | [TD_Design_Comparison_Claude_vs_DevTeam.md; T-2026-07-02] |
| TD | Design novo, do zero (Wallisson) | — | pedido em 2026-08-25 | A fazer | [T-08-25] |
| CI | Regulation Design do Claude (48 regs) | v1.0 / v1.1 | jul–ago/2026 | Revisado pelo Mohit em 25/08; precisa de revisão (contas, fórmulas, linguagem) | [T-2026-07-10; T-08-25] |
| CI | Accuracy Score (v1.0 contra os 18 regs do dev) | v2 | 2026-08-14 | ≈85% | [CI_Accuracy_Score_v2.md] |
| CG | Comparação clean-room × CT-A-590 | — | 2026-08-28 | 77%; cobertura funcional 26/26 | [FR-pack] |
| HU | Design do dev team (Suman Rai) | — | concluído ~2026-06-25 | Finalizado | [T-2026-05-26..29; T-2026-06-25] |
| HU | Report specifications | — | 2026-06-25 | Em andamento (Suman) | [T-2026-06-25] |
| HU | SR-A-1 (design spec, regs 9348011–061) e SR-A-5 (versão convertida para o formato artigo) | — | upload 2026-09-10 | [INCERTO] status; as duas versões divergem (ver seção 5) | [SR-A-1.md; SR-A-5.md] |
| HU | Design "new track pattern" (Wallisson), para a Manju comparar | — | pedido em 2026-07-10 | A fazer | [T-2026-07-10] |
| TR | Product spec (as-is + gaps) para o Andre; 2 simulações G2N/N2G (Manju) | — | 2026-07-16 | Em elaboração | [T-2026-07-16] |
| UK | Directors' NI (artigo de KB) | — | 2026-06-18 | Desenvolvimento no pipeline | [T-2026-06-16_18] |
| GB | Country Data Dictionary (102 campos; 14 mappers) | 3.0 (arquivos v3 e "v31" idênticos) | 2026-05-27 | Publicado | [GB_Country_Data_Dictionary_v3/v31.xlsx] |
| IN | Global WTC Taxability Display (566 PEs × 10 regulations) | 2 cópias, só a formatação muda | ~2026-08-20 | Entregue; 9356204 a confirmar | [Global_WTC_Taxability_Display(1).xlsx] |
| Gabon / Iraq ou Yemen | Designs novos (Manju / Enaakshi) | — | pedido em 2026-08-25 | A fazer | [T-08-25] |

### Global: padrões, prompts e ferramentas

| Artefato | Versão | Data | Status | Fonte |
|---|---|---|---|---|
| Master Index da KB (24 arquivos) | — | 2026-06-25 | — | [00_INDEX.md] |
| Global Wage Type Catalogue (~2.000 contas) | v1.0 | 2026-06-25 | Referência | [KB_Global_Wage_Type_Catalogue_v1.0.md] |
| Referência de sintaxe do engine (formulas.xlsx, 12 abas) | — | jun/2026 | A seção 8 está desatualizada | [KB_Engine_Formula_Syntax.md] |
| KB de fórmulas Mercans (Google Sites) | — | consultado em 2026-05-27 | Referência | [KB_Mercans_Knowledgebase_Formulas.md] |
| KB dos prompts do dev team + catálogo de Tax Rule Groups | — | 2026-07-02 | "AUTHORITATIVE" | [DevKB] |
| Master Data Dictionary Template | v1.5 | ~2026-06-03 | Publicado | [Master_Data_Dictionary_Template_v1.5.xlsx] |
| Prompt Mercans Payroll Formula (.md e .docx idênticos) | — | upload 2026-08-25 | Em uso | [FormulaPrompt] |
| Prompt Master Client Manual: variante NL e variante genérica "(1)" | — | upload 2026-08-25 | [INCERTO] qual variante vale | [Master AI Prompt…(1).docx] |
| Prompts WTC→Taxability Matrix e Matrix→WTC (Expander) | "Revised" | upload 2026-08-25 | Para uso no Gemini com thinking | [Conversion…docx; Prompt to create WTC…docx] |
| WTC_Build_Prompt (design → WTC + matriz; baseline de ~491 códigos) | — | upload 2026-08-25 | — | [WTC_Build_Prompt.md] |
| Regulation Design → JSON (.md e .docx idênticos; tabelas quebradas no .docx) | "Revised" | upload 2026-08-25 | — | [Regulation_Design_JSON_Prompt_Revised.md] |
| YouTrack Table → JSON (Combined) | V1.0 | upload 2026-08-25 | — | [YouTrack_Regulation_Table_to_JSON_Prompt V1.0.md] |
| YouTrack artigo antigo → artigo novo | V1.1 | upload 2026-08-25 | — | [Prompt to Convert Youtrack…V1.1.md] |
| Export horizontal de 3 seções → artigo | — | upload 2026-08-25 | — | [Prompt_to_Convert_Horizontal…md] |
| Payroll Design Review Prompt (revisado após a revisão de Iraq Federal + KRI) | v2 | upload 2026-08-25 | — | [PayrollDesignReviewPrompt_v2.md] |
| Country Settings Automation Scripts (14 scripts JS para o back-office de acceptance) | — | upload 2026-08-25 | Ferramenta | [Country Settings Automation Scripts.docx] |
| Executive Brief + Blueprint de HR Fields (Layered Metadata Inheritance) | — | upload 2026-08-25 | Proposta; aprovação não registrada | [Executive Brief…docx; HR Fields Architecture…docx] |
| Global WTC Display Project (spec de tela) | — | upload 2026-08-25 | Formato proposto | [Global WTC Display Project.docx] |
| HR Fields Selection Automation (backlog com 10 áreas; o título diz "9") | — | upload 2026-08-25 | Lista de ideias | [HR Fields Selection Automation] |
| Contribution Pay Elements (~174 linhas) / Global G2N Specifications (rótulo "DK Specific") | — | — | G2N em rascunho | [Contribution Pay Elements.xlsx; Global G2N Specifications.xlsx] |
| Country AI Validation File Board (35 países/blocos) | — | export do Monday | Todos "Not Started" | [Country AI Validation File Board.xlsx] |

**Board de validação estatutária por IA.** A coluna é "Priority (Given by Yoyo)". Os prazos são semanais. [Country AI Validation File Board.xlsx]

| Prioridade | Países e prazos |
|---|---|
| Critical | Egypt 31/08/2026; GCC 07/09; Singapore 14/09 |
| High | Australia 21/09; Denmark 28/09; Finland 05/10; Indonesia 12/10; New Zealand 19/10; Norway 26/10; South Africa 02/11; Spain 09/11; Sweden 16/11; UK 23/11; Vietnam 30/11 |
| Medium | Algeria 07/12; Angola 14/12; Colombia 21/12; Costa Rica 28/12; Estonia 04/01/2027; Malaysia 11/01; Nigeria 18/01; Philippines 25/01; Thailand 01/02 |
| Low | Ireland 08/02; Lebanon 15/02; Taiwan 22/02; Belarus 01/03; Iran 08/03; Jordan 15/03; Kazakhstan 22/03; Kenya 29/03; Morocco 05/04; Pakistan 12/04; Portugal 19/04; Tunisia 26/04/2027 |

[INCERTO] Os prazos de Egypt, GCC, Singapore, Australia e Denmark já passaram com status "Not Started". O export pode estar desatualizado.

## 3. Decisões tomadas

### Globais (engine, método, processo)

| Data | Decisão | Motivo | Quem decidiu | Fonte |
|---|---|---|---|---|
| 2026-04-20 | Antes de desenvolver, o dev monta um blueprint em steps (Input → Step calc → Output). Um step travado vira gap query para a compliance | "Without this… your calculation will break" | Mohit (Dev Lead) | [T-2026-04-20] |
| 2026-04-20 | A ordem dos steps depende do que é pre-tax. Se SS é pre-tax: SS → gross taxable → imposto | Dependência entre bases | Mohit | [T-2026-04-20] |
| 2026-04-20 | Na regulação, trabalha-se com "gross taxable"; "gross salary" é parâmetro de sistema. Steps e intermediates são reaproveitados, nunca duplicados. Na matriz, usar séries em vez de linhas individuais | Arquitetura e performance | Mohit | [T-2026-04-20] |
| 2026-04-20 | A compliance aprende design participando das design calls (BG, HU) | "By telling me you will not learn anything" | Mohit | [T-2026-04-20] |
| 2026-05-22 | 1 regulation step = 1 artigo YouTrack, convertível direto em JSON. A matriz fica embutida no artigo de gross taxable. BG é a referência | Elimina interpretação manual do PSD | Mohit / Dev | [T-2026-05-22] |
| 2026-05-22 | Usar IA para **validar** designs existentes (mais valor, menos risco) em vez de gerá-los. Compartilhar outros designs só depois de checar IP com o Andre | Vários caminhos válidos; conhecimento tácito; IP | Mohit | [T-2026-05-22] |
| 2026-05-29 | Flags 58xxx carregam condições; regulações 9xxxxxx carregam cálculos. Assertion simples do tipo `GREATER(SUM(flag);0)` | Reuso e auditabilidade | Mohit | [T-2026-05-29] |
| 2026-06-11 | Datas comparadas sempre como `yyyyMMdd`, nunca `MMdd` | Falso positivo entre anos; anos fiscais fora do calendário (BW) | Ruchi; Mohit confirmou | [T-2026-06-11; KB_Engine_Formula_Syntax.md] |
| 2026-06-11 | Joiner no meio do período: fora da base, mas no relatório com base zero. Leaver no meio do período: período completo | Regra de elegibilidade | Ruchi | [T-2026-06-11] |
| 2026-06-11 | Padrão Taxation Type `Flat` + TRG `simple_tax`. Muda para `retro_simple_tax_post_formula` só quando há fórmula. Para designers novos, o dev define TT/TRG na call | Curva de aprendizado | Ruchi; Mohit | [T-2026-06-11] |
| 2026-06-18 | Papéis: RA/Compliance só pesquisa; Configuration Analyst só desenha; Andre só desenvolve. Cyprus foi o primeiro uso do sistema colaborativo por módulos | Orientação da liderança | Crystal [INCERTO cargo] | [T-2026-06-16_18] |
| 2026-06-24 | Seis learnings da IE: (1) triplet YTD→Cumulative→Current; (2) decomposição atômica Threshold/Base/Amount (**revogado em 07-02**); (3) regs "Paid" explícitas; (4) reconciliações no ordinal 0 e no fim; (5) levar a sério os open items do Claude; (6) o ID 9+ISO+ordinal funciona | Comparação com produção | Análise comparativa | [IE_Design_Comparison…md] |
| 2026-07-02 | Imposto progressivo normal = **uma** regulação `Differential` com faixas | O engine soma as faixas | Mohit | [DevKB; T-2026-07-02] |
| 2026-07-02 | Design primeiro; WTC e DD são documentação do design. Matrix-first e WTC-first são os dois aceitos | "Design doesn't come from WTC and DD" | Mohit | [DevKB] |
| 2026-07-02 | Reconciliação in-period padrão: Regular + retro Single Period. "All Payroll" fica obsoleto; "First Payroll" nunca foi usado | Abordagem moderna | Mohit (contradiz Ruchi em 06-25) | [DevKB; T-2026-07-02] |
| 2026-07-02 | Ceiling amount = valor na band. Ceiling account = valor vindo de flag ou de step. MIN/MAX não é ceiling. Dependência circular só existe em gross-up | Definições oficiais | Mohit | [DevKB] |
| 2026-07-10 | Docs de design padronizados em **Markdown**. Chat compartilhado de KT entre os workflows Claude do Mohit e do Wallisson | Decisão do time | Mohit/Ruchi/Manju/Wallisson | [T-2026-07-10] |
| 2026-07-10 | Bug fix tem escopo restrito por padrão; redesign só com estrutura errada | Caso do 30% ruling (NL) | Mohit | [T-2026-07-10] |
| 2026-07-14 | Acesso a country settings revogado para todos, exceto o compliance team | Report TXT de TH quebrado pelo integration team | Manju, Mohit, Ruchi | [T-2026-07-14] |
| 2026-08-25 | Automação de design começa por países pequenos (CI, Chad, Gabon, Iraq, Yemen), depois os complexos (ES, DE, AU, CA). Piloto com países **novos**, sem reaproveitar designs de IA anteriores | Revisar país complexo leva mais tempo; replicação de padrões falhos | Manju (proposta), Mohit concordou | [T-08-25; FR-pack] |
| 2026-08-25 | Design por IA só com prompt detalhado + especificação escrita. Human-in-the-loop obrigatório. Aprendizado manual em paralelo. Reuniões fixas às terças e quintas | Output não implementável sem isso | Mohit; consenso | [T-08-25] |
| 2026-08-28 | Design Method v3 substitui a v2: convenção anual é regra escrita; Floor = Ceiling é padrão legítimo; "Formula" tem semântica precisa | Leitura de CT-A-264, CT-A-263 e CT-A-119 | Wallisson | [FR-pack] |
| s.d. | Arredondamento: não arredondar intermediários; dinheiro final com 2 casas; fator arredondado com ≥4 casas | Erro material com 2 casas | Dev (prompt) | [FormulaPrompt] |
| s.d. | JSON: `regulationId` é sempre um UUID v4 novo; o ID numérico nunca vai para o output | "CRITICAL" no prompt | — | [Regulation_Design_JSON_Prompt_Revised.md; YouTrack…V1.0.md] |
| s.d. | Payroll Design Review Prompt v2 é aditivo ("Nothing below removes an original rule") | Falsos positivos e negativos na revisão de Iraq | — | [PayrollDesignReviewPrompt_v2.md] |
| s.d. | Master DD v1.1–v1.5: `applicability_rule` substitui `visibility_rule`; bulk STRICT (Policy A); `dependency_rule` com 4 tipos; i18n em colunas inline `label_<locale>`; catálogo de tipos de 20 para 8; is_email/phone/url passam a `regex_lib`; `field_id` e keys de mapper imutáveis (desativar com is_active=false); "NOT APPLICABLE always wins"; mesma engine em Form, Bulk e API | Evolução do template | — | [Master_Data_Dictionary_Template_v1.5.xlsx] |
| s.d. | WTC (BW): colunas laranja (dev) preenchidas a partir das azuis (research) por regras determinísticas; vale também para o DD | Objetivo de automação | Wallisson | [KB_Botswana_Full_Package.md] |
| s.d. | HR Fields: **proposta** (não decisão) de trocar o modelo de duplicação por herança em 3 camadas (L1 Global / L2 Country / L3 Entity delta) | Drift, órfãos, inchaço | Não registrado | [Executive Brief…; HR Fields Architecture…] |

### Por país

| Data | País | Decisão | Motivo | Quem decidiu | Fonte |
|---|---|---|---|---|---|
| 2026-05-26 | HU | ID `9348xxx`; começa com Gross Salary em 58008; flag Mother<30 em 58205; idade contra `$period.begin_date` | Padrão universal; slot livre no WTC | Suman / Mohit | [T-2026-05-26] |
| 2026-05-26 | HU | Isenções complexas por declaração (empregado declara, empregador aprova, sistema aplica); só o término é automatizado | Evita assertions com várias condições | Manju ("authoritative") | [T-2026-05-26] |
| 2026-05-27 | HU | Dependente no dependent screen conta como declarado. Flags 0/1 em ordinais anteriores; a isenção credita contra 58008. Under-25 com idade no fim do período | Separa condição de cálculo | Suman / Manju | [T-2026-05-27] |
| antes de 2026-05-27 | HU | Módulo de pagamento de benefício de SS pelo empregador (100+ empregados) **não** será construído; entra como input de gross | Escopo do produto | Marko Taylor + compliance | [T-2026-05-27] |
| 2026-05-29 | HU | Nacionalidade/residência numa flag única reusada (`$58218`, igual ES). Under-25 aplicado por padrão com flag de **opt-out** | Não replicar lógica; regra legal | Suman / Manju | [T-2026-05-29] |
| 2026-06-03 | CL | Comissão AFP: 1 regulação, 7 bands, assertion por código de AFP, taxa na band (sem 52xxx e sem 58212) | Uma AFP por empregado | Ruchi Gupta | [KB_Chile_Design_Decisions.md] |
| 2026-06-03 | CL | Reliquidação Art. 46 manual em steps (sem suporte nativo); vale para qualquer bônus multi-mês | Engine | Ruchi | idem |
| 2026-06-03 | CL | UF/UTM/IMM entram todo mês à mão em HR field da legal entity (`$legal_entity_hr.uf_eom/utm/imm`) | Sem integração | Ruchi | idem |
| 2026-06-03 | CL | `gratificacion_method` na legal entity (1 = Art. 50, 2 = Art. 47); dois caminhos por assertion | Escolha do empregador | Ruchi | idem |
| 2026-06-03 | CL | APV-B: SS sobre o bruto; APV-B + contribuições EE em intermediária 58xxx que reduz só o IUSC | Padrão existente | Ruchi | idem |
| jun/2026 | CL | IUSC em 3 passos (BTM→UTM 58121; lookup 58122/58123; posting 2552), sem `differential`; excesso ISAPRE em 1 reg com 2 bands (9152081); Art. 47 com 1 step YTM (`$58120.ytm`) | Orientação do dev | Ruchi | [CL_Regulation_Design_v1.0.md] |
| 2026-06-16 | EG | SS mantém decimais, sem FLOOR. A lacuna apontada em 06-11 (FLOOR por ramo no CCG) não será tratada | Configuração atual confirmada | Mohit + Manju | [T-2026-06-16_18] |
| 2026-06-16/18 | EG | ≥60 anos fora de old-age/disability/death. Elegibilidade por **ineligibility flag** (default 0). Joiner `58203` suprime o SS no mês de entrada. Base SS = todas as earnings. Personal exemption anual só para residentes (floor = ceiling). Severance/PILON isentos (nova conta 62929). Private insurance fund 15% do net revenue (conservador) | Regras de design | Time de design / Mohit | [T-2026-06-16_18] |
| 2026-06-18 | ES | Redesign de ~40%. `52560` combina IT+IMS por CNAE. Floor/ceiling SS anuais | Gaps apontados pelo implementation expert | Mohit | [KB_Spain_Regulation_Design_v2.md; T-2026-06-16_18] |
| s.d. | ES | `58197`/`58198` só para o BASES L03. CRA de severance 62180/62181: 0001 → 0054. PEs 65816–65849 remapeados no M190 (L/24 e exclusões) | Requisitos de relatório | Lily Li | [KB_Spain_DevTeam_Questions_And_Reports.md] |
| s.d. | ES | `PROJECT_VARIABLE = MAX(0; var_ano_anterior − var_YTD)` | Dupla contagem; Art. 83.2/87 RIRPF; DGT V0131-26 | Compliance (HRBS-10121) | [KB_Spain_Research_Artifacts_v2.md] |
| s.d. | ES | DD v3.7: `extra_pay_month_1/2/3` e `employment_status` no lugar de number_of_extra_pays/remaining/board_of_directors. DD v3.6 tira os códigos SEPE derivados. DD v3.2 tira campos "not user input" | Exigências do design v2 | Pesquisa + dev | idem |
| 2026-06-25 | TD | Piso CNPS fixo, sem proração. Classe de risco AT/MP só metadado; taxa fixa de 4% | RA default; correção M2 | RA | [TD_Regulation_Design_v1_0.md] |
| 2026-07-02 | TD | IRPP numa regulação Differential anual (÷12 automático). Teto de dedução numa ceiling account calculada. Reconciliação de flags MTD no ordinal 1 e de passivos no 301 | Cross-training de 07-02 | Mohit | idem |
| 2026-07-07 | TD | Retirar 9148041/58126 (teto de 5.000/filho): o Art. 45-4° não tem teto. Base TFE/TAFP literal do Art. 189 (sem 58125/58127). Base NR 18% = 58008. Pre-tax de aposentadoria só "caractère obligatoire" (Art. 47-II). Severance indenizatória fora da TFE. Forfait BIK do Art. 46 sobre a base em dinheiro. Escala de garnishment é tarefa do RA | Pesquisa primária (CGI 2025, LFI, CdT 1996) | Pesquisa (Claude/RA) | [TD_Regulation_Design_v1_0.md; TD_Statutory_Research_CCG_Positions.md] |
| 2026-07-10 | CL | Retro: SS parcial, tax 100% (falta testar) | Encerrar questão antiga | Ruchi + Mohit | [T-2026-07-10] |
| 2026-07-14 | RO | Dados de medical leave/work accident do D12 fora do escopo de payroll (labor law) | Não é processamento de folha | Mohit, Enaakshi (Marko a confirmar) | [T-2026-07-14] |
| 2026-08-14 | CI | Pontuar a v1.0 (não a v1.1), sem razão por contagem | Comparável com IE/TD | Autor do score | [CI_Accuracy_Score_v2.md] |
| 2026-08-25 | CI | Cap de previdência privada 320.000: anual e cumulativo | CCG | Mohit | [T-08-25] |
| s.d. | CI | Reconciliação dirigida por flag (58206) em vez de retro | Retro de componente único é impraticável | Mohit | [FR-pack] |
| 2026-08-26 | FR | Escopo travado no régime général privado. Fora: RATP, ENIM, CNBF, CRPCEN, CAVIMAC, CNIEG/CAMIEG, MSA, SSI/TNS, fonctionnaires, A1 inbound, Mayotte, LODEOM. Dentro: Alsace-Moselle e DOM (só PAS); mandataires sem chômage/AGS | Regimes especiais não pesquisados | Scope owner Wallisson | [07-qa-report.md] |
| ~2026-08-27 | FR | PASRAU/NEORAU fora (FR-DGFIP-006). Art. 197 A não modelado. SIPSI fora (o manifest prevalece sobre o CCG M10) | Nível de lançamento; obrigação do receptor | Build / QA | [01-ccg.md; 07-qa-report.md] |
| 2026-08-27 | FR | Não adicionar ao DD as linhas "sem contraparte". Share schemes S89 (30 rubriques) fora, sinalizados ao owner. Contract Nature 60 pendente com o owner; 32 e 80 excluídos | Adicionar campo é mudança de escopo (Stage 4) | Wallisson (patch) | [07-qa-report.md; 05-data-dictionary.md] |
| 2026-08-27 | FR | Colunas laranja do WTC (D, H, I, K, L, M, V, W) vazias para o dev. Justificativa Yes-No na col. F ("YES-NO JUSTIFICATION:"). Coluna "Notes" nos mappers do DD. Coluna E das specs mantida | Precedente BE; checks C3/C14 | Build | [02-wtc.md; 05-data-dictionary.md; 07-qa-report.md] |
| 2026-08-27 | FR | DPAE formato 120 como alvo; modelo concentrateur para DSN/DPAE. Model A DGFIP-EDI (74 pessoa-dia) é só recomendação: decidir no nível do portfólio | Esforço e SLA | Runbook | [03-sir.md] |
| 2026-08-28 | FR | m-3 (verde do net pay) não é corrigido só na FR | BE/TN usam navy; escalar ao standard owner | QA | [07-qa-report.md] |
| ~2026-08-28 | FR | Reconciliação progressiva do teto como default. Flags booleanas 1/2 (sem EQUALS 0). SMIC vivo e congelado em contas separadas (52572/52573). `_monthly` na 9250021. IDCC como flag sem override. ID interno derivado `$<entity>.<field_id>` com tag [DERIVED] | CCG M1.3; CT-A-264; Master DD v1.5 | Wallisson | [FR-pack] |
| — | FR | Payslip no modelo simplificado (Arrêté 25/02/2016 alterado em 31/01/2023); não antecipar o modelo novo | Adiado para 01/01/2027 | Build | [06-payslip.md] |

## 4. Valores e regras estatutárias definidos

> Os valores vêm como estão registrados nos docs. As transcrições trazem valores ditados em reunião: veja os `[INCERTO]`.

### FR (2026) [01-ccg.md; 02-wtc.md; 06-payslip.md; 05-data-dictionary.md]

| Item | Valor | Vigência | Fonte citada |
|---|---|---|---|
| PASS | 4.005/mês; 48.060/ano; 12.015/tri; 220/dia; 30/h (2025: 3.925/mês) | 2026 | Arrêté 22/12/2025 |
| SMIC | 12,02/h, 1.823,03/mês, a partir de 01/01; 12,31/h, 1.867,02/mês (+2,41%), a partir de 01/06 | 2026 | L3231-1; Décret 1/6/2026 |
| SMIC congelado para a RGDU | 21.876,40 o ano todo (12,02 × 1.820) | 2026 | Décret 2026-509 |
| Minimum garanti | 4,22 → 4,35 (01/06) | 2026 | — |
| SMIC Mayotte | 9,56/h | 01/06/2026 | — |
| SMIC de menores e aprendizes | <17: −20%; 17–18: −10%; aprendizes 27–78% | — | D3231-3; D6222-26 |
| Contribuições EE | Velhice plafonnée 6,90% / déplafonnée 0,40%; Agirc-Arrco T1 3,15% / T2 8,64%; CEG 0,86/1,08%; CET 0,14%; Apec 0,024%; Alsace-Moselle 1,30%; CSG dedutível 6,80% / não dedutível 2,40%; CRDS 0,50% | 2026 | CSS; ANI 17/11/2017 |
| Contribuições ER | Saúde 13,00%; velhice 8,55/2,11%; família 5,25%; AT/MP taxa do estabelecimento; CSA 0,30%; FNAL 0,10% (<50) ou 0,50% (≥50); AA 4,72/12,95%; CEG 1,29/1,62%; CET 0,21%; Apec 0,036%; chômage 4,00%; AGS 0,25%; diálogo social 0,016%; prévoyance cadre 1,50% T.A; versement mobilité = taxa local (≥11 empregados) | 2026 | CSS; UNEDIC 15/11/2024 |
| Taxas reduzidas de 7% (saúde) e 3,45% (família) | Revogadas, absorvidas pela RGDU | 01/01/2026 | — |
| Tranches | T1 0–4.005; T2 até 8 PASS (32.040); chômage até 4 PASS (16.020); abatimento CSG 1,75% até 4 PASS | 2026 | L136-1-1 |
| RGDU | C = Tmin + Tdelta × [0,5 × (3 × 21.876,40 / bruto anual − 1)]^1,75; Tmin 0,0200; Tdelta 0,3781 (FNAL 0,10%) ou 0,3821 (FNAL 0,50%); máx. 0,3981 / 0,4021; 4 casas; corte abrupto em 65.629,20; fração AT 0,49 | 2026 | L241-13; D241-2-4; Décrets 2025-1446 / 2026-509 |
| Horas extras | +25% (36ª–43ª), +50% (44ª+); contingente 220 h; isenção IR 7.500/ano; alívio EE até 11,31%; dedução ER 1,50/h (<20) ou 0,50/h | 2026 | L3121-36; 81 quater CGI; LFSS 2025-1403 |
| Horas complementares | +10% até 1/10; +25% acima | — | L3123-28 a 31 |
| Grade PAS, 01/01 a 30/04/2026 | 20 faixas, de 0% (<1.620) a 43% (≥55.062) | Jan–Abr | BOI-BAREME-000037 |
| Grade PAS a partir de 01/05/2026 (+0,9%) | 0% <1.635; 0,5% até 1.697,99; 1,3% até 1.806,99; 2,1% até 1.927,99; 2,9% até 2.059,99; 3,5% até 2.169,99; 4,1% até 2.314,99; 5,3% até 2.737,99; 7,5% até 3.134,99; 9,9% até 3.570,99; 11,9% até 4.018,99; 13,8% até 4.689,99; 15,8% até 5.623,99; 17,9% até 7.036,99; 20% até 8.788,99; 24% até 12.199,99; 28% até 16.522,99; 33% até 25.936,99; 38% até 55.557,99; 43% acima. DOM começa em 1.875 (GP/MQ/RE) e 2.008 (GF/YT). A grade aplicada segue a data de pagamento | 01/05/2026 | LOI 2026-103; BOI-BAREME-000037-20260407 |
| Abatimento contrato curto (≤2 meses) | 748 → 766 (01/06) | 2026 | — |
| Escala IR anual por parte (fora da folha) | 0% até 11.600; 11% até 29.579; 30% até 84.577; 41% até 181.917; 45% | rendas 2025 | LF 2026 art. 4 |
| Não residente (182 A) | 0% até 17.275; 12% até 50.112; 20% acima (mensal 1.440 / 4.176); DOM 8% e 14,4%; dedução fixa 10% | 2026 | 182 A CGI |
| Art. 197 A (não modelar) | 20% até 29.579; 30% acima | — | 197 A CGI |
| Arredondamento | Linhas com 2 casas; URSSAF e PAS remetidos em euro inteiro; nominativos da DSN sem arredondar | — | L130-1; 204 H; R242-2 |
| Prazos | DSN dia 5 (≥50) ou 15; PAS dia 8 ou 18; DPAE até 8 dias antes do início; sinal de evento em 5 dias; DAT em 48 h; DOETH e saldo TA na DSN de abril; SOLTéA 26/05–21/10/2026 | 2026 | R243-6; L1221-10 |
| Taxe sur les salaires | 4,25 / 8,50 / 13,60%; anual <4.000; trimestral 4.000–10.000; mensal >10.000 | 2026 | 231 CGI |
| Taxas patronais | TA 0,68% (A-M 0,44%); saldo TA 0,09%; CFP 0,55% / 1,00%; CPF-CDD 1%; PEEC 0,45%; forfait social 8/10/16/20%; penalidade sênior 1% | 2026 | — |
| Rescisão | Indemnité légale 1/4 de mês por ano até 10 anos, 1/3 depois (mín. 8 meses de casa). Isenção IR = maior entre legal, 2× bruto ou 50%, limitada a 6 PASS (288.360). SS isenta até 2 PASS (96.120). Tudo perdido acima de 10 PASS. Contribuição ER sobre rupture conventionnelle 40% (antes 30%). Fim de CDD 10%. Aviso 1 mês (6m–2a) ou 2 meses | 2026 | R1234-2/4; 80 duodecies; L137-12 (LFSS 2026 art. 15) |
| BIK | Refeição 5,50; moradia 79,70–225,60 por cômodo; veículo (≥01/02/2025) 15% / 10% (20% / 15% com combustível), leasing 50% (67%); elétrico com abatimento 70% até 4.641,60/ano; NTIC 10% | 2026 | Arrêté 10/12/2002 alt. 25/02/2025 |
| Isenções | Ticket-restaurant 7,32; transporte 50% obrigatório; forfait mobilités 600 (900 combinado); PPV 3.000 / 6.000 (regime ampliado até 31/12/2026); intéressement/participation 36.045; estágio 4,50/h; DFS teto 7.600 | 2026 | 81 CGI; L3261-2; Lei 2022-1158 |
| Previdência complementar | Social: saúde + prévoyance 6% PASS + 1,5% da remuneração, limitado a 12% PASS; aposentadoria máx(5% PASS; 5% da remuneração). Fiscal art. 83: prévoyance 5% PASS + 2%, limitado a 2% de 8 PASS; aposentadoria 8% | 2026 | D242-1; 83 CGI |
| Penhora | 1/20 até 373,33 … integral acima de 2.150,83; +145/dependente; protegido 651,69 | 2026 | Décret 2025-1299 |
| Doença | IJ 50% de (bruto 3m / 91,25), base limitada a 1,4 SMIC; máx. 41,95 → 42,97 (01/07); carência 3 dias; complemento ER 90% por 30 dias + 66,66% por 30 dias; carência ER 7 dias; AT/MP 60% → 80%; maternidade máx. 104,02; CSG sobre IJ 6,20% | 2026 | L1226-1; D1226-1 |
| Férias e licenças | 2,5 dias ouvrables/mês (máx. 30); licença médica acumula 2 dias/mês até 24; regra 1/10 × manutenção. Maternidade 16/26/34/46 semanas; paternidade 25 (32) + 3 dias; congé supplémentaire de naissance a partir de 01/07/2026 | 2026 | L3141-3; Lei 2024-364; Lei 2026-492 |
| Ações (L137-13/14) | ER 30% (antes 20%, aquisições desde 01/03/2025); EE 10% acima de 300.000 | 2026 | L137-13/14 |
| Retenção de documentos | Holerite papel 5 anos; eletrônico 50 anos ou até os 75 anos; DSN 6 anos | — | L3243-4; D3243-8 |

### ES (2026) [KB_Spain_Research_Artifacts(_v2).md; KB_Spain_Regulation_Design(_v2).md]

| Item | Valor | Fonte citada |
|---|---|---|
| Escala IRPF | 19% até 12.450; 24% até 20.200; 30% até 35.200; 37% até 60.000; 45% até 300.000; 47% acima (differential) | CT-A-491 / CCG |
| Não residente | UE/EEE 19%; resto 24% | CCG |
| Beckham | 24% até 600.000; 47% acima (ordinais 596–616) | CCG |
| Board of Directors | 35%, ou 19% com faturamento <100K (ordinal 621) | Design v2 |
| Bônus irregular | Redução de 30% | Ordinal 441 |
| Reduções e mínimos | Dedução padrão 2.000. Low income reduction: 7.302 até 14.852, com fase de redução até 19.747,50. Mínimo pessoal 5.550 (+1.150 >65; +2.550 >75). Deficiência 3.000–12.000. Descendentes 2.400/2.700/4.000/4.500 (+2.800 <3 anos). Ascendentes 1.150/2.550 | CCG / CT-A-490 |
| Taxa de regularização | Truncada em 2 casas | CCG |
| Zero Tax Floor | FS1 17.644 / 18.694. FS2 17.197 / 18.130 / 19.262. FS3 15.876 / 16.342 / 16.867. [INCERTO] o design v1 cita 17.179 | CCG |
| Planos de pensão | Teto EE = menor entre 1.500 e coeficiente (×2,5 / 1.250+0,25× / ×1,0); 1:1 com bruto >60.000 | CCG |
| Regime foral | Álava = Bizkaia; Gipuzkoa ≈; Navarra própria. Roteamento por province_code 01/48/20/31 | CCG |
| Isenções | Meal voucher 11/dia; seguro saúde 500 (1.500 com deficiência); transporte 1.500/ano; km 0,26; stock options 12.000/ano; dietas 53,34 / 26,67 / 91,35 / 48,08 | Design v2 |
| SS | CC EE 4,70 / ER 23,60; MEI 0,15/0,75; desemprego indefinido 1,55/5,50 e prazo 1,60/6,70; FOGASA 0,20; FP 0,10/0,60; estagiário 2/7; HE força maior 2/12, padrão 4,7/23,6, máx. 80 h/ano; contrato <30 dias +40% CC ER; board sem desemprego e sem FOGASA | CCG |
| Quota de solidariedade | 0,19/0,96; 0,21/1,04; 0,24/1,22 (faixas do excesso 0–10%, 10–50%, >50%) | CT-A-492 / CCG |
| Bases | G1 1.929,00; G2 1.599,60; G3 1.391,70; G4–7 ~1.424,50 (provisório); teto 5.101,20; diárias 47,48–170,04 | CCG |
| Mínimo part-time por hora | v1.0: 11,62/9,64/8,38/8,32 → v1.3: **11,98/9,94/8,65/8,58** | Orden PJC/297/2026 |
| AT/EP Cuadro II | a 1,50; b 2,00; d 6,70; f 6,70; g 3,60; h 3,60; sem CNAE → maior taxa | CCG v1.3 §5.1.3 |
| IT | Dias 1–3 nada; 4–15 empregador; 16+ SS; recaída em até 180 dias | CCG §8.2.1 |
| Pagas extras / proração | SS rateada em 1/12 (zero SS no mês do pagamento); G1–7 divisor 30; G8–11 dias reais | CCG |
| Prazos | RED/SILTRA dia 20 (fev/dez) ou 22 de M+1; sobretaxa 10%/20%; M111 dia 20 ou trimestral; M190 31/jan; corte do débito direto dia 15 | CCG |
| Penhora | Inembargável = SMI 1.184; 0/30/50/60/75/90% por múltiplo do SMI; 3 tabelas | CT-A-493..495 |

### CL (2026) [KB_Chile_Research_Artifacts.md; CL_Regulation_Design_v1.0.md]

| Item | Valor | Fonte citada |
|---|---|---|
| UF / UTM / IMM (jan/2026) | 39.706 / 69.265 / 539.000 (IMM pode ter 2º degrau em jul/2026) | BC / SII / Ley 21.578 |
| Tetos | SS 89,9 UF (≈3.569.576); AFC 135,1 UF (≈5.364.581) | — |
| AFP | 10% EE. Comissões: Uno 0,46; Modelo 0,58; PlanVital 1,16; Habitat 1,27; Cuprum/Capital 1,44; ProVida 1,45. Códigos: 03 Cuprum, 05 Habitat, 08 ProVida, 29 PlanVital, 33 Capital, 34 Modelo, 35 Uno | — |
| Saúde / AFC | FONASA 7%; ISAPRE 7% pré-imposto, excesso pós-imposto. AFC EE 0,6% (indefinido); ER 2,4% indefinido / 3,0% demais | — |
| Encargos ER | SIS 1,54%; Mutual 0,90% + DS67 0–3,4%; SANNA 0,03%; CCAF EE ~0,6% | Ley 16.744; DS 67; Ley 21.063 |
| APV-B | Até 50 UF/mês e 600 UF/ano; reduz IUSC, não SS. APV-A pós-imposto, bônus 15% | — |
| IUSC (UTM) | 0% até 13,5; 4% até 30 (ded. 0,54); 8% até 50 (1,74); 13,5% até 70 (4,49); 23% até 90 (11,14); 30,4% até 120 (17,80); 35% até 310 (23,32); 40% acima (38,82) | Art. 43 LIR |
| Outros | Imposto adicional NR 35%; Art. 55 bis até 8 UTA; gratificación Art. 50 = MIN(25%; 4,75 IMM ÷ 12) ≈ 213.479/mês; Art. 47 = 30% do lucro; asignación familiar A 22.007 / B 13.505 / C 4.267 / D 0; zona extrema ~40%; piso de penhora 56 UF; ordem de 8 descontos; divisor 30; HE 1,5× (jornada 44 h → 42 h em 01/04/2026 → 40 h em 2028); IAS até 990 UF; Previred dia 10/13; F29 dia 12/20; LRE dia 15 | LIR; CdT; DFL 150; DL 889; Ley 21.561 |

### BW, BG, IE

| País | Item | Valor | Fonte citada / Doc |
|---|---|---|---|
| BW | Ano fiscal | 1/jul–30/jun | [KB_Botswana_Full_Package.md] |
| BW | PAYE residente | 0% até 48.000; 5% até 84.000; 1.800 + 12,5% até 120.000; 6.300 + 18,75% até 156.000; 13.050 + 25% acima | idem |
| BW | PAYE não residente | 5% até 84.000; 4.200 + 12,5%; 8.700 + 18,75%; 15.450 + 25% | idem |
| BW | Pensão / gratuity / SS | Pensão MIN(real; 15%) pre-tax; gratuity 1/3 isento; sem SS (BOTA 52534, WC 52564); anualização YTD × 12 / meses | idem |
| BG | Base segurável | Piso 620,20; teto 2.111,64/mês | [KB_Bulgaria_Design_BG_Design_and_JSON.md] |
| BG | Contribuições | DOO 6,58/8,22 (cat. 3: 2,20/2,80); PPF ER 12% / 7%; Teachers 4,3%; UPF 2,20/2,80; GDM 1,40/2,10; desemprego 0,40/0,60; NHIF 3,20/4,80; TZPB 0,40–1,10%; GVRF 0% | idem |
| BG | PIT e alívios | PIT 10%; por filho 3.067,75 (6.135,50 com deficiência); voluntário até 10%. Deficiência: [INCERTO] 3.930 (design) vs 660/mês = 7.920/ano (análise) | idem; [KB_Bulgaria_Design_Pattern_Analysis.md] |
| BG | Arredondamento SS | 2 casas por componente | CCG 1.5 |
| IE | PAYE / USC | Taxas via RPN. PAYE 20/40% (emergência: 110 = 20/40; 120/130 = 40% fixo). USC 0,5/2/3/8% (8% acima de 42.662) | [IE_Regulation_Design_v1.0.md] |
| IE | PRSI | EE 4,1%. Subclasses AO ≤352 / AX / AL / A1 >527. Crédito MAX(0; 12 − (sem − 352)/6). ER 8,9% / 11,15% / 0,6% | idem |
| IE | Pensão / PHBS | Pensão até 115.000 × % por idade (15–40%); PHBS 10% | idem |

### HU (hu_2026)

| Item | Valor | Fonte |
|---|---|---|
| PIT / SS EE / Szocho | 15% / 18,5% (pensionista 8,5%) / 13% ER, inclusive sobre BIK | [SR-A-1.md; SR-A-5.md; T-2026-05-29] |
| Composição dos 18,5% | [INCERTO] Em 27/05: "pension ~10 + health ~7 + 1,5". Em 29/05: "15 + 4 aprox." Não fecham | [T-2026-05-27; T-2026-05-29] |
| Tetos de isenção | <25 anos 8.589.180; deficiência 1.291.200; 1º casamento 400.020; healthcare 147.600 (floor = ceiling) | [SR-A-5.md] |
| Family allowance por dependente | Solo 133.340 / 266.660 / 440.000; conjunto 66.670 / 133.330 / 220.000. Crédito não usado convertido a 15% | [SR-A-1.md; SR-A-5.md] |
| Family allowance (transcrição) | [INCERTO] 10.000 / 20.000 / 33.000 por filho, "a verificar". Conflita com SR-A. Crédito de SS = 50% de max(0; FA − base PIT) | [T-2026-05-29] |
| SZÉP / habitação / EMJ | BKJ 450.000; Aktív 120.000; habitação <35 anos 1.800.000; EMJ base ×1,18 → 17,7% + 15,34% | [SR-A-1.md; SR-A-5.md; T-2026-05-29] |
| Piso SS | 96.840 (30% do mínimo, por dia) | [SR-A-5.md] |
| Crédito Szocho | 503.568 / 251.784; trabalhador não qualificado 50% | [SR-A-1.md] |
| Regras de isenção | 3+ filhos: 3º filho nascido ≥01/10/2025. 4+: mães. Mothers turning 40: portão anual, que amplia a cada ano. <30: mulher com ≥1 filho. Nacionalidade HU/EU/EEA/UA/RS **e** residente fiscal (EU não residente só com ≥75% da renda húngara) | [T-2026-05-26..29] |

### Outros países

| País | Item | Valor | Fonte |
|---|---|---|---|
| EG | SS | Old age 9/12; sickness 1/3,25; work injury só ER; sem unemployment; ≥60 só sickness/WI (1/4,75); base = todas as earnings; floor/ceiling mudaram (taxas não) | [T-2026-06-11; T-2026-06-16_18] |
| EG | Personal exemption / fundo privado / severance | [INCERTO] 15.000 vs 15.250 por ano, só residentes. Fundo 15% do net revenue, cap 10.000/12 por mês. Severance/PILON isentos | [T-2026-06-16_18] |
| TD | IRPP-TS anual | 0% até 800.000; 10,5% até 6M; 15% até 7,5M; 20% até 9M; 25% até 12M; 30% acima. 1/12 do anual | Art. 1-IV / 122 CGI [TD_Regulation_Design_v1_0.md] |
| TD | NR / CNPS / TAFP / TFE | NR 18% final (Art. 116). CNPS EE PVID 3,5%; ER PVID 5 + PFM 7,5 + AT/MP 4. Piso 60.000 / teto 500.000 por mês. TAFP 1,2%. TFE 7,5% | Art. 116; Guia CNPS; Art. 173–190 CGI |
| TD | Isenções | Transporte até 30% do base; frais d'emploi até 15% da masse globale; abono familiar sem teto (Art. 45-4°); plan-social isento; aposentadoria pré-tax 3,5% (obrigatório); jovem graduado 60 meses (<35 anos na admissão); deficiência isenta de IRPP | Art. 3, 45, 47 CGI |
| TD | Forfaits BIK (sobre 58105) | Moradia 20; veículo 10; alimentação MIN(15%; 75.000); interior 5; doméstico 4; eletricidade 4; água 4; telefone 3; gás 2. CNPS usa o valor real | Art. 46 [TD_Design_Comparison…; T-2026-07-07] |
| TD | Teto família 5.000/dependente | Afirmado pelo Mohit, **sem base legal** (é o valor CNPS de CI) | [T-2026-07-07; TD_Statutory_Research…] |
| TD | Arredondamento (produção) | FLOOR(x+0,5); base TAFP em múltiplos de 1.000 (para baixo); imposto TAFP na dezena | [TD_Design_Comparison…] |
| TD | Exemplo validado | Base 350.000 → PVID EE 12.250; IRPP 28.464; ER ≈ 88.200 | CCG M12 |
| CI | Cap de previdência privada | 320.000 anual, cumulativo | CCG [T-08-25] |
| TR | SS, teto e crédito do salário mínimo | [INCERTO] SS ~24,75 / 23,75; teto ≈ 297.270; crédito ~4.211 (resultado conciliado 139.527) | [T-2026-07-16] |
| LB | Proração SS | Base fixa de 30 dias | [T-2026-06-25] |
| India | HRA | MIN(HRA; aluguel − 10% do salário; 40% / 50% metro) | [T-2026-05-22] |
| IN | Regulations do WTC Display | Tax: 9356046 (566 PEs) / 9356051 (60). SS: 9356631 ESI (111). Pre-tax: 9356071, 136, 156, 176, 196, 201, 204 | [Global_WTC_Taxability_Display.xlsx] |
| GB | DD 2026/27 | Ano 06/04/2026–05/04/2027; LEL default 542 [INCERTO vs £125 semanal]; levy 0,5% com allowance de 15.000; recovery 1,03 / 0,92; AE 5% EE / 3% ER; tax code 1257L [INCERTO, nota diz 2025/26]; NI H só <25; forçar C aos 66+; 17 letras NI; student loan planos 1/2/4 (+5) | [GB_Country_Data_Dictionary_v3.xlsx; Master DD v1.5] |
| NL | Config do prompt de Client Manual (sem fonte legal) | Exclusão por idade >67 nas flags WGA/PAWW/ZW-Flex/Aof/Wko/AWf; PAWW 0,10; 30% ruling 0,30 / 0,27; códigos de income relationship expirados 35 (2022) e 54 (2021); código 10 substituído por 21–24 | [Master AI Prompt for Creation of Client Manual.docx] |
| BG/Global | Contas | PIT 2552; pensão 2556/2566; saúde 2554/2564; desemprego 2555/2565; net pay `2610 + 1310 + 26100 + 26102 + 26105` | [KB_Global_Wage_Type_Catalogue_v1.0.md; KB_Mercans_Knowledgebase_Formulas.md] |

## 5. Erros e correções

| País | O que estava errado | O correto | Fonte | Onde aconteceu |
|---|---|---|---|---|
| FR | F-1: 264 linhas em 12 specs marcadas "NO DD COUNTERPART" (o manifest falava em 199 e chamava o e-mail de omissão genuína) | ≥156 têm contraparte, ~25 são CALC, o resto está fora de escopo. Refazer o join por nome + conceito. O e-mail já existe no DD | [07-qa-report.md] | Specs / manifest (join pela rubrique NEODeS) |
| FR | F-2: sem WT de BIK refeição e NTIC | Criar 4 WTs no padrão 62400/62410/62403 | idem | WTC |
| FR | F-3: SIPSI marcado "in scope" no CCG M10 | Fora de escopo; criar FR-MOL-001 | idem | CCG / manifest |
| FR | m-1: chave composta em só 53/90 linhas. m-2: arquivo DD com nome v1.0 e conteúdo v1.1 | Propagar a chave para as 90 linhas; renomear o arquivo | idem | Specs / DD |
| FR | "Description (NL)" nos cabeçalhos (resíduo da BE); 247 opções fora de escopo sem marca; `[provisional]` em 1.357 linhas; códigos 32/60/80 excluídos sem nome | "Description (FR)"; marca vermelha FFFFC7CE; 403 confirmadas e 952 com motivo; códigos nomeados | idem | Specs / DD |
| FR | QA das 12:21 deu 486/562 (86,5%) | 720/984 (73,2%); C13 53/90 | idem | QA anterior |
| FR | Manifest: DPAE "via net-entreprises", só XML; FR-DGFIP-003 em XML só outbound | Host da URSSAF; TXT 120 ou XML. DGFIP-003 é UN/EDIFACT INFENT DP nos dois sentidos | [03-sir.md] | Manifest |
| FR | Fontes secundárias: 50.122; faixa começando em 4.440,01; PASS derivado de "+2%" | 50.112; 4.480,01; usar o decreto (×1,02038) | [01-ccg.md] | Fontes externas |
| FR | Crítica 2.2: "não existe coluna de valor no mapper" | `local_value` existe no Master DD v1.5: conformar o DD FR | [FR-pack] | Crítica de pesquisa |
| FR | [INCERTO] Ex. 1 do FR-pack: bruto 2.915,50; contribuições 640,50; IR 126,61 | CCG M12/payslip: 2.800; 616,44; 4,10%; IR 94,06; líquido 2.089,50 | [FR-pack; 01-ccg.md; 06-payslip.md] | Alvo de validação do design |
| FR | [INCERTO] Diálogo social 0,016% também EE (CCG M5.1, WTC FR-019) | CCG M3, Ex. 1 e payslip: só ER | idem | Inconsistência interna |
| FR | [INCERTO] ÷151,67 (CCG M4.2, Ex. 6) | O payslip proíbe 151,67 e manda usar 151,6667 | idem | Inconsistência interna |
| FR | [INCERTO] Crítica cita WTC com 378 WTs e DD com 173 campos/53 mappers | Entregue: 374; 189; 54 | [FR-pack] | Provável versão anterior |
| FR | [INCERTO] CCG M10 cita "FR-NSSO / FR-FIN series" | IDs reais FR-DSN/URSSAF/DGFIP (resíduo da BE?) | [01-ccg.md] | CCG |
| FR | Prazo do 2502-SD: Vol. III-C diz 31/jan; impots.gouv e manifest dizem 15/jan | Não resolvido | [03-sir.md] | DGFiP |
| CG | Limiar de solidariedade anualizado (6.000.000); divisor fixo `12`; `_monthly` ausente; wildcards faltando (65%%%, 794%%, 6286/7/8%); 58204 usado como flag bilateral | 500.000 (valor em fórmula não é dividido); `$period_divisor`; `simple_tax_monthly`; wildcards incluídos; 58204 = "No Child" (0,5 parte), que falta no CCG CG | [FR-pack] | Design CG |
| CI | `_table` sobre "parts" (9384241) dava 44.000 para todos; intermediárias em 58201–229 (faixa de flags); defeito de 12× em faixas/pisos/tetos | Flag + fórmula; renumerar para 581xx; declarar valores anuais | [FR-pack] | Design CI |
| CI | ITS mensal × anual tratado como divergência | Resolvido a favor do Claude (CT-A-623 = mesmo valor × 12) | [CI_Accuracy_Score_v2.md] | Comparação |
| CI | v1.0 sem intern/apprentice/first-employment/senior officer nem o teto de 320k | Corrigido na v1.1 | idem | Design v1.0 |
| CI | Design de IA: contas erradas; flags, intermediates e bases trocados; fórmulas em "linguagem explicativa"; RICF via mapper | Distinguir tipos de conta; código executável com variáveis; Mohit usa fórmula por family parts | [T-08-25] | Design CI |
| CI | Flags string (`$hr.marital_status`, `transport_zone`, `benefit_in_kind_type`) | Chave numérica no mapper ou if/else (o engine só lê números) | [T-2026-07-14] | Design CI |
| EG | Flag joiner com `DATE_FORMAT(...;'MMdd')`: contratado em 13/04/2025 virava joiner em abr/2026 | `yyyyMMdd` | [T-2026-06-11] | Sessão de design |
| EG | Produção arredonda o total de SS, e o CCG pede FLOOR por ramo | Decidido em 06-16: manter decimais, sem FLOOR | [T-2026-06-11; T-2026-06-16_18] | Produção EG |
| EG | Label "stamp tax" no lugar de "gratuity" na UI | Limitação do SaaS (só display) | [T-2026-06-16_18] | UI |
| EG [INCERTO] | Fator de proporcionalização com 2 casas: erro de 70 num salário de 21.000 | ≥4 casas | [FormulaPrompt] | Exemplo do prompt |
| HU | Under-25 com idade no begin_date; nacionalidade só com `CONTAINS`; condição repetida em cada reg; lógica multi-condição na assertion | end_date; nacionalidade **e** residência (`$58218`, ex. `LESS($58218;2)`); flag única; flag 0/1 + `GREATER(SUM(58205);0)` | [T-2026-05-27; T-2026-05-29] | Design HU |
| HU | Under-40 com idade na data de início | Fim do período ou 31/12 (portão anual): **não resolvido** | [T-2026-05-27] | Design HU |
| HU | `$employee.years_worked` usado como idade | Conta desde a admissão; usar `$person.birth_date` | [KB_Mercans_Knowledgebase_Formulas.md] | Design HU |
| HU [INCERTO] | SR-A-5 diverge da SR-A-1: mantém bandas riscadas (9348055); omite a banda 8 de 9348021, a banda 7 de 9348059 e os regs 9348044–046 (GYED); contas 6035/2535 vs 6037/2537 e 6038/2538; "MUTLIPLY" em 9348053; 58130 com dois usos | Reconciliar | [SR-A-1.md; SR-A-5.md] | Conversão para artigo |
| IE / Global | Learning #2 "decompor imposto progressivo em Threshold/Base/Amount" | Uma reg `Differential`; a decomposição era específica do RPN | [T-2026-07-02; DevKB] | KB |
| IE | Design do Claude com 31 regs: faltavam o triplet, as regs Paid (9372611–661), Flag Reconciliation MTD (9372001), reconciliações 671/681, 3 bases de relevant earnings e 3 créditos | Produção tem 52 regs | [IE_Design_Comparison…] | Design IE |
| IE | Pontuação: a tabela soma ~84%, o resumo diz ~72% | 72% = ponto médio entre lógica 84% e contagem 60% | idem | Comparação |
| CL | Dependência circular na gratificación (ordinal 15 vs 281) | Não existe circularidade fora de gross-up: linearizar | [T-2026-07-02] | Design do Claude |
| CL | IUSC em 8 regs por faixa; reliquidação com 12 acumuladores | 3 passos; 1 step YTM | [CL_Regulation_Design_v1.0.md; KB_Chile_Design_Decisions.md] | v1.0 → v1.1 |
| CL [INCERTO] | A Parte 2 ainda lista as 8 regs; o resumo dos 3 passos diverge do detalhe; 58212 listada mas "não necessária"; assertion 9152301 com `MULTIPLY(1.439668;1000)` (escala?) | Não resolvido no doc | [CL_Regulation_Design_v1.0.md] | Design CL |
| BG [INCERTO] | Pattern #7 cita 52980 como taxa do TZPB; teto voluntário `$21640` (conta ou valor?); GVRF 6031/2531 sobreposto ao GDM | 52560 = taxa do TZPB; os demais a verificar | [KB_Bulgaria_Design_*] | Docs BG |
| BW | Band de 15% em 58101 (ordinal 11) | Propósito "needs verification" | [KB_Botswana_Full_Package.md] | Design BW |
| ES | KB v1: `58205` com dois usos; 58238/58215 trocados; 58233/58212 trocados; rótulos de desemprego invertidos | Corrigidos conforme o WTC v3.6 e o CCG | [KB_Spain_Research_Artifacts.md] | Extração de PDF multicoluna |
| ES | `PROJECT_VARIABLE` contava em dobro (projetava o ano anterior × meses restantes) | `MAX(0; SUBTRACT($58901;$59009))` | [KB_Spain_Research_Artifacts_v2.md] | CCG v1.0 → v1.1 |
| ES [INCERTO] | Ordinais 456/461 do design v2 ainda usam `ADD($58901;MULTIPLY($59009;12))` | Fórmula MAX acima. Correção em produção não confirmada | idem | Design v2 |
| ES | Floor SS prorrateado só pelos dias trabalhados; mínimos part-time desatualizados; 58550/58551 | Trabalhados + licenças (79006–79032); mínimos novos; renomeados para 58199/58194 | idem | WTC v3.3–v3.9 |
| ES | Teto errado no CCG; SS não deduzida da base IRPF; stock options e severance inconsistentes entre CCG e WTC; FS3 e mapper de deficiência faltando no DD; sem data de nascimento de ascendentes | 5.101,20; deduzir; demais apontados nos IDs 271/245/10/136/178/180/277 [INCERTO sobre a resolução final] | [KB_Spain_DevTeam_Questions_And_Reports.md] | CCG / WTC / DD |
| ES | "employee termination event HR" usado na tela de termination | "HR termination reason" | [T-2026-07-14] | Design ES |
| TD | Transporte como isenção total no WTC | Isento até 30%; o excesso é tributável e sujeito a CNPS | [TD_DevTeam_Critique_PreSubmission.md] | WTC v1.1 |
| TD | Teto de 5.000/filho no CCG e nas regs do dev (9148032/033) | Art. 45-4° não tem teto | [TD_Statutory_Research…] | CCG / design do dev |
| TD | Design do dev: frais de 15% ausente; jovem graduado com `>60` anos; aposentadoria `2164%` sem teto; `6218% No` em IRPP/TFE/TAFP; base NR bruta; base TFE/TAFP alinhada ao Art. 45 | 15% por empregado; 60 meses e <35 anos; teto 3,5% só obrigatório; severance ordinária tributável no IRPP; NR líquida do Art. 45; TFE literal do Art. 189 | [TD_Design_Comparison…; TD_Statutory_Research…] | Design de produção TD |
| TD | Design do Claude: delta única 58128 para BIK; isenção em MAX(0; excess); 58125/58127 na base TFE (dupla contagem); severance ordinária na TFE | Reg nocional por benefício; crédito negativo na intermediate; PEs brutos pelo valor cheio; excluir a parte indenizatória | [T-2026-07-07; TD_Regulation_Design_v1_0.md] | Design do Claude |
| TD | "Czechia Report" no DD; atestado de deficiência TELK (CCG) vs CNPS (DGI-001); cash-in-lieu como TD-BIK-A46 | Remover; reconciliar; TD-IRPP-PROG | [TD_Lista_Problemas_Pesquisa.md] | DD / CCG / WTC |
| TD [INCERTO] | A base 58105 do forfait inclui `65%%%`? | A comparação diz que sim; a pesquisa diz bruto em dinheiro | [TD_Design_Comparison…; TD_Statutory_Research…] | Design do dev |
| TR [INCERTO] | Crédito do salário mínimo tratado como redução da base de gross-up | É crédito contra o imposto, aplicado depois; com isso bate 139.527 | [T-2026-07-16] | Simulação |
| NL | Bug do 30% ruling (valor cumulativo ia para bônus); o Claude propôs redesign completo | Fix pontual | [T-2026-07-10] | Produção NL |
| TH | Option mapper alterado pelo integration team (Dayforce) quebrou o report TXT | Acesso restrito à compliance | [T-2026-07-14] | Produção TH |
| Iraq → Global | Revisão de design: falso "missing row" coberto por wildcard; "defeito" que era comportamento implícito do engine; split tratado como defeito sem rastrear o consumo; finding fechado com base em descrição verbal; exceção aplicada só a um membro de par estatutário | Regras novas do Review Prompt v2 | [PayrollDesignReviewPrompt_v2.md] | Revisão de Iraq (Federal + KRI) |
| Global | Datas comparadas como string crua | `DATE_FORMAT` com `yyyyMMdd` / `yyyyMM` / `'dd'` | [FormulaPrompt] | — |
| Global | `$employee_cost_center.*_cost_center_id` | Descontinuado: `$employee.primary_cost_center` / `secondary_cost_center` | [KB_Engine_Formula_Syntax.md] | — |
| Global | Tax Rule Groups vistos como valores atômicos "pendentes" | São combinações de componentes; catálogo fechado em 07-02 | [DevKB] vs [KB_Engine_Formula_Syntax.md §8] | KB |
| Global | Docs dizem que All Payroll serve para 52xxx e First Payroll para 58901 (Ruchi, 06-25) | Mohit: All Payroll obsoleto; First Payroll nunca usado | [T-2026-06-25; T-2026-07-02] | Conflito entre transcrições |
| Global [INCERTO] | Script "Upload Taxability Matrix" só converte 'Yes' → 1 (linhas com "1" viram não tributáveis); override de bands tira o ponto decimal | Validar antes de usar | [Country Settings Automation Scripts.docx] | Scripts |
| GB | DD: defaults de AE invertidos (EE 3 / ER 5); LEL 542 vs £125; tax code marcado 2025/26; Tax Basis default W1/M1 com exemplo Cumulative; mapper Fuel Code (A/D/F) e "Boolean" faltando; dropdowns prometidos no Cover e ausentes; campo "Password" | EE 5% / ER 3%; demais a confirmar | [GB_Country_Data_Dictionary_v3.xlsx] | DD GB v3 / v31 |
| Global | Master DD v1.5: diz "8 types" e lista 6; validadores usados sem catálogo (sum_equals, is_date, is_decimal, enum_lookup); gramática "v1.2" no Cover e "v1.1" na aba 09 | Alinhar | [Master_Data_Dictionary_Template_v1.5.xlsx] | Template |
| Global [INCERTO] | Contribution Pay Elements: Other loan 3, 27128 → 67118 (igual ao loan 2); descrições duplicadas (Social Fund ER, EIS ER, Medical) | Provável 67128 | [Contribution Pay Elements.xlsx] | Planilha |
| Global | Prompt JSON em .docx com tabelas quebradas | Usar o .md | [Regulation Design JSON Prompt.docx] | Conversão |

## 6. Padrões e método

### 6.1 Fluxo e papéis

- **Ciclo dos artefatos**
  - Sequência: CCG (pesquisa) → Design (dev) → DD/WTC atualizados. WTC e DD documentam o design; não são a origem dele. [KB_Spain_Research_Artifacts_v2.md; DevKB; 00_INDEX.md]
  - Vida de uma flag: o CCG identifica a necessidade → o DD define o campo → o WTC define `$hr.{code}` → o design referencia. [KB_Spain_Research_Artifacts_v2.md]
- **Fluxo do Mohit:** CCG + skill → lista de exceções → taxability matrix → IA gera WTC → IA gera DD. O fluxo WTC-first também é válido. [DevKB]
- **Contradições:** o Claude detecta contradições entre CCG, WTC e reports. Cada uma vai por e-mail ao dono da pesquisa (Wallisson). [T-2026-07-07]
- **Benchmarks de esforço:**
  - 15–25 regs ≈ 5 dias.
  - Chad ≈ 2 dias com IA.
  - Spain (~150 steps) até 2 meses.
  - Prompt de design ≈ 200–300 páginas de conhecimento; prompt de fórmula ≈ 50–60.

  [T-2026-07-02; T-2026-07-10; DevKB]
- **Limites da IA:**
  - Erra ou omite ~15% em pesquisa estatutária (TR e HU precisaram de retrabalho). [T-2026-06-16_18]
  - Claude é melhor em análise de documentos; Gemini às vezes é melhor em fórmulas. Usar IA para **testar** fórmulas, não para gerá-las. [T-08-25; T-2026-06-11]
  - Alimentar com a pesquisa completa, não com resumos. [T-2026-07-10]
- **Onboarding:** percorrer um design real ordinal por ordinal, com o trainee explicando de volta. [T-2026-07-07]
- **Deploy:** reescrito à mão em produção depois do acceptance. O Andre faz os deploys de país inteiro. [T-2026-05-22]
- **Uso do YouTrack com Claude:** KB → país → ⋮ Export as Markdown (com sub-artigos) → Claude. Para país novo: gerar o design e depois reconciliar com o real. [T-2026-07-02; TD_Design_Comparison…]

### 6.2 IDs, ordinais e contas

- **Regulation ID:** `9` + ISO numérico + ordinal de 3 dígitos.
  - Exemplos: BG 9100, BW 9072, TD 9148, CL 9152, FR 9250, HU 9348, IN 9356, IE 9372, CI 9384, ES 9724.
  - Ordinais vão de 10 em 10 a partir de 11 (1–10 reservados).
  - Nome = prefixo do país + descrição. Tax year `<cc>_2026`.

  [00_INDEX.md; CL_Regulation_Design_v1.0.md; T-2026-05-26]
- **Faixas de conta**

  | Faixa | Uso |
  |---|---|
  | 58008 | Gross taxable |
  | 581xx | Intermediárias |
  | 582xx | Flags (58205–58299) |
  | 585xx | Acumuladores |
  | 52xxx | Taxas |
  | 53xxx | Tabelas |
  | 645xx / 63xxx | Notionals / units |
  | 62xxx | Earnings (62100 = salário base) |
  | 65xxx | BIK |
  | 794xx | Leave payout |
  | 99999 | Sink nocional |
  | 99998 | Sink de `_period` |
  | 9999 | Balanceamento |
  | 2610 | Clearing do líquido |
  | 21xxx | Espelho de dedução |
  | 25xxx | EE |
  | 81–87xxx | YTD (`8` + prefixo) |

  [FR-pack; KB_Bulgaria_Design_Pattern_Analysis.md; KB_Global_Wage_Type_Catalogue_v1.0.md; T-2026-05-26]
- **Contas fixas:** 2552 PIT; 2554/2564 saúde; 2555/2565 desemprego; 2556/2566 pensão; 2572 imposto secundário; 2592 NR; 2597 penhora. 58901/58911 = empregador anterior (P16). [KB_Global_Wage_Type_Catalogue…; CL_Regulation_Design…; KB_Botswana…]
- **Séries canônicas:** uma série por conceito em todos os países (ex.: meal 6286x). Quando a taxabilidade diverge, documenta-se a exceção em vez de trocar de série; trocar quebra o report mapping. Regra #1: trabalhar por série, não por elemento. [T-2026-07-02; T-2026-07-07]
- **Pay elements:** em trinca (base / Arrears / Adjustment). [FR-pack]

### 6.3 Estrutura da regulação e engine

- **Três seções**
  - Form Data (ID, Name, Country, Currency, Taxation Type, Tax Group, TRG, Assertion, Ordinal).
  - Matrix.
  - Bands, com 18 colunas em ordem fixa. Os prompts JSON trabalham com 15 + creditAmount. [Youtrack Knowledge Base Article.docx]
- **Taxation Type:** Flat / Formula / Differential. **Tax Group:** Income Tax / Social Security. [idem; T-2026-07-02]
- **Tax Rule Group**
  - É uma combinação de componentes: `_simple_tax`, `_table` (pega a band, sem progressão), `_monthly` (desliga a divisão), `_$` (gross-up), `_post_formula`, `_period` (off-cycle), `_retro`, `_ytm`, `_ytd`, `_ytd_only`, `_fixed`.
  - Combinações usadas: `retro_simple_tax`, `retro_simple_tax_period`, `simple_tax_ytm(_negate)`, `retro_simple_tax_post_formula`.

  [DevKB; KB_Bulgaria_Design_Pattern_Analysis.md]
- **Variáveis de resultado:**
  - Com Taxation Type = Formula, `$employee_taxable_amount` é a soma da matriz.
  - `$band_amount_raw` é taxa × matriz depois do floor/ceiling e antes da coluna Formula.
  - As variáveis de sistema são os nomes das colunas da band. [DevKB; T-2026-07-07]
- **Divisão automática por período:** só Income From/To, Floor e Ceiling, declarados **anuais**. `_monthly` interrompe a divisão. Valores dentro de fórmula não são divididos. [T-2026-06-11; T-2026-07-02; FR-pack]
- **Assertions:** a da regulação é o gate de elegibilidade; a da band escolhe a taxa (P6). Se a assertion falha, o step não roda. [T-2026-06-11; KB_Bulgaria…]
- **Várias bands numa regulação:** só se compartilham a mesma matriz. Base diferente exige outra regulação. [T-2026-06-11]
- **Ceiling:**
  - Amount (na band) vs account (vinda de flag ou step). MIN/MAX não é ceiling.
  - Floor = Ceiling é legítimo (devolve constante).
  - Cauda de acumulação para bases com teto: YTM → Cumulative → Ceiling → Reconciled. [DevKB; FR-pack]
- **Isenção:** postar no lado crédito da intermediate (valor negativo) e incluir na matriz. Não usar MAX(0; excess). [T-2026-07-07; T-2026-05-27]
- **Pre-tax:** intermediárias negativas −(SS) somadas na base de imposto (P4). Dedução reduz a base; crédito reduz o imposto depois do cálculo. [T-2026-06-16_18; T-2026-07-16]
- **Dependência circular:** só existe em gross-up. O gross-up itera ~50 vezes por elemento; não codificar caps na fórmula de gross-up. [DevKB; T-2026-07-16]
- **Flags**
  - Valores numéricos 0–4. O engine não lê string; usar if/else ou chave numérica.
  - Uma flag não lê o HR field direto.
  - Booleanos codificados 1/2; evitar `EQUALS(x;0)`; preferir GREATER/LESS (seguro em retro).
  - Minimizar o número de flags (performance).
  - `$58206` = `$entry.reporting_period.ordinal`. [T-2026-07-14; T-2026-04-20; FR-pack; T-2026-06-11]
- **Combinações de flags:** combinação não codificada retorna zero sem erro. Toda combinação precisa estar coberta. [T-2026-04-20]
- **Joiner e leaver**
  - Joiner: `GREATER(DATE_FORMAT($employee.hire_date;'yyyyMMdd'); DATE_FORMAT($period.begin_date;'yyyyMMdd'))`.
  - Leaver `58299`: LTE sobre a data de término.
  - Gate de idade: `YEARS_BETWEEN($person.birth_date; $period.end_date)`. [T-2026-06-11; T-2026-06-16_18]
- **Reconciliação**
  - Padrão: Regular + retro Single Period.
  - Retro types: All Periods, All Periods Full, Single Period, Current Period.
  - Não funciona em ciclo submensal. [T-2026-07-02]
- **Duas linguagens:** HRBliss (flags/WTC) e o engine G2N "Noah" (bands). [T-2026-06-11]

### 6.4 Sintaxe de fórmula [FormulaPrompt; KB_Engine_Formula_Syntax.md; KB_Mercans_Knowledgebase_Formulas.md]

- **Básico:** `;` como separador; proibido `+ - * /` (usar ADD/SUBTRACT/MULTIPLY/DIVIDE; ÷0 = 0); aspas simples; decimal com ponto.
- **SUM:** `SUM(79010)` sem aspas em pay element; `SUM('79010')` em dynamic report. `SUM('6210:6299')` para faixa e `SUM('6210+6240')` para lista.
- **Funções disponíveis:**
  - Lógicas: EQUALS, GREATER, LESS, GTE, LTE, AND, OR, NOT, IS_BETWEEN, IS_NULL, CONTAINS (valor exato do mapper).
  - Controle: IF, MIN, MAX, WITH.
  - Arredondamento: ROUND, FLOOR, CEIL.
  - Datas: DATE_FORMAT, DAYS_BETWEEN (inclusivo), YEARS_BETWEEN, ADD_MONTHS.
  - Texto: SUBSTRING, CONCAT, REPLACE.
  - Outras: CURRENCY, RANGE, WHEN.
  - WARNING e ASSERT só em dynamic report.
- **Sufixos de option mapper:** `::key`, `::orLabel`, `::orAndLabel`.
- **Variáveis:**
  - `$period`, `$payroll`, `$employee`, `$person`, `$job`, `$hr.{code}`, `$legal_entity_hr.{code}`, `${conta}.amount/ytm…`, `$entry.*`, `$child.[n]`, `$relationship.number_of_children`, `$termination`, `$employee_loan`.
  - Só em pay element: `$actual_prorata_days` e `$total_prorata_days`.
- **Arredondamento:** não arredondar intermediárias; dinheiro com 2 casas; fatores com ≥4 casas.
- **Teste de fórmula:**
  - 10 cenários padrão: admissão e saída no meio do mês, retro, desligamento futuro, LOP, salário zero.
  - Tabela `ID | Scenario | Hire | LWD | Guard Hit | Math | Expected | Result | Pass/Fail`.
- **Escrita:** escrever os guards primeiro. Entregar a versão indentada e a de uma linha. Marcar funções fora do vocabulário como "assumed".

### 6.5 Taxability matrix

- **Ordem:** overrides "No" no topo, wildcard "Yes" depois.
- **Wildcards:** bloco de 10 = último código + `xxx%`; bloco de 100 = último código + `xx%%`. Código isolado leva pattern vazio. Exclusão por omissão.
- **Continuidade implícita:** dentro de um bloco, códigos ausentes seguem o status dominante. [Conversion…docx; Youtrack KB Article.docx]
- **Expansão:** `%` = 0–9 e `%%` = 00–99. Código explícito vence wildcard; wildcard mais estreito vence o mais amplo. Na expansão Matrix→WTC não se inventam códigos "No". [Prompt to create WTC…; Global WTC Display Project.docx]
- **No JSON:** `account` troca `%` por `9` (6265% → 62659). [YouTrack…V1.0.md]
- **Condensação em 10 regras:** usada na FR. Há uma matriz por perímetro de base (6 na FR). Matriz não leva elementos de unidade ou %. [FR-pack]
- **BIK dual (TD):** a série 65xx fica fora da matriz de imposto e dentro da matriz de SS. [T-2026-07-07]

### 6.6 Padrões de design por país (reutilizáveis)

- **Bulgária (P1–P11)** [KB_Bulgaria_Design_Pattern_Analysis.md]
  - P1: ordinais seguem a cadeia G2N.
  - P2: duas bases → duas matrizes.
  - P3: acumulador YTM por valor reconciliado.
  - P4: capture band só para EE.
  - P5: SS em 2 fases (interim + posting arredondado).
  - P6: assertion de regulação vs de band.
  - P7: 58299 libera a reconciliação.
  - P8: tipos de alívio (mensal+anual, anual, contagem, teto).
  - P10: flag → assertion.
  - P11: convenção de contas.
  - Algoritmo de tradução CCG→Design em 10 passos.
- **Chile:** 3 bases (SS / AFC / IUSC); comissão por assertion na band; tetos em UF_eom; tratamento duplo do APV-B; reliquidação retrospectiva (vs regularização prospectiva da ES); sufixos `_Arrears` / `_Adjustment` / `_Advance`. [KB_Chile_Research_Artifacts.md]
- **Botswana (BW-1..7):** ano fiscal fora do calendário; anualização `DIVIDE(MULTIPLY(x;$period_divisor);$58206)`; sem SS; ceiling account; semeadura P16; gate por flag; dois débitos. [KB_Botswana…]
- **Espanha**
  - Caminhos mensal / diário / part-time convergindo.
  - Projeção anual por notionals com 2 bands (`$58299`).
  - BIK em 5 passos (YTM → Cumulative → NT Cumulative MIN → NT YTM → NT Current).
  - IRPF em 6 linhas (máx(calculada; voluntária)).
  - Cash vs BIK separados (2552 / 2572).
  - Floor/ceiling em contas armazenadas.

  [KB_Spain_Regulation_Design_v2.md]
- **Espanha, relatórios (R1–R6):** WTs só para relatório (58197/58198); cada PE novo mapeado em todos os relatórios; "taxable" sempre qualificado (IRPF ou SS); colunas CRA e AEAT no WTC. [KB_Spain_DevTeam_Questions…]
- **Irlanda:** taxas via RPN em 52/53xxx; triplet; regs Paid; reconciliação no ordinal 0 e no fim. [IE_Design_Comparison…]
- **Hungria:** isenção por declaração; opt-out; flag única de nacionalidade+residência; Mothers-40 como portão anual. [T-2026-05-26..29]
- **Egito:** ineligibility flag (default 0, só exceções); joiner suprime o step inteiro. [T-2026-06-16_18]
- **Índia (HRA):** 12 PEs por variável mensal; projeção com real passado + contratual futuro. [T-2026-05-22]
- **Carryover genérico:** se (gross − ceiling) < 0, guardar o positivo numa intermediate e somar ao ceiling seguinte. Perguntas obrigatórias: teto anual ou mensal? retro? [T-2026-04-20]

### 6.7 Formatos de artefato e QA

- **Artefatos de pesquisa (FR)**
  - CCG: 13 módulos com títulos do template.
  - DD: formato CZ V2.0, 8 abas, só as colunas azuis (4472C4) preenchidas; as laranja (FF9900) ficam vazias.
  - WTC: CZ V2.0 + Global WTC de 300 códigos na ordem do baseline + Form Reference Guide. Coluna Q dividida em Q1–Q4 + R.
  - Report Specs: "formato Spain", 9 abas, Sheet 4 com 21 colunas.
  - Payslip: 8 abas, navy FF1F3864.

  [07-qa-report.md; 02-wtc.md]
- **Checks v2.4:** C3, C9, C13, C14, C16, C17, C20; método de 4 buckets (DD / SYS / CALC / fora de escopo); failure patterns F1–F31.
- **Patch de DD por cirurgia XML** (openpyxl perde objetos), com SHA-256 e `verify.py`. [07-qa-report.md]
- **SIR**
  - Runbook de 7 fases + INTERLINKAGES + esforço.
  - Integração = M2M sem humano.
  - AEE ≠ aceitação.
  - Arquivar os retornos antes do purge de 3 meses.
  - Esforço: NETENT-DSN 59 pessoa-dia; DPAE 50 (37,5 depois da DSN); DGFIP-EDI Model A 74, Model B ~17–23, EFI ~2.

  [03-sir.md]
- **Skill FR:** ler a referência antes de responder; citar valores literais com base legal e vigência; usar a terminologia francesa; `[VERIFY WITH RA]`; checar contra o 07-qa-report. [SKILL.md]
- **Template de design (FR Method v3)**
  - Partes: A (cabeçalho); B1 (flags primeiro); B2 (Account Register tipado); B3 (3 seções por regulação).
  - Assertion de regulação `""`, de band `null`.
  - Build order em 11 passos; 10 cenários de teste; auto-revisão com o Review Prompt v2.

  [FR-pack]
- **Score de acurácia**
  - Pesos: lógica 50 / arquitetura 25 / precisão 15 / completude 10. CG acrescenta a dimensão de executabilidade (35/25/20/15/5).
  - Não citar percentual sem a dimensão de executabilidade.
  - Benchmarks: IE ~72%, CG 77%, TD ~83%, CI ~85%. Meta ≥90% em lógica.

  [CI_Accuracy_Score_v2.md; TD_Design_Comparison…; FR-pack]
- **Checklist pré-submissão do CCG** (121 perguntas da Lily, 10 categorias)
  - Escopo.
  - Consistência entre CCG, WTC e DD.
  - Pseudo-código + exemplo com divisor e período explícitos.
  - CRA/AEAT por PE.
  - Separar a parte isenta da tributável.
  - 4 colunas por PE.
  - Citar o artigo de lei nas contradições.

  Prioridades 🔴 / 🟠 / 🟡 / 🟢. [KB_Spain_DevTeam_Questions…; TD_DevTeam_Critique…]
- **Review Prompt v2**
  - Nada de memória; perguntar antes sobre o comportamento implícito do engine; citar o skill e a fórmula verbatim.
  - Rótulos 🔴 / 🟡 / ✅; Revision N; ruling do RA é autoritativo.
  - Descrição verbal não confirma correção; reconstruir os downstreams com código; retratar e procurar a mesma classe de erro.
  - Checklist A–I. [PayrollDesignReviewPrompt_v2.md]

### 6.8 Prompts de conversão (JSON, artigos, Client Manual)

- **JSON**
  - Root: `country` (iso2 minúsculo), `regulationCount`, `regulations` (por ordinal).
  - Regulação com 13 chaves; `regulationId` UUID v4; `status` "active"; `systemReportingPeriodIds` omitido se vazio.
  - Band com 16 chaves; `creditAmount` null.
  - Contas sempre string. Assertion de regulação `""` e de band `null`.
  - Saída `[cc].json`, sem fences.

  [Regulation_Design_JSON_Prompt_Revised.md]
- **YouTrack → JSON V1.0:** vazio → null; contas empilhadas → uma band por par; `employeeRate` = 100 quando não há taxa ER nem contas de taxa; Yes/No → bool; Start/End Date omitidos. [YouTrack…V1.0.md]
- **Artigo novo V1.1**
  - Cabeçalho `# [ID] - [Name]`.
  - Seções 1 Classification, 2 Execution Conditions, 3 Bands (15 colunas), 4 Taxability Rules.
  - Sem `###`; Yes/No; datas em nota. [Prompt…V1.1.md]
- **Horizontal → artigo**
  - Mapeamento posicional pelo header.
  - Remove as bands com End Date (sinaliza regulação sem band aberta).
  - 18 colunas com creditAmount.
  - Mantém a ordem da fonte. [Prompt_to_Convert_Horizontal…]
- **Client Manual:** persona de Senior Implementation Consultant; integridade de 100%; linguagem leiga; seções Pre-tax / SS / Tax; taxas vigentes (sem End Date); matriz completa e débito/crédito por regulação (variante NL). [Master AI Prompt…docx]
- **WTC_Build_Prompt**
  - Carregar o Global WTC baseline de uma skill `payroll-compliance-*`; esse passo é "load-bearing".
  - Códigos fora do catálogo levam ⚑.
  - Coluna Basis: Explicit vs Derived.
  - Re-verificação independente.
  - Perguntar pelo baseline/DD e pelo formato antes de começar.

  [WTC_Build_Prompt.md]

### 6.9 HR fields e master data

- **Tipos de HR field:** 4 (system, user, country, transactional). Configurados por legal entity. Prefixos `$legal_entity.HR…` e `::`. Direção do produto: ~3–4 system fields, o resto por país ou por entity. Local labels para muitas chaves com poucos valores (ID). [T-2026-07-14]
- **Master DD v1.5** [Master_Data_Dictionary_Template_v1.5.xlsx]
  - Schema: field_id snake_case imutável; label_en, description_en, field_group, ordinal, type e required obrigatórios; `applicability_rule`, `cross_field_rule`, `dependency_rule`, `pii_class`, `review_frequency`; template de país com 25 colunas.
  - Gramática: `$entity.field_code`, funções em maiúsculas, `;`, aspas simples. Funções ⚙ ainda não confirmadas.
  - Guards G1–G3, invariantes L1–L11, execução R1–R6.
  - PERCENT guarda 5.0 (não 0.05). Regex nomeadas (gb_ni_number, in_pan, cl_rut…). i18n BCP 47 com fallback R1–R4.
- **Layout do GB DD:** seções HR-friendly + colunas técnicas (Display Code `$entity.code`); 102 campos (36 obrigatórios). [GB_Country_Data_Dictionary_v3.xlsx]
- **Arquitetura proposta para HR fields**
  - L1 Global (Product), L2 Country Template (Compliance, fonte da verdade), L3 Entity Delta (Implementação).
  - Resolução por `COALESCE` e tabela `entity_field_properties_override`.
  - Tiers 1–3 de governança e "Legacy Shield".

  [HR Fields Architecture…; Executive Brief…]
- **Country DD:** entidades HR, Employee, Person, Address, Bank, Recurring, Future/History PE, Relative, Role, Termination Event, Login, Pay Group. [Country DD.docx]

### 6.10 Ferramentas

- **Country Settings Automation Scripts:** JS no console do back-office de acceptance (`backoffice-webapp.acceptance.k8s.hrblizz.dev`).
  - Option mappers: preencher.
  - DD e mapper: extrair.
  - HR fields: criar em lote (localStorage `batch_idx`).
  - Pay elements: subir.
  - Bands: inserir, fechar, sobrescrever, baixar.
  - Matriz: subir, extrair.
  - Intermediárias: extrair.
  - Export TSV de 3 seções para o YouTrack.

  [Country Settings Automation Scripts.docx]
- **WTC Taxability Display:** só PEs do Global WTC referenciados pelas regulations-alvo; cabeçalho em 2 linhas por grupo; cores Yes/No/branco; autofilter. [Global_WTC_Taxability_Display.xlsx; Global WTC Display Project.docx]
- **Faixas de conta do Global G2N** (rótulo "DK Specific"): Earnings 62100–62999 + 79401–79499; Benefits 65000–65999; Deductions 21100–21999 + 25500–25899; ER 23550–23900. [Global G2N Specifications.xlsx]
- **Contribution Pay Elements:** 23xxx ↔ 60xxx; empréstimos 270–271xx ↔ 670–671xx; famílias "recon" 2363x–2368x. [Contribution Pay Elements.xlsx]

## 7. Tickets e dúvidas de suporte

> Não há fila formal de tickets de suporte no projeto. A tabela junta tickets HRBS/SR/CT, escalações citadas em reuniões e dúvidas de design registradas.

| Ticket | País | Pergunta | Resposta dada | Fonte | Mudou artefato? |
|---|---|---|---|---|---|
| HRBS-10121 | ES | A projeção de variável conta em dobro? | Sim; corrigido para `MAX(0; prev − YTD)` | [KB_Spain_Research_Artifacts_v2.md] | Sim (CCG v1.1) |
| HRBS-10272 | ES | Faltam AT/EP por CNAE, recaída IT e data de incapacidade | Seções 5.1.3, 8.2.1 e 7.1.2; 10 campos novos | idem | Sim (CCG v1.2, DD v3.7) |
| Queries da Lily | ES | CNAE incompleto; mínimos part-time | Tabelas CNAE I/II; mínimos atualizados | idem | Sim (CCG v1.3) |
| 41 queries de specs | ES | Lacunas SEPE/AEAT | 16 campos de empregado + 13 de LE + 5 mappers | idem | Sim (DD v3.3) |
| ES-BASES-001 | ES | Campos do arquivo Bases do SILTRA | Alinhamento + campos de retificação TGSS | idem | Sim (DD v3.4) |
| CT-4357 | ES | Retro | Regulação 9724476; simulação em acceptance (LE 3982) | [KB_Spain_DevTeam_Questions_And_Reports.md] | Sim |
| SR-79 / SR-81 / SR-83 | ES | Severance no L03; CRA por PE; AEAT Key/Subkey | 58197/58198; coluna CRA (severance → 0054); colunas AEAT + remapeamento 65816–65849 | idem | Sim (WTC/design) |
| ID:118 / ID:253 / ID:155 | ES | Imposto cash vs BIK no 111; reemitir no retro; categorias CRA | Padrão Cash/BIK; requisito de retro; revisão das categorias | idem | Sim |
| ID:124 / ID:49 / ID:51 / ID:192 | ES | MAX(YTD; ano anterior) via Gemini; separar PEs (bônus irregular, km, extra pay) | Citar a base legal; pedidos de split | idem | [INCERTO] |
| — (implementation expert) | ES | Gaps de regulação | ~40% de redesign + reteste | [T-2026-06-16_18] | Sim (pendente) |
| GChat Q1–Q5 (2026-06-03) | CL | AFP, Art. 46, UF, Art. 50/47, APV-B | Ver decisões na seção 3 | [KB_Chile_Design_Decisions.md] | Sim (design CL) |
| Design Q2/Q3/Q4 | CL | YTM da reliquidação; faixas IUSC; excesso ISAPRE | Resolvidas | [CL_Regulation_Design_v1.0.md] | Sim (v1.1) |
| E-mail Mohit → Wallisson | TD | Meal cash: WTC diz tributável, CCG não | Respondido em 1–2 dias; exceção 628x tributável | [T-2026-07-07; T-2026-07-02] | [INCERTO] |
| KT 2026-07-07 | TD | Teto familiar de 5.000 | Sem base legal; pedir o documento-fonte | [TD_Statutory_Research…] | Pendente |
| CT-A-580 (OI-2/4/6/7/12) | TD | Estimativa anual, BIK dual, arredondamento, piso, constantes | Produção: ×12; 9 forfaits sobre 58105; FLOOR(x+0,5); piso fixo; constantes em 9148009 | [TD_Design_Comparison…] | Não |
| Escalação | VN | Desligar o retro imediatamente? | Não dá: exige mudar o engine e retestar. Manju verifica os requisitos | [T-2026-06-25] | Pendente |
| — | VN | Mudança do imposto NR a partir de julho | Aguarda esclarecimento [INCERTO "ICE"] | [T-2026-06-16_18] | Pendente |
| — | AU | Implementar STSL | 1 mudança de design, a primeira implementação; follow-up | [T-2026-06-25] | Pendente |
| Incidente | TH | Report TXT falhou | Mappers alterados pelo integration team; acesso revogado | [T-2026-07-14] | Sim (governança) |
| Produção | NL | Bug do 30% ruling | Fix pontual | [T-2026-07-10] | Sim |
| Pergunta da Lily | RO | D12 medical leave/work accident é payroll? | Não; é labor law | [T-2026-07-14] | Não |
| — | IN | 9356204 Food Allowance referencia 58167, que não existe no Global WTC | Confirmar com o cliente | [Global_WTC_Taxability_Display.xlsx] | Pendente |
| Refs de design | BW / IE | CT-A-507/508 (BW); CT-A-31/192/32/33/34/435/370 (IE) | Fontes do design de produção | [KB_Botswana…; IE_Design_Comparison…] | — |

## 8. Pendências em aberto

> As datas dos registros vão de abr a set/2026. Muitas pendências podem ter sido resolvidas fora do projeto.

### FR

| Pendência | Dono | Fonte |
|---|---|---|
| QA: F-1, F-2, F-3 bloqueiam a entrega ao dev. Corrigir também m-1 e m-2. m-3 vai para o standard owner. Depois disso o status passa a READY FOR DEV TEAM | Build / Wallisson | [07-qa-report.md] |
| Escopo, itens W-01 a W-03: promover a L137-13 (30%) e a L137-14 (10%) para in_scope; criar linha out_of_scope para o 182 A ter; tratar A1 só como flag de exclusão; rotular F1–F22 e acrescentar F23–F31. [INCERTO] o ID sugerido FR-DGFIP-006 já é usado pelo PASRAU | Scope owner | idem |
| Limitações registradas: FR-LIM-001 (Stage 4), FR-LIM-002 (layout CARSAT), FR-LIM-003 (OCR SOLTéA) | Owner | idem |
| Decisões do owner ainda pendentes: share schemes S89; Contract Nature 60; Version Control das specs (linhas 19–20) | Wallisson | [05-data-dictionary.md; 07-qa-report.md] |
| SIR: FR-SI-Q1–Q5. NETENT-DSN: charte concentrateur, registro EDITEUR, pacote XSD, yml CNAM. DPAE: tabelas C_URSSAF e C_APPLICATION, que bloqueiam o go-live, mais 10 itens não verificados. DGFIP-EDI: Q1–Q7 (a Q2 decide o Model A) | — | [03-sir.md] |
| Design: Blocos 2 (contribuições + 6 matrizes), 3 e 4; mapear quais WTs ER alimentam 58130 (bloqueia 9250061); RA confirmar 24 [DERIVED]; escopo IDCC; 52560 sem valor; 52562/52563 fixo ou taxa | Wallisson / RA | [FR-pack] |
| Pesquisa: preencher Internal Code no DD e conformar ao v1.5; preencher as colunas laranja do WTC; grade PAS em valores anuais; entregar FR-DGFIP-002 e FR-DSN-001 ao design | Research | [FR-pack] |
| Revisões datadas: PPV ampliado acaba em 31/12/2026; DFS cai −1 ponto/ano; DPAE na DSN não antes de 01/01/2027; payslip novo em 01/01/2027 | — | [01-ccg.md; 02-wtc.md] |

### ES, CL, BW, BG, IE

| Pendência | Dono | Fonte |
|---|---|---|
| ES: confirmar a fórmula MAX nos ordinais 456/461; ordinal 161/211 [TBD]; IDs truncados na v1; specs Open/On Hold; redesign de 40% + reteste (Manju sugeriu usar o Claude) | Dev / Compliance | [KB_Spain_*; T-2026-06-16_18] |
| ES: report specs restantes (AFI, SEPE, M216/296, Payslip, Finiquito) | — | [00_INDEX.md] |
| CL: Q1 (ordinal da gratificación, 15 ou 281) e Q5 (asignación usa 58101 ou 58100) | Mohit / Ruchi | [CL_Regulation_Design_v1.0.md; 00_INDEX.md] |
| CL: 9152011 vira 3 sub-regs ou 1 com 3 bands? | — | idem |
| CL: Previred v82 entra no escopo v1? | — | idem |
| CL: fórmula da 9152321 é só conceito; conta da 9152311 indefinida | — | idem |
| CL: testar o retro (SS parcial / tax 100%) e atualizar KB_Chile_Design_Decisions.md | Ruchi / Mohit | [T-2026-07-10] |
| BW: verificar a band de 15% e os dois débitos da 9072011 | — | [KB_Botswana…] |
| BW: próximos países sugeridos são CO, AU V2.0, NL, NO | — | idem |
| BG: criar o PE 52531 | — | [KB_Bulgaria_Design_BG…] |
| BG: piso e teto do TZPB variam por empregado? | Wallisson | idem |
| BG: GVRF 6031/2531 | — | idem |
| IE: Advance Holiday Pay (sem campo no DD v3.4) | — | [IE_Regulation_Design…] |
| IE: `$hr.state_pension_contributory` na 58202 | — | idem |
| IE: aplicar os learnings para chegar a 85–90% | Wallisson | idem |

### HU, EG, TD, CI, CG, outros

| Pendência | Dono | Fonte |
|---|---|---|
| HU: definir a data do portão de idade (`$legal_entity.tax_yearend_date` vs 31/12 fixo) | Mohit | [T-2026-05-27; T-2026-05-29] |
| HU: flag vs inline | Mohit | idem |
| HU: nacionalidade + residência (CCG p.38) | Suman | idem |
| HU: validar a isenção de 3 filhos | Suman | idem |
| HU: workflow de aprovação de declarações (fronteira HRB × engine) | Aberto | idem |
| HU: o componente de pensão de 10% depende de config do cliente? | Aberto | idem |
| HU: verificar os valores de family allowance | Suman / Mohit | idem |
| HU: reconciliar SR-A-1 com SR-A-5 | — | [SR-A-1.md; SR-A-5.md] |
| HU: ajustar as report specs | Suman | [T-2026-06-25] |
| HU: design "new track" | Wallisson | [T-2026-07-10] |
| EG: personal exemption para quem entra ou sai no meio do mês | Manju | [T-2026-06-16_18] |
| EG: base do emergency fund | Manju | idem |
| EG: 15.000 vs 15.250 | Manju | idem |
| EG: avaliar o impacto do arredondamento combinado em clientes ativos | Manju | [T-2026-06-11] |
| TD: fonte do teto de 5.000/dependente; se não houver, remover das regs 9148032/033 | Mohit | [TD_Design_Comparison…] |
| TD: teto do Art. 47 na 9148181 | Dev | idem |
| TD: severance contra o WTC | Dev | idem |
| TD: frais 15% | Dev | idem |
| TD: regularização anual CNPS (Art. 12) | Dev | idem |
| TD: defeito dos "60 anos" | Dev | idem |
| TD: posições sobre NR e TFE/TAFP no CCG + pedido de ruling da DGI | Compliance / DGI | idem |
| TD: localizar o décret de garnishment (Art. 277) | RA | [TD_Statutory_Research…] |
| TD: OI-3 PE plan-social 62182 | Mohit / Andre | [TD_Regulation_Design_v1_0.md] |
| TD: OI-11 perímetro dos "appointements" | Compliance | idem |
| TD: contas a pagar ER | Dev | idem |
| TD: confirmar a LFI 2026 (Loi 008 de 26/12/2025) | Compliance | idem |
| TD: população diária/horista não coberta | Compliance | idem |
| TD: status final dos itens C1–L2 da crítica [INCERTO] | Compliance | idem |
| TD: novo design do zero | Wallisson | [T-08-25] |
| CI: KT passo a passo + revisão de linguagem/estrutura | Wallisson | [T-08-25; T-2026-07-10] |
| CI: review points | Mohit | idem |
| CI: 3 flags string | — | [T-2026-07-14] |
| CI: local labels para a Part 9 (266 códigos na 9384011) | — | idem |
| CI: convenção de arredondamento | — | [CI_Accuracy_Score_v2.md] |
| CI: matriz da 9384011 | — | idem |
| CG: perguntas Q1–Q11 ao Mohit (atomização, mapper, `_period` × cauda, nº de matrizes, Tax Group, `_$$`, bandas 2,4/9,6, registro 58xxx, `.99`, FLOOR, rubrica) | Wallisson → Mohit | [FR-pack] |
| CG: incluir o "No Child" relief no CCG CG | RA | idem |
| TR: confirmar com o Andre a regra "net amount for pre-tax" | Manju / Mohit | [T-2026-07-16] |
| TR: taxas e teto | Manju / Mohit | idem |
| RO: escopo do D12 | Marko | [T-2026-07-14] |
| VN: NR e retro | Manju | [T-2026-06-16_18; T-2026-06-25] |
| AU: follow-up do STSL | Suman | [T-2026-06-25] |
| Gabon: design | Manju | [T-08-25] |
| Iraq/Yemen: design | Enaakshi | idem |
| Canada: JSON parado sem registro de 58xxx | — | [00_INDEX.md] |
| GB: LEL, Fuel Code, campo "ID", "Maintained By", defaults de AE, tax code 2026/27, v3 vs v31 | — | [GB_Country_Data_Dictionary_v3.xlsx] |
| IN: 9356204 / 58167 | Cliente | [Global_WTC_Taxability_Display.xlsx] |

### Globais

| Pendência | Dono | Fonte |
|---|---|---|
| Catálogo de Tax Rule Groups (fechado em 07-02, mas o KB_Engine_Formula_Syntax §8 continua desatualizado) | Andre / atualizar o doc | [00_INDEX.md; DevKB] |
| Regulation content spec do Andre e liberação de IP para usar designs com IA | Wallisson / Manju (com Andre / Marko) | [T-2026-05-22] |
| Especificações de design para automação: passos, exemplos, limitações | Mohit | [T-08-25] |
| Prompts melhores e mais contexto de engine | Mohit | [T-2026-07-10] |
| Compartilhar a documentação de design e o chat de KT | Wallisson | idem |
| Próximo país como teste completo | Wallisson | [00_INDEX.md] |
| Gargalo de aprovação: só Mohit, "Wii" [INCERTO] e Lily aprovam designs | — | [T-08-25] |
| Sem alinhamento sobre a verificação manual de G2N | — | [T-2026-07-10] |
| In-period reconciliation não funciona em ciclo submensal | Produto | [T-2026-07-02; DevKB] |
| Variáveis de sistema que falham em fórmulas compostas ainda não mapeadas (`$remaining_future_periods`, `$period_divisor`) | — | idem |
| Conflitos de sintaxe: `CONTAINS` com lista vs `RANGE`; aspas no SUM; formato de data `dd-MM-yyyy` vs ISO | — | [FormulaPrompt; KB_Engine_Formula_Syntax.md; KB_Mercans_Knowledgebase_Formulas.md] |
| Rótulos de conta: Catálogo v1.0 (2582, 2592, 2550, 2531, 2517, 2554, 2560, com rótulos aparentemente indonésios) vs WTC Display | — | [KB_Global_Wage_Type_Catalogue…; Global WTC Display Project.docx] |
| Catálogo: proventos "debitam" ou "creditam" 2610? | — | idem |
| Prompts divergentes em: datas das bands; creditAmount (15 vs 18 colunas); regra de employeeRate = 100; ordem de saída; tax year fixo `_2026` | — | [prompts de conversão] |
| Qual variante do Client Manual vale (NL ou genérica)? Onde fica "Differential" (TT ou TRG)? | — | [Master AI Prompt…] |
| Inconsistências no prompt NL: 58202, permanent_disability, start_date vs begin_date, ordinais duplicados | — | idem |
| HR Fields: aprovação e implementação da proposta | — | [Executive Brief…] |
| HR Fields: comentário pendente do dev (master template, campos com vigência, interdependências) | Dev | idem |
| Tela WTC Display: revisar usabilidade | — | [Global WTC Display Project.docx] |
| Backlog de automação sem dono nem prioridade | — | [HR Fields Selection Automation] |
| IA no YouTrack para tickets de support desk (plano futuro) | — | [DevKB] |
| Master DD: confirmar as funções ⚙ | Engenharia | [Master DD v1.5] |
| Master DD: alinhar tipos e validadores | — | idem |
| G2N: Accrual e interim sem fórmula; anexo citado ausente | — | [Global G2N Specifications.xlsx] |
| Scripts: validar o parser 1/0 e a remoção de decimais | — | [Country Settings Automation Scripts.docx] |
| Board de validação por IA: 35 itens "Not Started", alguns com prazo vencido | — | [Country AI Validation File Board.xlsx] |

## 9. Fronteiras

| Tema | Responsabilidade | Fonte |
|---|---|---|
| Pesquisa (CCG/WTC/DD, verdade legal) vs design e regulations no YouTrack | Compliance/RA pesquisa; Configuration Analyst/dev desenha (Mohit, Ruchi, Lily, Suman, Luci); Andre só desenvolve e faz deploy de país inteiro | [T-2026-06-16_18; T-2026-05-22; KB_Spain_Research_Artifacts_v2.md] |
| Colunas azuis vs laranja de WTC e DD | Azuis: research. Laranja: dev | [KB_Botswana…; 02-wtc.md; T-2026-06-25] |
| Mapeamento de tax codes | Report spec (compliance), não o WTC | [T-2026-06-25] |
| Contradições de pesquisa | Dono da pesquisa (Wallisson), não o BA | [T-2026-07-07] |
| Gaps bloqueantes no guia | O dev abre gap query; a compliance responde | [T-2026-04-20] |
| TT/TRG para designers novos | Dev, na development call | [T-2026-06-11] |
| Retro e parâmetros do engine | Configuração do engine (dev), não toggle de compliance | [T-2026-06-25] |
| Validação e aprovação de designs feitos por IA | Seniors de design; human-in-the-loop | [T-08-25] |
| IP e docs internos do engine | Andre | [T-2026-05-22] |
| Country settings | Só o compliance team; o integration team (Dayforce etc.) ficou sem acesso | [T-2026-07-14] |
| Labor law (leave e work accident no D12 RO) | Fora do escopo de payroll | [T-2026-07-14] |
| Pagamento de benefício de SS pelo empregador (HU) | Módulo de terceiro, entra só como input | [T-2026-05-27] |
| Workflow de aprovação de declarações (HU) | Fronteira HRB × engine não definida | idem |
| Dependentes e nacionalidade | Campos de HR / dependent screen, não flags | idem |
| Label SaaS (EG) | Limitação de produto | [T-2026-06-16_18] |
| TR | Andre constrói a partir de product spec (não dá pela ferramenta HRB) | [T-2026-07-16] |
| FR: Egapro, bilan social, BDESE, ACEMO | HRMS / secretariado do [cliente] | [07-qa-report.md] |
| FR: taxas de veículos, PEEC, 182 B | Finanças / frota do [cliente] | idem |
| FR: TNS/SSI | Contador do [cliente] | idem |
| FR: SIPSI | Entidade receptora / mobilidade | idem |
| FR: SEPA, GL, feed HRMS, migração | Workstream de pagamentos e interfaces, fora da SIR | [03-sir.md] |
| FR: conteúdo NEODeS | Report Spec / DD / WTC, não integração | idem |
| FR: transmissão EDI | Partenaire EDI credenciado | idem |
| FR: saldo TA (SOLTéA) | Decisão de negócio do [cliente] | idem |
| FR: taxa PAS | DGFiP | [01-ccg.md] |
| FR: taxa AT/MP | CARSAT | [02-wtc.md] |
| FR: L1224-1 | Advogado trabalhista do [cliente] | [01-ccg.md] |
| FR: venda de ações e poupança salarial | Administradores dos planos | idem |
| FR: PASRAU | Pagador terceiro | idem |
| FR: códigos [DERIVED] | RA | [FR-pack] |
| FR: cor do net pay (m-3) | Standard owner | [07-qa-report.md] |
| CL: UF/UTM/IMM | Publicados por BC/SII; digitados pelo operador | [KB_Chile_Design_Decisions.md] |
| CL: DS67 | Específico de cada empregador | [CL_Regulation_Design…] |
| CL: Art. 55 bis | Certificado do banco entregue pelo empregado | [KB_Chile_Research_Artifacts.md] |
| CL: asignación | Recuperada via Previred | idem |
| CL: crédito de zona | Form 1902 do SII | idem |
| IE: taxas PAYE/USC | Revenue, via RPN | [IE_Regulation_Design…] |
| TD: rulings NR e TFE | DGI | [TD_Statutory_Research…] |
| TD: quotité de penhora | Tribunal du travail (o engine é fallback) | idem |
| TD: garnishment | Pesquisa (RA), não dev | idem |
| BG: juros de hipoteca de famílias jovens e doações | Fora da folha | [KB_Bulgaria_Design_Pattern_Analysis.md] |
| HR Fields (proposta) | L1 Product, L2 Compliance, L3 Implementação | [HR Fields Architecture…] |
| Scripts de automação | Ambiente de acceptance, não produção | [Country Settings Automation Scripts.docx] |
| Global WTC | Não inclui contas de engine 58xxx/52xxx | [KB_Global_Wage_Type_Catalogue_v1.0.md] |

---

### Lacunas do projeto (o que falta para fechar)

- **Faltam no projeto:**
  - O conteúdo do Regulation content spec do Andre.
  - O KB interno com a sintaxe completa de `WHEN`.
  - As planilhas Google referenciadas pelo prompt genérico de Client Manual.
  - Os achados da revisão de Iraq.
  - O CI_Regulation_Design_v1_0.md (citado, mas não está no projeto).
  - CTA632.md / design IN.
- **Docs desatualizados ou com versões conflitantes:**
  - KB_Engine_Formula_Syntax.md §8 está desatualizado: precisa refletir o fechamento de 07-02.
  - Há duas cópias do transcript 06-25, dois GB DD idênticos (v3/v31) e dois WTC Display IN quase idênticos. Vale consolidar.

