---
title: "3. Planning"
nav_order: 3
parent: "Parte 1 — Approccio"
---
# 3. Planning

## Joint Project Planning Session (JPPS)

La pianificazione dettagliata è stata condotta in due sessioni JPPS consecutive, secondo le pratiche del modello Iterative Scrum con adattamenti per R&D. Le sessioni hanno coinvolto il Project Manager e l'intero Core Team, con la partecipazione del Committente nella fase di validazione.

### JPPS -- Sessione #1

| Campo | Dettaglio |
|---|---|
| **Data** | 2026-03-18 |
| **Ora** | 14:00 - 17:00 |
| **Luogo** | Laboratorio didattico, Campus |
| **Partecipanti** | Studente PM, Team di progetto (3 sviluppatori) |

#### Agenda

1. Review del POS approvato e validazione del PDS
2. Scomposizione del lavoro: dalla RBS alla WBS
3. Stima delle attività con tecnica dei tre punti
4. Identificazione delle dipendenze tra attività

#### Sintesi dello Svolgimento

Il PM ha presentato il PDS come estensione del POS, includendo obiettivi dettagliati (O1-O5), criteri di successo misurabili e vincoli aggiornati. Il team ha proceduto alla scomposizione del lavoro utilizzando la RBS come riferimento: ogni risk package è stato tradotto in work package della WBS. Per ogni pacchetto di lavoro, sono state identificate le attività elementari e stimate utilizzando la tecnica dei tre punti (Ottimistico, Pessimistico, Più Probabile). Le stime sono state inserite in un foglio di calcolo condiviso. Le dipendenze sono state mappate: emerge che il modulo LLM (Sprint 2) dipende dal motore BDI funzionante (Sprint 1), mentre la console web (Sprint 3) può partire in parallelo alla pipeline LLM dopo una fase di progettazione condivisa.

#### Decisioni

- WBS composta da 4 macro-pacchetti corrispondenti agli sprint
- Tecnica dei tre punti adottata per tutte le stime
- Stime in giorni/uomo con fattore di correzione per impegni accademici (0.5 FTE per membro)

#### Azioni

- PM: completare il network diagram e identificare il critical path
- Team: validare le stime sul tempo necessario per l'apprendimento di DSPy
- PM: preparare la matrice di responsabilità (RACI)

### JPPS -- Sessione #2

| Campo | Dettaglio |
|---|---|
| **Data** | 2026-03-19 |
| **Ora** | 14:00 - 16:30 |
| **Luogo** | Laboratorio didattico, Campus |
| **Partecipanti** | Studente PM, Team di progetto (3 sviluppatori), Referente Cardiologia di Forlì (validazione) |

#### Agenda

1. Presentazione del network diagram e critical path
2. Analisi dei rischi e strategie di mitigazione
3. Pianificazione economica e delle risorse
4. Definizione del piano sprint
5. Validazione da parte del committente

#### Sintesi dello Svolgimento

Il PM ha presentato il network diagram evidenziando il critical path: configurazione ambiente Jason -> implementazione agenti BDI -> integrazione LLM -> validazione golden case. Il percorso critico attraversa gli Sprint 1, 2 e 4, con lo Sprint 3 (console web) in parallelo non critico. L'analisi dei rischi ha portato a identificare 6 rischi con strategie di mitigazione specifiche. La stima economica conferma costo zero (strumenti open-source, crediti gratuiti LLM). Il piano sprint è stato definito in 4 sprint di 2 settimane ciascuno, più una settimana di riserva e una di chiusura. Il referente della Cardiologia di Forlì ha validato la pianificazione, suggerendo di prevedere un buffer di gestione del 10% per imprevisti tecnici.

#### Decisioni

- Critical path formalizzato: Setup BDI -> Agenti -> Pipeline LLM -> Validazione
- Strategie di mitigazione per tutti i 6 rischi approvate
- 4 sprint di 2 settimane: dal 23 marzo al 17 maggio 2026
- Management reserve fissata al 10% (da scope bank)
- Piano sprint approvato dal committente

#### Azioni

- PM: finalizzare il PDS con dati di pianificazione
- PM: configurare il repository GitHub con Projects (kanban board)
- Team: setup ambienti di sviluppo individuali

## PDS -- Project Definition Statement

Il PDS estende il POS con i dettagli emersi durante la pianificazione.

### Obiettivi (O1-O7)

| Codice | Obiettivo | Priorità MoSCoW | Criterio di Successo |
|---|---|---|---|
| O1 | Runtime BDI: 4 agenti Jason (coordinator, reasoner, guardian, planner) | Must | Agenti operativi e cooperanti sul golden case gc04 |
| O2 | Pipeline LLM per estrazione claim e bozza regole | Should | Modulo DSPy funzionante con Groq/OpenRouter |
| O3 | Console web per revisione regole e ispezione tracce | Should | App React/Vite operativa con visualizzazione tracce |
| O4 | Tracciabilità: structured trace per ogni decisione | Must | Traccia con regola, fonte, input, output per ogni decisione |
| O5 | Golden case: validazione su gc00, gc04, gc_gray_zone | Must | 3/3 golden case superati end-to-end |
| O6 | Esecuzione CLI: script unico di avvio del flusso | Must | Comando `ctaf run scenario.json` completa il flusso |
| O7 | Open source: repository GitHub con README e licenza | Could | Repository pubblicato con README, licenza MIT |

## WBS (Work Breakdown Structure)

WBS sintetica orientata agli sprint (la versione completa è in
[`documentazione/WBS.md`](../documentazione/WBS.md)):

- **1. Runtime BDI** — Sprint 1
    - 1.1 Setup ambiente Jason
    - 1.2 Implementazione agenti (4 agenti)
    - 1.3 Golden case gc04 su runtime
    - 1.4 Test unitari agenti
- **2. Pipeline LLM** — Sprint 2
    - 2.1 Setup DSPy e provider LLM
    - 2.2 Modulo claim extraction
    - 2.3 Modulo rule drafting
    - 2.4 Test su claims clinici
- **3. Web App Review** — Sprint 3
    - 3.1 Setup React/Vite
    - 3.2 Componenti rule review
    - 3.3 Visualizzazione tracce BDI
    - 3.4 Test UI/UX
- **4. Integrazione e Test** — Sprint 4
    - 4.1 Flusso end-to-end
    - 4.2 Validazione golden case
    - 4.3 Documentazione finale
    - 4.4 Preparazione deliverable

## Stime (Three-Point Technique)

| attività | Optimistic (d) | Most Likely (d) | Pessimistic (d) | PERT Estimate |
|---|---|---|---|---|
| Setup ambiente Jason | 0.5 | 1 | 2 | 1.1 |
| Agenti BDI (4 agenti) | 4 | 6 | 10 | 6.3 |
| Golden case gc04 su runtime | 1 | 2 | 4 | 2.2 |
| Setup DSPy e provider LLM | 1 | 2 | 3 | 2.0 |
| Modulo claim extraction | 3 | 5 | 8 | 5.2 |
| Modulo rule drafting | 3 | 5 | 8 | 5.2 |
| Setup React/Vite | 0.5 | 1 | 2 | 1.1 |
| Componenti rule review | 3 | 4 | 7 | 4.3 |
| Visualizzazione tracce BDI | 2 | 3 | 5 | 3.2 |
| Flusso end-to-end | 2 | 3 | 6 | 3.3 |
| Validazione golden case | 2 | 3 | 5 | 3.2 |
| Documentazione finale | 1 | 2 | 4 | 2.2 |

*Stime in giorni/uomo effettivi. Ogni membro del team lavora al 50% (0.5 FTE).*

Il calcolo PERT (tE = (O+4M+P)/6), la deviazione standard di attività (σ = (P−O)/6) e i
totali sono mantenuti nel foglio di calcolo allegato con formule live:
[`documentazione/allegati/Stime_PERT.xlsx`](../documentazione/allegati/Stime_PERT.xlsx).
Effort totale stimato: **39,17 giorni-uomo** (σ di progetto ≈ 2,12).

## Network Diagram e Critical Path

![Network diagram a livello di task — critical path in arancione](../img/network_tasks.svg)

*Sorgente: [`img/network_tasks.mmd`](../img/network_tasks.mmd). In arancione il percorso critico, in verde le attività parallele non critiche (console web).*

**Critical Path**: 1.1 -> 1.2 -> 1.3/2.1 -> 2.2 -> 2.3 -> 4.1 -> 4.2 -> 4.3
**Durata stimata del critical path**: 29.4 giorni/uomo (circa 6 settimane a 0.5 FTE)
**attività in parallelo (non critiche)**: 3.1, 3.2, 3.3 (console web)

> **Nota sulla granularità**: il critical path qui riportato (≈29,4 giorni-uomo, ~6 settimane
> a 0,5 FTE) è calcolato a livello di *task*. Quello in
> [`documentazione/Project_network_diagram.md`](../documentazione/Project_network_diagram.md)
> (9 settimane di calendario) è a livello di *macro-fase*. Le due misure hanno granularità
> diverse e sono coerenti tra loro.

## Analisi dei Rischi

| Codice | Rischio | P | I | PxI | Strategia | Mitigazione |
|---|---|---|---|---|---|---|
| R1 | Indisponibilità o degrado del servizio LLM (Groq/OpenRouter) | M | A | 6 | Mitigazione | Provider multiplo (Groq + OpenRouter), fallback locale (Ollama/llama.cpp) |
| R2 | Complessità integrazione Jason-Python (bridge BDI-LLM) | A | A | 9 | Mitigazione | Prototipo bridge HTTP, fallback file-based, test di integrazione continuo |
| R3 | Ritardi per impegni accademici del team | M | M | 4 | Accettazione | Buffer nel piano, scope bank 10% |
| R4 | Ambiguità/inconsistenza dei claim clinici generati dall'LLM | M | M | 4 | Mitigazione | Validazione strutturale output + post-processore di disambiguazione |
| R5 | Incompatibilità tra versioni delle librerie (Jason/DSPy/Java) | B | A | 3 | Contingenza | Container Docker con versioni fissate |
| R6 | Timeline semestrale insufficiente | M | A | 6 | Mitigazione | MoSCoW rigido, sprint di riserva, priorità Must-have |

P = Probabilità (A=Alta, M=Media, B=Bassa); I = Impatto (A=Alto, M=Medio, B=Basso); PxI su scala 3×3 (1–9). Il registro completo dei rischi (R1–R10) è in [`documentazione/Risk_analysis.md`](../documentazione/Risk_analysis.md).

## Stima Economica

| Voce | Importo | Note |
|---|---|---|
| Licenze software | EUR 0 | Tutti open-source (Jason, Python, React, Vite) |
| Servizi LLM | EUR 0 | Crediti free-tier Groq e OpenRouter |
| Infrastruttura | EUR 0 | Repository GitHub, GitHub Projects, GitHub Pages |
| Strumenti di sviluppo | EUR 0 | VS Code, Git, Docker |
| **Totale** | **EUR 0** | Progetto accademico a budget zero |

## Piano Sprint

| Sprint | Periodo | Obiettivi | Deliverable |
|---|---|---|---|
| Sprint 1 | 23 Mar -- 5 Apr 2026 | O1: Runtime BDI | 4 agenti Jason funzionanti su gc04 |
| Sprint 2 | 6 Apr -- 19 Apr 2026 | O2: Pipeline LLM | Moduli DSPy per claims e rule drafting |
| Sprint 3 | 20 Apr -- 3 May 2026 | O3: Web App | Console React/Vite per review e trace |
| Sprint 4 | 4 May -- 17 May 2026 | O4 + O5: Integrazione e documentazione | Flusso E2E, golden case, report finale |

## Matrice delle Responsabilità (RACI)

Legenda: **R** = Responsible (esegue), **A** = Accountable (risponde del risultato), **C** = Consulted (consultato), **I** = Informed (informato).

| Attività | PM | Dev Jason (BDI) | Dev Python (LLM) | Dev Frontend | Committente |
|---|---|---|---|---|---|
| Requisiti e Scoping | A | C | C | C | C |
| Planning (PDS, WBS, stime) | A/R | C | C | C | I |
| Runtime BDI (agenti) | A | R | C | I | I |
| LLM Pipeline | A | C | R | I | I |
| Web App Review | A | I | C | R | I |
| Tracciabilità (Justification Tree) | A | R | C | C | I |
| Integrazione e Test e2e | A | R | R | R | I |
| Documentazione | A/R | C | C | C | I |
| Gestione rischi e monitoraggio | A/R | C | C | C | I |
| Sprint Review e accettazione | R | C | C | C | A |
