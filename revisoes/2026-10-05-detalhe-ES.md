# Revisão ES (2026-10-05)

Nota de método: a ferramenta Read não renderiza PDF neste ambiente (pdftoppm ausente, erro nas 2 tentativas). Como substituto usei `pdftotext -layout` no PDF original de CT-A-485, que preservou a ordem das linhas da tabela (a ordem das fórmulas G1, G2, G3, G4-7 e os rótulos das diárias ficaram legíveis). Se quiserem conferência visual, abrir o PDF p. 5-6 e 7.

## A. Alterações feitas nos hubs
- Espanha: regra 8 aplicada. CCG "v1.6 (vigente: maior versão)"; DD "VC 4.6 (vigente: maior versão)" (remoção dos 58 campos, V4.0 Draft e demais numerações foram para Observação como histórico; [INCERTO] removido); Bases "v2.5 (vigente: maior versão)"; CRA V2.3, AFI-OUT VC 1.4 e M296 V2.3 com sufixo; M190 "v3.3 (vigente: maior versão)" com v2.7 no histórico. WTC já estava V4.4.
- Espanha: Pendência de conflito de versão WTC/DD marcada [x] resolvida (regra 8).
- Espanha: tope máximo: removido [INCERTO] do diário 170,04 e completada a vigência (2026-01-01) e fonte (skill 01-ccg.md §2.2).
- Espanha: bases mínimas G1/G2/G3/G4-7: removido [INCERTO] da associação grupo-valor (confirmada no PDF de CT-A-485: 1929 / 1599,60 / 1391,70 / 1424,50, nessa ordem); acrescentada nota de que a skill traz valores diferentes (ver B1/B2). Valores do hub NÃO alterados.
- Espanha: vigência e fonte completadas a partir da skill (mesmo valor): CC 4,7/23,6 (Orden art. 4.a), desemprego 1,55/5,5 e 1,6/6,7 (art. 33.2.a), FOGASA/FP (art. 33.2.b/c), solidariedade 0,19/0,96; 0,21/1,04; 0,24/1,22 (art. 17, DT 42.ª), acidente de trabalho (art. 173.1).
- Espanha: pendência CT-A-485 reescrita: "per km" resolvido como erro de rótulo da fonte (são valores por dia: 26,67 / 91,35 / 48,08, confirmados em 01-ccg.md §8 como per day; a linha 53,34 já diz "per day"); associação resolvida; 58208 permanece [INCERTO].
- Espanha: pendência da divergência G4-7 anotada com a confirmação da skill (checkbox segue aberto, aguarda aprovação).

## B. Propostas (precisam de aprovação)
| País | Item | Hub diz | Fonte diz (trecho curto + ref) | Proposta concreta | Risco |
|---|---|---|---|---|---|
| Espanha | B1. Base mínima G4-7 | ~1.424,50 (provisório) (CT-A-485) | "not below €1,424.40/month"; grupos 4-7 = 1.424,40; diário 47,48 × 30 (01-ccg.md §2.2; Orden PJC/297/2026 arts. 2-3) | Fechar linha antiga com Até 2026-10-05 (ou marcar como valor de CT-A-485 divergente) e acrescentar nova linha G4-7 = 1.424,40 a partir de 2026-01-01 (fonte: Orden PJC/297/2026 art. 3, via skill). Corrigir o KB CT-A-485 (fórmulas 1424.50 nos itens "Group 4-7", "Ceiling Part-Time" e "Floor Daily Employee", além de 529xx) | alto |
| Espanha | B2. Bases mínimas G1/G2/G3 | 1.929,00 / 1.599,60 / 1.391,70 (CT-A-485, fórmulas dos WTs 52982-52984) | Skill: G1 1.989,30; G2 1.649,70; G3 1.435,20 (01-ccg.md §2.2; Orden arts. 2-3, verbatim) | Fechar as linhas antigas e acrescentar G1 1.989,30 / G2 1.649,70 / G3 1.435,20 a partir de 2026-01-01 (fonte: Orden PJC/297/2026 art. 3). Os valores do CT-A-485 parecem de outro ano ou de cálculo antigo: a inconsistência G3 (1.391,70) < G4-7 (1.424,50) some com os valores da skill (G3 1.435,20 > 1.424,40). Revisar fórmulas dos WTs de piso no design | alto |
| Espanha | B3. Bases mínimas part-time por hora G1/G2/G3/G4-11 | 11,98 / 9,94 / 8,65 / 8,58 (CT-A-485 confirma; chat cita Orden) | Skill não traz tabela horária (grep sem resultado) | Sem alteração; se B2 for aprovado, conferir se estas taxas horárias derivam dos pisos antigos e reverificar contra a Orden | médio |
| Espanha | B4. Versões M190 / Bases | (aplicada regra 8 mecanicamente) | M190: v2.7 (SR-83) × "cópia v3.3 do Compliance" (numeração de outra origem); Bases: v2.5 (HRBS-13757) × v2.1-v2.4 e consolidado (SR-79) | Confirmar que a numeração é a mesma série; se for outra série, reverter para v2.7 e para "consolidado" | baixo |

## C. Perguntas para o Wallisson (respondíveis em 1 linha)
- [Espanha] O que significa 58208 = 1/2/3/4/5 no CT-A-485 (2/3 parecem estagiários; 4 = 2%/7%)? (não consta na skill nem no ticket; origem: CT-A-485)
- [Espanha] Os valores 1.929 / 1.599,60 / 1.391,70 / 1.424,50 das fórmulas de piso no CT-A-485 estão em produção nos WTs (52982-52984 etc.) ou são rascunho antigo? (B1/B2)
- [Espanha] O DD V4.0 Draft de 29/09 é arquivo novo posterior ao VC 4.6 ou o VC foi renumerado? Hoje vale VC 4.6 pela regra 8, mas o V4.0 é o mais recente em data. (origem: chat mercans-compliance)
- [Espanha] A amostra A3 A26S0003.AFI valida o AFI inbound (SR-80) ou o outbound (SR-432)? (origem: SR-80 × SR-432)

## D. Contagem
- Espanha: linhas com [INCERTO] 14 → 10 (marcadores removidos: DD versão, tope diário, associação grupo-valor, conflito de versão WTC/DD; "per km" resolvido dentro da pendência de CT-A-485, que mantém [INCERTO] só para 58208). Divergências hub × skill: 1 confirmada e virou proposta (B1, estendida a G1-G3 em B2); 6 completamentos de fonte/vigência feitos. Os [INCERTO] restantes (M190 regressão, A3, SR-85, SR-79, SR-432 x2, SR-342, HRBS-13757/10563, ordinais 456/461, 58208) dependem de informação do ticket/Dev e foram mantidos.
