---
title: "Final Report"
nav_order: 14
parent: "Parte 2 — Documentazione"
---
# Final Report — CTAF

## Risultati Raggiunti

- Realizzazione di un framework multi-agente BDI in Jason/AgentSpeak con 4 agenti (runtime_coordinator, case_reasoner, trace_guardian, care_planner) funzionanti su 3 scenari clinici cardiologici.
- Integrazione di un pipeline LLM per estrazione e validazione di regole cliniche da linee guida ESC, con bridge HTTP Jason-Python e fallback su modello locale open-source.
- Sviluppo di una web app React con backend FastAPI per la revisione umana delle raccomandazioni, comprendente dashboard, dettaglio con traccia e flusso approvazione/rifiuto.
- Implementazione del sottosistema di tracciabilità Justification Tree, con esportazione in formato Markdown e HTML navigabile per ogni decisione clinica.
- Pubblicazione del repository open-source su GitHub con licenza MIT, documentazione completa (14 artefatti di progetto), README e istruzioni di setup.

## Obiettivi vs Risultati

| Obiettivo | Descrizione | Priorità | Raggiunto | Note |
|---|---|---|---|---|
| O1 | Runtime BDI: 4 agenti Jason | Must | Sì | coordinator, reasoner, guardian, planner funzionanti su 3 scenari |
| O2 | Pipeline LLM (claim extraction + rule drafting) | Should | Sì | DSPy + Groq/OpenRouter, fallback locale; valutazione su 3 casi |
| O3 | Console web per revisione umana | Should | Sì | Frontend React + backend FastAPI, flusso di revisione completo |
| O4 | Tracciabilità (Justification Tree) | Must | Sì | Traccia per ogni decisione, export Markdown e HTML |
| O5 | Golden case (gc00, gc04, gc_gray_zone) | Must | Sì | 3/3 scenari validati end-to-end |
| O6 | Esecuzione CLI | Must | Sì | `ctaf run scenario.json` completa il flusso |
| O7 | Open source su GitHub | Could | Sì | Repository pubblico, licenza MIT, README |

## Lezioni Apprese

### Cosa ha Funzionato

1. **Architettura modulare a agenti**: La separazione in 4 agenti BDI con responsabilità distinte ha facilitato lo sviluppo parallelo e il test indipendente di ogni componente, riducendo i conflitti di integrazione.
2. **Bridge HTTP Jason-Python**: Nonostante le preoccupazioni iniziali, il bridge via chiamate HTTP su localhost si e rivelato semplice da implementare e sufficientemente performante per un prototipo accademico (latenza media < 200 ms).
3. **Prioritizzazione MoSCoW**: La definizione rigorosa delle priorità ha permesso al team di concentrarsi sugli obiettivi Must-have, evitando dispersione su funzionalità accessorie e completando il nucleo del sistema entro la deadline.

### Cosa Migliorare

1. **Pianificazione regole ambigue**: Il terzo scenario clinico (gc_gray_zone) ha richiesto più tempo del previsto a causa della complessità delle linee guida. Una fase di analisi più approfondita delle fonti cliniche prima dello sviluppo avrebbe ridotto l'imprevisto.
2. **Comunicazione asincrona**: Nei primi sprint il team ha sottoutilizzato gli strumenti di comunicazione asincrona, causando ritardi nella risoluzione di dubbi tecnici. L'adozione di Discord dal Sprint 3 ha migliorato significativamente il flusso informativo.
3. **Test automatizzati**: I test sono stati eseguiti prevalentemente in modo manuale. L'implementazione di una suite di test automatizzati (es. pytest per il pipeline, JUnit per Jason) avrebbe aumentato la confidenza nelle regressioni.

### Raccomandazioni

1. Per futuri progetti accademici su Jason/AgentSpeak, si consiglia di dedicare una settimana iniziale interamente alla familiarizzazione con il runtime e le sue peculiarità.
2. Il formato Justification Tree sviluppato per CTAF può essere riutilizzato come base per un progetto di ricerca su explainable AI agents in ambito medico.
3. Si raccomanda di estendere il test su almeno 10 scenari clinici per validare la robustezza del sistema prima di qualsiasi uso in contesti non accademici.
4. Il fallback LLM locale (Ollama/llama.cpp) si e dimostrato un'alternativa valida; si consiglia di mantenerlo come opzione predefinita per garantire riproducibilità dei risultati.

## Post-Implementation Audit Summary

| Area | Valutazione | Note |
|---|---|---|
| Completezza funzionale | 100% | Tutti i requisiti Must-have implementati |
| Stabilità del sistema | Buona | 3/3 scenari e2e completati senza crash |
| Qualità del codice | Discreta | Codice funzionante ma con margini di refactoring |
| Documentazione | Completa | 14 artefatti + README + documentazione tecnica |
| Copertura tracciabilità | 100% | Ogni decisione produce traccia simbolica verificabile |
| Rispetto timeline | Raggiunta | Consegna entro deadline con utilizzo di 1 settimana di riserva |
| Pubblicazione open-source | Completata | Repository pubblico su GitHub, licenza MIT |

Il progetto CTAF ha dimostrato la fattibilità di un sistema multi-agente BDI per il supporto decisionale clinico tracciabile, integrando LLM e revisione umana in un flusso auditabile. I risultati costituiscono una base solida per futuri sviluppi in ambito di trustworthy AI e explainable agency.
