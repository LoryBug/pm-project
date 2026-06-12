---
title: "Meeting Minutes"
nav_order: 12
parent: "Parte 2 — Documentazione"
---
# Meeting Minutes — CTAF

---

## Meeting 1 — Scoping Meeting #1

| Campo | Dettaglio |
|---|---|
| Data | 2026-03-04 |
| Ora | 14:00 - 15:30 |
| Luogo | Aula riunioni DIBRIS / Google Meet |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend |
| Tipo | Scoping e Kick-off |

### Ordine del Giorno

1. Presentazione dell'idea progettuale e contesto clinico
2. Definizione dell'ambito "Cardiac Traceability Agent Framework"
3. Identificazione tecnologie e stack
4. Assegnazione ruoli preliminari
5. Prossimi passi e milestone

### Sintesi

Il team ha discusso l'idea progettuale. Toni iniziali confusi sul dominio clinico — qualcuno proponeva "qualunque patologia cardiaca", poi si è circoscritto alle masse cardiache per via delle linee guida ESC. Stack scelto in 10 minuti: Jason per agenti, Python per LLM, React per web app. Il rischio del bridge Jason-Python è stato sollevato ma non approfondito — rimandato al JPPS.

### Decisioni

- Stack tecnologico: Jason 3.2 + Python 3.11 + FastAPI + React 18
- Repository GitHub creato su organizzazione del team
- Meeting settimanale ogni lunedi alle 14:00
- Strumento di project management: GitHub Projects

### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Creare repository GitHub con struttura base | Sviluppatore Jason | 05/03/2026 |
| Redigere POS | PM | 08/03/2026 |
| Redigere CoS | PM | 08/03/2026 |
| Redigere SWOT e RBS | PM | 10/03/2026 |
| Setup ambiente di sviluppo Jason | Sviluppatore Jason | 10/03/2026 |
| Setup ambiente Python con FastAPI | Sviluppatore Python | 10/03/2026 |

---

## Meeting 2 — Scoping Meeting #2

| Campo | Dettaglio |
|---|---|
| Data | 2026-03-11 |
| Ora | 14:00 - 16:00 |
| Luogo | Google Meet |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend |
| Tipo | Scoping e Pianificazione |

### Ordine del Giorno

1. Review documenti di scoping (POS, CoS, SWOT, RBS, PDS)
2. Validazione architettura preliminare
3. Definizione sprint e milestone
4. Identificazione rischi iniziali
5. Pianificazione primo sprint

### Sintesi

Documenti di scoping revisionati. POS approvato senza modifiche. CoS ha avuto una discussione di 20 minuti sulla numerazione degli obiettivi — risolta con una rinumeratione veloce. L'architettura presentata dal PM aveva un flusso poco chiaro tra trace_guardian e il bridge, corretto con un diagramma a blocchi sulla lavagna. 6 sprint definiti, dal 9 marzo al 7 giugno. Backlog Sprint 1: setup ambienti e scoping documentale.

### Decisioni

- Struttura repository: `/agents`, `/pipeline`, `/webapp`, `/docs`, `/scenarios`
- Formato scambio Jason-Python: JSON su HTTP (localhost)
- Fallback LLM: Ollama + llama.cpp in caso di indisponibilita API
- Sprint Review ogni 2 settimane il lunedi

### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Pubblicare documenti scoping su repository | PM | 12/03/2026 |
| Implementare Hello World Jason con 2 agenti | Sviluppatore Jason | 15/03/2026 |
| Implementare endpoint Python di test | Sviluppatore Python | 15/03/2026 |
| Setup boilerplate React + Vite | Sviluppatore Frontend | 15/03/2026 |

---

## Meeting 3 — JPPS (Joint Project Planning Session) #1 e #2

### Sessione 1

| Campo | Dettaglio |
|---|---|
| Data | 2026-03-18 |
| Ora | 14:00 - 15:00 |
| Luogo | Aula seminari DIBRIS |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend, Referente Cardiologia di Forlì (Committente) |
| Tipo | Stato avanzamento e validazione architettura |

#### Ordine del Giorno

1. Pianificazione Sprint 1
2. Validazione architettura con docente
3. Rischi emersi e mitigazioni

#### Sintesi

Il team ha pianificato le attività dello Sprint 1, definendo il backlog iniziale con i task di setup ambienti, implementazione agenti BDI e preparazione del golden case gc04. Il docente ha validato l'architettura proposta, suggerendo di aggiungere un agente dedicato alla gestione della tracciabilità (care_planner) separato dal case_reasoner per mantenere la separazione delle responsabilità. È stata discussa l'importanza della tracciabilità simbolica come elemento distintivo del progetto rispetto ad altri sistemi di Clinical Decision Support. Lo sviluppatore Jason ha mostrato un prototipo funzionante con due agenti (case_reasoner e runtime_coordinator) che comunicano via tell/ask su uno scenario mock di gc04. Il docente ha raccomandato di documentare tempestivamente le interfacce tra componenti.

#### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Aggiungere care_planner all'architettura | PM / Sviluppatore Jason | 21/03/2026 |
| Documentare specifica interfacce agente | Sviluppatore Jason | 22/03/2026 |

### Sessione 2

| Campo | Dettaglio |
|---|---|
| Data | 2026-03-19 |
| Ora | 14:00 - 15:30 |
| Luogo | Aula seminari DIBRIS |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Referente Cardiologia di Forlì (Committente) |
| Tipo | Review architetturale e pianificazione Sprint 2 |

#### Ordine del Giorno

1. Review dettaglio tecnico bridge Jason-Python
2. Validazione schema JSON scambio dati
3. Pianificazione Sprint 2

#### Sintesi

La sessione si è concentrata sul dettaglio tecnico del bridge Jason-Python. Il team ha presentato due opzioni: bridge HTTP via chiamate POST da Jason a un server FastAPI, e bridge file-based con polling su directory condivisa. Il docente ha consigliato di iniziare con il bridge HTTP per semplicita, ma di preparare l'architettura per supportare entrambi. Lo schema JSON per lo scambio dati è stato validato, con la raccomandazione di includere un campo "trace_id" univoco per ogni raccomandazione fin dalla prima chiamata. La pianificazione dello Sprint 2 è stata definita con i seguenti obiettivi: completamento agenti BDI di base, bridge Jason-Python funzionante e primo scenario di estrazione regole LLM.

#### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Implementare bridge HTTP Jason-Python | Sviluppatore Python | 28/03/2026 |
| Completare agenti BDI (runtime_coordinator, trace_guardian) | Sviluppatore Jason | 04/04/2026 |
| Preparare scenario clinico #1 (gc04) | PM | 28/03/2026 |

---

## Meeting 4 — Sprint Review #1

| Campo | Dettaglio |
|---|---|
| Data | 2026-04-06 |
| Ora | 14:00 - 15:30 |
| Luogo | Google Meet |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend |
| Tipo | Sprint Review e Retrospettiva |

### Ordine del Giorno

1. Demo Runtime BDI Sprint 1
2. Review bridge Jason-Python
3. Feedback su primi 2 scenari
4. Retrospettiva sprint
5. Pianificazione Sprint 2

### Sintesi

Demo dal vivo di 4 agenti su gc04 e gc00. Flusso ok, ma il trace_guardian è crashato alla prima chiamata al bridge Python — errore di timeout. Riavviato, ha funzionato. Tempo medio 8 sec per scenario, accettabile. Retrospettiva breve: "comunichiamo troppo poco tra sprint, usiamo Discord". Decisione presa. Nessun blocker grave.

### Decisioni

- Runtime BDI considerato stabile per procedere con Sprint 2
- Aggiungere test automatizzati per il bridge HTTP
- Adottare canale Discord per comunicazione asincrona

### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Implementare test unitari per agenti BDI | Sviluppatore Jason | 13/04/2026 |
| Aggiungere gestione fallback LLM locale | Sviluppatore Python | 13/04/2026 |
| Iniziare sviluppo frontend React | Sviluppatore Frontend | 13/04/2026 |
| Preparare scenario clinico #3 (gc_gray_zone) | PM | 13/04/2026 |

---

## Meeting 5 — Sprint Review & Retrospective #2

| Campo | Dettaglio |
|---|---|
| Data | 2026-04-19 |
| Ora | 14:00 - 15:30 |
| Luogo | Google Meet |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend, Referente Cardiologia di Forlì (Committente) |
| Tipo | Sprint Review e Retrospettiva |

### Ordine del Giorno

1. Demo pipeline LLM (claim extraction + rule drafting)
2. Valutazione qualità bozze regole generate
3. Discussione integrazione con la web app di review
4. Retrospettiva Sprint 2

### Sintesi

Il team ha mostrato la pipeline DSPy che estrae claim da testo clinico e genera bozze di regole in formato standard, con Groq come provider primario e OpenRouter come fallback. Su 10 claim testati, 8 corretti e 2 con ambiguità minori. Il rate limit Groq è stato superato durante lo sprint (R1) ma il fallback OpenRouter ha funzionato. Il committente ha valutato positivamente le bozze, chiedendo di migliorare la gestione dei claim ambigui/borderline.

### Decisioni

- Pipeline LLM approvata con riserva sui claim ambigui
- Si procede con Sprint 3 (Web App Review) come pianificato
- La gestione dei claim ambigui viene rinviata allo Sprint 4

### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Documentare i casi di ambiguità nei claim | Sviluppatore Python | 26/04/2026 |
| Avviare sviluppo Rule Review Console | Sviluppatore Frontend | 26/04/2026 |
| Documentare i pattern di chiamata API e rate limiting | Sviluppatore Python | 26/04/2026 |

---

## Meeting 6 — Sprint Review & Retrospective #3

| Campo | Dettaglio |
|---|---|
| Data | 2026-05-03 |
| Ora | 14:00 - 15:30 |
| Luogo | Google Meet |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend, Referente Cardiologia di Forlì (Committente) |
| Tipo | Sprint Review e Retrospettiva |

### Ordine del Giorno

1. Demo web app (Rule Review Console + Trace Inspector)
2. Test flusso end-to-end con regole approvate manualmente
3. Pianificazione Sprint 4
4. Retrospettiva Sprint 3

### Sintesi

La console web è stata mostrata funzionante: lista regole con stato (bozza, in revisione, approvata, rigettata), dettaglio con cronologia, Trace Inspector con visualizzazione delle tracce JSON tramite react-mermaid. Il flusso end-to-end è stato testato: regole approvate nella web app → caricate come beliefs nel runtime BDI → eseguite su gc04 → traccia generata e visualizzata. Il TraceViewer ha richiesto un giorno aggiuntivo (stima sottostimata). Il committente ha apprezzato la chiarezza dell'interfaccia.

### Decisioni

- Web app approvata
- Sprint 4 dedicato a integrazione completa e validazione dei 3 golden case
- Aggiungere test su gc00 e gc_gray_zone

### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Preparare ambiente per validazione sui 3 golden case | Team | 10/05/2026 |
| Preparare demo finale end-to-end | PM | 17/05/2026 |
| Includere margine maggiore per componenti di visualizzazione | PM | — |

---

## Meeting 7 — Sprint Review & Retrospective #4

| Campo | Dettaglio |
|---|---|
| Data | 2026-05-17 |
| Ora | 14:00 - 16:00 |
| Luogo | Aula seminari DIBRIS / Google Meet |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend, Referente Cardiologia di Forlì (Committente) |
| Tipo | Sprint Review, Retrospettiva e accettazione prodotto |

### Ordine del Giorno

1. Demo flusso completo end-to-end
2. Validazione dei 3 golden case (gc00, gc04, gc_gray_zone)
3. Gestione ambiguità claim (post-processore)
4. Retrospettiva Sprint 4 e accettazione del committente

### Sintesi

Dimostrazione del flusso completo: input testo clinico → pipeline LLM → bozze regole → revisione umana sulla console → integrazione nel runtime BDI → esecuzione agenti → visualizzazione tracce. I 3 golden case sono stati validati. Durante lo sprint il rischio R4 (ambiguità claim su gc_gray_zone) si è materializzato: il PM ha attivato la management reserve per aggiungere un post-processore di disambiguazione, assorbendo 2 giorni di ritardo senza impattare la consegna. Dei 10 test di integrazione, 9 passati e 1 con warning minore. Il committente ha formalmente accettato il deliverable.

### Decisioni

- Sprint 4 completato; tutti gli obiettivi O1–O7 raggiunti
- Deliverable di prodotto accettato dal committente (17/05/2026)
- Passaggio alla fase di chiusura e preparazione consegna elaborato

### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Finalizzare documentazione (14 artefatti) | PM | 31/05/2026 |
| Archiviare Project Notebook con tag v1.0.0-final | Sviluppatore Jason | 24/05/2026 |
| Condurre post-implementation audit | PM + Team | 20/05/2026 |

---

## Meeting 8 — Chiusura e Post-Implementation Audit

| Campo | Dettaglio |
|---|---|
| Data | 2026-05-20 |
| Ora | 14:00 - 15:00 |
| Luogo | Google Meet |
| Partecipanti | PM, Sviluppatore Jason, Sviluppatore Python, Sviluppatore Frontend |
| Tipo | Closing e audit di progetto |

### Ordine del Giorno

1. Verifica obiettivi vs risultati
2. Post-implementation audit
3. Lessons learned
4. Archiviazione del Project Notebook

### Sintesi

Il team ha verificato il raggiungimento di tutti gli obiettivi O1–O7 e condotto il post-implementation audit (dettagli in [`Final_report.md`](Final_report.md) e in [`../descrizione/6-closing.md`](../descrizione/6-closing.md)). Sono state consolidate le lessons learned: la stima delle attività LLM è risultata ottimistica (raccomandata correzione +25-30%) e la management reserve del 10% è risultata al limite (raccomandato 15-20% per progetti con componenti AI). Il Project Notebook è stato archiviato con tag `v1.0.0-final`.

### Decisioni

- Lessons learned documentate per progetti futuri
- Repository congelato sul branch `main`, tag `v1.0.0-final`
- Elaborato PM pronto per la consegna finale (07/06/2026)

### Azioni

| Azione | Assegnatario | Scadenza |
|---|---|---|
| Esportare l'elaborato in PDF | PM | 07/06/2026 |
| Verifica finale coerenza documentale | PM | 07/06/2026 |
