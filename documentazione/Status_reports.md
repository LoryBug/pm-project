---
title: "Status Reports"
nav_order: 13
parent: "Parte 2 — Documentazione"
---
# Status Reports — CTAF

---

## Status Report — Sprint 1

| Campo | Dettaglio |
|---|---|
| Sprint | 1 |
| Periodo | 23/03/2026 - 05/04/2026 |
| Stato | Verde |

### Attività

| Task | Stato | Note |
|---|---|---|
| 1.3.1 Agenti Jason (coordinator, reasoner, guardian, planner) | Completato | 4 agenti implementati e testati |
| 1.3.2 Regole e beliefs per gc04 | Completato | Regole approvate caricate come beliefs |
| 1.3.3 Trace export e validazione | Completato | Traccia JSON generata e validata con validate-trace |
| Esecuzione golden case gc04 | Completato | End-to-end funzionante su sospetto CMR-driven |
| Test unitari agenti BDI | Completato | 12 test, 12 passati |

### Rischi Attivi

| Rischio | Stato |
|---|---|
| R5 — Incompatibilità versioni librerie | Non attivato: Docker ha risolto i problemi di setup |

### Blocker

Nessun blocker.

### Prossimi Passi

- Sprint 2: sviluppo pipeline LLM (DSPy + Groq/OpenRouter)
- Test su claim clinici da letteratura

---

## Status Report — Sprint 2

| Campo | Dettaglio |
|---|---|
| Sprint | 2 |
| Periodo | 06/04/2026 - 19/04/2026 |
| Stato | Verde |

### Attività

| Task | Stato | Note |
|---|---|---|
| 1.4.1 Setup DSPy e provider LLM | Completato | Groq (primario) + OpenRouter (fallback) |
| 1.4.2 Claim extraction module | Completato | Estrazione claim da testo clinico |
| 1.4.3 Rule drafting module | Completato | Generazione bozze regole in formato standard |
| 1.4.4 Integrazione DSPy | Completato | Pipeline end-to-end funzionante |
| Test su claim gc00 e gc04 | Completato | 10 claim testati: 8 corretti, 2 con ambiguità minori |

### Rischi Attivi

| Rischio | Stato |
|---|---|
| R1 — LLM API non disponibile | Mitigato: rate limit Groq superato, fallback OpenRouter attivato |
| R4 — Ambiguità/inconsistenza claim LLM | Monitorato: 2 claim ambigui documentati, da gestire in Sprint 4 |

### Blocker

Nessun blocker.

### Prossimi Passi

- Sprint 3: sviluppo web app review console
- Preparazione trace inspector

---

## Status Report — Sprint 3

| Campo | Dettaglio |
|---|---|
| Sprint | 3 |
| Periodo | 20/04/2026 - 03/05/2026 |
| Stato | Verde |

### Attività

| Task | Stato | Note |
|---|---|---|
| 1.5.1 Rule Review Console | Completato | Approvazione/scarto regole con commenti |
| 1.5.2 Trace Inspector | Completato | Visualizzazione tracce JSON con react-mermaid |
| 1.5.3 Proxy LLM backend | Completato | API key gestite lato server |
| 1.5.4 Integrazione backend-frontend | Completato | API integrate e testate |
| Test UI/UX | Completato | 5 scenari testati, 5 superati |

### Rischi Attivi

| Rischio | Stato |
|---|---|
| Nessun rischio attivo | — |

### Blocker

Nessun blocker.

### Prossimi Passi

- Sprint 4: integrazione end-to-end, validazione golden case
- Gestione ambiguità claim su gc_gray_zone

---

## Status Report — Sprint 4

| Campo | Dettaglio |
|---|---|
| Sprint | 4 |
| Periodo | 04/05/2026 - 17/05/2026 |
| Stato | Giallo |

### Attività

| Task | Stato | Note |
|---|---|---|
| 1.6.1 Integrazione end-to-end | Completato | Tutti i componenti integrati |
| 1.6.2 Golden case gc00 validation | Completato | Rischio basso: nessun esame, traccia valida |
| 1.6.3 Golden case gc04 validation | Completato | Rischio alto: CMR-driven, traccia valida |
| 1.6.4 Golden case gc_gray_zone validation | Completato | Zona grigia: PET mancante, richiesto post-processore |
| 1.6.5 Gestione ambiguità claim (gc_gray_zone) | Completato | Post-processore disambiguazione (management reserve) |
| 1.7 Documentazione | Completato | 14 artefatti completati |
| 1.8.4 Demo script | Completato | Script end-to-end |

### Rischi Attivi

| Rischio | Stato |
|---|---|
| R4 — Ambiguità claim clinici | Attivato su gc_gray_zone, mitigato con management reserve |
| R6 — Timeline insufficiente | Monitorato: ritardo assorbito dalla riserva |

### Blocker

Nessun blocker. Il ritardo di 2 giorni su gc_gray_zone è stato assorbito dalla management reserve senza impattare la consegna.

### Prossimi Passi

- Chiusura: verifica finale, archiviazione Project Notebook
- Preparazione consegna elaborato
