---
title: "POS — Project Overview Statement"
nav_order: 1
parent: "Parte 2 — Documentazione"
---
# Project Overview Statement — Cardiac Traceability Agent Framework

## Problema / Opportunità

I sistemi di supporto alle decisioni cliniche basati su LLM (Large Language Models) soffrono di mancanza di trasparenza e tracciabilità. Ogni raccomandazione generata da un modello black-box può essere clinicamente rischiosa senza un meccanismo che ne registri la derivazione logica, le fonti e il passaggio di revisione umana. Il framework Cardiac Traceability Agent Framework (CTAF) si propone come soluzione multi-agente BDI (Jason/AgentSpeak) che orchestra un pipeline LLM, produce una traccia simbolica di ogni decisione e sottopone il risultato a revisione umana tramite web app, garantendo auditabilità completa.

## Obiettivo del Progetto

Progettare e realizzare un framework multi-agente in Jason/AgentSpeak per il supporto decisionale clinico tracciabile in ambito cardiologico, integrando un pipeline LLM per l'elaborazione del linguaggio naturale e una web app per la revisione umana, con consegna di codice open-source su GitHub e documentazione completa entro Giugno 2026.

## Obiettivi Specifici

| ID | Obiettivo | Priorità MoSCoW | Criterio di Successo |
|---|---|---|---|
| O1 | Runtime BDI: 4 agenti Jason (coordinator, reasoner, guardian, planner) | Must | Agenti operativi e cooperanti sul golden case gc04 |
| O2 | Pipeline LLM per estrazione claim e bozza regole | Should | Pipeline produce output JSON valido per almeno 3 casi d'uso |
| O3 | Console web per la revisione umana delle raccomandazioni | Should | Review simulata completata con esito registrato |
| O4 | Tracciabilità: structured trace per ogni decisione | Must | Ogni decisione produce traccia simbolica leggibile (Markdown/HTML) |
| O5 | Golden case: validazione su gc00, gc04, gc_gray_zone | Must | 3/3 golden case superati end-to-end |
| O6 | Esecuzione CLI del flusso completo | Must | Comando `ctaf run scenario.json` completa il flusso |
| O7 | Open source: repository GitHub con README e licenza | Could | Repository pubblicato con README e licenza MIT |

## Criteri di Successo (IRACIS)

IRACIS = *Increased Revenue* (IR), *Avoided Cost* (AC), *Improved Service* (IS). In un progetto accademico a budget zero i criteri sono interpretati in chiave di valore generato, costi evitati e qualità del servizio.

| Categoria IRACIS | Criterio | Target | Misura |
|---|---|---|---|
| IR — Increased Revenue | Valore generato come base per progetti/tesi futuri | Framework riusabile e dimostrabile | Demo accettata + repository riutilizzabile |
| AC — Avoided Cost | Riuso dell'architettura per altri domini clinici | Componenti modulari riutilizzabili senza riscrittura | Architettura modulare documentata |
| IS — Improved Service | Trasparenza e tracciabilità delle decisioni | 100% delle decisioni tracciate e 0 raccomandazioni senza revisione umana | Log di sistema per ogni ciclo BDI + audit tracce |

## Assunzioni, Rischi e Ostacoli

| Categoria | Elemento |
|---|---|
| Assunzione | I membri del team hanno competenze di base in Jason/AgentSpeak |
| Assunzione | LLM API gratuita rimarrà disponibile per tutto il semestre |
| Rischio | Complessità di integrazione tra Jason runtime e pipeline Python |
| Rischio | Variazioni nelle API LLM durante lo sviluppo |
| Ostacolo | Timeline semestrale vincolata alla sessione estiva |
| Ostacolo | Documentazione Jason/AgentSpeak frammentata e di nicchia |
