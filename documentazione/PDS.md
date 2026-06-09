---
title: "PDS — Project Definition Statement"
nav_order: 5
parent: "Parte 2 — Documentazione"
---
# Project Definition Statement — CTAF

## 1. Problema / Opportunità

### 1.1 Contesto clinico

Il percorso diagnostico per masse cardiache richiede imaging multimodale (ecocardiografia, TC, CMR, PET) e linee guida ESC. Ogni decisione deve essere tracciabile per audit medico-legale. I CDS basati su LLM attuali producono raccomandazioni opache (black box) senza giustificazione simbolica, rendendo impossibile l'audit ex-post.

### 1.2 Limiti dei sistemi CDS attuali

1. **Assenza di tracciabilità simbolica**: le raccomandazioni LLM non includono una catena di derivazione esplicita (belief -> regola -> conclusione -> revisione).
2. **Impossibilità di audit ex-post**: non esiste un formato strutturato per riesaminare il ragionamento che ha portato a una raccomandazione.
3. **Mancanza di controllo umano strutturato**: il revisore non dispone di strumenti per validare, modificare o rigettare singoli passaggi del ragionamento prima della pubblicazione.

### 1.3 Soluzione proposta

CTAF (Cardiac Traceability Agent Framework) affronta questi limiti orchestrando quattro agenti BDI in Jason/AgentSpeak (runtime_coordinator, case_reasoner, trace_guardian, care_planner) che cooperano per produrre raccomandazioni clinicamente fondate, simbolicamente tracciate e validate da un revisore umano tramite web app dedicata. Il dominio cardiaco (masse cardiache) offre un contesto clinicamente ricco ma circoscritto, ideale per la validazione del prototipo tramite tre golden case: gc00 (exclusion rule, basso rischio), gc04 (CMR-driven high suspicion, alto rischio) e gc_gray_zone (CT gray-zone PET-mancante, complessità decisionale).

---

## 2. Obiettivo del Progetto

Progettare, sviluppare e validare un framework multi-agente in Jason/AgentSpeak per il supporto decisionale clinico tracciabile in ambito cardiaco (masse cardiache), composto da:
- un runtime BDI con 4 agenti cooperanti
- una pipeline LLM per estrazione regole e generazione bozze (DSPy)
- una web app per revisione umana (React/Vite)
- un sottosistema di tracciabilità strutturata (Justification Tree in JSON)

Il tutto rilasciato come repository open-source su GitHub entro la sessione estiva 2026.

---

## 3. Obiettivi Specifici

| ID | Obiettivo | Priorità MoSCoW | Descrizione Tecnica | Criterio di Successo |
|---|---|---|---|---|
| O1 | Runtime BDI | Must-have | MAS Jason con 4 agenti (coordinator, reasoner, guardian, planner); ciclo percept-deliberate-meansEnd-execute su golden case | Tutti e 4 gli agenti rispondono e cooperano su gc04 |
| O2 | LLM Pipeline | Should-have | Pipeline DSPy per claim extraction da linee guida ESC e rule drafting in formato regole standard | Almeno 3 fonti cliniche processate con output JSON valido |
| O3 | Web App Review | Should-have | React/Vite per rule review console (approva/scarta bozze) e trace inspector (visualizzazione giustificazione) | UI funzionante su 3 scenari di test |
| O4 | Traceability | Must-have | Justification Tree JSON per ogni decisione con: premesse, regola applicata, esito, timestamp, revisore | 100% decisioni con traccia valida e non vuota |
| O5 | Golden Cases | Must-have | Validazione end-to-end su gc00 (no-exam), gc04 (CMR-driven), gc_gray_zone (CT gray-zone) | 3/3 golden case superati |
| O6 | CLI Execution | Must-have | Script unico `ctaf run scenario.json` che avvia MAS + pipeline + export traccia | Esecuzione completa su macchina pulita |
| O7 | Open Source | Could-have | Repository GitHub con README, licenza MIT, struttura `/agents`, `/pipeline`, `/webapp`, `/docs`, `/scenarios` | Repository pubblicato e accessibile |

---

## 4. Stakeholder

| Stakeholder | Ruolo | Interesse | Coinvolgimento |
|---|---|---|---|
| Team di sviluppo (3 persone) | Realizzazione tecnica | Alto | Tutti gli sprint |
| Project Manager | Coordinamento, reporting | Alto | Continuo |
| Cardiologia di Forlì | Committente (cliente clinico) | Medio | Milestone review + consegna finale |
| Cardiologo referente (Cardiologia di Forlì) | Validazione raccomandazioni | Alto | Sprint 3-4 |
| Utente finale (medico, simulato) | Destinatario della raccomandazione | Basso | Feedback indiretto tramite revisore |

---

## 5. Criteri di Successo

| Criterio | Metrica | Target | Modalità di Verifica |
|---|---|---|---|
| Completezza funzionale | # requisiti implementati / # requisiti totali | >= 90% | Review checklist a fine Sprint 4 |
| Stabilità runtime | Scenario e2e eseguito 3/3 senza crash | 100% | Test automatizzato su gc04 |
| Copertura tracciabilità | # decisioni con traccia / # decisioni totali | 100% | Script audit su log |
| Completezza documentale | Checklist 14 artefatti PM completati | 100% | Revisione PM |
| Rispetto timeline | Consegna entro deadline | 07/06/2026 | Data delivery |
| Copertura test | Test unitari + integrazione passati | >= 90% | Report pytest/CI |

---

## 6. Vincoli e Assunzioni

Vincoli:
- Tecnologici: Jason/AgentSpeak per BDI, Python 3.11+ per LLM, React/Vite per frontend
- Temporali: consegna entro 07/06/2026
- Risorse: 3 persone + PM, budget zero, solo free tier API LLM
- Dati: sintetici, golden case predefiniti, nessun dato clinico reale

Assunzioni:
- API LLM (Groq/OpenRouter) disponibili in free tier per tutta la durata
- Jason v3.2+ stabile su Java 17+
- Golden case coprono varietà clinica sufficiente
- Revisore umano simulato rappresentativo del workflow reale

---

## 7. Budget e Risorse

| Voce | Costo | Note |
|---|---|---|
| Sviluppo software | 0 EUR | Team studenti, nessun costo orario |
| API LLM (Groq, OpenRouter) | 0 EUR | Free tier accademico |
| Hosting web app | 0 EUR | Localhost + Vercel free tier |
| Docker per runtime Jason | 0 EUR | Docker Desktop free |
| Repository GitHub | 0 EUR | Free per repository pubblici |
| **Totale** | **0 EUR** | Progetto interamente basato su strumenti gratuiti |

---

## 8. Matrice dei Rischi

| # | Rischio | P | I | PxI | Strategia | Azione |
|---|---|---|---|---|---|---|
| R1 | Indisponibilità o degrado del servizio LLM (Groq/OpenRouter) | M | A | 6 | Mitigazione | Provider multiplo + fallback locale (Ollama/llama.cpp) |
| R2 | Complessità integrazione Jason-Python (bridge BDI-LLM) | A | A | 9 | Mitigazione | Prototipo bridge HTTP, fallback file-based |
| R3 | Ritardi del team per impegni accademici | M | M | 4 | Accettazione | Buffer nel piano + scope bank 10% |
| R4 | Ambiguità/inconsistenza dei claim clinici generati dall'LLM | M | M | 4 | Mitigazione | Validazione strutturale + post-processore disambiguazione |
| R5 | Incompatibilità tra versioni delle librerie (Jason/DSPy/Java) | B | A | 3 | Contingenza | Docker con versioni fissate |
| R6 | Timeline semestrale insufficiente | M | A | 6 | Mitigazione | Priorità Must-have, sprint di riserva |

**Legenda**: P = Probabilità (B=1/Bassa, M=2/Media, A=3/Alta), I = Impatto (B=1, M=2, A=3), PxI = Prodotto rischio (max 9). Il registro completo R1–R10 è in [`Risk_analysis.md`](Risk_analysis.md).

### Risk Response Plan

| Rischio | Trigger | Owner | Azione Preventiva | Azione Correttiva |
|---|---|---|---|---|
| R1 | Rate limit 429/503 persistente sul provider primario | Team LLM | Provider multiplo configurato | Fallback OpenRouter → locale Ollama/llama.cpp |
| R2 | Errore comunicazione Jason-Python | Team BDI | Schema JSON convalidato + prototipo HTTP | Bridge file-based su directory condivisa |
| R3 | Assenza ricorrente di un membro alle daily | PM | Buffer e scope bank pianificati | Ridistribuzione task critici |
| R4 | 2+ output LLM consecutivi ambigui/malformati | Team LLM | Validazione JSON-schema a monte | Post-processore disambiguazione + review umana prioritaria |
| R5 | Conflitto di versioni in fase di build | Team BDI | Docker con versioni fissate | Container rebuild + rollback versione |
| R6 | Task non completato a fine Sprint 4 | PM | MoSCoW rigido, sprint di riserva | Ridurre ambito task Could-have (O7) |
