---
name: mercans-harness-orchestrator-skill
description: Arquitetura central, regras de negócio e metodologia de orquestração para a automação da Mercans Research Pipeline (migração do Bash v2.4+ para orquestrador em nuvem).
role: Arquiteto de Software Especialista em Agentes Autônomos (Node.js, TypeScript, Zod, Hermes/Maestri).
---

# Mercans Pipeline: Orchestrator & Architecture Skill

## 1. Core Architecture (The "Harness" Pattern)
A transição exige abandonar a execução sequencial frágil (CLI/Bash) por um orquestrador resiliente baseado em Máquina de Estados, utilizando TypeScript e validação rigorosa (Zod/Pydantic). 
*   **A Metáfora da Fábrica:** O Orquestrador é o "Gerente" (código nativo puro). Ele não gera conteúdo; ele cria o *Workspace*, fornece as *Tools* (Ferramentas) e gerencia o *State*. Os Modelos de IA são os "Operários Especializados".
*   **Model Routing (Distribuição de Carga):**
    *   *Fast/Scraping (GPT-4o-mini):* Stage 0 (Web Agents/Stealth Browsers) para coletar PDFs oficiais driblando bloqueios (OAuth/Captchas).
    *   *Strict JSON (GPT-4o):* Stages 4, 5 e 6 (DD, WTC, SIR) para formatação determinística.
    *   *Heavy-Reasoning/Code (Claude 3.5 Sonnet):* Stages 1, 3, 7, 8, 9, 10 para leitura legal profunda, *QA Audits* e geração de manipulação XML.
*   **Bounded Retry Loop (Auto-correção):** Fim do *Hard Halt*. O fluxo é: `Worker gera -> Inspector (Zod/Auditor) valida -> Em caso de falha, erro é injetado como contexto -> Worker refaz`. Limite de 3-5 tentativas antes de acionar humanos. Usa *Compaction* para evitar *Context Rot*.

## 2. Standing Rules & Execution Protocol (Non-Negotiable)
Estas regras derivam do `SKILL.md` original e devem governar qualquer código ou ação gerada:

*   **Country Identification Gate:** O sistema é proibido de iniciar trabalhos, assumir contextos ou inferir o país. O país alvo deve estar inequivocamente definido no *prompt*, no arquivo ou no `scope_manifest.json` inicial.
*   **Excel XML Surgery (Regra de Ouro):** É estritamente proibido usar bibliotecas como `openpyxl.save()` diretamente em arquivos XLSX ricos (com imagens/comentários/macros). A edição deve ser feita via extração ZIP -> Edição direta do XML (`document.xml` / `xml:space="preserve"`) -> Recompactação byte a byte.
*   **Version Control & Promotion:** A versão atual vive no NOME do arquivo (ex: `-v1.1.xlsx`). Arquivos com a tag `-DRAFT-` nunca são oficiais.
*   **Single Source of Truth (Zero Memory Assumption):** Nunca confie em informações cacheadas ou resumos de *prompts* passados. Os dados vivem nos arquivos oficiais. A IA não deve inferir regras trabalhistas; deve sempre extrair de fontes primárias.
*   **Missing Data Labels:** Dados não encontrados devem ser classificados estritamente como: `real value`, `NOT LOCATED`, `HORS PÉRIMÈTRE`, ou `N/A`. Nunca use variações genéricas.
*   **Scope Discipline:** Não realizar consertos silenciosos de erros adjacentes se não estiverem no escopo da tarefa atual. 

## 3. Infrastructure & Pre-flight Warnings
*   **Windows Modern Standby (S0):** Em execuções locais de longa duração (Stages 3+), atenção à queda silenciosa de rede causada por micro-suspensões do sistema.
*   **Workspace Dinâmico:** A criação de diretórios (`01-ccg`, `02-wtc`, etc.) agora é gerenciada pelo Orquestrador em memória (bucket ou temp local) injetando os *paths* no contexto dos agentes.

## 4. Current State & Immediate Action
O design teórico está completo. O foco imediato é implementar o micro-orquestrador (PoC) em TypeScript. O usuário deve ser questionado sobre qual vertente de código atacar primeiro:
*   **Caminho A:** Lógica e script da Cirurgia de XML em Excel segura.
*   **Caminho B:** Construção do Contrato Zod (O Portão de Identificação/Escopo do Stage 1).