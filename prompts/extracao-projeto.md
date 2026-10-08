# Prompt de extração: projetos do Claude da Mercans

> Como usar: abra cada projeto (ou chat importante) no Claude da Mercans, cole o prompt abaixo,
> copie a resposta e salve em `raw/chats/AAAA-MM-DD-<projeto>.md`. Depois diga aqui: "ingere raw/chats/<arquivo>".
> Para projetos grandes, rode uma vez por país ou por tema.

---

```
Preciso extrair o conhecimento acumulado neste projeto (instruções, arquivos e conversas que você consegue ver) para uma base de conhecimento do nosso serviço. Responda SOMENTE com o que está registrado aqui. Não invente nem complete com conhecimento geral. Quando não tiver certeza, marque [INCERTO].

NÃO inclua dados pessoais de funcionários de clientes (nomes, IDs, salários individuais).

Responda em Markdown, com estas seções:

## 1. Sobre este projeto
- Para que serve, qual etapa do nosso serviço cobre (Research Pipeline / Design / Suporte) e quais países.

## 2. Entregas
Tabela: País | Artefato (CCG, WTC, DD, Report Specs, SIR, Payslip, outro) | Versão | Data | Status

## 3. Decisões tomadas
- AAAA-MM-DD (ou aproximada) | País | Decisão | Motivo | Quem decidiu (cargo/papel)

## 4. Valores e regras estatutárias definidos
Tabela: País | Item | Valor | Vigência (a partir de / até) | Fonte citada

## 5. Erros e correções
Tabela: País | O que estava errado | O correto | Fonte | Onde aconteceu

## 6. Padrões e método
- Regras de formato, nomes de arquivo, modelos (ex.: "mesmo modelo da Espanha"), checagens de qualidade.

## 7. Tickets e dúvidas de suporte
Tabela: Ticket | País | Pergunta | Resposta dada | Fonte | Mudou artefato?

## 8. Pendências em aberto
- O que ficou para fazer, de quem é.

## 9. Fronteiras
- O que foi tratado como responsabilidade de outro time.
```
