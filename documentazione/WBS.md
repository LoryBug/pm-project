---
title: "WBS — Work Breakdown Structure"
nav_order: 6
parent: "Parte 2 — Documentazione"
---
# Work Breakdown Structure — CTAF

![WBS — Work Breakdown Structure](../img/wbs.svg)

*Diagramma: [`img/wbs.mmd`](../img/wbs.mmd) → `img/wbs.svg`*

## Dettaglio dei work package

- **1.1 Requisiti e Scoping**
    - 1.1.1 Analisi requisiti funzionali
    - 1.1.2 Definizione casi d'uso clinici (3 scenari)
    - 1.1.3 Definizione MoSCoW e priorità
    - 1.1.4 Condizioni di soddisfacimento
- **1.2 Progettazione**
    - 1.2.1 Architettura sistema multi-agente
        - 1.2.1.1 Diagramma componenti e flussi
        - 1.2.1.2 Specifica interfacce inter-agente
    - 1.2.2 Progettazione LLM pipeline
        - 1.2.2.1 Schema input/output JSON
        - 1.2.2.2 Prompt engineering template
    - 1.2.3 Progettazione web app
        - 1.2.3.1 Wireframe UI
        - 1.2.3.2 Schema database SQLite
    - 1.2.4 Progettazione tracciabilità
        - 1.2.4.1 Formato Justification Tree
- **1.3 Runtime BDI (Jason)**
    - 1.3.1 Definizione agenti e credenze
        - 1.3.1.1 runtime_coordinator
        - 1.3.1.2 case_reasoner
        - 1.3.1.3 trace_guardian
        - 1.3.1.4 care_planner
    - 1.3.2 Implementazione piani e goal
    - 1.3.3 Comunicazione inter-agente (tell/ask)
    - 1.3.4 Test unitario runtime su scenari
- **1.4 LLM Pipeline**
    - 1.4.1 Bridge Jason-Python (chiamata HTTP)
    - 1.4.2 Modulo estrazione regole
        - 1.4.2.1 Parser linee guida ESC
        - 1.4.2.2 Generatore regole strutturate
    - 1.4.3 Modulo valutazione caso clinico
    - 1.4.4 Test pipeline con mock e LLM reale
- **1.5 Web App**
    - 1.5.1 Backend API REST (Python/FastAPI)
        - 1.5.1.1 Endpoint raccomandazioni
        - 1.5.1.2 CRUD revisioni
        - 1.5.1.3 Logging eventi
    - 1.5.2 Frontend React
        - 1.5.2.1 Dashboard raccomandazioni
        - 1.5.2.2 Pagina dettaglio con traccia
        - 1.5.2.3 Flusso approvazione/rifiuto
        - 1.5.2.4 Storico revisioni
    - 1.5.3 Integrazione backend-frontend
- **1.6 Integrazione e Test**
    - 1.6.1 Integrazione Runtime + LLM Pipeline
    - 1.6.2 Integrazione Runtime + Web App
    - 1.6.3 Test end-to-end su gc04
    - 1.6.4 CLI script e packaging Docker
    - 1.6.5 Test di accettazione (3 scenari)
- **1.7 Documentazione**
    - 1.7.1 Documenti di progetto (14 artefatti)
    - 1.7.2 README e setup guide
    - 1.7.3 Documentazione tecnica API
    - 1.7.4 Pubblicazione su GitHub
- **1.8 Gestione Progetto**
    - 1.8.1 Pianificazione sprint
    - 1.8.2 Riunioni (scoping, sprint review, JPPS)
    - 1.8.3 Monitoraggio rischi
    - 1.8.4 Status report settimanali
