---
title: "4. Execution"
nav_order: 4
parent: "Parte 1 — Approccio"
---
# 4. Execution

## Framework Scrum adottato

Il progetto è stato eseguito secondo il framework Scrum con sprint della durata di 2 settimane. Ogni sprint ha incluso le cerimonie previste:

- **Sprint Planning**: all'inizio di ogni sprint, con definizione dello Sprint Goal e selezione delle storie dal Product Backlog.
- **Daily Standup**: 15 minuti giornalieri (online su Discord), tre domande: cosa fatto ieri, cosa farò oggi, blocchi.
- **Sprint Review**: alla fine di ogni sprint, con dimostrazione dell'incremento al committente.
- **Sprint Retrospective**: dopo la review, analisi del processo e identificazione di azioni di miglioramento.

Il Product Backlog è stato gestito su GitHub Projects con board kanban (To Do, In Progress, Review, Done).

## Product Backlog (MoSCoW)

| Priorità | Categoria | Elementi |
|---|---|---|
| Must Have | M | Agenti BDI funzionanti, pipeline LLM base, console review, golden case funzionante |
| Should Have | S | Visualizzazione tracce, gestione ambiguità, test automatici |
| Could Have | C | Export report, dashboard metriche, dark mode |
| Won't Have | W | Deployment production, autenticazione utenti, multi-dominio clinico |

## Definition of Done (DoD)

La Definition of Done formale è documentata in [`documentazione/Sprint_plan.md`](../documentazione/Sprint_plan.md#definition-of-done-dod). In sintesi, ogni story è considerata completata quando:

1. Il codice soddisfa i criteri di accettazione della user story
2. La pull request è approvata da almeno un reviewer
3. I test unitari e di integrazione passano
4. La documentazione minima è aggiornata
5. La funzionalità è dimostrabile allo Sprint Review
6. Non ci sono errori runtime o warning bloccanti

## Sprint 1: Runtime BDI (23 Mar -- 5 Apr 2026)

### Sprint Planning (2026-03-23)

**Partecipanti**: PM, Team (3 sviluppatori), Committente

**Sprint Goal**: Implementare 4 agenti BDI in Jason e verificare il funzionamento sul golden case gc04.

**Storie selezionate**:
- Setup ambiente Jason e toolchain
- Implementazione agente `runtime_coordinator` (orchestrazione ed export tracce)
- Implementazione agente `case_reasoner` (esecuzione regole approvate)
- Implementazione agente `trace_guardian` (meta-regole di sicurezza)
- Implementazione agente `care_planner` (pianificazione prossimi step)
- Esecuzione golden case gc04 su runtime BDI
- Test unitari degli agenti

### Daily Standup

Le Daily Standup si sono svolte ogni giorno alle 17:30 su canale Discord dedicato. Durata media: 12 minuti. Principali blocchi segnalati:
- Giorno 3: difficoltà su configurazione Jason su Windows (risolto con Docker)
- Giorno 7: dipendenza ciclica tra piani `case_reasoner`/`trace_guardian` (risolta con redesign interfaccia)

### Sprint Review (2026-04-05)

**Partecipanti**: PM, Team (3 sviluppatori), Committente

**Dimostrazione**: Esecuzione del golden case gc04 con 4 agenti BDI interagenti. Il sistema produce tracce dettagliate delle inferenze.

**Risultati**:
- 4 agenti implementati e funzionanti
- Golden case gc04 completato con output corretto
- Tracce BDI generate e salvate in formato JSON
- Test unitari: 12 test, 12 passati

**Feedback del committente**: "Il runtime BDI soddisfa le attese. La tracciabilità delle inferenze è chiara. Procedere con la pipeline LLM."

### Sprint Retrospective (2026-04-05)

| Categoria | Elemento |
|---|---|
| Andato bene | Buona collaborazione, Docker ha risolto i problemi di setup |
| Da migliorare | Stima ottimistica sul setup (1 giorno -> 2.5 giorni effettivi) |
| Azioni | Riservare tempo extra per setup tecnologici nei prossimi sprint |

**Velocità misurata**: 18 story point su 20 pianificati (90%)

## Sprint 2: Pipeline LLM (6 Apr -- 19 Apr 2026)

### Sprint Planning (2026-04-06)

**Partecipanti**: PM, Team (3 sviluppatori)

**Sprint Goal**: Realizzare pipeline DSPy per estrazione di claim clinici e generazione di bozze regole.

**Storie selezionate**:
- Setup DSPy e configurazione provider Groq/OpenRouter
- Implementazione modulo claim extraction
- Implementazione modulo rule drafting
- Implementazione validatore formato regole (traduzione in AgentSpeak)
- Test su 10 sample claim da letteratura
- Integrazione con output Sprint 1

### Daily Standup

Blocchi segnalati:
- Giorno 4: DSPy richiede Python 3.11+ (aggiornamento ambienti)
- Giorno 6: formato output LLM non consistent (aggiunto post-processore)
- Giorno 9: rate limit Groq superato (attivato fallback OpenRouter)

### Sprint Review (2026-04-19)

**Partecipanti**: PM, Team (3 sviluppatori), Committente

**Dimostrazione**: Inserimento di un testo clinico, estrazione di 3 claim, generazione di bozze regole in formato compatibile Jason.

**Risultati**:
- Pipeline LLM funzionante con Groq (primario) e OpenRouter (fallback)
- 10 claim testati: 8 corretti, 2 con ambiguità minori
- Bozze regole generate e validabili dal revisore umano
- Integrazione con il formato regole di Jason completata

**Feedback del committente**: "Pipeline funzionante. Da migliorare la gestione delle ambiguità nei claim borderline."

### Sprint Retrospective (2026-04-19)

| Categoria | Elemento |
|---|---|
| Andato bene | Fallback provider efficace, test su claims reali positivi |
| Da migliorare | Documentazione API LLM, gestione rate limiting |
| Azioni | Aggiungere test su claims ambigui, documentare i pattern di chiamata API |

**Velocità misurata**: 18 story point su 22 pianificati (82%)

## Sprint 3: Web App Review (20 Apr -- 3 May 2026)

### Sprint Planning (2026-04-20)

**Partecipanti**: PM, Team (3 sviluppatori)

**Sprint Goal**: Sviluppare console web per la revisione delle regole e l'ispezione delle tracce BDI.

**Storie selezionate**:
- Setup React/Vite + TypeScript
- Componente RuleList (visualizzazione bozze regole)
- Componente RuleReview (approvazione/rigetto con commenti)
- Componente TraceViewer (ispezione tracce BDI)
- Integrazione con API backend (lettura regole e tracce)
- Test UI/UX (5 scenari utente)

### Daily Standup

Blocchi segnalati:
- Giorno 2: scelta libreria grafica per diagrammi tracce (Decisa: Mermaid tramite libreria react-mermaid)
- Giorno 8: ritardo su componente TraceViewer per complessità parsing JSON (risolto con libreria dedicated)

### Sprint Review (2026-05-03)

**Partecipanti**: PM, Team (3 sviluppatori), Committente

**Dimostrazione**: Console web funzionante: lista regole con stato (bozza, in revisione, approvata, rigettata), dettaglio regola con cronologia, visualizzazione tracce BDI con diagramma temporale.

**Risultati**:
- Console React/Vite completa e funzionante
- Rule Review: approvazione, rigetto con commento, modifica bozza
- Trace Viewer: diagramma temporale delle inferenze
- 5 scenari testati: 5 superati

**Feedback del committente**: "Interfaccia chiara e funzionale. La visualizzazione delle tracce è molto utile per la validazione."

### Sprint Retrospective (2026-05-03)

| Categoria | Elemento |
|---|---|
| Andato bene | Componenti riutilizzabili, interfaccia pulita, test utente positivi |
| Da migliorare | Stima del TraceViewer sottostimata (3 -> 5 giorni) |
| Azioni | Includere margine maggiore per componenti di visualizzazione dati complessi |

**Velocità misurata**: 16 story point su 18 pianificati (89%)

## Sprint 4: Integrazione e Testing (4 May -- 17 May 2026)

### Sprint Planning (2026-05-04)

**Partecipanti**: PM, Team (3 sviluppatori), Committente

**Sprint Goal**: Completare il flusso end-to-end, validare il golden case, finalizzare la documentazione.

**Storie selezionate**:
- Integrazione end-to-end (BDI + LLM + Web App)
- Validazione golden case gc04 completo
- Gestione ambiguità claim (miglioramento post-processore)
- Test di integrazione (10 scenari)
- Documentazione del framework
- Preparazione deliverable finali
- Archiviazione Project Notebook

### Daily Standup

Blocchi segnalati:
- Giorno 2: discrepanza nel formato dati tra pipeline LLM e console web (risolta con interfaccia di trasformazione)
- Giorno 5: ambiguità su claim clinici non gestita correttamente (assorbita da management reserve)
- Giorno 8: ritardo su documentazione per sovrapposizione con esami accademici

### Gestione del Ritardo -- Giorno 5

Durante la validazione del golden case, è emerso che due claim clinici generavano regole ambigue non direttamente utilizzabili. Il problema era stato identificato come R4 nell'analisi dei rischi. Il PM ha attivato la management reserve (10% del budget temporale) per aggiungere un post-processore di disambiguazione. Il ritardo di 2 giorni è stato assorbito senza impattare la data di consegna.

### Sprint Review (2026-05-17)

**Partecipanti**: PM, Team (3 sviluppatori), Committente

**Dimostrazione**: Dimostrazione del flusso completo: input testo clinico -> pipeline LLM -> bozze regole -> revisione umana sulla console -> integrazione automatica nel motore BDI -> esecuzione agenti -> visualizzazione tracce.

**Risultati**:
- Flusso end-to-end funzionante
- Golden case gc04 validato con tutti i componenti
- Gestione ambiguità implementata con post-processore
- 10 test di integrazione: 9 passati, 1 con warning minore
- Documentazione completa del framework
- Project Notebook archiviato su GitHub

**Feedback del committente**: "Il progetto raggiunge tutti gli obiettivi. Framework funzionante e ben documentato. Consegna accettata."

### Sprint Retrospective (2026-05-17)

| Categoria | Elemento |
|---|---|
| Andato bene | Management reserve ha funzionato come previsto, integrazione riuscita |
| Da migliorare | Documentazione da iniziare prima, test di integrazione da automatizzare |
| Azioni | Lezioni apprese documentate per progetti futuri |

**Velocità misurata**: 15 story point su 18 pianificati (83%)

## Velocità Complessiva

| Sprint | Story Point Pianificati | Story Point Completati | Percentuale |
|---|---|---|---|
| Sprint 1 | 20 | 18 | 90% |
| Sprint 2 | 22 | 18 | 82% |
| Sprint 3 | 18 | 16 | 89% |
| Sprint 4 | 18 | 15 | 83% |
| **Totale** | **78** | **67** | **86%** |
