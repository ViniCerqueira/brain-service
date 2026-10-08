# Colômbia

> Hub do país. Índice: [[00-INDEX]] · Skill: `payroll-compliance-colombia`

## Situação
| Etapa | Status | Data | Observação |
|---|---|---|---|
| [[research-pipeline]] | 🔄 | 2026-09 | Pesquisa CO "na fila depois da Bélgica" (chat: mercans-compliance); gap analysis atribuída ao Wallisson (HRBS-12487..13692). Mohit: CO exige "redesign ou ao menos grande correção de gaps" (~2026-08-29). |
| [[design]] | ⏳ | | [INCERTO] Colômbia citada como país sugerido para o próximo design (chat: design-dev-kb). Sem design registrado. |
| Produção (outro time) | — | | PMI em produção/BAU; transição para Instaroll em curso (outro time) |
| [[suporte]] | 🔄 | ~2026-09-03 | 5 tickets PMI sem resposta nossa no snapshot de 2026-09-16 |

## Ficha do país (da skill)
> Resumo do que mais importa para o serviço. Fonte: skill `payroll-compliance-colombia`, lida em 2026-10-02. Valores exatos e tabelas: ler a skill. Se divergir, vale a skill.

- **Escopo:** ano fiscal 2026, empregados do setor privado (CST), COP. Fora: servidores públicos, militares/polícia, independentes e contratistas.
- **Órgãos:** DIAN (retención, nómina electrónica, exógena), UGPP, MinTrabajo, MinSalud (PILA); EPS/AFP/fondos de cesantías, ARL e CCF.
- **Relatórios principais:** nómina electrónica (CO-RPT-001, SOAP/M2M, por período), Formulario 350 (retención, mensal), PILA (mensal, por operador privado), Formulario 220, Formato 2276 v4 (exógena, anual), depósito de cesantías (CO-RPT-006) e relatório MinTrabajo (CO-RPT-007).
- **Confiança da skill:** pesquisa de 2026-08-27, build do zero; veredito READY WITH DOCUMENTED GAPS; 15 itens abertos (1 fechado). Maioria das seções 92-97%; abaixo do piso de 95%: PILA 55%, Form. 350 60%, aprendizes 45%, reforma de pensão 70%, cesantías/MinTrabajo 25-30%. Listas de códigos de instituições (EPS/AFP/ARL/CCF) e bancos: 0%, não obtidas.

**Armadilhas confirmadas** (correções da skill)
1. SMMLV $1.750.905 vale pelo Decreto 0159 de 19-02-2026 (transitório), não pelo 1469/2025 (suspenso pelo Consejo de Estado) (engine) → `01-ccg.md`
2. Divisor da hora ordinária: 220 até 14-07-2026 e 210 desde 15-07-2026; 240 é obsoleto; folha de julho cobre os dois (engine) → `01-ccg.md` §5
3. Dominical/festivo sobe de 80% para 90% em 2026-07-01; semana de 42 h/divisor 210 só em 07-15; não juntar (engine) → `01-ccg.md` §5
4. Janela noturna começa às 19:00, não 21:00, desde 2025-12-25 (engine) → `01-ccg.md`
5. Exoneração ET art. 114-1: estritamente MENOS de 10 SMMLV; em $17.509.050 perde; CCF 4% e pensão 12% nunca exonerados (engine) → `01-ccg.md`
6. Três bases, três tetos: IBC (1 a 25 SMMLV = $43.772.625), base parafiscal (sem teto) e base de retención; não reusar (engine) → `01-ccg.md`
7. Pacto não salarial: limite de 40% (Ley 1393 art. 30) só para seguridade social; excesso volta ao IBC (engine) → `01-ccg.md`
8. Renta exenta de 25% calculada por último, depois do limite combinado 40%/1.340 UVT; 72 UVT/dependente fica fora do limite (engine) → `01-ccg.md`
9. FSP é linha própria do empregado (1% desde 4 SMMLV + subcuenta 0,2-1,0% desde 16 SMMLV), não parte dos 4% de pensão (engine) → `01-ccg.md`
10. Três regimes de arredondamento no mesmo mês (PILA, XML da nómina, formulários DIAN); isolar resíduo em `Redondeo` (engine) → `01-ccg.md` §11
11. Vacaciones não são prestação social; entram no IBC e na base parafiscal; salario integral não absorve vacaciones (engine) → `01-ccg.md`
12. Enum de horas extras do Anexo Técnico DIAN (§5.5.5) está desatualizado (dominical 100/75/150/110) e é obrigatório: conflito não resolvido (engine) → `07-qa-report.md` Q-3
13. Reforma de pensão (Ley 2381/2024) não vale em 2026 (Auto 841/2025 suspendeu); não fixar a data de 2027-04-01, só imprensa → `07-qa-report.md` Q-24
14. Não há artigo do CST sobre conteúdo do payslip; vale Res. DIAN 000013/2021 arts. 5 e 24 (13 itens; QR ≥ 2 cm se emitir) → `06-payslip.md`
15. ARL Classe IV máximo é 6,060% (6,960% é o valor inicial da Classe V) → `07-qa-report.md` D-1

**O que mais dá errado** (do QA)
- Quatro defeitos em documentos oficiais: ARL IV (D-1), exemplo de CUNE do Anexo Técnico não reproduz (D-2), data impossível no exemplo de QR (D-3), enum de horas extras desatualizado (D-4). Não usar os exemplos do Anexo como teste de conformidade.
- Riscos vivos de cálculo: divisor 210 (Q-19, ~88%, doutrina administrativa lida em espelho) e enum DIAN (Q-3).

**Lacunas abertas / não confirmado** (candidatos a ticket ou nova pesquisa)
- Não dá para gerar arquivo PILA (Q-10) nem declaração Formulario 350 (Q-23); aprendizes (Q-5, 45%) e `AltoRiesgoPension` (Q-14) não configuráveis.
- Q-2: apropriação mensal dos tetos anuais de 790 e 1.340 UVT é DERIVADA (÷ 12, ~75%).
- Q-4: sem código de documento para PPT; Q-6 e Q-7: tarifa dos 2 primeiros dias de incapacidade e piso mínimo; Q-8: aportes em licença não remunerada.
- Q-11 (Formato 2276 encoding, 70%) e Q-12 (relatório MinTrabajo, 25%); códigos de EPS/AFP/ARL/CCF e bancos não obtidos.
- Q-21: auxilio de transporte na base de prestaciones é prática consolidada, não lei (~90%).

**Valores-âncora** (2026; fonte: SKILL.md e `01-ccg.md`)
| Item | Valor | A partir de | Fonte |
|---|---|---|---|
| SMMLV | $1.750.905 (transitório) | 2026 | Decreto 0159 de 2026-02-19 |
| UVT | $52.374 | 2026-01-01 | Res. DIAN 000238 de 2025 |
| Auxilio de transporte | $249.095 (até 2 SMMLV) | 2026 | Decreto 1470 de 2025 |
| Saúde / pensão | 12,5% (4/8,5) / 16% (4/12); IBC 1 a 25 SMMLV | 2026 | Ley 100 arts. 18, 20, 204; Ley 797/2003; Ley 1122/2007 |
| Parafiscales | CCF 4%, SENA 2%, ICBF 3% | 2026 | Ley 21/1982; Ley 89/1988 |
| Dominical/festivo | 80% até 2026-06-30; 90% desde 2026-07-01 | 2026-07-01 | CST art. 179 par. trans.; Ley 2466 art. 14 |

## Artefatos entregues
| Artefato | Versão | Data | Arquivo/local | Observação |
|---|---|---|---|---|
| Skill `payroll-compliance-colombia` | n/a | n/a | skill Mercans | Existe (uso como consulta) |
| WTC CO | sem versão citada | — | — | WTs citados nos tickets: 63123, 62837, 52552, 21125, 64993, 2552–2556, 21330, 22110, 22112. Redesign/gap fixing pendente. |
| Board de validação estatutária por IA | — | prazo 2026-12-21 (prioridade Medium) | Monday | Status "Not Started" (chat: design-dev-kb) |

## Valores-chave (com vigência)
> Os valores dos tickets foram **declarados pelo solicitante (PMI)**, não validados por nós. Conteúdo estatutário geral: ver a skill.

| Item | Valor | A partir de | Até | Fonte |
|---|---|---|---|---|
| Taxa máxima ARL Classe IV | 6,060% | ⚠️ vigência? ("vigente") | | normograma.mintic.gov.co (chat: mercans-compliance) |
| UVT | COP 52.374 | 2026-01-01 (ano fiscal 2026) | | DIAN Resolução 000238 de 15/12/2025 (HRBS-13627, citada pelo solicitante) |
| SMMLV | COP 1.750.905 | 2026 | | skill (Decreto 0159 de 2026-02-19, transitório; Decreto 1469/2025 suspenso) (declarado em HRBS-12491) |
| Limite vacation bonus para SS + retenção | 95 UVT | 2026 (offcycle sem. 31/2026) | | ⚠️ sem fonte (HRBS-12487) |
| Fórmula do bônus de férias | ROUND(Total Días × 2,8 × salário base mensal / 30; 0); Total Días = Days Taken + Cash Out | ⚠️ vigência? | | regra do cliente/sistema, ⚠️ sem fonte legal (HRBS-12487) |
| Embargo (garnishment) | 1/5 do excedente sobre o SMMLV, após deduzir 2552/2553/2554/2556; base ≤ SMMLV = 0 | ⚠️ vigência? | | ⚠️ sem fonte legal (HRBS-12491) |
| Pagamentos não salariais | máx. 40% da remuneração total; excesso entra no IBC | ⚠️ vigência? | | Lei 1393/2010 (citada, HRBS-12492) |
| IBC mín./máx. | 1 SMLMV / 25 SMLMV | 2026 | | skill (Ley 100 de 1993 arts. 18/20/204; Ley 797 de 2003; Ley 1122 de 2007; IBC 1 a 25 SMMLV) (HRBS-12492, citado pelo solicitante) |
| Saúde | 12,5% (EE 4% / ER 8,5%); ER exonerado até 10 SMLMV | 2026 | | skill (Ley 100 arts. 18/20/204; Ley 1122/2007; exoneração: ET art. 114-1; ver Pendências, divergência 1) (HRBS-12492) |
| Pensão | 16% (EE 4% / ER 12%) | 2026 | | skill (Ley 100 de 1993; Ley 797 de 2003) (HRBS-12492) |
| Parafiscales | Caja 4%, ICBF 3%, SENA 2% (ICBF/SENA exonerados até 10 SMLMV) | 2026 | | skill (Ley 21 de 1982; Ley 89 de 1988; exoneração: ET art. 114-1; ver Pendências, divergência 1) (HRBS-12492) |
| IBC nas férias | salário do mês anterior ao início das férias | ⚠️ vigência? | | Art. 3 Decreto 1072/2015 e guias PILA (citados, HRBS-12492) |
| Isenções/deduções de retención | auxílio alimentação 41 UVT/mês (Art. 387-1); juros moradia 100 UVT; medicina pré-paga 16 UVT; dependentes máx. 32 UVT; AFC+VFP 30% (Art. 126-1); renda isenta 25% = 790 UVT/ano (Art. 206-10); limite global 40% / 1.340 UVT/ano (Art. 388) | 2026 | | E.T., citados pelo solicitante (HRBS-13627) |
| Tabela Art. 383 | 0–95 UVT 0%; até 150 19%; até 360 28%; até 640 33%; até 945 35%; até 2.300 37%; acima 39% | 2026 | | Art. 383 E.T. (HRBS-13627) |
| Expat / não residente | 20% sobre total tributável (configuração do cliente) | ⚠️ vigência? | | ⚠️ sem fonte legal (HRBS-13627) |
| Cesantías / intereses | 1 mês por ano; juros 12% a.a. (cesantías × 12% × dias/360); base variável conforme Art. 253 CST | ⚠️ vigência? | | Art. 253 CST (citado); resto ⚠️ sem fonte (HRBS-13692) |

## Decisões
- ~2026-08-29: Colômbia "requires a redesign or at least a major gap fixing work" — Mohit Jain, Head of Compliance Product (HRBS-12487..13692)
- ~2026-09-03: os 5 tickets PMI de transição Instaroll vão para a gap analysis da pesquisa CO, atribuídos ao Wallisson — Mohit Jain, após conversa com Manju (HRBS-12487..13692)

## Suporte (tickets)
Contexto comum: lista "PMI Instaroll Transition Tracker" (ELT); cliente PMI (Compañía Colombiana de Tabaco SAS, REF-LE-00-505). Nenhuma resposta nossa em nenhum dos cinco (snapshot 2026-09-16).

| Data | Ticket | Assunto | Resolução | Mudou artefato? |
|---|---|---|---|---|
| ~2026-09-03 | HRBS-12487 | Automação do vacation bonus offcycle acima de 95 UVT (WTs 63123/62837/52552) | Sem resposta nossa; Pending on reporter; gap analysis | Não |
| ~2026-09-03 | HRBS-12491 | Explicação do cálculo de embargo (itens 21125, 64993) | Sem resposta; Romano perguntou nº de embargos por período, sem retorno | Não |
| ~2026-09-03 | HRBS-12492 | Regras de contribuição de SS (40% Lei 1393, exonerações, IBC nas férias) | Sem resposta; Pending on reporter | Não |
| ~2026-09-03 | HRBS-13627 | Explicação do cálculo de retención en la fuente (2552, 21330) | Sem resposta; Open, resolução estourada (−20d) | Não |
| ~2026-09-03 | HRBS-13692 | Provisões de cesantías e intereses (22110, 22112) + relatório de consolidação | Sem resposta; Open, resolução estourada (−19d) | Não (novo report sem spec) |

## Pendências
- [ ] Gap analysis dos 5 tickets PMI dentro da pesquisa CO — Wallisson — (HRBS-12487, 12491, 12492, 13627, 13692)
- [ ] Acumulado anual do limite de 1.340 UVT: o validador do cliente aplica 1.340 ÷ 12 por mês, risco de sub-retenção — Wallisson/Compliance — (HRBS-13627)
- [ ] Confirmar se o sistema calcula o IBC de férias sobre o bruto do mês (observação do Support, 4 dias de férias) — Compliance/Dev — (HRBS-12492) [INCERTO]
- [ ] Spec de report de consolidação de cesantías (inexistente) — Compliance/Reports — (HRBS-13692)
- [ ] Validar os valores declarados pelo cliente contra fonte oficial/skill antes de usar como confirmados — Wallisson — (todos)
- [ ] Pesquisa CO "na fila depois da Bélgica" no pipeline — Wallisson — (chat: mercans-compliance)
- [ ] Divergência hub × skill: Valores-chave diz "ER exonerado até 10 SMLMV" (saúde, SENA, ICBF); a skill diz estritamente MENOS de 10 SMMLV (ET art. 114-1; em $17.509.050 perde a exoneração) — verificar (skill lida em 2026-10-02)
- [ ] Divergência hub × skill: Valores-chave lista dependentes "máx. 32 UVT" (declarado pelo PMI); a skill traz também 72 UVT/dependente (ET art. 336 num. 3, máx. 4, fora do limite 40%/1.340 UVT) além do art. 387 (10%, máx. 32 UVT/mês) — verificar (skill lida em 2026-10-02)
- [ ] Divergência hub × skill: Pendência sobre 1.340 UVT ÷ 12 do validador do cliente como risco de sub-retenção; a skill adota ÷ 12 como convenção do engine, mas DERIVADA (~75%, Q-2), sem regra mensal no DUR 1625 — verificar (skill lida em 2026-10-02)
- [ ] Divergência hub × skill: IBC das férias "salário do mês anterior" (HRBS-12492) e fórmula do embargo (HRBS-12491), bônus de férias 95 UVT (HRBS-12487) e cesantías base variável não aparecem na skill (SKILL.md/QA; embargo só como "inembargable" no CCG) — verificar (skill lida em 2026-10-02)
- [ ] Divergência hub × skill: Situação mostra Research 🔄 "na fila"; a skill traz pesquisa CO concluída em 2026-08-27 (READY WITH DOCUMENTED GAPS) — verificar (skill lida em 2026-10-02)

## Correções ligadas
- [[correcoes]]: taxa máxima ARL Classe IV estava errada em batch anterior; correto 6,060% (normograma.mintic.gov.co) (chat: mercans-compliance)

## Fontes
- raw/tickets/extracao/2026-10-02-tickets-OUT.md
- raw/chats/2026-10-01-mercans-compliance.md
- raw/chats/2026-10-01-mercans-design-dev-kb.md
- skill payroll-compliance-colombia (lida em 2026-10-02)
