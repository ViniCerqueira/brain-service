# Extração: projeto "Compliance Research" (Claude da Mercans)

Data da extração: 2026-10-01
Fontes lidas no projeto: PROJECT_INSTRUCTIONS.md, AUTOMATION_ROADMAP.md (e cópia idêntica "(1)"), README.md, ticket_HRBS-1534.json, transcrição "Research Team Weekly Discussion" (2026-06-30), transcrição "Coordination on YouTrack & Claude Integration" (2026-07-07). Os arquivos .py e requirements.txt não foram usados como fonte de fatos estatutários.
Observação: os arquivos do projeto são todos de 2026-07-07; não há registro de nada posterior a essa data aqui.

## 1. Sobre este projeto

- Projeto compartilhado do time de Research / Compliance (HRBLIZZ) para automatizar o fluxo de pesquisa de compliance com a Claude API, com humano no loop para qualquer escrita em artefato.
- Etapa do serviço: principalmente **Research Pipeline** (manutenção de CCG, WTC, DD, Report Specs, SIR, payslips, QA) e **Suporte** (tickets YouTrack resolvidos alimentando os artefatos). Toca **Design** apenas pelo status "Submitted for design" e pelo backlog de facelift de payslips.
- Entrega principal construída: **hrblizz-drift-sync** (ticket resolvido → CCG no Drive → Claude decide se há drift → tracked change + comentário no Word → cópia redlined de volta no Drive). Provado no caso HRBS-1534 (NL, 30% ruling) contra NL-CCG-001 §7.1.4.
- Países citados: Netherlands (caso de prova); revisados no roadmap: Spain, Canada, Bahrain, Kuwait, Jordan, Congo-Brazzaville, Côte d'Ivoire, Chad. Citados nas reuniões: Algeria, Angola, South Africa, Cameroon, Iraq, Hungary, Germany, Turkey, Ireland, Tunisia, Republic of Congo.

## 2. Entregas

| País | Artefato | Versão | Data | Status |
|---|---|---|---|---|
| (transversal) | Automação drift-sync (compliance_sync.py, _docx_redline.py, README.md) | [INCERTO] sem número de versão | até 2026-07-07 | Construída, funcionando ponta a ponta (🟢) |
| Netherlands | CCG NL-CCG-001 — cópia redlined §7.1.4 (prova do drift-sync, ticket HRBS-1534) | — | até 2026-07-07 | Demonstração; redline aguarda aceite/rejeição humana [INCERTO se aceita] |
| (transversal) | Drift Console PoC (ticket sync + legislation watcher) | — | até 2026-07-07 | PoC para stakeholders |
| (transversal) | AUTOMATION_ROADMAP.md | — | 2026-07-07 | Publicado |
| (transversal) | Pipeline de compliance | v2.8 (citada em 30/06) → v2.9, 33 checks (roadmap) | jun–jul 2026 | Em uso; erro de parsing Stage 1→2 relatado na v2.8 |
| Países legados (Q2) | Artefatos de pesquisa | — | 2026-06-30 | Todos postados no Monday (segundo Manju); South Africa e Angola eram as últimas tarefas dela |
| Republic of Congo | Pesquisa | — | 2026-06-30 | Concluída (Wallisson); atualizar Monday |
| Chad | Pesquisa | — | 2026-06-30 | Concluída (Wallisson); design a avaliar na call de quinta |
| Algeria, Angola | Payslip facelift / design | — | 2026-06-30 | Marcar "Submitted for design" (Manju) |
| Cameroon | [INCERTO] artefatos | — | previsto até 2026-07-03 | Em atualização (Manju) |
| Iraq | [INCERTO] artefatos | — | semana de 2026-06-30 | Em atualização (Manju) |
| Hungary | Artefatos de integração (SIR) | — | 2026-06-30 | Aguardando feedback do Ilia sobre o arquivo de integração |
| Turkey | Payslip (saída de IA) | — | 2026-06-30 | Reprovado: não mostrava bruto e líquido por elemento |
| Canada | Pesquisa | — | 2026-06-30 | Em andamento (Wallisson) |
| Germany | Pesquisa / integração com autoridade fiscal | — | 2026-06-30 | Reinício previsto na semana seguinte (Manju) |

## 3. Decisões tomadas

- 2026-06-30 | Todos | Adicionar o status **"Submitted for design"** no Monday | Deixar claro o status entre pesquisa e design e excluir países já tratados do backlog de facelift | Proposto por Manju (Global Head of Compliance), acordado com Wallisson
- 2026-06-30 | Todos | Requisitos de integração estruturados **no nível de step** para todos os países | Comunicação padronizada com stakeholders | Grupo
- 2026-06-30 | Todos | **PII de cliente mascarada antes de qualquer processamento por IA** (tax IDs, datas de nascimento, nomes → números seriais), manualmente até existir o pré-processador | Alinhamento com ELT | ELT, comunicado por Manju
- 2026-06-30 | Todos | Payslips gerados **em lotes**, testando primeiro em um país antes de compartilhar o pipeline | Complexidade da estrutura visual; pipeline atual de payslip com baixa performance | Wallisson, a pedido de Manju
- 2026-06-30 | Todos | Pesquisa de integrações: **uma autoridade por vez** e IA deve destacar **interligações entre autoridades** | Melhorar detalhe da pesquisa | Sugestão de Manju, acordada pelo grupo
- 2026-06-30 | Todos | Atualização de skill file: usar **Projects do Claude** com o pacote completo de artefatos | Melhor memória e atualização precisa | Sugestão de Wallisson
- 2026-06-30 | Chad, Ireland | Usar Chad e Ireland como **baseline** das sessões de gap-filling de acurácia | — | Manju
- 2026-07-07 | Todos | Trigger por evento via **ferramenta externa de automação/scheduler** (ex.: n8n ou Zapier) entre YouTrack e Claude, e não trigger manual via MCP no navegador | YouTrack e Claude não disparam triggers sozinhos; time quer fluxo totalmente automático | Wallisson + Kriztian (consultoria), alinhado na reunião
- 2026-07-07 | Todos | Integração **QCRM** segue o plano existente YouTrack ↔ **Arbites**, separado deste projeto | Já faz parte do plano Arbites | Kriztian, com Manju
- 2026-07-07 (roadmap) | Todos | Leitura/escrita de ticket via **REST API ou MCP**; MCP preferível se houver write-back no ticket | MCP permite ler e atualizar | Roadmap (Wallisson)
- 2026-07-07 (roadmap) | Todos | Trigger natural = ticket **"Resolved"** (precisa de determinação confirmada), embora o fluxo tenha sido descrito como disparo na criação — **a confirmar** | — | Roadmap
- até 2026-07-07 | Todos | Política de modelo: Haiku (triagem), Sonnet (determinações e redline; drift-sync usa claude-sonnet-4-6), Opus só para reconciliações mais difíceis; Batch API para volume; prompt caching | Custo/qualidade | Instruções do projeto
- até 2026-07-07 | Todos | Caminho de produção para Drive = **service account membro de Shared Drive**; OAuth pessoal só como paliativo de demo | Workspace da Mercans bloqueia apps OAuth de terceiros | Instruções do projeto
- até 2026-07-07 | Todos | Sequência do roadmap: (0) PII masking → (2) trigger YouTrack → (3–5) legislation watcher, skill files, Monday sync em paralelo → (6–8) → (9–11) | — | Roadmap

## 4. Valores e regras estatutárias definidos

| País | Item | Valor | Vigência | Fonte citada |
|---|---|---|---|---|
| Netherlands | Base da 30% ruling — deduções pré-tax admitidas | Somente **salary sacrifice** reduz a base; dedução pré-tax de pensão e allowances (ex.: academia/gym) **não** reduzem | [INCERTO] não informada | Resolução do ticket HRBS-1534 ("based on the legislative aspect"); artigo de lei não citado no projeto |
| Netherlands | 30% ruling — percentual | Cai para **27%** | a partir de 2027 | Citado no roadmap como exemplo do legislation watcher; fonte primária não citada no projeto [INCERTO] |

Nenhum outro valor estatutário (alíquota, teto, faixa) está registrado neste projeto.

## 5. Erros e correções

| País | O que estava errado | O correto | Fonte | Onde aconteceu |
|---|---|---|---|---|
| Netherlands | Payslip interno divergia do payslip do cliente/simulação no cálculo da 30% ruling; cliente esperava que a dedução pré-tax de pensão reduzisse a base; questionada a exclusão do gym allowance | Só salary sacrifice reduz a base; pensão e gym não | Ticket HRBS-1534 (resolução de Wallisson) | Ticket de suporte; CCG NL-CCG-001 §7.1.4 tinha exemplo mas não dizia quais deduções pré-tax entram (drift detectado, confiança 92%) |
| Turkey | Payslip gerado por IA não mostrava bruto e líquido de cada elemento | Exibir gross e net por elemento | Reunião 2026-06-30 (Manju) | Pipeline de payslip |
| (pipeline) | Erro de parsing recorrente na transição Stage 1 → Stage 2 (v2.8) | [INCERTO] correção não registrada aqui | Reunião 2026-06-30 | Pipeline |
| (pipeline) | Falso positivo no check C20 | [INCERTO] correção não registrada aqui | Roadmap item 7 | Auditoria do pipeline |
| (segurança) | Chave da Anthropic API exposta recentemente | Rotacionar a chave no Passbolt (Jasper) | Roadmap, open items | [INCERTO] onde ocorreu a exposição |

## 6. Padrões e método

- Fontes primárias acima de tudo; amostras reais de filing de cliente e specs oficiais prevalecem sobre layouts pesquisados/derivados. Meta de acurácia ≥95% (reunião de 30/06 falava em perto de 90%).
- "tem certeza?" / "verifica" = reverificar de fato.
- Lente de fornecedor de software de folha: separar o que o motor calcula do que é responsabilidade estatutária do empregador.
- Humano no loop: automação nunca edita artefato vivo; gera tracked change (Word) ou rascunho; original sempre preservado. Redline do drift-sync tem autor "HRBLIZZ Drift Console" e comentário citando o ticket, inserido após o anchor da seção (ex.: "7.1.4 30% Ruling").
- Escopo RA: só WTC, DD, colunas RA das specs e CCG. Nunca editar planilhas de outros (ex.: Income Nature / Income Key da Lily Li).
- Idioma: responder no idioma do membro (PT ou EN); entregáveis para gestão/time sempre em inglês.
- Segredos só em .env local ou Passbolt; nunca em chat, código, prints ou anexos; não subir credentials.json, token.json, .env ao projeto.
- Skill files seguem o **padrão Chile de progressive disclosure** (router fino + subpasta `references/`).
- Pedido de amostras ao cliente: abrir as specs primeiro, listar os relatórios exatos, **um e-mail consolidado por country owner**.
- SI (Stage 6): discover-first (agente `si-discovery`, auto-fetch de artefatos públicos da AEAT, `[[NEEDS-ARTEFACT]]` só para itens fechados); classificação HAS_INTEGRATIONS / MANUAL_ONLY / NO_INTEGRATIONS; entregáveis P1–P7.
- Ambiente: Mac, zsh, Python 3.9; raiz `~/mercans-pipeline/` com `shared/` e `{CODE}-compliance/`; subagentes em `.claude/agents/`. Sem comentários `#` em comandos zsh colados; `pip3 install --user`; variáveis de ambiente via .env.
- Integrar ao pipeline único em vez de multiplicar ferramentas avulsas.
- Inconsistência a notar: o README do drift-sync ainda mostra `export ANTHROPIC_API_KEY=...` inline e `pip install`, o que contraria as regras de .env e `pip3 --user` das instruções.
- Custo estimado do drift-sync: US$ 0,01–0,05 por ticket com claude-sonnet-4-6.

## 7. Tickets e dúvidas de suporte

| Ticket | País | Pergunta | Resposta dada | Fonte | Mudou artefato? |
|---|---|---|---|---|---|
| HRBS-1534 | Netherlands | Por que o gym allowance ficou fora do cálculo da 30% ruling e por que a dedução pré-tax de pensão não reduz a base (divergência entre payslip interno e do cliente)? | Só salary sacrifice é dedução pré-tax admitida na base da 30% ruling; pensão e allowances como gym não reduzem | "Legislative aspect" (artigo não citado) | Sim, como proposta: tracked change + comentário em NL-CCG-001 §7.1.4 gerado pelo drift-sync; aceite humano [INCERTO] |

## 8. Pendências em aberto

Situação registrada em 2026-07-07; pode já ter sido resolvida fora do projeto.

- Escolher a ferramenta de automação para o trigger YouTrack (n8n / Zapier / similar) a partir do documento de opções do Kriztian (previsto ~2026-07-08) — time.
- Enviar e-mail de follow-up ao Kriztian confirmando o escopo da automação do research — Wallisson.
- Confirmar o evento de trigger (Resolved vs. criação) — time.
- Construir o pré-processador de mascaramento de PII (item 0, primeiro do roadmap) — Wallisson.
- Estender o drift-sync de CCG para WTC e DD — Wallisson.
- Provisionar Shared Drive de compliance + service account do Google — TI.
- Rotacionar a chave da Anthropic API no Passbolt — Jasper.
- Confirmar fontes oficiais por país para o legislation watcher — time.
- Roadmap Wave 1–3: legislation watcher, skill-file generator, Monday board sync, payslip batch generator, QA cross-check, gerador de pedidos de artefato ao cliente, assistente de SI, intake de arquivos criptografados (base `chad_decrypt_peek.py`; 11 arquivos OLE2 do Chad), knowledge-gap miner.
- Da reunião de 30/06:
  - Wallisson: pedir acesso aos boards de implementação; criar script de payslip em lote; passar ao Mohit os tickets YouTrack dos países concluídos; atualizar Chad no Monday; rascunhar plano de automação/legados para o Marco; follow-up com Ilia sobre o arquivo de integração (Hungary); melhorar o pipeline com o gap report em MD; incluir payslips e mudanças de integração estatutária na próxima atualização; explicar a metodologia do Canada à Manju.
  - Manju: e-mail ao Yoyo sobre conclusão dos legados do Q2; compartilhar link do BAU Master Client list; nota de status sobre necessidade de artefatos de cliente; marcar Algeria e Angola como "Submitted for design"; gerar artefatos de integração da Hungary; enviar logs de erro do Stage 2; pesquisar integração com autoridade fiscal da Germany.
  - Grupo: instruir a IA a destacar interligações entre autoridades; perguntar à IA quais lacunas resolver para refinar os dados; alinhar o design do Chad na call de quinta.
- Backlog de facelift de payslips: 30+ países (Wallisson 17, Inaki 11, Manju 8).

## 9. Fronteiras

- **QCRM**: integração YouTrack ↔ Arbites é projeto do time QCRM, separado deste.
- **Kriztian (Chris)**: está em outro time; apoio apenas consultivo (documento de opções de ferramentas). O research não tem dev dedicado e constrói sozinho.
- **Time do Kine**: mapeamento de produto e configuração após os requisitos serem submetidos.
- **Design**: recebe os artefatos marcados "Submitted for design" (ex.: facelifts de payslip).
- **Lily Li**: dona das planilhas Income Nature / Income Key; não editar.
- **Ilia Virchenko**: Integration / Config Factory; dá feedback sobre arquivos de integração (Hungary, Spain).
- **BAU** (ex.: Ahmed) e **implementação** (ex.: Daniel, Karim): fontes de relatórios/artefatos de cliente por país.
- **TI**: provisionamento de Shared Drive e service account.
- **Jasper Guevarra**: gestão da chave da Anthropic API no Passbolt.
- **Empregador vs. motor de folha**: obrigações estatutárias do empregador são separadas do que o motor calcula.
