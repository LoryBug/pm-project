---
title: "Risk Analysis"
nav_order: 9
parent: "Parte 2 — Documentazione"
---
# Risk Analysis — CTAF

Questo documento è il **registro dei rischi master** del progetto. Tutti gli altri
documenti (PDS, planning, monitoring) fanno riferimento ai codici R1–R10 qui definiti.

## Registro dei Rischi

| # | Rischio | Categoria | P | I | PxI | Strategia | Proprietario |
|---|---|---|---|---|---|---|---|
| R1 | Indisponibilità o degrado del servizio LLM (Groq/OpenRouter) | Tecnologico | M | A | 6 | Mitigazione | Team LLM |
| R2 | Complessità di integrazione Jason-Python (bridge BDI-LLM) | Tecnologico | A | A | 9 | Mitigazione | Team BDI |
| R3 | Ritardi nella disponibilità del team per impegni accademici | Risorse | M | M | 4 | Accettazione | PM |
| R4 | Ambiguità/inconsistenza dei claim clinici generati dall'LLM | Qualitativo | M | M | 4 | Mitigazione | Team LLM |
| R5 | Incompatibilità tra versioni delle librerie (Jason/DSPy/Java) | Tecnologico | B | A | 3 | Contingenza | Team BDI |
| R6 | Timeline semestrale insufficiente per tutti i componenti | Pianificazione | M | A | 6 | Mitigazione | PM |
| R7 | Difficoltà di debugging del ciclo BDI in Jason | Tecnologico | M | M | 4 | Accettazione | Team BDI |
| R8 | Documentazione tecnica insufficiente per manutenzione futura | Qualitativo | M | B | 2 | Mitigazione | PM |
| R9 | Runtime Jason instabile o versione non più mantenuta | Tecnologico | B | A | 3 | Contingenza | Team BDI |
| R10 | Scope creep verso funzionalità cliniche aggiuntive o verso la tesi | Gestionale | M | M | 4 | Prevenzione | PM |

### Legenda

| Sigla | Probabilità (P) | Impatto (I) |
|---|---|---|
| B | Bassa (< 25%) | Basso (ritardo < 1 settimana) |
| M | Media (25–60%) | Medio (ritardo 1–2 settimane) |
| A | Alta (> 60%) | Alto (blocco componente o fallimento obiettivo) |

PxI è calcolato su scala 3×3 (B=1, M=2, A=3), valore massimo 9. Rischi con PxI ≥ 6 sono considerati prioritari (R1, R2, R6).

## Piano di Risposta ai Rischi

| # | Trigger | Risposta | Azione Specifica |
|---|---|---|---|
| R1 | Errore 429/503 persistente > 24h sul provider primario | Attivare fallback | Passare a OpenRouter; in ultima istanza inference locale via Ollama/llama.cpp |
| R2 | Bridge HTTP non funzionante dopo 1 settimana | Implementazione alternativa | Passare da bridge HTTP a bridge file-based con polling JSON |
| R3 | Assenza ricorrente di un membro alle daily | Accettazione + buffer | Ripianificare con scope bank 10%, ridistribuire i task critici |
| R4 | Output LLM ambiguo o contraddittorio in 2+ chiamate consecutive | Rafforzare validazione | Validatore JSON-schema + post-processore di disambiguazione + revisione umana prioritaria |
| R5 | Conflitto di versioni in fase di build | Contingenza | Container Docker con versioni fissate di Jason/DSPy/Java |
| R6 | Sprint in ritardo > 1 settimana rispetto alla milestone | Riduzione ambito | Tagliare gli obiettivi Could-have (O7), usare lo sprint di riserva |
| R7 | Ciclo agente non termina dopo 3 tentativi | Logging avanzato | Isolare l'agente e testarlo con input minimo |
| R8 | Modulo nuovo senza README dopo 1 settimana | Checklist review | Task dedicato di documentazione nella DoD |
| R9 | Crash del runtime su uno scenario golden | Docker image bloccata | Rollback a versione certificata in container |
| R10 | Richiesta di nuove funzionalità cliniche in Sprint Review | Rinvio a backlog futuro | MoSCoW rigido, backlog congelato dopo Sprint 2; se > 2 giorni → "future work" |

## Rischi Attivati durante l'Esecuzione (consuntivo)

| # | Esito | Note |
|---|---|---|
| R1 | Attivato (Sprint 2) | Rate limit Groq superato → fallback OpenRouter funzionante |
| R3 | Attivato parzialmente (Sprint 4) | Esami accademici → assorbito dal buffer |
| R4 | Attivato (Sprint 4) | Claim ambigui su gc_gray_zone → post-processore via management reserve |
| R5 | Prevenuto | Docker ha evitato problemi di versione |
| R2, R6–R10 | Non attivati | Mitigazioni preventive efficaci |
