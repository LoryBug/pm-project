---
title: "6. Closing"
nav_order: 6
parent: "Parte 1 — Approccio"
---
# 6. Closing

## Verifica degli Obiettivi

Tutti gli obiettivi definiti nel POS e nel PDS sono stati raggiunti entro la data di consegna del 17 maggio 2026.

| Obiettivo | Criterio di Successo | Risultato | Stato |
|---|---|---|---|
| O1 -- Runtime BDI | 4 agenti Jason operativi su golden case gc04 | 4 agenti (coordinator, reasoner, guardian, planner) implementati e funzionanti | Raggiunto |
| O2 -- Pipeline LLM | Modulo DSPy funzionante con Groq/OpenRouter | Pipeline operativa con provider multiplo; claim extraction e rule drafting funzionanti | Raggiunto |
| O3 -- Console Web | App React/Vite + backend FastAPI per review | Console completa: rule review, approvazione/rigetto, TraceViewer con diagrammi | Raggiunto |
| O4 -- Tracciabilità | Structured trace per ogni decisione | Justification Tree per ogni decisione, export Markdown/HTML | Raggiunto |
| O5 -- Golden case | Validazione su gc00, gc04, gc_gray_zone | 3/3 golden case validati end-to-end (9/10 test integrazione passati) | Raggiunto |
| O6 -- Esecuzione CLI | Comando unico di avvio del flusso | `ctaf run scenario.json` completa il flusso | Raggiunto |
| O7 -- Open source | Repository GitHub con README e licenza | Repository pubblicato, licenza MIT, README e documentazione | Raggiunto |

## Accettazione Formale

In data **17 maggio 2026**, al termine della Sprint Review dello Sprint 4, il committente (Cardiologia di Forlì) ha formalmente accettato il deliverable del progetto.

**Dichiarazione di accettazione** (verbale):

> "Il progetto Cardiac Traceability Agent Framework raggiunge tutti gli obiettivi definiti in fase di pianificazione. Il framework è funzionante, ben documentato, e dimostra l'efficacia dell'integrazione tra motore BDI simbolico e LLM assistito con revisione umana. La consegna è accettata."

La dichiarazione è stata verbalizzata e archiviata nel repository di progetto.

## Consegna Finale

I seguenti artefatti sono stati consegnati al committente:

| Artefatto | Formato | Note |
|---|---|---|
| Report finale di progetto | PDF | Documento completo di tutte le sezioni |
| Repository codice sorgente | GitHub (privato) | Include README, documentazione API, esempi |
| Project Notebook | GitHub (cartella docs/) | Verbali riunioni, decisioni, change log |
| Golden case gc04 | Script eseguibile | Caso dimostrativo completo |
| Console web | Build statica | Deploy su GitHub Pages per dimostrazione |
| Backlog storico | GitHub Projects | Dashboard completa con storia sprint |
| Status report (4 sprint) | PDF | Report settimanali e sprint review |

## Lessons Learned

### Processo e Metodologia

1. **Scrum si adatta bene a progetti R&D con incognite tecniche.**
   Gli sprint brevi (2 settimane) hanno permesso di rilevare precocemente i problemi di integrazione e di adattare il backlog di conseguenza. Le cerimonie Scrum (in particolare la Sprint Review e la Retrospective) hanno fornito momenti strutturati di ispezione e adattamento.

2. **La separazione dei componenti ha ridotto le dipendenze critiche.**
   La decisione di sviluppare il motore BDI, la pipeline LLM e la console web come moduli separati (Sprint 1, 2, 3) ha permesso di lavorare in parallelo sui tre fronti, riducendo i conflitti di integrazione. Solo lo Sprint 4 ha richiesto un effort congiunto.

3. **MoSCoW ha prevenuto lo scope creep.**
   La prioritizzazione Must Have / Should Have / Could Have / Won't Have ha permesso di concentrare le risorse sulle funzionalità essenziali. Durante lo Sprint 4, la tentazione di aggiungere funzionalità accessorie è stata contenuta dalla disciplina MoSCoW.

### Stime e Pianificazione

4. **La stima dell'integrazione LLM è stata più difficile del previsto.**
   Nonostante l'uso della tecnica dei tre punti (PERT), le stime per il modulo pipeline LLM (Sprint 2) sono risultate ottimistiche. La variabilità introdotta dalla dipendenza da servizi esterni (rate limit, qualità output, latenza) e difficile da catturare con tecniche di stima tradizionali. Per progetti simili, si consiglia di:
   - Aggiungere un fattore di correzione del 25-30% per componenti basati su LLM
   - Prevedere sempre un provider di fallback
   - Includere tempo per post-processing e validazione degli output

5. **La management reserve dovrebbe essere del 15-20% per progetti con componenti AI.**
   Il buffer del 10% (scope bank) è stato sufficiente ma al limite: l'attivazione del rischio R4 ha consumato il 25% della riserva disponibile. Per progetti con componenti basati su LLM o AI generativa, si raccomanda una riserva di gestione del 15-20% per assorbire la variabilità tecnica.

### Documentazione e Comunicazione

6. **Documentare le decisioni in tempo reale su GitHub riduce il carico finale.**
   La pratica di registrare verbali, decisioni e change log direttamente su GitHub (Project Notebook) ha notevolmente ridotto il lavoro di documentazione finale. Ogni decisione era tracciata con data, motivazione e impatto, facilitando la stesura del report conclusivo.

### Tabella Riepilogo Lessons Learned

| Area | Lezione Appresa | Raccomandazione |
|---|---|---|
| Metodologia | Scrum adatto a R&D con incognite | Mantenere sprint brevi (1-2 settimane) |
| Architettura | Separazione moduli riduce rischi | Progettare interfacce chiare tra moduli |
| Scope | MoSCoW previene scope creep | Applicare rigorosamente all'inizio di ogni sprint |
| Stima | LLM difficile da stimare | Aggiungere fattore correttivo 25-30% |
| Riserve | Buffer 10% al limite per AI | Riserva 15-20% per progetti AI |
| Documentazione | Documentazione in tempo reale | Usare GitHub come journal di progetto |

## Post-Implementation Audit

L'audit post-implementazione è stato condotto in data **20 maggio 2026** dal Project Manager con la partecipazione del team.

### Risultati dell'Audit

| Dimensione | Valutazione | Note |
|---|---|---|
| Soddisfazione del committente | 5/5 | Tutti gli obiettivi raggiunti, accettazione formale |
| Qualità del prodotto | 4/5 | Framework funzionante, un warning minore in un test di integrazione |
| Rispetto delle tempistiche | 4/5 | Consegna entro la data, 3 story point non critici rinviati |
| Gestione del budget | 5/5 | Costo zero confermato |
| Copertura dei test | 4/5 | Test unitari e di integrazione coprono l'80% del codice |
| Documentazione | 5/5 | Completa, ben strutturata, archiviata |
| Gestione dei rischi | 4/5 | R4 attivato ma mitigato, riserve adeguate |

### Raccomandazioni per il Futuro

1. **Evoluzione del framework**: estendere il dominio clinico a patologie cardiache reali con validazione su dati clinici anonimizzati.
2. **Automazione dei test**: integrare test automatici in CI/CD per ridurre il testing manuale.
3. **Validazione clinica formale**: sottoporre il framework a un processo di validazione con personale medico specializzato.
4. **Pubblicazione accademica**: valutare la stesura di un articolo scientifico sull'architettura di integrazione BDI-LLM.

## Project Notebook Archiving

Il Project Notebook (repository GitHub) contiene tutta la documentazione del progetto ed è stato archiviato in data **20 maggio 2026** con tag `v1.0.0-final`.

### Contenuto del Project Notebook

Il notebook è organizzato in tre aree sotto `docs/`:

| Cartella | Contenuto |
|---|---|
| `docs/verbali/` | Verbali di scoping (2) e JPPS (2); per ciascuno dei 4 sprint, i verbali di planning, review e retrospettiva; verbale di audit finale (20/05/2026) |
| `docs/decisioni/` | Registri vivi del progetto: `change-log.md`, `issue-log.md`, `risk-log.md` |
| `docs/deliverable/` | Versioni approvate degli artefatti (POS, CoS, PDS, RBS, SWOT, WBS) e `report-finale.pdf` |

Il file `docs/README.md` funge da indice e guida di navigazione del notebook.

### Stato dell'Archivio

- Repository: `github.com/uni-prj/ctaf` (privato)
- Tag finale: `v1.0.0-final`
- Branch: `main` (congelato alla consegna)
- Licenza: MIT (open-source, come da vincolo di progetto)

## Conclusioni

Il progetto **Cardiac Traceability Agent Framework** si conclude con successo in data 17 maggio 2026. Tutti gli obiettivi O1-O5 sono stati raggiunti, il committente ha formalmente accettato il deliverable, e le lezioni apprese sono state documentate per progetti futuri.

Il framework dimostra che l'integrazione tra un motore BDI simbolico (Jason) e un LLM assistito con revisione umana è una strada percorribile per il supporto decisionale clinico tracciabile, affrontando le criticità di black-box e non riproducibilità tipiche dei sistemi puramente neurali.

La documentazione completa e il codice sorgente sono archiviati e disponibili per eventuali sviluppi futuri, che rimangono però al di fuori del perimetro del presente progetto.
