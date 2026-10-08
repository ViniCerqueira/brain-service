# Serviço 2 — Design

> Etapa 2 do fluxo. Anterior: [[research-pipeline]] · Depois: produção ([[fronteiras]]) · Índice: [[00-INDEX]]
> Fonte principal: projeto "Mercans Design & Development KB" (chat: design-dev-kb). Escopo registrado ali: design autônomo de regulações para países novos, a partir de padrões de países já em produção. Dono: Compliance Regulations Team (Wallisson Gomes).
> **Atenção ao escopo:** o desenho oficial de regulação em produção é feito pelo dev/configuration analyst (Mohit, Ruchi, Lily, Suman, Luci); o nosso é o design gerado com IA (clean-room), comparado com o real. Ver [[fronteiras]]. O que exatamente a Mercans espera de nós nesta etapa precisa de confirmação (ver pendências abaixo).

## O que recebemos (entradas)
- Artefatos do [[research-pipeline]]: CCG (verdade legal), WTC e DD (documentam o design, não são a origem dele). Alimentar a IA com a pesquisa completa, não com resumos (chat: design-dev-kb).
- Designs de países já em produção, usados como padrão (BG, CL, BW, ES, IE, TD, CI, FR...) e a documentação do dev team (prompts, catálogo de Tax Rule Groups, sintaxe de fórmula) (chat: design-dev-kb).
- Tickets de regulation/spec no YouTrack (CT-A-xxx) para comparar o design nosso com o do Dev (chat: design-dev-kb).
- Países marcados "Submitted for design" no Monday, inclusive backlog de payslip facelift (30+ países) (chat: compliance-research).
- Cross-training com o dev team (transcrições Otter/Gemini, abr a set/2026): não são literais; a de 2026-07-16 foi reconstruída de auto-transcript ruim e nada nela é ratificado (chat: design-dev-kb).

## O que entregamos (saídas)
- **Regulation Design por país**: flags, regulations (ID `9` + ISO numérico + ordinal de 3 dígitos; ordinais de 10 em 10 a partir de 11), bands (18 colunas fixas), taxability matrices, Account Register com contas tipadas. Exemplos: FR Bloco 1 v0.1 (prefixo 9250: 7 regs, 21 flags, 13 bases, 18 contas), CL v1.1 (36 regs), IE v1.0 (31 regs), TD v1.0 (24 artigos) (chat: design-dev-kb).
- **Comparações Claude vs Dev** (design de produção como régua): IE ~72% (52 regs reais), TD lógica ~89% / geral ~83% (CT-A-580, Mohit fez em ~2 dias com IA), CG 77% (CT-A-590), CI ~85% (chat: design-dev-kb).
- **Crítica pré-submissão** de CCG/WTC/DD e lista de problemas de pesquisa (TD, 14 itens, 2026-06-25); checklist de 121 perguntas da BA em 10 categorias (chat: design-dev-kb).
- **Conversões** de design: Regulation Design -> JSON, tabela YouTrack -> JSON, artigo antigo -> artigo novo, export horizontal -> artigo; WTC <-> Taxability Matrix; Client Manual (chat: design-dev-kb).
- **Ferramentas e padrões reutilizáveis:** Global WTC Taxability Display (566 PEs x 10 regulations, IN), Master Data Dictionary Template v1.5, Country Settings Automation Scripts (JS no back-office de acceptance), Design Method v3 (FR) (chat: design-dev-kb).
- **Payslip facelift / Payslip Generator**: ligado a esta etapa pelo status "Submitted for design" (chat: compliance-research). Quem desenha o payslip além do que geramos no pipeline [INCERTO].

### Padrões do engine (resumo operacional; detalhes na KB do projeto)
- **Estrutura da regulação:** Form Data, Matrix e Bands. Taxation Type Flat / Formula / Differential; Tax Group Income Tax / Social Security. Tax Rule Group = combinação de componentes (`_simple_tax`, `_table`, `_monthly`, `_$`, `_period`, `_retro`, `_ytm`, `_ytd`...) (chat: design-dev-kb).
- **Flags:** só valores numéricos 0-4 (engine não lê string); uma flag não lê o HR field direto; toda combinação precisa estar coberta (combinação não codificada retorna zero sem erro); minimizar o número de flags (chat: design-dev-kb).
- **Divisão automática por período:** só Income From/To, Floor e Ceiling (declarados anuais); valor dentro de fórmula não é dividido; `_monthly` interrompe a divisão (chat: design-dev-kb).
- **Contas por faixa** (58008 gross taxable, 581xx intermediárias, 582xx flags, 585xx acumuladores, 52xxx taxas, 53xxx tabelas, 62xxx earnings, 65xxx BIK, 21xxx/25xxx deduções, 99999 sink etc.) e **séries canônicas**: uma série por conceito em todos os países; trabalhar por série, não por elemento (chat: design-dev-kb).
- **Taxability matrix:** overrides "No" no topo, wildcard "Yes" depois; `%` = 0-9, `%%` = 00-99; código explícito vence wildcard; uma matriz por perímetro de base (chat: design-dev-kb).
- **Sintaxe de fórmula:** `;` como separador, sem `+ - * /` (usar ADD/SUBTRACT/MULTIPLY/DIVIDE), datas sempre via `DATE_FORMAT` com `yyyyMMdd`; escrever os guards primeiro; testar com 10 cenários padrão (chat: design-dev-kb).
- Padrões por país reutilizáveis (BG P1-P11, CL, BW, ES, IE, HU, EG, IN) estão na seção 6.6 da extração (chat: design-dev-kb).

## Como sabemos que ficou certo (qualidade)
- **Score de acurácia** com pesos lógica 50 / arquitetura 25 / precisão 15 / completude 10; para CG acrescenta-se executabilidade (35/25/20/15/5). **Não citar percentual sem a dimensão de executabilidade.** Meta: >=90% em lógica (chat: design-dev-kb).
- **Comparação com o design real do Dev** (clean-room x produção) e **validação do design contra um exemplo numérico do CCG** (ex.: Ex. 1 do FR) (chat: design-dev-kb).
- **Review Prompt v2** (revisado após a revisão de Iraq Federal + KRI): sem memória, perguntar antes sobre comportamento implícito do engine, citar skill e fórmula verbatim; descrição verbal não confirma correção; ruling do RA é autoritativo; checklist A-I (chat: design-dev-kb).
- **Checklist pré-submissão do CCG:** escopo, consistência CCG/WTC/DD, pseudo-código com divisor e período explícitos, CRA/AEAT por PE, isento x tributável separados, 4 colunas por PE, artigo de lei nas contradições (chat: design-dev-kb).
- **Aprovação:** só poucos seniors aprovam designs (Mohit, Lily e um terceiro [INCERTO]); design feito por IA exige human-in-the-loop e é gargalo (chat: design-dev-kb).
- **Benchmarks de esforço** para planejar: 15-25 regs ~5 dias; Chad ~2 dias com IA; Spain (~150 steps) até 2 meses (chat: design-dev-kb).
- **Cross-training:** onboarding percorrendo um design real ordinal por ordinal, com o trainee explicando de volta (chat: design-dev-kb).

## O que já deu errado
Erros de **processo** (erros por país: [[correcoes]]):
- **Design de IA que parece certo e não executa:** contas trocadas (flag x intermediate x base), fórmulas em "linguagem explicativa", flags string, `_table` sobre "parts", valores anuais usados como mensais (defeito de 12x). Mitigação: distinguir tipos de conta, código executável com variáveis, declarar valores anuais (CI, CG) (chat: design-dev-kb).
- **Aplicar padrão de um país em outro sem conferir a base legal:** decomposição de imposto progressivo que era específica do RPN (IE); redesign completo proposto onde bastava fix pontual (NL, bug do 30% ruling); circularidade inventada fora de gross-up (CL) (chat: design-dev-kb).
- **Revisão de design com falso diagnóstico** (Iraq): "missing row" coberto por wildcard, "defeito" que era comportamento implícito do engine, finding fechado só por descrição verbal. Originou o Review Prompt v2 (chat: design-dev-kb).
- **Inconsistências entre artefatos de pesquisa que chegam ao design:** CCG x WTC x DD divergentes (FR, ES, TD), manifest com contagem errada (FR F-1), QA com percentual refeito (86,5% -> 73,2%) (chat: design-dev-kb).
- **Extração de PDF multicoluna** trocou flags e rótulos (ES KB v1) (chat: design-dev-kb).
- **Cross-training/KB com conflitos entre fontes** (All Payroll obsoleto x doc; catálogo de Tax Rule Groups tido como pendente; doc de sintaxe §8 desatualizado) (chat: design-dev-kb).
- **Prompts de conversão divergentes** entre si (colunas de band 15 x 18, regra de employeeRate, tax year fixo `_2026`); script de upload de matriz que só converte 'Yes' (chat: design-dev-kb).
- **Acesso:** option mapper alterado pelo integration team quebrou report em produção (TH); country settings só com o compliance team (chat: design-dev-kb).
- **Escopo:** sem alinhamento sobre verificação manual de G2N; backlog de automação (HR Fields) sem dono; proposta de HR Fields sem aprovação registrada; liberação de IP para usar designs com IA pendente (chat: design-dev-kb).

## Países
[[Africa-do-Sul]] · [[Alemanha]] · [[Australia]] · [[Bahrein]] · [[Belarus]] · [[Belgica]] · [[Botsuana]] · [[Bulgaria]] · [[Canada]] · [[Chade]] · [[Chile]] · [[China]] · [[Chipre]] · [[Colombia]] · [[Congo]] · [[Costa-Rica]] · [[Costa-do-Marfim]] · [[Dinamarca]] · [[Egito]] · [[Espanha]] · [[Estonia]] · [[Filipinas]] · [[Finlandia]] · [[Franca]] · [[Gabao]] · [[Guine-Equatorial]] · [[Holanda]] · [[Hungria]] · [[India]] · [[Indonesia]] · [[Irlanda]] · [[Kuwait]] · [[Libano]] · [[Lituania]] · [[Malasia]] · [[Marrocos]] · [[Mocambique]] · [[Namibia]] · [[Noruega]] · [[Portugal]] · [[RD-Congo]] · [[Reino-Unido]] · [[Romenia]] · [[Singapura]] · [[Suecia]] · [[Tailandia]] · [[Tchequia]] · [[Ucrania]] · [[Vietna]]
