# Tickets YouTrack: Ucrânia (UA)

> Fonte: 40 snapshots em `raw/tickets/txt/` (grupo UA), 18 tickets distintos. O snapshot `03 - Ticket SR-340 UA - Payslip` foi lido pelo PDF original (imagem).
> **Datas:** o YouTrack imprime datas relativas ("14 days ago"). As datas abaixo foram calculadas a partir da data de impressão do snapshot e são **aproximadas (~)**, com margem de ±1 dia (ou ±1 mês quando o ticket diz "X months ago").
> **Texto em cirílico:** o pdftotext perdeu quase todo o cirílico (aparece em branco). Onde o termo ucraniano faltava, o texto foi mantido como está, sem reconstruir.
> **Papéis (lado Mercans/HRBlizz), conforme aparecem nos tickets:** Wallisson dos Santos Gomes = Research Analyst / Compliance (nós). Lily Li = Business Analyst (BA). Michael Mukosi John = Developer. Mohit Jain = Head of Compliance Product. Vaishnavi Mane = configuração / payroll [INCERTO: papel exato não declarado]. Abarna Khaliq = Senior Specialist-Configurations. Archit Naik = L2 Support. Nataliia Hahan = quem abre quase todos os tickets HRBS da Ucrânia, especialista local de payroll UA do lado Mercans [INCERTO: papel/time não declarado no ticket; o Phase dos tickets é "Live/BAU" ou "Implementation"].

---

## HRBS-12181: Ukraine WTC update (série BIK "PIT sem Military Tax" e gross-up)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / Altium (REF-04-254 Altium Ukraine) / Service Request, Tier 3, Support Group Compliance Support / Medium / **Resolved** (snapshot de 2026-09-01; SLA status "Breached") / criado ~2026-07-21; última atualização ~2026-08-18 (Lily Li); resolvido entre ~08-17 e 09-01.
- **Arquivos-fonte:** `05 - Ticket - HRBS-12181 - Ukraine WTC update.txt` (08-05), `14 - ...` (08-12), `36 - ...` (09-01).
- **Evolução entre snapshots:** 08-05 Paused/SLA Exempt, assignee Wallisson, só a 1ª resposta (v3.5). 08-12: mais 5 trocas (gross-up, v3.7, regra de motor, escopo de 109 códigos, correção da Nataliia, limite de 20 PEs). 09-01: Resolved, assignee Lily Li, com a resposta v3.8 e o link do WTC finalizado. Inward mentions: HRBS-11702 e CT-4537 ("UA: Ukraine Regulation Support").
- **Quem pediu:** Nataliia Hahan (pedido original, em nome da Altium); Vaishnavi Mane (configuração); Lily Li (BA) repassou para Compliance.
- **Pergunta / problema:** a Altium pediu uma série nova de wage types BIK com PIT = Sim, mas Military Tax e USC = Não, para 8 códigos (65816, 65805, 65806, 65810, 65808, 65812, 65720, 62224), e o gross-up de benefícios não monetários com o coeficiente 1.219512 (2026). A Vaishnavi também apontou códigos 4DF que não achou no WTC de compliance (103, 109, 124, 157, 169), a falta de um código de "Mobilization (without pay)" e uma dúvida sobre 160/126 (presentes).
- **Resposta / decisão nossa:**
  - **~2026-08-03 (WTC v3.5):** *não criar* a série "PIT only, no Military Tax", porque não tem base legal: o Military Tax segue a base do PIT e nenhuma exceção cobre esses itens. Essa combinação não existe em nenhuma das 1281 linhas do WTC. Os códigos existentes de seguro médico/vida e presentes (62610-619, 65630, 58113, 65801, 65804) já estão corretos como PIT=Sim/Military=Sim/USC=Não. Sobre os códigos 4DF: 103/109/157 não são de payroll de empregado (royalties/dividendos/pagamento a contractor); para o 124 (exclui contribuições pagas pelo empregador), usar o 125; o 169 é um código estreito de ajuda de caridade (confirmar com o cliente). Mobilization foi criado como **79417**, sem pagamento nem imposto. Também apontamos que os números de código da Lily não batem com os do ticket (ex.: 65816).
  - **~2026-08-06 (WTC v3.7):** gross-up confirmado no 65816: base do PIT = valor × 1.219512 e base do Military = valor sem ajuste. No exemplo da Nataliia, a base certa é **2.439,02** (não 2.360) e o PIT de 18% é **439,02**; o Military continua 100 sobre 2.000. Os códigos 65805/65806/65808/65810/65812 foram nomeados (Medical, Life, Family Insurance, Representation Expenses), e 65720/62224 conferidos. Ponto em aberto para a Altium: o Art. 170.9 PKU isenta de PIT as despesas de representação documentadas e com finalidade publicitária. 65806/65808 ficaram PIT=Sim como o cliente descreveu, mas é preciso confirmar se algum deles deveria virar PIT=Não.
  - **~2026-08-11:** base legal: o coeficiente 1.219512 do Art. 164.5 PKU vale só para a base do PIT. A base do Military Tax (§16-1, pidrozd. 10, rozd. XX PKU, Disposições Transitórias) não incorpora o coeficiente (posição atual da DPS, orientações 2025-2026). A citação foi incluída no WTC V3.7. Achado: a coluna Formula do 65816/65801/65804 está em branco, e essa coluna não serve para definir a base de cada imposto. A separação PIT/Military tem de ser **regra de motor** para wage types de Category=Benefit. Se o motor tributa as duas bases pelo valor com gross-up, é defeito do motor, não lacuna do WTC (sinalizado para "Drew" [INCERTO: provavelmente Dev/engine]).
  - **~2026-08-12:** o gross-up é por **categoria**, não por lista fixa como na Espanha. São 109 wage types com 4DF=126 (BIK), e o gross-up deve ser chaveado por 4DF=126. Os 51 códigos genéricos "Benefit Earning" (65805, 65807, 65809, 65810-65859) são placeholders do template global e não foram renomeados.
  - **~2026-08-12/13 (WTC v3.8, destaques em verde):** aceitamos a correção da Nataliia. O coeficiente só se aplica a renda em **forma não monetária** (pp. 164.2.17 PKU). Um pagamento em dinheiro ligado à remuneração é salário (101), não BIK (pp. 14.1.47/14.1.48 PKU). Como a Lily informou que o sistema só suporta **20 PEs de benefício com gross-up**, definimos os 20 (35 códigos Mercans, contando arrears/adjustment/notional): Housing (65400-402), Housing Utility (65410), Company car private use (65500-502), Car notional (65508/65509), Car Fuel (65520-523), Phone (65600-602/65608), Phone notional (65609), Phone 2 (65620), Meal (65650-652), Meal notional (65659), Meal Vouchers (65670-672), Education (65720), Gift/prize in-kind (65801), Gym (65802), Employer-paid education taxable part (65803), Private medical services taxable part (65804), Medical Insurance (65805), Life Insurance (65810), Family Insurance (65812), Additional Benefit 1 (65816). Renomeamos 65805/65810/65812/65816 e retiramos a citação do coeficiente de 65806/65808 (Representation Expenses: forma monetária, fora dos 20).
  - A Lily ajustou o código de alguns benefícios e publicou o WTC "finalizado" com a matriz de tributação de benefícios (~08-13). O desenvolvimento do gross-up (PIT sim, Military não) ficou com a Lily/Dev.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Coeficiente natural de gross-up (benefício não monetário) | 1.219512, só na base do PIT | 2026 (o ticket diz "applicable for 2026") | Art. 164.5 PKU; pp. 164.2.17 PKU |
| Base do Military Tax para BIK | valor bruto, sem coeficiente | posição DPS 2025-2026 | §16-1, pidrozd. 10, rozd. XX PKU |
| PIT | 18% | sem vigência no ticket | sem fonte no ticket (no exemplo) |
| Military Tax / Levy | 5% | sem vigência no ticket | sem fonte no ticket (no exemplo) |
| Presentes: parte não tributável (código 4DF 160) / excedente (126) | limite de "25%" (citado pela Vaishnavi) | sem vigência no ticket | sem fonte no ticket [INCERTO: 25% de quê; ver HRBS-14324] |
| Despesas de representação documentadas, com finalidade publicitária | isentas de PIT | sem vigência no ticket | Art. 170.9 PKU |
| Additional benefit (definição) | renda não ligada à obrigação do empregador na relação de emprego | sem vigência no ticket | pp. 14.1.47 / 14.1.48 PKU |

- **Artefato afetado:** WTC (Ukraine_Wage_Type_Catalogue_Mercans) v3.4 → v3.5 → v3.7 → **v3.8**. Códigos novos: 79417 (Mobilization).
- **Erros corrigidos:**
  - O WTC "v3.5" foi entregue com nome de arquivo V3.4 e sem controle de versão (apontado pela Lily). Corrigido; depois a Lily converteu para Google Sheets.
  - No WTC v3.7 só 2 dos PEs tinham sido renomeados (apontado pela Lily). Corrigido na v3.8.
  - O changelog da v3.7 dizia que 65801/65804 já tinham o coeficiente na fórmula, mas a coluna estava vazia.
  - O escopo do gross-up mudou de "todos os 109 códigos 4DF=126" (nossa resposta de ~08-12) para "só os não monetários, limitados a 20 PEs" (correção da Nataliia, que confirmamos).
  - O exemplo da Nataliia tinha a base do PIT errada (2.360 → 2.439,02; PIT 439,03 → 439,02).
- **Pendências:** confirmação da Altium sobre 65806/65808 (Art. 170.9: despesa documentada e publicitária → PIT=Não?). Confirmação com o cliente do uso do 4DF 169. Pergunta da Nataliia sobre indexação (índice CPI mensal + "base month" por empregado: campo/tabela ou fórmula?), **sem resposta neste ticket** (o HRBS-13392 diz depois que o base month está coberto pelo campo "Effective Date of Current Salary"). Desenvolvimento do gross-up (Lily/Dev).
- **Fronteira:** a separação PIT/Military é regra de motor (Dev/"Drew"). O limite de 20 PEs de gross-up é restrição do produto (Mohit/Lily). A atribuição de códigos é da BA (Lily).

---

## HRBS-12368: Ukraine Data Dictionary e master data file para EEs
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / Altium Ukraine / Service Request, Tier 3, Compliance Support / Medium / **Paused, SLA Exempt** (último snapshot 2026-08-17), assignee Wallisson / criado ~2026-07-27; última atualização ~2026-08-17.
- **Arquivos-fonte:** `15 - ...HRBS-12368...` (08-12), `19 -Ticket - HRBS-12368...` (08-13), `22 - ...HRBS-12368...` (08-17).
- **Evolução:** 08-12 e 08-13: só o pedido e a troca com Abarna Khaliq, até a Lily repassar para Compliance. 08-17: nossa entrega do DD v3.5 e o novo pedido da Nataliia (apagar o option mapper de Region).
- **Quem pediu:** Nataliia Hahan; Abarna Khaliq (Senior Specialist-Configurations) avaliou primeiro se os campos eram de nível país; Lily Li (BA) repassou.
- **Pergunta / problema:** ao validar o Master Data contra o DD V3.4, a Nataliia achou 15 campos usados no payroll/HR da Ucrânia que faltam em Country Fields (Ukraine): 1C Personnel Number, nome em ucraniano, dados do passaporte, salário oficial em UAH, data de vigência da taxa de ESV, certificado de deficiência, titular da conta bancária etc. Seis deles precisavam de decisão de configuração. Pediu também ajustes de option mapper (short names de tipo de contrato e de Disability Group III, Part-Time Indicator no mapper, Region sem option mapper).
- **Resposta / decisão nossa (~2026-08-13, Ukraine_Data_Dictionary_V3.5):**
  - Adicionados em Country Fields: 1C Personnel Number, Name (Ukrainian), Email, Residential Address: Suburb, Division (1C Department), Cost Centre (Department), Monthly Salary (UAH) Gross official, Effective Date of Current Salary, FTE (Rate), [ESV] Rate Effective Date, Disability Certificate (series, issue date), Bank 1 Account Holder.
  - Adicionados em ID Information (junto de passport_number): Passport: Issued By, Passport: Issue Date.
  - **Não adicionado:** Monthly Salary (USD) gross. Pela descrição (indexação, férias, fórmula tipo bônus), é lógica de wage type do WTC, não master data do DD (pedimos confirmação).
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| ESV (taxa padrão / taxa de deficiência) | 22% / 8.41% (o campo "Rate Effective Date" serve para dividir a base no mês em que começa a deficiência) | sem vigência no ticket | sem fonte no ticket |

- **Artefato afetado:** DD V3.4 → **V3.5**.
- **Erros corrigidos:** nenhum declarado.
- **Pendências:** a Nataliia (~08-17) pede para apagar o campo de option mapper de Region (sem resposta no snapshot). Confirmação da Nataliia de que o salário em USD vai para o WTC. Insurance Record (para auxílio-doença) não entrou aqui e foi tratado no HRBS-13389. Decisões de configuração (Division ↔ conta contábil; Cost Centre para o relatório GTN) não detalhadas.
- **Fronteira:** Configurations (Abarna) avaliou primeiro "country level vs. client". O salário em USD foi apontado como lógica de WTC/configuração.

---

## HRBS-12548: Ukraine Statistic reports (1-PV mensal/trimestral, relatório de licença médica do Pension Fund, relatórios internos)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / Altium Ukraine / Service Request, Tier 3, Compliance Support / Medium / **Paused, SLA Exempt** (único snapshot 2026-08-07), assignee Wallisson / criado ~2026-07-30; última atualização ~2026-08-02.
- **Arquivos-fonte:** `08 - Ticket - HRBS-12548 - Ukraine Statistic reports.txt`.
- **Quem pediu:** Nataliia Hahan; Lily Li repassou a Wallisson (~07-31).
- **Pergunta / problema:** (1) incluir no escopo os relatórios estatísticos 1-PV mensal e trimestral (templates anexados: S0301016 e S0301121); (2) criar relatórios internos para cruzar com os estatísticos; (3) relatório do Pension Fund ligado a licença médica (a "Tab. 2" é a mais importante); (4) relatório interno de salário médio para licença médica, férias e viagens a trabalho.
- **Resposta / decisão nossa:** não há resposta nossa neste snapshot. O ticket originou as specs **SR-414** (1-PV mensal) e **SR-415** (1-PV trimestral), que aparecem como inward mention nelas.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Report Specs UA-1PV-001 e UA-1PV-002 (ver SR-414/415).
- **Pendências:** relatório do Pension Fund para licença médica (Tab. 2), relatórios internos de cruzamento e de salário médio [INCERTO: não há registro de tratamento nos snapshots].
- **Fronteira:** relatórios internos/de cliente podem ser de configuração/Dev [INCERTO: o ticket não diz].

---

## HRBS-12631: Ukraine Reserve vacation report (saldo de férias + salário médio + revisão do CCG)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / Altium / Service Request, Tier 3, Compliance Support / Medium / **Pending on reporter** (último snapshot 2026-09-28), assignee Lily Li / criado ~2026-08-03; última atualização ~2026-08-18 (Nataliia).
- **Arquivos-fonte:** `04 - ...HRBS-12631...` (08-05), `25 - ...` (08-19), `46 - ...` (09-07), `93 - ...` (09-28).
- **Evolução:** 08-05: assignee Wallisson, com o pedido, a resposta da Lily e o comentário da Nataliia sobre salário médio. 08-19: assignee passou para Lily Li, já com as duas respostas nossas (WTC v3.6/CCG v1.1 e CCG v1.2) e o pedido final da Nataliia. 09-07 e 09-28: sem novidades (o ticket parou em "Pending on reporter").
- **Quem pediu:** Nataliia Hahan; Lily Li (BA).
- **Pergunta / problema:** a Altium quer o cálculo automático da reserva de férias por empregado (dias de direito, usados e restantes, proporcionais ao tempo trabalhado; padrão de 24 dias/ano contados da data de admissão) e um relatório exportável. Depois a Nataliia levantou as regras de salário médio e fez uma revisão detalhada do CCG (prazo do PIT/ML, semana 53, frequência do 4DF, proração, base mínima do ESV).
- **Resposta / decisão nossa:**
  - **Lily (~08-03):** os dias e o saldo de férias podem entrar como PE 79xxx no WTC, mas não são calculados automaticamente no payroll, porque são do **leave module** (com a Vaishnavi).
  - **Wallisson (~2026-08-05, WTC v3.6, CCG Module 8 v1.1):** férias = 12 meses (§7), já certo no CCG. **Donor leave** = 2 meses (§8), novo tipo de licença no CCG (LC Art. 124) e novo WT **79414**. **Business trip** = 2 meses (§8), novo WT **79415**; paga o MAIOR entre a média de 2 meses e a diária do próprio mês da viagem (LC Art. 121 §4). Sick leave = 12 meses, mas por outro regulamento (**Postanova No. 1266**, não No. 100); incluímos nota no CCG para ele não ser construído com a fórmula de férias. A seção de salário médio do CCG, que era uma fórmula única de 12 meses, foi dividida nos casos de 12 e de 2 meses. Campos e relatório de saldo de dias continuam com a Vaishnavi.
  - **Wallisson (~2026-08-11, CCG v1.2):** checamos cada ponto contra a lei.
    1. Prazo de PDFO/Military Levy: os "3 dias bancários" valem só para renda não monetária ou dinheiro do caixa. Em salário por transferência bancária, o imposto é devido no momento da transferência (TCU Art. 168.1, confirmado pela DPS). Corrigido no Module 1.2.
    2. Base mínima do USC no mês de admissão/desligamento: **não se aplica** (nem proporcional), e o USC incide sobre o salário real. Corrigido nos Modules 4.4 e 5.1.1 (Instruction 449 s.III).
    3. Empregado com deficiência (8.41%): sem complemento até a base mínima. Corrigidos a tabela de taxas, o pseudo-código (agora exclui is_disabled) e a nota de dev (Instruction 449 s.III; DPS 04.02.2026 676/[...]).
    4. Proração: mudou de dias corridos para **dias úteis** (cartas de 27.05.2019 nº 4340 e 15.04.2019 nº 553; o órgão emissor sumiu na extração do cirílico [INCERTO]), e saiu a citação errada do Art. 115.
    5. Frequência do 4DF: **mensal** para pessoa jurídica, como anexo do cálculo unificado mensal (a partir de 2026-01-01, Law 4536-IX; formulários pelas MinFin Orders 4/243/284). Só FOPs entregam trimestral. Corrigido nos Modules 6.6, 10.3 e 1.2.
    6. **Não mudou:** a ressalva "(if main place of work)" do contrato civil (CPC) fica. Se o contractor também é empregado do mesmo empregador, o valor soma ao salário e o total é testado contra a base mínima; no contractor puramente externo não há mínimo.
    7. A seção da semana 53 está rotulada "rare, permitted" como orientação de motor, não regra legal; oferecemos o rótulo "theoretical".
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Período-base do salário médio de férias | 12 meses | sem vigência no ticket | Postanova/Poryadok No. 100, §7 (como citado) |
| Período-base de donor leave e business trip | 2 meses | sem vigência no ticket | Poryadok No. 100, §8; LC Art. 124 (donor) |
| Business trip: pagamento | maior entre a média de 2 meses e a diária do mês da viagem | sem vigência no ticket | LC Art. 121 §4 |
| Período-base de sick leave | 12 meses | sem vigência no ticket | Postanova No. 1266 |
| Prazo de PDFO/ML (salário por transferência) | no momento da transferência; 3 dias bancários só para dinheiro/não monetário | sem vigência no ticket | TCU Art. 168.1 (confirmado pela DPS) |
| USC: base mínima no mês de admissão/desligamento | não se aplica | sem vigência no ticket | Instruction 449 s.III |
| USC: taxa de deficiência sem complemento mínimo | 8.41% sobre a base real | sem vigência no ticket | Instruction 449 s.III; DPS 04.02.2026 676/[...] |
| USC: taxa padrão | 22% | sem vigência no ticket | sem fonte no ticket |
| Salário mínimo (no exemplo do CCG) | UAH 8.647 | 2026 [INCERTO: vigência implícita] | sem fonte no ticket |
| Frequência do 4DF/D1 (pessoa jurídica) | mensal (FOP: trimestral) | a partir de 2026-01-01 | Law 4536-IX; MinFin Orders 4/243/284 |
| Proração de salário | por dias úteis do horário | sem vigência no ticket | cartas de 27.05.2019 nº 4340 e 15.04.2019 nº 553 |
| Férias padrão (dado pela Nataliia) | 24 dias/ano a partir da admissão | sem vigência no ticket | sem fonte no ticket |

- **Artefato afetado:** WTC **v3.6** (novos 79414 Donor leave e 79415 Business trip); CCG (Ukraine_Country_Configuration_Guide_FY2026) Module 8 **v1.1** → **v1.2**.
- **Erros corrigidos (no CCG):** prazo de PDFO/ML exposto como universal ("3 dias bancários") → no momento da transferência. Base mínima proporcional no mês de admissão/desligamento (8.647 × 21/31) → sem base mínima. Pseudo-código e nota de dev completavam a base de empregado com deficiência → agora excluem is_disabled. Proração por dias corridos citando o Art. 115 → dias úteis, sem o Art. 115. 4DF trimestral → mensal para pessoa jurídica. Seção de salário médio como fórmula única de 12 meses → dividida em 12 e 2 meses.
- **Pendências:** o código de tipo de acréscimo do D1 para 79414 e 79415 está **TBC** (não confirmado no classificador oficial; sinalizado no WTC para quem fizer o mapeamento do D1). A Nataliia (~08-18) pergunta como criar o relatório de reserva de férias no HRBlizz, sem resposta. Campos de saldo de dias ficam com o leave module (Vaishnavi). A Nataliia discorda da ressalva CPC/main place of work [INCERTO: sem tréplica]. Rótulo "theoretical" na seção da semana 53 (oferecido, não confirmado).
- **Fronteira:** cálculo de saldo de férias e relatório = leave module / configuração (Vaishnavi Mane), não compliance.

---

## HRBS-13389: Ukraine "Insurance Record" (страховий стаж)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / Altium / Service Request, Tier 3, Compliance Support / Medium / **Open** (único snapshot 2026-08-18), assignee Wallisson / criado 2026-08-18; atualizado no mesmo dia por Archit Naik.
- **Arquivos-fonte:** `23 - Ticket - HRBS-13389 - Ukraine Insurance Record страховий стаж.txt`.
- **Quem pediu:** Nataliia Hahan.
- **Pergunta / problema:** o campo Insurance Record (tempo acumulado de seguro social) não está no DD, só no template de Master Data ("Insurance Record (for sick pay)"). É um valor acumulado de toda a vida laboral, informado na admissão, e define o percentual do auxílio-doença. Pede: incluir no DD V3.4, definir o tipo (anos/meses/dias ou data), dizer se é estático ou se acumula automaticamente, e dizer se liga à fórmula do WTC de sick pay.
- **Resposta / decisão nossa:** nenhuma neste snapshot.
- **Valores estatutários (afirmados pela solicitante, não confirmados por nós):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| % do auxílio-doença por tempo de seguro | <5 anos 60%; 5-8 anos 80%; 8+ anos 100% | sem vigência no ticket | sem fonte no ticket. **[INCERTO: contradiz as faixas que a mesma solicitante deu no HRBS-14331]** |

- **Artefato afetado:** DD (V3.4 citado).
- **Pendências:** tudo em aberto conosco. Relacionado: HRBS-12368 (campo pedido junto) e HRBS-13499 (GSK: "Insurance Record Type (Year, months, days)", importante para todos os clientes UA).
- **Fronteira:** nenhuma declarada.

---

## HRBS-13392: Ukraine 12 meses de histórico de payroll (para salário médio)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / Altium / Service Request, Tier 3, Support Group **L2 Support** / Medium / **Open** (snapshot 2026-08-20), assignee Archit Naik / criado ~2026-08-19; última atualização ~2026-08-19 (Nataliia).
- **Arquivos-fonte:** `24 - Ticket - HRBS-13392 - Ukraine 12 Months of Historical Payroll Data (for Average Earnings Calculation).txt`.
- **Quem pediu:** Nataliia Hahan.
- **Pergunta / problema:** para o go-live, o sistema precisa de 12 meses de histórico de rendimentos por empregado e mês, ou as médias de sick pay, férias e viagens saem erradas no primeiro ano. Pergunta onde e como carregar (template, carga de backend ou upload de arquivo), se os dias também precisam vir, e como fica a carga em lote.
- **Resposta / decisão nossa (~2026-08-19):** são três elementos distintos, todos adicionados ao DD num novo grupo **"Historical Payroll Data (Pre-Go-Live Migration)"**, separado dos campos do cartão do empregado porque é carga única:
  1. 12 meses de rendimentos mensais sujeitos a ESV (sick pay/maternidade pelo Poryadok 1266 e férias pelo Poryadok 100, ramo de 12 meses);
  2. 12 meses de dias corridos trabalhados/justificados, que são o denominador do sick pay (1266) e não equivalem a dias corridos comuns;
  3. 2 meses de dias úteis trabalhados, denominador de viagens e outros eventos com remuneração mantida (Poryadok 100, ramo de 2 meses).
  
  A indexação não precisa de histórico de rendimentos, só do base month, já coberto pelo campo "Effective Date of Current Salary".
- **Réplica da Nataliia (~08-19), sem resposta nossa no snapshot:**
  1. No ramo de 2 meses, o denominador são os **dias úteis do horário da empresa**, não os dias efetivamente trabalhados. O rótulo "worked" pode gerar o denominador errado.
  2. As listas de exclusão do 1266 p.4 e do 100 p.4 não são iguais. O sistema vai usar dois conjuntos de regras sobre o mesmo dataset? A exclusão fica no WTC ou no template de carga? Ela pede a lista completa de WTs excluídos antes do go-live.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Período-base de sick pay/maternidade | 12 meses corridos antes do mês do evento | sem vigência no ticket | Procedure No. 1266 |
| Período-base de viagens/garantias | 2 meses corridos antes do evento | sem vigência no ticket | Procedure No. 100 |
| Período-base de férias | 12 meses antes do mês de início | sem vigência no ticket | Procedure No. 100 (citado pela Nataliia sem número; nós citamos 100) |
| Indexação | depende do base month e do índice acumulado | sem vigência no ticket | Procedure No. 1078 |
| Exclusões da base do sick pay (Nataliia) | pagamentos únicos não sistêmicos, indenização de desligamento, compensação de férias não gozadas, pagamentos de viagem, médias pagas de períodos anteriores, dividendos, pagamentos não sujeitos a ESV | sem vigência no ticket | Poryadok 1266 p.4 (citado pela solicitante) |

- **Artefato afetado:** DD. **[INCERTO: o texto diz "Data Dictionary (v3.7)", mas o arquivo anexado se chama "Ukraine_Data_Dictionary_V3.8"; a Nataliia fala em "before we finalize v3.8".]**
- **Pendências:** responder às duas perguntas da Nataliia (rótulo do denominador de dias úteis do horário; dois conjuntos de exclusão 1266/100 e onde moram). Mecanismo técnico de carga (template ou backend), não respondido.
- **Fronteira:** o mecanismo de carga é técnico (L2 Support/Dev; o assignee é Archit Naik, L2).

---

## HRBS-13499: Data Dictionary GSK Ukraine
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / **GSK** (GSK Ukraine REF-LE-04-222) / Service Request, **Tier 1**, Compliance Support, Phase **Implementation** / Medium / **Open** (snapshot 2026-08-24), assignee Wallisson / criado ~2026-08-19; atualizado ~2026-08-24 (Pradeep Duraisamy).
- **Arquivos-fonte:** `31 - Ticket - HRBS-13499 - Data Dictionary GSK Ukraine.txt`.
- **Quem pediu:** Nataliia Hahan.
- **Pergunta / problema:** campos extras do Master Data da GSK: (1) Insurance Record Type (for Sick Leave) (Year, months, days); (2) Grade 2; (3) City of Work; (4) Manager. Os itens 2-4 são específicos desse cliente. O Insurance Record vale para todos os clientes UA e tem ticket próprio (HRBS-13389).
- **Resposta / decisão nossa:** nenhuma no snapshot (a Nataliia pediu nossa orientação ~08-20).
- **Valores estatutários:** nenhum.
- **Artefato afetado:** DD (UA).
- **Pendências:** orientação nossa. Decidir se campos específicos de cliente (Grade 2, City of Work, Manager) entram no DD de país.
- **Fronteira:** campos só da GSK tendem a ser configuração de cliente, não DD de país [INCERTO: não decidido no ticket].

---

## HRBS-14255: Ukraine setup de Advance Payroll no nível país
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / GSK no campo Client (Company Name: Altium Ukraine, GSK Ukraine, SDL Ukraine) / Service Request, Tier 1, Compliance Support, Phase Implementation / Medium / **Pending on reporter** (snapshot 2026-09-11), assignee Lily Li / criado ~2026-09-07; última atualização ~2026-09-11 (Nataliia).
- **Arquivos-fonte:** `47 - ...HRBS-14255...` (09-08), `62 - Ticekt - HRBS-14255...` (09-11).
- **Evolução:** 09-08: Open, assignee Wallisson, só o "No Requirements?" do Mohit. 09-11: assignee Lily Li, Pending on reporter, com nossa resposta, a cobrança do Mohit e o detalhamento da Nataliia.
- **Quem pediu:** Nataliia Hahan; Mohit Jain (Head of Compliance Product) e Lily Li cobraram requisitos.
- **Pergunta / problema:** configurar o Advance Payroll (pagamento da primeira quinzena) no nível país para a Ucrânia.
- **Resposta / decisão nossa (~2026-09-08):** os requisitos estão no CCG (Ukraine_Country_Configuration_Guide_FY2026_**V1_3**). Piso de cálculo no Module 4, §4.2: adiantamento = dias trabalhados × oklad puro, sem bônus (Law 108/95-VR Art. 24). Regra de data fixa única no Module 1, §1.2, e Module 13 ("Typical Monthly Payroll Calendar"), com o LC Art. 115 como gatilho de prazo.
- **Réplica:** Mohit (~09-11): "não é suficiente, alguém precisa dizer o que exatamente desenvolver". A Lily pediu à Nataliia requisitos detalhados e cenários reais. A Nataliia (~09-11) explicou: dois pagamentos por mês (adiantamento = 1ª metade, pelos dias trabalhados; saldo = cálculo de fim de mês com relatórios). Qualquer tipo de provento pode cair em qualquer metade. Alguns empregadores pagam um valor fixo (ex.: 53% do bruto). Licença médica e férias têm de ser pagas com impostos junto com a 1ª ou a 2ª parte, conforme quando ocorrem. No HRBlizz: 1º run = adiantamento; 2º run = tudo, com uma coluna do adiantamento líquido já pago. Saldos de abertura e fechamento (o que falta pagar) por mês.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Base mínima do adiantamento | dias trabalhados × salário-base (oklad), sem bônus | sem vigência no ticket | Law 108/95-VR Art. 24 |
| Frequência/prazo de pagamento | pelo menos 2× por mês | sem vigência no ticket | LC Art. 115 |
| Adiantamento fixo (prática de mercado) | ex.: 53% do bruto | n/a (prática, não lei) | sem fonte no ticket |

- **Artefato afetado:** CCG V1.3.
- **Pendências:** especificação funcional de desenvolvimento (Lily/Mohit com a Nataliia). Não está claro se Compliance precisa entregar algo além do CCG [INCERTO].
- **Fronteira:** o desenvolvimento do produto (dois runs, coluna de adiantamento líquido, saldos) é de Product/Dev (Mohit/Lily).

---

## HRBS-14324: fórmulas de salário médio e de benefício adicional (Ucrânia)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / sem cliente no campo (Company Name: Altium Ukraine, GSK Ukraine, SDL Ukraine) / Service Request / Medium / **Open**, assignee Wallisson (antes: New, Unassigned, L2) / criado 2026-09-08; último snapshot 2026-09-08 21:28 (atualizado pela Vaishnavi).
- **Arquivos-fonte:** `48 - ...HRBS-14324...` (09-08 10:34), `49 - ...` (09-08 11:21), `51 - ...` (09-08 21:28).
- **Evolução:** 48/49: New, Unassigned, L2 Support. 51: Open, assignee Wallisson, Compliance Support. O conteúdo não muda.
- **Quem pediu:** Nataliia Hahan (para Wallisson e Lily; Vaishnavi em FYI).
- **Pergunta / problema:** documentar as fórmulas, com base legal, para a configuração: 1.1 férias (Order 100, 12 meses); 1.2 licença médica/maternidade (Order 1266, meses efetivamente trabalhados, base tributada pelo ESV, exclusões diferentes); 1.3 donor leave (2 ou 12 meses?); 1.4 viagem (Order 100 + LC Art. 121, 2 meses; viagens anteriores pagas pela média ficam fora); 1.5 indexação (Order 1078, não é média); 1.6 paralisação sem culpa do empregado (2/3, LC Art. 113, base = tarifa/salário, não média); 2. presentes; 3. gross-up em duas variantes; 4. feriado/dia não útil em dobro (LC Art. 107), com que base horária.
- **Resposta / decisão nossa:** nenhuma neste ticket nos snapshots. Parte foi respondida em outros tickets: donor leave = 2 meses (HRBS-12631); coeficiente só na base do PIT (HRBS-12181/14331).
- **Valores estatutários (como propostos pela solicitante):**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Presente: parte isenta | 25% do salário mínimo em 1º de janeiro do ano | ano de referência | subparágrafo 165.1.39 do Tax Code |
| Gross-up, variante 1 (posição da autoridade) | K(PIT) = 100 / (100 − alíquota do PIT); Military sem coeficiente | sem vigência no ticket | sem fonte no ticket |
| Gross-up, variante 2 (estendida) | K = 100 / (100 − (PIT + Military)) | sem vigência no ticket | sem fonte no ticket |
| PIT Diia City | 5% | sem vigência no ticket | sem fonte no ticket |
| Paralisação sem culpa do empregado | 2/3 da tarifa/salário | sem vigência no ticket | LC Art. 113 |
| Trabalho em feriado/dia não útil | dobro | sem vigência no ticket | LC Art. 107 |

- **Artefato afetado:** CCG/WTC (fórmulas) [INCERTO: o ticket não especifica].
- **Pendências:** tudo aberto conosco: a base horária do Art. 107 (norma de horas do horário ou norma mensal), o tratamento da paralisação (Art. 113), a variante de gross-up padrão (decisão da empresa; nossa posição em outros tickets é a variante 1) e a fórmula de presentes.
- **Fronteira:** a escolha da variante de gross-up é "a empresa precisa decidir" (cliente/Product).

---

## HRBS-14331: Ukraine WTC catalog, checagem do catálogo do cliente Altium
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / sem cliente no campo (Company Name: Altium Ukraine, GSK Ukraine, SDL Ukraine) / Service Request, Compliance Support / Medium / **Resolved** (snapshot 2026-09-23; SLA "Breached"), assignee Wallisson / criado ~2026-09-08; última atualização ~2026-09-22 (Nataliia, com perguntas novas após o Resolved).
- **Arquivos-fonte:** `50 - ...HRBS-14331...` (09-08), `53 - ...` (09-09), `58 - ...` (09-10), `63 - ...` (09-11), `76 - ...` (09-18), `81 - Ticekt - HRBS-14331...` (09-23).
- **Evolução:** 09-08: só o pedido. 09-09: 1ª resposta (WTC_Altium_Ukraine_2026_2), réplica da Nataliia (157, seguro de vida, 14 itens grossed-up) e pedido sobre dias de feriado. 09-10: resposta com WTC V3_8 (colunas W/X/Y) e mais pedidos. 09-11: respostas sobre os códigos livres e 79401/21142. 09-18: Lily/Nataliia sobre o 65894, correções no CCG 8.2, regras de sick leave, 62209, 65817, GTN. 09-23: nossa resposta final (CCG V1.5 / WTC V3.9 em draft), WTC finalizado pela Lily, e o ticket Resolved com 4 perguntas novas da Nataliia em aberto. O estado passou de Open para Pending on reporter (09-09 a 09-18) e depois para Resolved.
- **Quem pediu:** Nataliia Hahan; Vaishnavi Mane (configuração); Lily Li (BA); Mohit Jain citado.
- **Pergunta / problema:** revisar o catálogo de WT do cliente Altium contra o master WTC: (1) colunas de inclusão na média (para coletar 12 meses de histórico); (2) WTs destacados; e, ao longo do ticket, várias perguntas de tributação, códigos 4DF, gross-up, dias de feriado na proração de bônus, compensação/dedução de férias, correções no CCG.
- **Resposta / decisão nossa:**
  - **~09-08/09 (WTC_Altium_Ukraine_2026_2):** as colunas de média já existem (J/K/L, 114 WTs): férias J = 12 meses (Poryadok 100 p.2); sick leave K = **6 meses** sobre renda tributada pelo ESV (1266 p.4) [INCERTO: contradiz os 12 meses do HRBS-12631/13392]; viagem/doação L = 2 meses (100 p.2). Linha 5 "Non-taxable individual anniversary gifts": PIT/Military corrigido de Sim/Sim para **Não/Não**, mesma fórmula e 4DF 160 da linha 2 (p. 165.1.39). Linhas 93-101 (seguros médico/vida/família, representação): PIT=Sim/Military=Sim corretos (p. 16-1, pidrozd. 10, rozd. XX). Linha 17 "Payment Civil Contractors": Sim/Sim/Sim não bate com o p. 177.8 (FOP com comprovante de registro fica isento dos três), ainda sem código. Demais linhas: corretas.
  - **~09-09 (WTC V3_8):** colunas W/X/Y populadas para os 114 WTs (102 com correspondência no master). **Seguro de vida: USC corrigido para Sim** (Poryadok 1170, p. 2, rozd. II isenta de ESV só seguro médico e previdenciário, não vida). Civil contractors: 4DF **157** confirmado, configurado no **62942**, PIT/Military/USC = Não/Não/Não (p. 177.8). Os 14 itens grossed-up vs. benefício ganharam código (coluna Mercans Code destacada); os dois códigos de curso de inglês são entradas separadas, cada uma com seu par base/grossed-up. Feriado/fim de semana: na proração de bônus trimestral/anual conta +1 dia (20 + 3 = 23, Poryadok 100 p.3). Na média de férias a regra é outra: dias corridos, com feriados já excluídos, e o pagamento em dobro entra nos rendimentos.
  - **~09-10:** confirmado que feriados e fins de semana trabalhados contam como dias inteiros na proração de bônus (Poryadok 100 p.3; carta de 28.06.2024 nº 4702-05/46462-09; LC Art. 107). Catálogo do cliente está **fora do escopo** (mantemos só o master WTC; encaminhar ao team lead). Não precisa de segundo código para "65808 Life Insurance (BIK) 126 + SSC Sim": o ESV só tem uma base (valor real, sem o coeficiente do Art. 164.5). A divisão PIT/Military (65808 base + 65894 grossed-up) existe porque esses impostos têm bases diferentes [INCERTO: 65808 era "Representation expenses (financial)" no HRBS-12181].
  - **~09-11 (Ukraine_Wage_Type_Catalogue_Mercans, destaques em verde):** Representation expenses (65806, 65807) com PIT=Sim, sem coeficiente (mecanismo de dinheiro/adiantamento a prestar contas, Art. 170.9), PIT e Military sobre o valor bruto. English courses (65720, 65803) com PIT=Sim e coeficiente (benefício não monetário, Art. 164.5). **79401** (compensação de férias não gozadas): média nova dos últimos 12 meses no desligamento. Correção da citação: Poryadok No. 100, p. 2, segundo parágrafo (não "sub-para. 3"). **21142** (dedução de férias adiantadas): usa a média já aplicada, sem recalcular. Exceções = Art. 127 LC **combinado com** Art. 22 da Lei "On Vacations" nº 504/96 (as listas não são idênticas). No master, 21142 já é outro WT ("Unpaid leave deduction"), então o código não pode ser 21142.
  - **~09-21 (CCG V1.5 e master WTC V3.9, ambos draft para revisão):**
    - **65894 não existe** no master (nem na faixa 65880-65900). O changelog que dizia que foi criado estava errado e foi retirado. Não deve ser criado: não há linha PIT=Sim/Military=Não, e os 4 "(notional)" (65508, 65509, 65609, 65659) são PIT=Sim/Military=Sim. A diferença está na base, não na incidência: PIT = valor × 1.219512 (Art. 164.5); Military Levy e USC = valor bruto. Isso não é expressável em flags.
    - **Decisão pendente sinalizada:** o arquivo tem dois desenhos contraditórios para o mesmo mecanismo: a conclusão de 2026-08-11 (regra de motor, sem linha no WTC) e a aba "BIK Gross Up" (PE agregado "58134", nunca construído; a série 5813x para no 58133). Precisa de acordo Compliance/BA/Dev.
    - Dedução de férias adiantadas: linha de spec adicionada ao master com o código em branco (a Lily atribui), Category = Deduction, PIT/Military/USC = Não/Não/Não (KZpP Art. 127 §2 + Law 504/96 Art. 22). Sobre dias negativos: usar um código dedicado, não dias negativos no WT de pagamento de férias.
    - **65817** Additional benefit (monetary): sem coeficiente (Art. 164.5 só vale para forma não monetária). Segue como placeholder "Benefit Earning", sem renomear a partir de um arquivo de cliente (um rename de 65811/65812 já teve de ser revertido).
    - **CCG 8.2 corrigido:** o CCG aplicava a lista de exclusão do 1266 p.3 ao cálculo de férias (Poryadok 100). Agora a lista de férias tem só: licença-cuidado até 3 anos, licença não remunerada, suspensão de contrato por guerra, serviço militar sem média mantida e meses sem dados de payroll. Sick leave e maternidade **permanecem** na média de férias, dias e valores (Poryadok 100, p. 3, sub-p. 4).
    - **Regras de sick leave adicionadas ao CCG:** empregador paga os dias 1-5; Pension Fund a partir do 6º dia, via zayava-rozrakhunok, com o empregador desembolsando; Pension Fund desde o 1º dia para cuidado de filho/familiar e para maternidade. Faixas de tempo de serviço com exceções de 100%, tratamento de bônus e tributação: sick leave comum 18% + 5% + 22% (8.41% com deficiência) sobre o total; maternidade isenta de PDFO (p. 165.1.1) e por isso do Military Levy, mas com USC; reportada no 4DF com o código 128. Também corrigido no CCG: ele citava o Social Insurance Fund, que se fundiu ao Pension Fund of Ukraine em 2023-01-01.
    - **GTN:** a Ucrânia não tem layout estatutário de GTN, então as colunas são decisão de relatório. O fixo é a base: PIT sobre o valor com gross-up; Military e USC sobre o valor bruto. As colunas 3/3 do 4DF trazem o valor com gross-up.
    - **WTs cinza:** são do catálogo do cliente, e mantemos só o master (pedimos a lista de códigos Mercans para checar).
    - **62209** (Monthly bonus compensation): o divisor pedido de 0.77 deveria ser **0.82**, porque o coeficiente vale só para a base do PIT e o Military fica sobre o valor sem gross-up.
  - **Lily (~09-21):** 65894 removido após alinhamento com a Nataliia. Regra daqui em diante: PEs novos entram no WTC **sem código** e a Lily atribui (a atribuição de código é do BA, não do RA). Publicou o WTC finalizado.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Presentes de aniversário não tributáveis | PIT/Military = Não, 4DF 160 | sem vigência no ticket | p. 165.1.39 PKU |
| Pagamento a FOP com comprovante de registro | PIT/Military/USC = Não, 4DF 157 (62942) | sem vigência no ticket | p. 177.8 PKU |
| ESV sobre seguro de vida | Sim (só médico e previdenciário são isentos) | sem vigência no ticket | Poryadok/Resolution 1170, p. 2, rozd. II |
| Coeficiente na base do PIT (não monetário) | ×1.219512 | sem vigência no ticket | Art. 164.5 PKU |
| Base de Military Levy e USC sobre BIK | valor bruto | sem vigência no ticket | p. 16-1, pidrozd. 10, rozd. XX PKU |
| Média de férias | 12 meses | sem vigência no ticket | Poryadok 100 p.2 |
| Média de sick leave | **6 meses** (nossa resposta) vs. 12 meses (Nataliia; HRBS-12631/13392) | sem vigência no ticket | Poryadok 1266 p.4. **[INCERTO: contradição]** |
| Média de viagem/doação | 2 meses | sem vigência no ticket | Poryadok 100 p.2 |
| Feriado/fim de semana trabalhado na proração de bônus | conta como dia inteiro (20 + 3 = 23) | sem vigência no ticket | Poryadok 100 p.3; carta de 28.06.2024 nº 4702-05/46462-09; LC Art. 107 |
| Compensação de férias não gozadas (79401) | média nova de 12 meses no desligamento | sem vigência no ticket | Poryadok 100, p. 2, segundo parágrafo |
| Dedução de férias adiantadas | média original, sem recalcular; exceções do Art. 127 LC + Art. 22 da Lei 504/96 | sem vigência no ticket | KZpP Art. 127 §2; Lei 504/96 Art. 22 |
| Sick leave: quem paga | dias 1-5 empregador; 6º dia em diante Pension Fund; maternidade e cuidado de familiar: PF desde o 1º dia | sem vigência no ticket | sem fonte específica no ticket (regras da Nataliia, que aceitamos) |
| Sick leave: % por tempo de seguro (Nataliia) | <3 anos 50%; 3-5 anos 60%; 5-8 anos 70%; >8 anos 100%; veteranos 100%; maternidade sempre 100%; tempo de seguro <6 meses nos últimos 12 → teto de salário mínimo/30.44 por dia | sem vigência no ticket | sem fonte no ticket. **[INCERTO: contradiz o HRBS-13389; nós dissemos "faixas adicionadas ao CCG" sem citar valores]** |
| Sick leave sem histórico | 1-12 meses: só meses completos; <1 mês: dias corridos reais; doença no 1º dia: salário contratual/30.44 | sem vigência no ticket | sem fonte no ticket (Nataliia) |
| Tributação de sick leave comum | 18% PDFO + 5% ML + 22% USC (8.41% deficiência) | sem vigência no ticket | sem fonte no ticket |
| Maternidade | isenta de PDFO e ML; USC incide; 4DF 128 | sem vigência no ticket | p. 165.1.1 PKU |
| Fusão do Social Insurance Fund no Pension Fund | — | a partir de 2023-01-01 | sem fonte no ticket |
| Divisor do 62209 (Military sem gross-up) | 0.82 (não 0.77) | sem vigência no ticket | Art. 164.5 PKU (raciocínio) |
| Per diem doméstico: teto (Nataliia) | UAH 864,70 por dia (0,1 × salário mínimo 8.647) | 2026 | p. 170.9.1 PKU |
| Per diem no exterior: teto (Nataliia) | EUR 80 por dia, à taxa NBU do dia | 2026 [INCERTO] | p. 170.9.1 PKU |
| Base máxima do ESV (Nataliia) | UAH 172.940/mês (20 × salário mínimo de 8.647) | 2026 | Lei nº 2464-VI, art. 7 parte 1 |
| Salário mínimo (Nataliia) | UAH 8.647 | 2026 (desde 1º de janeiro) | sem fonte no ticket |

- **Artefato afetado:** WTC do cliente (WTC_Altium_Ukraine_2026_2, mantido pela Nataliia); master WTC **V3.8 → V3.9 (draft)**; CCG **V1.5 (draft)**. Linha nova: dedução de férias adiantadas (sem código).
- **Erros corrigidos:**
  - Presente de aniversário não tributável: PIT/Military Sim/Sim → Não/Não (4DF 160).
  - Seguro de vida: USC Não → **Sim** (Poryadok 1170). Isso contradiz o que dissemos no HRBS-12181 (~08-03), que dava USC=Não como correto para seguro médico/vida. **Erro nosso corrigido.**
  - Civil contractors: Sim/Sim/Sim → 157 / Não/Não/Não (62942).
  - Citação do 79401: "sub-para. 3" → p. 2, segundo parágrafo.
  - 65894: o changelog dizia que a linha foi criada → a linha não existe, e o changelog foi retirado.
  - CCG 8.2 aplicava a lista de exclusão do sick leave às férias → corrigido.
  - CCG citava o Social Insurance Fund → Pension Fund of Ukraine (fusão em 2023-01-01).
  - Divisor do 62209: 0.77 → 0.82.
  - Na resposta de ~09-09, vacation average "em dias corridos com feriados excluídos" (para a média de férias) vs. a regra de dias da proração de bônus: esclarecido em ~09-10.
- **Pendências (perguntas novas da Nataliia em ~09-22, depois do Resolved, sem resposta no snapshot):**
  1. 4DF 128 só para a licença-maternidade de 126 + 14 dias. Os demais (65700-65702, 65710-65712 Maternity allowance (benefit) 1/2) seriam 101 (férias) ou 126 (benefício). Isso contradiz o que pusemos no CCG ("maternidade → 128").
  2. 62180 Severance Pay e 62181 Redundancy compensation não deveriam ser base de ESV.
  3. Per diem (62570, 65570-65572, 65580-65582) e 62965 Unreturned accountable excess: dividir em dentro/fora do teto (118, sem PIT/ML/ESV vs. 118 com PIT/ML + gross-up, sem ESV), ou fórmula com teto (63711, 63712, 75100, 75101). Inconsistência com 62803 e 58100/58101 (PIT/ML = Não), com risco de tributação dupla.
  4. Stock Options and Grants (62890-62899 e o bloco duplicado 62990-62999): 101 com ESV=Não é inválido. Cenário A (entidade UA é a fonte) → ESV=Sim, 101, gross-up no PIT, base máxima do ESV, revisar colunas de média. Cenário B (concedido pela matriz estrangeira) → fora do payroll e do 4DF. Terceira hipótese: 126 sem ESV. Precisa de resposta do cliente/global team.
  5. Um código que "deveria ser 102" e outro "sem nenhum imposto" (licença-cuidado até 3/6 anos?) [INCERTO: as imagens não foram capturadas no texto].
  6. Decidir o desenho do gross-up: regra de motor ou PE agregado 58134 (Compliance/BA/Dev).
- **Fronteira:** o catálogo do cliente (Altium) e os WTs cinza são do cliente/team lead, não nossos (mantemos só o master WTC). A atribuição de códigos é da BA (Lily). O gross-up é de motor (Dev). A qualificação de stock options depende do cliente/global team.

---

## HRBS-15216: Ukraine Data Dictionary check (campos obrigatórios)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / sem cliente no campo (Company Name: Altium) / Service Request, L2 Support / Medium / **New, Unassigned** (snapshot 2026-09-25) / criado 2026-09-25.
- **Arquivos-fonte:** `89 - Ticket - HRBS-15216 - Ukraine Data Dictionary check.txt`.
- **Quem pediu:** Nataliia Hahan (endereçado a Wallisson; FYI para Mohamed Nabil e Vaishnavi Mane).
- **Pergunta / problema:** revisar a obrigatoriedade no DD. Tornar não obrigatórios: Contract Start Date, Oblast (Region), Street and Building Number, Postal Code, Supporting Document Reference (D5) e TSB Eligibility (pede também explicação do que é). Apagar o 1C Personnel Number (não será usado "por ora"). Renomear "[ESV] Rate Effective Date" para "SSC Rate Effective Date" e criar o campo "SSC Rate" (22% ou 8.41%). Explicar o "ESV Category Code". Traduzir para o ucraniano os campos sem tradução.
- **Resposta / decisão nossa:** nenhuma no snapshot.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Taxas de SSC/ESV | 22% / 8.41% | sem vigência no ticket | sem fonte no ticket |

- **Artefato afetado:** DD (UA). O 1C Personnel Number tinha sido adicionado por nós no DD V3.5 (HRBS-12368) e agora o pedido é removê-lo.
- **Pendências:** tudo aberto. Atenção: "Supporting Document Reference" e o "ESV Category Code" ($hr.esv_category_code) alimentam D5 e D1 (ver SR-160/SR-162). Verificar o impacto antes de tirar a obrigatoriedade.
- **Fronteira:** nenhuma declarada.

---

## SR-160: UA D1-001_UnifiedSocialContribution (Report Spec D1 / ESV)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / n/a (país) / Statutory Reports, Phase "Final Review Phase - Business Analyst" / Major / **In Review** / criado ~2026-02/03 (por Wallisson); Due Date 2026-03-31; última atualização 2026-09-28 (Lily).
- **Arquivos-fonte:** `27 - Ticket - SR-160 - UA; D1-001_UnifiedSocialContribution.txt` (08-20), `84 - ...SR-160...` (09-25), `96 - ...SR-160...` (09-28).
- **Evolução:** 08-20: assignee Wallisson, terminando na pergunta da Lily sobre HZ/HBOS. 09-25: assignee **Michael Mukosi John**, com nossa resposta (mapeamento HZ e HBOS/HBUH) e o pedido da Lily do campo chief_accountant_name. 09-28: assignee de volta a Wallisson, com o campo adicionado e o pedido de "true XML sample".
- **Quem pediu:** Lily Li (BA); Michael Mukosi John (Dev).
- **Pergunta / problema:** revisão BA/Dev da spec D1: uso da coluna de categoria de segurado do WTC, campos part-time, idioma do relatório, totais de rodapé, flags de tipo de documento, tags HBOS/HBUH, campo de contador-chefe e amostra XML.
- **Resposta / decisão nossa:**
  - **~2026-04/05:** a coluna de categoria de segurado do WTC não mapeia para nenhum campo do XML do D1. O D1 Graf 8 (T1RXXXXG8) vem do HR ($hr.esv_category_code). A coluna do WTC foi renomeada para **"Insured Person Type for ESV Engine"** e é filtro do motor (20 = contrato de trabalho; 21 = contrato civil/CPC).
  - **~2026-05/06:** WTC **V3.2**: WT 62964 (Top-up to minimum wage) com D1 Accrual Type Code = **13** (MFU [ordem] 4 §IV). DD **V3.3**: novo campo Part-Time Indicator (part_time_indicator, Integer 0/1), linha 20, ordinal 15.1. D1 Graf 22 = 1 se part_time_indicator = 1. A Lily corrigiu: obrigatoriedade **M**, não CM, e sem default automático (concordamos).
  - **~2026-06/07:** os relatórios D1, D5, D6 e 4DF têm de ser desenvolvidos **em ucraniano** (requisito estatutário). Os totais de rodapé R01G16-R01G20 (linhas 37-41 da spec, posições 031-035) estão na spec, e o BA Mapping foi reescrito como SUM explícito: G16 = SUM(Graf 16 / PE 58133); G17 = SUM(Graf 17 / PE 58130); G18 = SUM(Graf 18); G19 = 0,00; G20 = SUM(Graf 20 / PE 2550), conciliado com o ESV pago à DPS.
  - **~2026-08-20:** D1, D6 e 4DF são anexos do mesmo formulário **J05**. Mapeamento: 011 → HZ=1/C_DOC_STAN=1; 012 → HZN=1/C_DOC_STAN=2; 013 → HZU=1/C_DOC_STAN=3 (os outros dois ficam 0). Faltavam só HBOS (nome do diretor) e HBUH (nome do contador), que foram adicionados. 57 tags checadas.
  - **~2026-09-25:** campo **chief_accountant_name** adicionado ao DD (Country Fields linha 77, ordinal 9.5), alimenta o HBUH.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| ESV do empregado | 0,00 (abolido) | a partir de 2016-01-01 | Law 77-VIII |
| Estrutura do D1 | — | sem vigência no ticket | MFU [ordem]; Law 2464-VI; DPS XSD R01G16-R01G20 |
| Código de acréscimo do D1 para top-up até o salário mínimo | 13 | sem vigência no ticket | MFU [ordem] 4 §IV |

- **Artefato afetado:** Report Spec UA-D1-001_UnifiedSocialContribution_Spec; WTC V3.2; DD V3.3 (e depois o campo chief_accountant_name). Configurado pelo Dev em acceptance, com o código de relatório `ua-unified-social-contribution` (entidade de teste REF-02-370 Mercans Ukraine).
- **Erros corrigidos:** obrigatoriedade do Part-Time Indicator CM com default → M, sem default (correção da Lily). Faltavam HBOS/HBUH na spec.
- **Pendências:** a Lily (09-28) pede um **XML de amostra real** (o atual é o schema), conosco. A Lily mandou o Dev aplicar a atualização do BA mapping das linhas 4 e 27 e os campos novos 46 e 47.
- **Fronteira:** o desenvolvimento e a configuração do relatório são do Dev (Michael).

---

## SR-161: UA 4DF-001_PersonalTax (Report Spec 4DF / PIT)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / n/a / Statutory Reports, Final Review Phase - Business Analyst / Major / **In Review**, assignee Wallisson / criado ~2026-02/03; Due Date 2026-03-31; última atualização 2026-09-28 (Lily).
- **Arquivos-fonte:** `98 - Ticket - SR-161 - UA 4DF-001_PersonalTax.txt` (09-28).
- **Quem pediu:** Lily Li (BA); Michael Mukosi John (Dev).
- **Pergunta / problema:** revisão BA da spec 4DF; mapeamento das flags de tipo de documento e tags faltando; QC do XML gerado.
- **Resposta / decisão nossa:** ~2026-04: queries respondidas e DD atualizado. **~2026-08-20:** mesmo padrão de cabeçalho do D6 (anexos do J05). Mapeamento 011/012/013 → HZ/HZN/HZU com C_DOC_STAN 1/2/3. Faltavam só HBOS/HBUH, adicionados. 54 tags checadas.
- **Achados de QC da Lily (09-28), para o Dev:** o U4 deve mapear para document_type_flag_4df (estava d1); U21/U22 mudam de 58120 para 58582 (58552/58582 não aparecem na configuração do relatório); códigos de renda por PE atualizados (abas Gross Income/101/102); o teste com 101 + 126 gerou só 101 (o código de renda não pode ter default 101); T1RXXXXG06D sai com traços (deve ser 05012026, formato DDMMAAAA); R02G03I vazio (deveria ser 1?); T1RXXXXG09 = 0 deveria ser omitido; valores com separador de milhar (21,600.00) quando a spec manda sem separador.
- **Valores estatutários:** nenhum novo (frequência mensal do 4DF: ver HRBS-12631).
- **Artefato afetado:** Report Spec UA-4DF-001_PersonalTax_Spec. Código de relatório `ua-personal-tax` (acceptance REF-02-370; QC em REF-04-125 Ukraine QC Entity). Linhas novas 60 e 61.
- **Erros corrigidos:** faltavam HBOS/HBUH na spec. O mapeamento do U4 apontava para a flag do D1 (erro de configuração do Dev, corrigido pela Lily).
- **Pendências:** XML de amostra real (conosco). Correções de QC (Dev).
- **Fronteira:** Dev (geração do XML e formatação).

---

## SR-162: UA D5-001_LabourRelations (Report Spec D5 / registro de relações de trabalho)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / n/a / Statutory Reports, Final Review Phase - Business Analyst / Major / **In Review**, assignee Wallisson (Business Analyst: "No business analyst" no campo, mas quem atua é a Lily) / criado ~2026-02/03; Due Date 2026-03-31; última atualização 2026-09-28.
- **Arquivos-fonte:** `28 - Ticket - SR-162 - UA; D5-001_LabourRelations.txt` (08-20), `97 - Ticket - SR-162 - UA D5-001_LabourRelations.txt` (09-28).
- **Evolução:** 08-20: termina nas 3 perguntas da Lily (gatilho, HZ, HBOS). 09-28: nossa resposta (spec v3), a regra de gatilho formalizada pela Lily, o template atualizado do Dev e o QC da Lily.
- **Quem pediu:** Lily Li; Michael Mukosi John.
- **Pergunta / problema:** criação dos campos HR para o D5 (o Dev listou 23, e a Lily disse que já existem no DD); gatilho de geração; flags de tipo de documento; tags faltando.
- **Resposta / decisão nossa (~2026-08-20, spec v3):** o D5 é **orientado a eventos** (§5 p.34, Report Matrix) e dispara em 7 tipos de evento (início/fim de contrato, novo posto de trabalho, transferência, serviço militar, licença-maternidade/cuidado), não só pela data de início dentro do período. Conferido no XML de teste. HZ/HZN/HZU/C_DOC_STAN: mesmo mecanismo do D1. HBOS/HBUH adicionados, e também TIN, C_DOC, C_DOC_SUB, C_DOC_VER, C_DOC_TYPE, C_DOC_CNT, C_REG, C_RAJ, C_STI_ORIG, LINKED_DOCS, SOFTWARE, PERIOD_TYPE. PERIOD_MONTH, PERIOD_YEAR e D_FILL são provavelmente duplicatas das linhas 6, 5 e 33 (adicionados, aguardando confirmação).
- **Formalização da Lily (~09-24):** gera o D5 se, para algum empregado, labour_event_period_start_date cai no período OU (categorias 1, 2, 9 → $employee.last_working_date no período; categoria 3 → $hr.contract_end_date no período; categorias 4-8 → $hr.labour_event_period_end_date no período). Se ninguém cumpre, o D5 não é gerado. Linhas 36-54 novas.
- **QC da Lily (09-28), para o Dev:** U4 deve mapear para document_type_flag_d5 (estava d1); C_DOC_SUB deve ser 105 (gerado 106); C_DOC_STAN vazio; espaço em `<HZ> 1</HZ>`; formato de data errado no HFILL (28-09-2026); T1RXXXXG12 vazio; campos "::key" precisam de valor default; HDDGV/HNDGV aparecem no schema (nillable) mas não na spec.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Report Spec UA-D5-001_LabourRelations_Spec **v3**. Código de relatório `ua-labour-relations-register`.
- **Erros corrigidos:** a leitura do gatilho como "só data de início no período" foi corrigida para orientado a eventos. Faltavam HBOS/HBUH e outras tags de cabeçalho.
- **Pendências:** XML de amostra real (conosco). Confirmar as duplicatas PERIOD_MONTH/YEAR/D_FILL. HDDGV/HNDGV fora da spec (conosco?). Correções de QC (Dev).
- **Fronteira:** Dev (Michael).

---

## SR-163: UA D6-001_SpecialSeniority (Report Spec D6 / tempo especial)
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / n/a / Statutory Reports, Final Review Phase - Business Analyst / Major / **In Review**, assignee Wallisson / criado ~2026-02/03; Due Date 2026-03-31; última atualização 2026-09-28.
- **Arquivos-fonte:** `29 - Ticket - SR-163 - UA; D6-001_SpecialSeniority.txt` (08-20), `95 - Ticket - SR-163 - UA D6-001_SpecialSeniority.txt` (09-28).
- **Evolução:** 08-20: termina nas perguntas da Lily. 09-28: nossa resposta (spec v3), a instrução da Lily ao Dev e o pedido de XML real.
- **Quem pediu:** Lily Li; Michael Mukosi John.
- **Pergunta / problema:** campos do DD (d6_duration_unit e o option mapper correspondente), gatilho de geração, flags de tipo de documento e tags faltando.
- **Resposta / decisão nossa:** ~2026-05/06: criado o campo $legal_entity_hr.d6_duration_unit no DD UA e depois o option mapper "D6 Duration Unit" (que a Lily apontou que faltava). **~2026-08-20 (spec v3):** gatilho em duas camadas: o empregador precisa de posto de trabalho qualificado (§6) e, por linha, special_seniority_code não nulo. HZ/C_DOC_STAN: mesmo mecanismo do D1/D5. HBOS/HBUH adicionados (vazios no XML, preenchidos pela assinatura digital), mais as mesmas tags de cabeçalho do D5. PERIOD_MONTH/YEAR/D_FILL provavelmente duplicam as linhas 6/5/30 (pendente).
- **Lily (~09-24) ao Dev:** gatilho = special_seniority_code não nulo; linha 4 atualizada; linhas 33-51 novas.
- **Valores estatutários:** nenhum.
- **Artefato afetado:** Report Spec UA-D6-001_SpecialSeniority_Spec **v3**; DD (d6_duration_unit + option mapper). Código de relatório `ua-special-seniority`.
- **Erros corrigidos:** o option mapper do D6 Duration Unit não tinha sido criado (apontado pela Lily, corrigido). No pedido do Dev, "Chief Accountant RNOCPP" estava mapeado para director_signatory_rnocpp [INCERTO: possível erro de mapeamento do Dev, sem tratamento no ticket].
- **Pendências:** XML de amostra real (conosco). Confirmar as duplicatas.
- **Fronteira:** Dev (Michael).

---

## SR-340: UA Payslip
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / n/a / Statutory Reports / Normal / **In Progress** (snapshot 2026-08-10), Phase "Development Phase - Developer", Developer Michael Mukosi John, Assignee Wallisson / criado ~2026-07-10 (por Wallisson); Due Date 2026-08-31; última atualização 2026-08-10 (Lily).
- **Arquivos-fonte:** `03 - Ticket SR-340 UA - Payslip.txt` (texto vazio; lido pelo PDF `raw/tickets/youtrack_tickets/03 - Ticket SR-340 UA - Payslip.pdf`, impresso em 2026-08-04), `11 - Ticket - SR-340 - UA - Payslip.txt` (08-10).
- **Evolução:** 08-04: Open, Phase "Product Mapping Phase - Business Analyst", sem developer; query da Lily (~07-23) com print: "Employer Address / EDRPOU". O EDRPOU está mapeado em outro campo ("company_tax_identification_number"); aparece no mesmo campo do endereço do empregador ou em outra linha? Formato de exibição? (Em "Field Explanation (UA)" se lê: "Full registered address and 8-digit EDRPOU code. [VERIFY WITH RA] ESV payer number normally = EDRPOU post-2016.") 08-10: In Progress, Development Phase, Developer Michael. Respondemos (~08-05) "queries reverted". O Dev pediu o mapeamento HRB de "ESV Payer Number" (dados do empregador) e "division" (dados bancários). A Lily disse que esses campos não estão na "Payslip Spec 1". O Dev respondeu que estão nos templates Ukraine (EN) e Ukraine (UK). A Lily pediu a Wallisson para resolver: **campos do template inconsistentes com os da spec**.
- **Quem pediu:** Lily Li (BA); Michael Mukosi John (Dev).
- **Pergunta / problema:** mapeamento de campos do payslip (EDRPOU/endereço; ESV Payer Number; division bancária) e a inconsistência entre os templates de payslip (EN/UK) e a "Payslip Spec 1".
- **Resposta / decisão nossa:** ~2026-08-05: "queries reverted" (conteúdo na planilha, não no ticket). A inconsistência template × spec segue em aberto no último snapshot.
- **Valores estatutários:** nenhum (nota na spec: "ESV payer number normally = EDRPOU post-2016", marcada [VERIFY WITH RA] e sem fonte no ticket).
- **Artefato afetado:** Payslip (UA: Ukraine Payslip; Payslip Spec 1; templates Ukraine (EN) e Ukraine (UK)).
- **Erros corrigidos:** nenhum declarado.
- **Pendências:** conosco: alinhar os templates EN/UK com a Payslip Spec 1 (ESV Payer Number, division) e confirmar o [VERIFY WITH RA] do EDRPOU/ESV payer number.
- **Fronteira:** Dev (Michael) desenvolve.

---

## SR-414: UA Form 1-PV Monthly (Labour Statistics Report), SPEC
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / n/a / Statutory Reports, "Product Mapping Phase - Business Analyst" / Major / **Open**, assignee Wallisson, sem developer / criado ~2026-07-24/08 (por Wallisson; "about 2 months ago" em 09-24); Due Date 2026-09-30; última atualização 2026-09-29 (Lily).
- **Arquivos-fonte:** `82 - Ticket - SR-414 - ...` (09-24), `100 - Ticekt - SR-414 - ...` (09-29).
- **Evolução:** 09-24: só a query da Lily (coluna V e formato de arquivo). 09-29: nossa resposta e um novo bloco de perguntas da Lily.
- **Quem pediu:** Lily Li (BA). Origem: HRBS-12548.
- **Pergunta / problema:** queries da coluna V da spec UA-1PV-001 e o formato do arquivo, que falta na Report Matrix.
- **Resposta / decisão nossa (~2026-09-24):** DD conferido. O campo certo não é Employment Contract Type, e sim **Labour Registry Person Category (D5)**: categorias 1-2 = quadro (escopo da r.1070); categoria 3 (CPC) = contrato civil, excluído.
- **Perguntas abertas da Lily (09-29):** qual categoria indica "external part-time"? O formato de arquivo continua faltando na matriz. O comentário do RA "worth a direct check if the 2024 text surfaces" ficou confuso. Se for preciso campo novo, criar "No-Data Indicator" no DD com option mapper. "Average FTE headcount": o que é "calendar-day average"? Ela pede fórmula e exemplo. Confirmar as exclusões do "staff": maternidade (categoria 5), licença-cuidado (4 ou 6), mobilizados (7 ou 8), contrato suspenso/evacuado/paradeiro desconhecido (qual campo?), licença não remunerada ilimitada da lei marcial (Art. 26(1) da Lei "On Vacations"): mapear para 79410 Unpaid Leave Payout? Campos de "deviation flag" de headcount (25%) e de salário médio (10%): é preciso campo HR de texto de motivo? A coluna O cita um option mapper na aba Field Options que não existe.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Limite de desvio de headcount | 25% | sem vigência no ticket | sem fonte no ticket |
| Limite de desvio de salário médio | 10% | sem vigência no ticket | sem fonte no ticket |
| Licença não remunerada ilimitada sob lei marcial | — | sem vigência no ticket | Art. 26(1) da Lei "On Vacations" |

- **Artefato afetado:** Report Spec UA-1PV-001_MonthlyLabourReport_Spec (template Derzhstat S0301016, citado no HRBS-12548).
- **Erros corrigidos:** mapeamento de "staff" por Employment Contract Type → Labour Registry Person Category.
- **Pendências:** conosco: todas as perguntas da Lily de 09-29 e o formato de arquivo na Report Matrix. O prazo (2026-09-30) estava vencendo.
- **Fronteira:** nenhuma.

---

## SR-415: UA Form 1-PV Quarterly (Labour Statistics Report), SPEC
- **País / Cliente / Tipo / Prioridade / Estado final / Datas:** UA / n/a / Statutory Reports, Product Mapping Phase - Business Analyst / Major / **Open**, assignee Wallisson / criado ~2026-07-24/08; Due Date 2026-09-30; última atualização 2026-09-29.
- **Arquivos-fonte:** `83 - Ticket - Ticket - SR-415 - ...` (09-24), `101 - SR-415 - ...` (09-29).
- **Evolução:** 09-24: query da Lily. 09-29: nossa resposta e duas perguntas novas.
- **Quem pediu:** Lily Li. Origem: HRBS-12548.
- **Pergunta / problema:** coluna V da spec UA-1PV-002 e o formato de arquivo na Report Matrix.
- **Resposta / decisão nossa (~2026-09-24):** coluna V respondida na coluna W. Formato adicionado à Report Matrix (linha 16): **XML, template Derzhstat S0301121, assinado com KEP, envio só eletrônico** via [portal; nome perdido no cirílico] (Law 2524-IX art. 10(4)).
- **Perguntas abertas da Lily (09-29):** (1) mudamos códigos 4DF de alguns PEs no WTC, e eles foram atualizados na aba Wage Fund Classification. As colunas E e F dessa aba também devem mudar? (2) Coluna V marcada em vermelho.
- **Valores estatutários:**

| Item | Valor | Vigência | Fonte |
|---|---|---|---|
| Formato/envio do 1-PV trimestral | XML S0301121 + KEP, só eletrônico | sem vigência no ticket | Law 2524-IX art. 10(4) |

- **Artefato afetado:** Report Spec UA-1PV-002_QuarterlyLabourReport_Spec (aba Wage Fund Classification ligada aos códigos 4DF do WTC).
- **Erros corrigidos:** nenhum declarado.
- **Pendências:** conosco: colunas E/F da Wage Fund Classification e a coluna V em vermelho.
- **Fronteira:** nenhuma.

---

## Síntese do grupo

### (a) Decisões recorrentes e padrões
1. **Gross-up de BIK (coeficiente 1.219512, Art. 164.5 PKU) vale só para a base do PIT.** Military Levy e USC/ESV ficam sobre o valor bruto. Não se cria série "PIT sem Military" (sem base legal; é diferença de base, não de incidência). A separação é **regra de motor**, não flag nem fórmula no WTC (HRBS-12181, HRBS-14331). O coeficiente só se aplica a benefício **não monetário**; benefício em dinheiro não tem coeficiente (65806/65807 representação, 65817). Limite do produto: 20 PEs com gross-up, que nós definimos (v3.8). O desenho final (motor ou PE agregado 58134) está **sem decisão** entre Compliance, BA e Dev.
2. **Salário médio tem regras diferentes por evento:** férias = 12 meses (Poryadok 100); donor leave e viagem = 2 meses (Poryadok 100 §8; viagem paga o maior entre média e diária, LC 121); sick leave/maternidade = Poryadok 1266, com **lista de exclusão própria**. Não misturar a lista do 1266 com a do 100 (erro corrigido no CCG 8.2). Indexação (1078) não é média e usa o base month = "Effective Date of Current Salary".
3. **Escopo de Compliance:** mantemos só o **master WTC**. Catálogo de cliente (Altium) e WTs "cinza" são do cliente/team lead. **A atribuição de códigos de PE é da BA (Lily)**: PEs novos entram sem código. Saldo de férias é do leave module (Vaishnavi). Desenvolvimento de relatório e payroll é do Dev (Michael) e do Product (Mohit).
4. **Relatórios estatutários UA (D1, D5, D6, 4DF) são anexos do mesmo formulário J05:** mesmo cabeçalho; flag 011/012/013 → HZ/HZN/HZU com C_DOC_STAN 1/2/3; tags HBOS/HBUH obrigatórias; **relatórios em ucraniano** (requisito estatutário). 4DF e D1 são **mensais** para pessoa jurídica desde 2026-01-01 (Law 4536-IX). Pedido recorrente da BA: "true XML sample" (não schema) para D1/D5/D6/4DF.
5. **Itens de DD vs. WTC:** salário em USD, bônus e indexação são lógica de WTC, não master data. Dados históricos pré-go-live vão num grupo separado do DD ("Historical Payroll Data (Pre-Go-Live Migration)").
6. **ESV:** base mínima não se aplica no mês de admissão/desligamento nem a pessoas com deficiência (8.41%); vale para o CPC só quando há emprego no mesmo empregador (mantivemos contra a objeção da Nataliia).
7. Padrão de trabalho: a solicitante (Nataliia) frequentemente corrige ou refina com base em PKU/Poryadok, e nós conferimos ponto a ponto, aceitamos quando procede e mantemos quando não procede (ex.: CPC main place of work).

### (b) Lista de [INCERTO]
1. **Período-base do sick leave:** "6 meses" (nossa resposta no HRBS-14331, colunas K/X) contra "12 meses" (nossas respostas no HRBS-12631 e no HRBS-13392, e as regras da Nataliia). Contradição nossa a resolver.
2. **Faixas de % do sick leave por tempo de seguro:** HRBS-13389 (<5 60% / 5-8 80% / 8+ 100%) contra HRBS-14331 (<3 50% / 3-5 60% / 5-8 70% / >8 100%). Ambas vêm da solicitante e nenhuma tem fonte. Não sabemos quais valores entraram no CCG V1.5.
3. **Versão do DD no HRBS-13392:** o texto diz v3.7 e o anexo se chama V3.8.
4. **Código 65808:** no HRBS-12181 é "Representation expenses (financial)"; no HRBS-14331 a Nataliia o chama de "Life Insurance (BIK)", e nossa resposta fala em "65808 base + 65894 grossed-up" (o 65894 depois se mostrou inexistente). Os códigos de representação também variam (65806/65808 contra 65806/65807).
5. **4DF 128 para maternidade:** pusemos no CCG "maternidade → 128". A Nataliia diz que 128 é só para a licença de 126 + 14 dias e que 65700-65712 seriam 101 ou 126. Sem resposta.
6. Papel exato de Nataliia Hahan e Vaishnavi Mane (não declarado). "Drew" (motor) não identificado.
7. HRBS-12548: não há registro de tratamento do relatório de sick leave do Pension Fund (Tab. 2) nem dos relatórios internos.
8. HRBS-14255: não está claro se Compliance precisa entregar algo além do CCG V1.3.
9. HRBS-13499: campos específicos da GSK (Grade 2, City of Work, Manager) ainda sem destino.
10. Órgão emissor das cartas de 27.05.2019 nº 4340 e 15.04.2019 nº 553 e o portal de envio do 1-PV: perdidos na extração do cirílico.
11. Limite de 25% nos presentes (Vaishnavi, HRBS-12181) contra "25% do salário mínimo em 1º de janeiro" (HRBS-14324). O primeiro não diz 25% de quê.
12. Valores UAH 8.647 (salário mínimo 2026), 172.940 (base máxima do ESV) e 864,70 / EUR 80 (per diem) foram afirmados pela solicitante e não confirmados por nós no ticket.
13. SR-163: o Dev mapeou "Chief Accountant RNOCPP" para director_signatory_rnocpp (possível erro, não tratado).
14. HRBS-14331, últimos comentários: "deveria ser 102" e "sem nenhum imposto (licença-cuidado 3/6 anos?)". Os códigos estavam em imagens não capturadas.
15. Os códigos de tipo de acréscimo do D1 para 79414/79415 estão TBC.

### (c) Artefatos e últimas versões citadas (Ucrânia)
| Artefato | Última versão citada | Ticket / data (~) | Estado |
|---|---|---|---|
| WTC master (Ukraine_Wage_Type_Catalogue_Mercans) | **V3.9 (draft, para revisão)**; antes v3.8 (2026-08-12/13, base do "WTC finalizado" da Lily) | HRBS-14331, ~2026-09-21 | Draft. A Lily publicou o "Finalized WTC" (Google Sheets) em ~09-21 |
| Histórico do WTC | V3.2 (D1, 62964 → 13) → v3.4 → v3.5 (79417) → v3.6 (79414/79415) → v3.7 → v3.8 (20 PEs gross-up) → V3.9 | SR-160, HRBS-12181/12631/14331 | |
| CCG (Ukraine_Country_Configuration_Guide_FY2026) | **V1.5 (draft)** | HRBS-14331, ~2026-09-21 | Histórico: v1.1 (Module 8, ~08-05) → v1.2 (~08-11) → V1.3 (~09-08) → V1.5 [V1.4 não citada] |
| Data Dictionary (Ukraine_Data_Dictionary) | **V3.8** (anexo do HRBS-13392, ~2026-08-19), depois incremento com chief_accountant_name (~09-25, sem número de versão) | HRBS-13392 / SR-160 | Histórico: V3.3 (part_time_indicator) → V3.4 → V3.5 (HRBS-12368) → v3.7/V3.8 [INCERTO] |
| WTC do cliente Altium | WTC_Altium_Ukraine_2026_2 | HRBS-14331 | Mantido pela Nataliia/cliente (fora do nosso escopo) |
| Report Spec D1 (UA-D1-001_UnifiedSocialContribution_Spec) | atualizada ~2026-08-20 (HBOS/HBUH) | SR-160 | In Review; falta XML real |
| Report Spec 4DF (UA-4DF-001_PersonalTax_Spec) | atualizada ~2026-08-20 | SR-161 | In Review; QC do Dev em andamento; falta XML real |
| Report Spec D5 (UA-D5-001_LabourRelations_Spec) | **v3** | SR-162 | In Review; falta XML real |
| Report Spec D6 (UA-D6-001_SpecialSeniority_Spec) | **v3** | SR-163 | In Review; falta XML real |
| Report Spec 1-PV mensal (UA-1PV-001) | sem número | SR-414 | Open; perguntas da BA de 09-29 |
| Report Spec 1-PV trimestral (UA-1PV-002) | sem número (Report Matrix linha 16 com formato) | SR-415 | Open; perguntas da BA de 09-29 |
| Payslip (Payslip Spec 1; templates Ukraine EN/UK) | sem número | SR-340 | In Progress (Dev); inconsistência template × spec em aberto |
