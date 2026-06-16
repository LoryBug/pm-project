---
title: "7. Strumenti di Supporto"
nav_order: 7
parent: "Parte 1 — Approccio"
---
# 7. Strumenti di Supporto

## Filosofia di selezione degli strumenti

La scelta degli strumenti di project management è stata guidata dalla natura del progetto
piuttosto che dall'abitudine: un progetto **adattivo (Scrum) con componente R&D**,
**code-centric**, a **budget zero** e con team distribuito. Da questi vincoli discende una
toolchain **leggera, integrata col codice, versionata e riproducibile** ("docs-as-code"),
coerente con il fatto che il prodotto stesso ha come obiettivo la *tracciabilità e
l'auditabilità*. Tutti gli strumenti adottati sono open-source o free-tier, in linea con il
vincolo di budget zero.

## Mappa Artefatto → Strumento → Motivazione

| Artefatto / Attività | Strumento | Motivazione della scelta |
|---|---|---|
| Product/Sprint backlog, board kanban, issue tracking | **GitHub Projects** | Board kanban integrata con issue, codice e pull request: *single source of truth* e tracciabilità delle decisioni |
| Gantt, Network diagram, WBS, RBS, architettura | **Mermaid** (diagram-as-code) | Diagrammi versionabili e diff-abili, mantenuti accanto al testo ed esportati in SVG |
| Esportazione diagrammi per la consegna | **mermaid-cli** | Rendering statico in SVG/PNG per PDF e GitHub Pages, indipendente dal renderer |
| Stime di durata ed effort | **Foglio di calcolo** ([`Stime_PERT.xlsx`](../documentazione/allegati/Stime_PERT.xlsx)) | Tecnica dei tre punti (O/M/P) con formule PERT e σ live |
| Monitoraggio performance | **Foglio di calcolo** ([`EVM_SPI_CPI.xlsx`](../documentazione/allegati/EVM_SPI_CPI.xlsx)) | EVM con SPI/CPI/SV/CV calcolati da formule |
| Budget ed effort | **Foglio di calcolo** ([`Budget_Effort.xlsx`](../documentazione/allegati/Budget_Effort.xlsx)) | Ore per ruolo/fase, percentuali e costo figurativo parametrico |
| Documentazione di progetto (14 artefatti) | **Markdown + Git** | Docs-as-code: portabile, versionata, diff-abile, esportabile in PDF |
| Knowledge management e note di progetto | **Obsidian** | Collegamento tra note (Project Notebook), navigazione a grafo |
| Versionamento e collaborazione | **Git / GitHub** | Storia completa, code review via PR, branch per feature |
| Comunicazione di team | **Discord** (async) + meeting sincroni | Daily standup e coordinamento asincrono tra sprint |

## Strumenti "classici" considerati e non adottati

L'analisi delle alternative mainstream è parte della giustificazione della scelta: gli
strumenti seguenti sono stati valutati e scartati con motivazione, non ignorati.

| Strumento | Valutazione | Motivo della non-adozione |
|---|---|---|
| **MS Project / Primavera** | Potente per pianificazione plan-driven | Orientato a Waterfall con baseline rigide e WBS contrattuale; eccessivo e poco adatto a un ciclo Scrum a backlog mutevole; licenza a pagamento (contro il vincolo budget zero) |
| **Jira** | Alternativa Agile valida | Ridondante: GitHub Projects copre board + issue ed è già integrato col repository di sviluppo; eviterebbe un ambiente in più da gestire |
| **Trello** | Semplice per kanban | Non integrato con codice e versionamento; nessuna tracciabilità verso commit/PR |
| **GanttProject / ProjectLibre** | Gantt desktop gratuiti | Strumenti isolati, non versionabili come testo; il Gantt Mermaid resta nel repo e segue le revisioni |

**Sintesi**: la toolchain scelta non è una rinuncia agli strumenti di PM, ma una loro
selezione coerente con un progetto Agile, code-centric e a budget zero. La preferenza è
andata a strumenti che vivono **dentro** il repository (board, diagrammi e documenti
versionati), in modo che la gestione di progetto erediti la stessa tracciabilità che il
prodotto si propone di garantire.

## Metodologie e tecniche utilizzate (strumenti concettuali)

Oltre al software, l'elaborato applica un insieme di tecniche di project management che
costituiscono a tutti gli effetti "strumenti" nel senso del corso:

| Tecnica | Dove è usata |
|---|---|
| **POS / CoS / PDS** | Scoping e definizione del progetto |
| **RBS (Requirements Breakdown Structure)** | Decomposizione dei requisiti |
| **WBS** | Decomposizione del lavoro |
| **JPPS** (Joint Project Planning Session) | Pianificazione partecipata |
| **MoSCoW** | Prioritizzazione del backlog |
| **Three-point / PERT** | Stima di durata ed effort |
| **Network diagram + Critical Path** | Analisi delle dipendenze |
| **EVM (SPI / CPI)** | Monitoraggio delle performance |
| **Burndown chart** | Avanzamento degli sprint |
| **Stoplight / status report** | Reporting semaforico |
| **RACI** | Matrice delle responsabilità |
| **Scope bank / management reserve** | Gestione degli imprevisti |
| **Risk register + risk response plan** | Gestione del rischio |

## Evidenze (screenshot)

Le linee guida ammettono screenshot per documentare gli strumenti utilizzati. Si prevede di
allegare le seguenti evidenze (da inserire in `img/` prima della consegna):

> 📷 *[Screenshot: board GitHub Projects con colonne To Do / In Progress / Review / Done]*

> 📷 *[Screenshot: storico issue e pull request del repository]*

Il foglio delle stime three-point/PERT è già allegato come file editabile con formule:
[`documentazione/allegati/Stime_PERT.xlsx`](../documentazione/allegati/Stime_PERT.xlsx)
(uno screenshot del foglio può essere aggiunto qui per la versione PDF).

Per inserirle, sostituire ciascun segnaposto con un riferimento immagine, ad esempio:
`![Board GitHub Projects](../img/screenshot-github-projects.png)`.
