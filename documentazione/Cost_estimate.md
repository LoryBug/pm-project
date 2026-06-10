---
title: "Cost Estimate"
nav_order: 10
parent: "Parte 2 — Documentazione"
---
# Cost Estimate — CTAF

## Stima dei Costi

| Voce | Costo | Note |
|---|---|---|
| Risorse umane (studenti) | € 0 | Progetto accademico senza compenso |
| API LLM (Groq / OpenRouter free tier) | € 0 | Tier gratuito con rate limit; fallback locale Ollama/llama.cpp |
| Hosting web app | € 0 | Esecuzione locale (localhost); nessun deploy cloud |
| Strumenti di sviluppo | € 0 | IDE gratuiti, GitHub Free, Docker gratuiti |
| Container runtime (Docker) | € 0 | Docker Desktop free per uso accademico |
| Repository GitHub | € 0 | GitHub Free con repository pubblici illimitati |
| **Totale** | **€ 0** | — |

## Stima dello Sforzo (Effort Estimation)

> Le stime di durata per attività (tecnica dei tre punti / PERT) sono mantenute nel foglio
> di calcolo con formule live: [`allegati/Stime_PERT.xlsx`](allegati/Stime_PERT.xlsx)
> (effort totale ≈ 39,17 giorni-uomo). La tabella ore/ruolo seguente è la vista aggregata.

| Ruolo | Quantità | Ore Stimate | Note |
|---|---|---|---|
| Sviluppatore Jason/AgentSpeak | 1 | 80 h | Ciclo BDI, agenti, piani, comunicazione |
| Sviluppatore Python (LLM Pipeline) | 1 | 40 h | Bridge Jason-Python, estrazione regole, validazione |
| Sviluppatore Frontend (React) | 1 | 40 h | Web app, dashboard, flusso revisione |
| Project Manager | 1 | 30 h | Sprint planning, riunioni, documentazione, risk tracking |
| Reviewer / Tester | 1 | 10 h | Test e2e, validazione scenari, feedback |
| **Totale** | **5** | **200 h** | — |

## Distribuzione Ore per Fase

| Fase | Ore | Percentuale |
|---|---|---|
| Scoping e Progettazione | 30 h | 15 % |
| Implementazione (Runtime BDI + LLM + Web App) | 120 h | 60 % |
| Integrazione e Test | 30 h | 15 % |
| Documentazione e Chiusura | 20 h | 10 % |
| **Totale** | **200 h** | **100 %** |

> Effort per ruolo e distribuzione per fase con formule live (percentuali e costo
> figurativo parametrico): [`allegati/Budget_Effort.xlsx`](allegati/Budget_Effort.xlsx).
