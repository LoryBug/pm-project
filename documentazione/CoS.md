---
title: "CoS — Conditions of Satisfaction"
nav_order: 2
parent: "Parte 2 — Documentazione"
---
# Conditions of Satisfaction — CTAF

## Condizioni di Soddisfacimento

| # | Condizione | Target | Criterio di Verifica |
|---|---|---|---|
| C1 | Il sistema multi-agente BDI funziona end-to-end sul golden case gc04 | Golden case gc04 (CMR-driven high suspicion) eseguito senza errori | Test di accettazione: beliefs gc04 -> runtime BDI -> traccia JSON valida e conforme a expected trace |
| C2 | La pipeline LLM genera bozze regole da fonti cliniche | Generazione bozze per gc00, gc04, gc_gray_zone con output JSON valido | Bozze regole valutabili da revisore umano tramite review console |
| C3 | La web app per revisione umana consente visualizzazione e approvazione/rigetto delle raccomandazioni | Review completata per raccomandazione generata con esito persistente | Test e2e: agente genera raccomandazione → web app mostra → revisore approva → traccia aggiornata |
| C4 | Ogni decisione clinica produce una traccia simbolica (Justification Tree) | 100% delle decisioni loggate con derivazione, fonti e revisione | Script di audit che verifica che per ogni raccomandazione finale esista una traccia non vuota |
| C5 | L'intero sistema è eseguibile da riga di comando | Un singolo script CLI (es. `ctaf run scenario.json`) avvia e completa il flusso | Test CLI su macchina pulita |
| C6 | Il codice sorgente è pubblicato su GitHub come repository open-source | Repository pubblico con README, licenza MIT, struttura chiara, istruzioni di setup | Verifica pubblicazione su organizzazione GitHub del team |
