---
title: "SWOT Analysis"
nav_order: 3
parent: "Parte 2 — Documentazione"
---
# SWOT Analysis — Cardiac Traceability Agent Framework

## Punti di Forza (Strengths)

| # | Forza | Descrizione |
|---|---|---|
| S1 | Architettura innovativa | Integrazione di agenti BDI con LLM per explaining agency è un approccio poco esplorato in letteratura |
| S2 | Traceability by design | Ogni decisione è tracciata simbolicamente fin dalla progettazione, non come ripensamento |
| S3 | Dominio circoscritto | L'ambito cardiologico (linee guida ESC) fornisce un contesto clinicamente significativo ma gestibile |
| S4 | Riuso di concetti preesistenti | Il progetto si basa su concetti già esplorati in tesi precedenti e letteratura consolidata sui BDI |
| S5 | Open-source | La pubblicazione su GitHub favorisce revisione tra pari e potenziali contributi esterni |

## Punti di Debolezza (Weaknesses)

| # | Debolezza | Descrizione |
|---|---|---|
| W1 | Team studentesco | Competenze in formazione; assenza di esperti di dominio clinico o di Jason/AgentSpeak senior |
| W2 | Dipendenza da API LLM | L'intero pipeline LLM dipende da API di terze parti con garanzie di servizio limitate (free tier) |
| W3 | Runtime di nicchia | Jason/AgentSpeak ha una comunità ristretta, documentazione limitata e tooling datato |
| W4 | Bassa maturità prototipale | Il risultato sarà un prototipo accademico, non un sistema pronto per produzione clinica |
| W5 | Documentazione sparuta | Le fonti su integrazione Jason-Python (es. JADE-Jason bridge) sono frammentate e obsolete |

## Opportunità (Opportunities)

| # | Opportunità | Descrizione |
|---|---|---|
| O1 | Pubblicazione accademica | L'architettura è potenzialmente pubblicabile in conferenze su agenti (AAMAS, EMAS, PAAMS) |
| O2 | Progetti futuri | Il framework può essere esteso ad altri domini clinici o a contesti di AI responsabile |
| O3 | Interesse industriale | La tracciabilità delle decisioni AI è un tema caldo in ambito regolatorio (AI Act europeo) |
| O4 | Riferimento per Trustworthy AI | CTAF può servire come case study per linee guida su AI spiegabile e affidabile |

## Minacce (Threats)

| # | Minaccia | Descrizione |
|---|---|---|
| T1 | Variazioni API LLM | Modifiche improvvise alle API (deprecation, rate limit, costi) possono bloccare il pipeline |
| T2 | Complessità di integrazione | L'integrazione tra Jason (Java), Python (LLM) e React (web app) presenta rischi tecnici |
| T3 | Scope creep | La tentazione di aggiungere funzionalità cliniche o analitiche può allontanare dalla deadline |
| T4 | Timeline semestrale | 14 settimane nette per un progetto multi-componente con tecnologie eterogenee |
