---
title: "Sprint Plan"
nav_order: 11
parent: "Parte 2 — Documentazione"
---
# Sprint Plan — CTAF

## Sprint

| Sprint | Durata | Periodo | Goal | Deliverable | Backlog Items |
|---|---|---|---|---|---|
| Sprint 1 | 2 settimane | 23/03 - 05/04/2026 | Runtime BDI funzionante | 4 agenti Jason, bridge Jason-Python, golden case gc04 | 1.3.1, 1.3.2, 1.3.3 |
| Sprint 2 | 2 settimane | 06/04 - 19/04/2026 | Pipeline LLM operativa | DSPy pipeline, claim extraction, rule drafting, validazione su gc00 e gc04 | 1.4.1, 1.4.2, 1.4.3, 1.4.4 |
| Sprint 3 | 2 settimane | 20/04 - 03/05/2026 | Web App review console | Rule Review Console, Trace Inspector, proxy LLM backend, integrazione | 1.5.1, 1.5.2, 1.5.3, 1.5.4 |
| Sprint 4 | 2 settimane | 04/05 - 17/05/2026 | Integrazione e validazione finale | Test e2e su gc00/gc04/gc_gray_zone, CLI, documentazione 14 artefatti | 1.6.1, 1.6.2, 1.6.3, 1.6.4, 1.6.5, 1.7 |
| Sprint 5 (Riserva) | 1 settimana | 18/05 - 24/05/2026 | Recupero imprevisti e rifiniture | Gestione ambiguità gc_gray_zone, bug fix, miglioramenti minori | Backlog arretrato |
| Sprint 6 (Chiusura) | 1 settimana | 25/05 - 31/05/2026 | Collaudo finale e consegna | Demo script, verifica finale, repository pubblico | 1.8.4, collaudo, delivery |

## Prioritizzazione MoSCoW

| Priorità | Item | Sprint Assegnato |
|---|---|---|
| **Must-have** | Agenti BDI (runtime_coordinator, case_reasoner, trace_guardian, care_planner) | Sprint 1 |
| **Must-have** | Pipeline LLM con estrazione regole e valutazione | Sprint 2 |
| **Must-have** | Bridge Jason-Python | Sprint 2 |
| **Must-have** | Web App (backend + frontend + flusso revisione) | Sprint 3 |
| **Must-have** | Tracciabilità (Justification Tree) | Sprint 3-4 |
| **Must-have** | Test e2e su 3 scenari | Sprint 4 |
| **Should-have** | Documentazione 14 artefatti | Sprint 4 |
| **Should-have** | CLI script unificato | Sprint 4 |
| **Could-have** | Repository GitHub pubblico | Sprint 6 |
| **Could-have** | Docker container | Sprint 6 |
| **Won't-have** | Deploy cloud, autenticazione avanzata, analisi statistica | — |

---

## Definition of Ready (DoR)

Una user story può entrare in uno sprint solo se soddisfa i seguenti criteri:

| # | Criterio | Verificato da |
|---|---|---|
| DoR-1 | Story scritta nel formato "Come <ruolo> voglio <obiettivo> per <valore>" | PO/PM |
| DoR-2 | Criteri di accettazione definiti e testabili | Team |
| DoR-3 | Stima in story point condivisa (planning poker) | Team |
| DoR-4 | Dipendenze identificate e non bloccanti | PM |
| DoR-5 | Dimensione adeguata a chiudersi entro lo sprint | Team |
| DoR-6 | Priorità MoSCoW assegnata | PM |

---

## Definition of Done (DoD)

Per ogni elemento del backlog, i seguenti criteri devono essere soddisfatti per considerare il task completato:

| # | Criterio | Descrizione | Verificato da |
|---|---|---|---|
| DoD-1 | Codice completo | Il codice soddisfa i criteri di accettazione della user story | Sviluppatore |
| DoD-2 | Code review | Pull review approvata da almeno un altro membro del team | Reviewer |
| DoD-3 | Test passati | Test unitari e di integrazione passano | CI pipeline |
| DoD-4 | Documentato | README, docstring o documentazione aggiornata | PM |
| DoD-5 | Dimostrabile | La funzionalità è dimostrabile allo Sprint Review | Team |
| DoD-6 | Nessun warning critico | Nessun errore runtime o warning bloccante | Sviluppatore |

### DoD per Sprint

| Sprint | DoD aggiuntivo specifico |
|---|---|
| Sprint 1 | Agenti rispondono correttamente a stimulate JSON, traccia esportabile |
| Sprint 2 | Bozze regole in formato JSON valido e validato |
| Sprint 3 | UI funzionante su 3 scenari di test, API integrate |
| Sprint 4 | CLI funzionante, e2e su 3 golden case, 14 artefatti PM consegnati |
| Sprint 5 (Riserva) | Bug critici risolti, ambiguità documentata |
| Sprint 6 (Chiusura) | Demo script funzionante, repository pubblico, consegna completata |

---

## Acceptance Criteria per Sprint

Criteri specifici di accettazione per le user story di ogni sprint, oltre alla DoD generale.

### Sprint 1 — Runtime BDI

| Story | Criterio di Accettazione |
|---|---|
| 1.3.1 Agenti Jason | Ogni agente risponde a stimulate JSON con il comportamento atteso |
| 1.3.2 Regole gc04 | Beliefs gc04 caricate correttamente, regole approvate eseguite |
| 1.3.3 Trace export | Traccia JSON generata e validata con validate-trace script |

### Sprint 2 — Pipeline LLM

| Story | Criterio di Accettazione |
|---|---|
| 1.4.1 DSPy setup | Pipeline esegue almeno una chiamata a Groq e restituisce output |
| 1.4.2 Claim extraction | Almeno 5 claim estratti da testo clinico gc00 e gc04 |
| 1.4.3 Rule drafting | Bozze regole in formato regole standard validato da JSON-schema |
| 1.4.4 Pipeline integrazione | Pipeline end-to-end: input testo -> output bozza regola |

### Sprint 3 — Web App

| Story | Criterio di Accettazione |
|---|---|
| 1.5.1 Rule Review Console | Revisore può approvare/scartare regole e aggiungere commenti |
| 1.5.2 Trace Inspector | Traccia JSON visualizzata con react-mermaid, nodi cliccabili |
| 1.5.3 Proxy LLM | API key gestite lato server, frontend chiama proxy |
| 1.5.4 Integrazione | API integrate, flusso completo da web app a runtime BDI |

### Sprint 4 — Integrazione Finale

| Story | Criterio di Accettazione |
|---|---|
| 1.6.1 End-to-end | CLI `ctaf run scenario.json` completa il flusso su gc00 |
| 1.6.2 gc00 validation | Rischio basso: nessun esame, traccia valida |
| 1.6.3 gc04 validation | Rischio alto: CMR-driven, traccia valida |
| 1.6.4 gc_gray_zone | Zona grigia: PET mancante gestito con post-processore |
| 1.6.5 Ambiguità claim | Post-processore disambiguazione funzionante |
| 1.7 Documentazione | 14 artefatti PM completati e revisionati |
