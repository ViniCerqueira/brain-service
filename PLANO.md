# Plano de ação: Brain Service

> Índice: [[00-INDEX]] · Regras: [[CLAUDE]] · Atualizado em 2026-10-05

## Fase 0: Estrutura ✅ (2026-10-01)
- [x] Pasta, `CLAUDE.md` (comandos ingere / responde / fechei o ticket / revisa), modelos, prompts
- [ ] **Você:** abrir `Documents\brain-service` como vault no Obsidian

## Fase 1: Capturar contexto ✅ em grande parte (2026-10-02)
- [x] 3 projetos do Claude da Mercans extraídos → `raw/chats/` (compliance-research, mercans-compliance, design-dev-kb)
- [x] 101 PDFs do YouTrack (58 tickets, 04/08–29/09/2026) → `raw/tickets/`
- [x] Fichas das 38 skills `payroll-compliance-*` nos hubs
- [ ] **Você:** extrair conversas de setembro em diante do projeto Mercans Compliance com [prompts/extracao-conversa.md](prompts/extracao-conversa.md) (uma conversa por vez)
- [ ] **Você:** nome da variável do token no `.env` → rodar `scripts/youtrack_fetch.ps1` desde 2026-01-01 (histórico antes de agosto + respostas depois de 29/09)

## Fase 2: Consolidar ⏳ (em andamento desde 2026-10-05)
- [x] 49 hubs de país, 67 correções, notas de serviço e fronteiras
- [x] Regra 8: versão vigente = maior versão
- [ ] Claude: revisão dos hubs (regra 8, triagem de [INCERTO], propostas para divergências hub × skill) → relatório em `revisoes/`
- [ ] **Você:** aprovar/rejeitar as propostas do relatório
- [ ] **Você:** responder às perguntas de 1 linha (serviço, Design, produção/ativação, SIR, decisões pendentes)

## Fase 3: Usar e medir (1 a 2 semanas após a Fase 2)
- [ ] Trabalhar sempre com sessão aberta nesta pasta
- [ ] A cada ticket/entrega: "fechei o ticket X" / "entreguei Y"
- [ ] Puxar tickets do YouTrack 1×/semana e "ingere"
- [ ] Anotar em [[log]]: ✅ contexto que não precisou repetir · ❌ erro repetido · ⏱️ minutos de manutenção/dia

## Fase 4: Decidir
| Resultado | Decisão |
|---|---|
| Economizou tempo e manutenção < 10 min/dia | Manter e escalar |
| Ajudou pouco | Manter só [[correcoes]] e levar as correções para as skills |
| Não ajudou | Encerrar |

## Fase 5: Escalar
- [ ] Skills para Ucrânia → Namíbia → Gabão (Stage 11, com o pacote de correções do cérebro; pipeline na outra máquina)
- [ ] Levar correções consolidadas para as skills ("revisa o cérebro")
- [ ] Claude Desktop (Filesystem ou MCP do Obsidian) e plugin para o time
- [ ] "revisa o cérebro" semanal
