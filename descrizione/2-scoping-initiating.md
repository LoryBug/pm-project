---
title: "2. Scoping & Initiating"
nav_order: 2
parent: "Parte 1 — Approccio"
---
# 2. Scoping and Initiating

## Processo di Scoping

Le attività di scoping sono state condotte tramite una serie di **Project Scoping Meeting** strutturati secondo le linee guida del PMBOK per la fase di avvio. L'obiettivo è stato definire il perimetro del progetto, identificare i requisiti preliminari, selezionare il PMLC model e stabilire gli artefatti di governance.

Le tecniche impiegate includono:

- **Facilitated group sessions**: discussioni guidate con tutti gli stakeholder per allineamento su obiettivi e vincoli.
- **Interviews with client**: colloqui one-to-one con il committente (referente della Cardiologia di Forlì) per approfondire la visione e i criteri di accettazione.

## Project Scoping Meeting #1

| Campo | Dettaglio |
|---|---|
| **Data** | 2026-03-04 |
| **Ora** | 14:00 - 16:00 |
| **Luogo** | Aula seminari, Campus; modalita ibrida (presente + Teams) |
| **Partecipanti** | Referente Cardiologia di Forlì (Committente), Studente PM, Team di progetto (3 sviluppatori) |

### Agenda

1. Presentazione dei partecipanti e dei ruoli
2. Esposizione della visione del progetto da parte del committente
3. Discussione delle Conditions of Satisfaction (CoS) preliminari
4. Prima raccolta requisiti ad alto livello
5. Definizione delle aspettative e dei vincoli

### Sintesi dello Svolgimento

Il referente della Cardiologia di Forlì ha aperto la seduta illustrando la visione di un framework multi-agente BDI per supporto decisionale clinico, sottolineando l'importanza della tracciabilità in ambito medico. Il team ha posto domande chiarificatrici sull'integrazione con LLM, specificando che l'ambito cardiaco è un dominio dimostrativo e non l'obiettivo clinico finale. Si è discusso della possibilità di utilizzare Jason come piattaforma BDI esistente e dei servizi LLM disponibili (Groq, OpenRouter). Il PM ha presentato una bozza di CoS che è stata discussa e raffinata collettivamente. Il committente ha ribadito il vincolo di human-in-the-loop e la separazione dalla tesi. La riunione si è conclusa con l'identificazione di 5 aree di requisiti preliminari da approfondire nel secondo incontro.

### Decisioni

- Le Conditions of Satisfaction vengono approvate come bozza, da validare nel meeting successivo
- Il dominio cardiaco è confermato come ambito dimostrativo
- Il vincolo human-in-the-loop è obbligatorio e non negoziabile
- Jason è selezionato come piattaforma BDI di riferimento

### Azioni

- PM: preparare la RBS (Requirements Breakdown Structure) e il Registro Rischi preliminare per il prossimo incontro
- PM: redigere SWOT analysis basata sulla discussione odierna
- Team: installare Jason e configurare l'ambiente di sviluppo locale

## Project Scoping Meeting #2

| Campo | Dettaglio |
|---|---|
| **Data** | 2026-03-11 |
| **Ora** | 14:00 - 16:30 |
| **Luogo** | Aula seminari, Campus |
| **Partecipanti** | Referente Cardiologia di Forlì (Committente), Studente PM, Team di progetto (3 sviluppatori) |

### Agenda

1. Validazione delle Conditions of Satisfaction revisionate
2. Presentazione e discussione RBS
3. Analisi SWOT
4. Selezione del PMLC model
5. Definizione POS (Project Overview Statement) preliminare

### Sintesi dello Svolgimento

Il PM ha presentato il CoS revisionato incorporando i feedback della prima seduta; il committente lo ha approvato con una modifica minore sulla formulazione degli obiettivi. Il Registro Rischi preliminare è stato discusso: sono emersi 6 rischi principali, di cui 3 classificati come critici/prioritari (integrazione Jason-Python, affidabilità LLM, timeline semestrale). La SWOT analysis ha evidenziato come punto di forza principale la competenza pregressa del team su Jason e come minaccia la dipendenza da servizi LLM esterni con possibili limiti di rate. Per la scelta del PMLC model, il PM ha presentato un'analisi comparativa tra i quattro modelli (Linear, Iterative, Adaptive, Extreme), evidenziando il dibattito sulla classificazione di Scrum. Dopo discussione, il team e il committente hanno concordato su Scrum come modello Iterativo con adattamenti per R&D (management reserve, technical spike, MoSCoW rigido), ritenendolo il modello più adatto per la natura del progetto. La riunione si è conclusa con la stesura del POS preliminare che sarà dettagliato nella fase di planning.

### Decisioni

- Conditions of Satisfaction approvate in versione definitiva
- RBS con 6 rischi approvata e archiviata
- Modello PMLC: Iterative (Scrum) con adattamenti R&D selezionato
- POS approvato come base per la fase di planning
- Sprint duration: 2 settimane (concordato)

### Azioni

- PM: preparare PDS (Project Definition Statement) come estensione del POS
- PM: schedulare lo sprint planning per il JPPS (2026-03-18/19)
- Team: iniziare l'analisi della letteratura sui casi clinici del dominio cardiaco

## Deliverable Prodotti

| Artefatto | Descrizione | Stato |
|---|---|---|
| **Conditions of Satisfaction (CoS)** | Condizioni di soddisfacimento condivise | Approvate (2026-03-11) |
| **Requirements Breakdown Structure (RBS)** | Requisiti funzionali e non funzionali gerarchici | Approvata (2026-03-11) |
| **Registro Rischi preliminare** | 6 rischi categorizzati (R1–R6) | Approvato (2026-03-11) |
| **SWOT Analysis** | Punti di forza/debolezza, opportunità/minacce | Completata (2026-03-11) |
| **Project Overview Statement (POS)** | Obiettivi, scopo, stime preliminari | Bozza approvata (2026-03-11) |

## Registro Rischi preliminare

> Nota terminologica: in questo elaborato la sigla **RBS** indica la *Requirements
> Breakdown Structure* (vedi [`documentazione/RBS.md`](../documentazione/RBS.md)).
> L'elenco dei rischi è qui chiamato **Registro Rischi**; la sua versione completa e
> definitiva (R1–R10) è in [`documentazione/Risk_analysis.md`](../documentazione/Risk_analysis.md).

| Codice | Rischio | Categoria | Probabilità | Impatto |
|---|---|---|---|---|
| R1 | Indisponibilità o degrado del servizio LLM (Groq/OpenRouter) | Tecnologico | Media | Alto |
| R2 | Complessità di integrazione Jason-Python (bridge BDI-LLM) | Tecnologico | Alta | Alto |
| R3 | Ritardi nella disponibilità del team per impegni accademici | Risorse | Media | Medio |
| R4 | Ambiguità/inconsistenza dei claim clinici generati dall'LLM | Qualitativo | Media | Medio |
| R5 | Incompatibilità tra versioni delle librerie (Jason/DSPy/Java) | Tecnologico | Bassa | Alto |
| R6 | Timeline semestrale insufficiente | Pianificazione | Media | Alto |

## SWOT Analysis

| Positivo | Negativo |
|---|---|
| **Punti di Forza (S)**: Competenza pregressa su Jason, chiarezza della visione, framework BDI noto per tracciabilità, team affiatato | **Punti di Debolezza (W)**: Nessuna esperienza pregressa su LLM in produzione, budget zero, dipendenza da servizi esterni |
| **Opportunità (O)**: Interesse della comunità accademica per AI trasparente, possibili pubblicazioni, riusabilità del framework in altri domini clinici | **Minacce (T)**: Limiti di rate dei servizi LLM gratuiti, possibile evoluzione normativa AI Act, impegni accademici concorrenti |
