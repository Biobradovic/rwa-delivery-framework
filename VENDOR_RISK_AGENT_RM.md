# Vendor Risk & Escalation Agent System
**Multi-Agent Architecture for Regulated Fintech Programmes**
*Built by Biljana Obradović · Concept360 · 2026*

---

## What This Is

This repository documents the architecture and decision logic behind an agentic AI system built to handle vendor risk escalation in regulated banking and tokenisation programmes.

The system was developed for two live programmes:
- **RWA Tokenisation Programme** — real-world asset tokenisation under MiCA and DORA
- **Bank123 Group Banking Implementation** — multi-country T24 core banking rollout across Western Balkans

The agent is not a chatbot. It is a structured decision-support and notification system that classifies vendor incidents, maps regulatory obligations, and routes escalations to the right stakeholders — automatically.

---

## The Problem It Solves

When a critical vendor fails in a live banking or tokenisation programme, Programme Managers typically spend 15–30 minutes answering the same questions manually:

- How severe is this?
- Which regulation applies?
- Who needs to be notified, and in what order?
- What are the immediate actions?
- What is the post-incident requirement?

In regulated environments under DORA, MiCA, and AML frameworks, slow or incorrect escalation is not just an operational issue — it is a compliance risk.

This agent answers all of those questions in under 10 seconds and triggers the notification chain automatically.

---

## Agent Architecture

The system is composed of three specialised agents orchestrated in sequence.

```
Input Signals
  ├── Monitoring alert (Datadog / PagerDuty)
  ├── Manual PM input
  ├── Webhook / API (T24, MuleSoft, Azure)
  └── Scheduled vendor health scan
          │
          ▼
┌─────────────────────────────┐
│      DISCOVERY AGENT        │  ← Entry point
│                             │
│  · Validates incident type  │
│  · Identifies vendor        │
│  · Maps programme layer     │
│  · Routes to correct agent  │
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────────────────────────────────┐
│            VENDOR RISK & ESCALATION AGENT               │  ← Core logic
│                                                         │
│  · Classifies severity: P1 (critical) / P2 (high)      │
│  · Maps regulatory obligation (DORA / MiCA / AML)      │
│  · Builds escalation chain with time thresholds        │
│  · Defines immediate actions and post-incident steps   │
│                                                         │
│  Knowledge base: AGENT_GUIDELINES.md                   │
│                  SCENARIO_TESTS.md                      │
│                  Vendor matrix (10 vendors, 6 layers)   │
└────────────┬────────────────────────────────────────────┘
             │
             ▼
┌─────────────────────────────┐
│       ACTION AGENT          │  ← Notification & logging
│                             │
│  · Selects stakeholders     │
│  · Sends structured email   │
│    or Slack notification    │
│  · Logs action + timestamp  │
│  · Tracks acknowledgement   │
└────────────┬────────────────┘
             │
    ┌────────┴──────────────────────────────────┐
    │         STAKEHOLDER ROUTING               │
    │                                           │
    │  Programme Director  → Always on P1       │
    │  Integration Architect → Technical events │
    │  Compliance Lead     → Regulatory flag    │
    │  Country PM          → Per wave / region  │
    │  COO / Steering      → P1 multi-country   │
    └───────────────────────────────────────────┘
```

---

## What the Agent Was Built On

The agent's knowledge and decision logic was derived from the following mapped documents:

| Document | Purpose |
|----------|---------|
| `AGENT_GUIDELINES.md` | System prompt: rules, format, escalation logic, hard stops |
| `SCENARIO_TESTS.md` | 10 test cases covering RWA and NLB incident types |
| Vendor matrix | 10 critical vendors mapped across 6 programme layers |
| DORA ICT Risk Framework | Third-party incident classification and NCA notification thresholds |
| MiCA Articles 70–76 | Crypto-asset service provider obligations, custody hard stops |
| AML / FATF Guidelines | Monitoring continuity requirements, SAR trigger conditions |
| NLB Wave Sequencing Rules | Country-specific escalation paths, go-live blocking criteria |
| T24 OFS API runbook | Integration-layer failure classification and workaround limits |

The agent does not invent answers. Every classification, escalation path, and regulatory reference traces back to one of these source documents.

---

## Use Case Scenario

### Scenario: Fireblocks API failure — 90 minutes before institutional token disbursement

**Incident input (via webhook from Azure Monitor):**
> "Fireblocks API returning errors. Custody wallet inaccessible. Token disbursement to 3 institutional investors scheduled in 90 minutes. Layer 6. Production environment."

**Discovery Agent output:**
- Vendor: Fireblocks (Layer 6 — Custody & Settlement)
- Programme: RWA Tokenisation
- Regulatory scope: MiCA Art. 70 (custody obligations)
- Routing: → Vendor Risk & Escalation Agent

**Vendor Risk Agent output:**
```
SEVERITY: P1 — Critical

IMMEDIATE ACTIONS (next 30 minutes):
1. Engage Fireblocks enterprise support — open Priority 1 ticket
2. Notify Programme Director immediately
3. Notify institutional investors of potential delay
4. Do NOT attempt manual custody workaround — hard stop per RWA-03

ESCALATION CHAIN:
Integration Architect → Programme Director (now)
Programme Director → COO (if unresolved in 30 min)
COO → Steering Committee (if unresolved in 60 min)

REGULATORY OBLIGATION:
MiCA Art. 70 — custody assets must remain accessible at all times.
Incident must be documented. If unresolved, NCA notification may be required.

POST-INCIDENT:
Root cause analysis required within 48h.
Incident log must be retained per DORA Art. 17.
```

**Action Agent output:**
- Email sent to: Programme Director, Integration Architect, Compliance Lead
- Slack alert posted to: #rwa-incidents channel
- Timestamp logged: 2026-05-02 09:14 UTC
- Acknowledgement tracking: active (15-minute follow-up if no response)

**Total time from alert to notifications sent: 12 seconds.**
Manual equivalent: 20–35 minutes.

---

### Scenario: T24 OFS API timeout — hypercare period, Wave 2 go-live in 48 hours

**Incident input (via manual PM input + Datadog alert):**
> "T24 OFS API returning intermittent timeout errors for the past 55 minutes. Affects payment processing and account inquiry modules. Wave 2 country is currently in hypercare — 48 hours from Wave 3 go-live. Bank environment, production."

**Discovery Agent output:**
- Vendor: Temenos T24 (Layer 2 — Core Banking Platform)
- Programme: Multi-Country Bank Core Banking Implementation
- Regulatory scope: DORA Art. 11 (ICT continuity), local central bank reporting obligations
- Context flag: Active hypercare period + adjacent wave go-live imminent
- Routing: → Vendor Risk & Escalation Agent

**Vendor Risk Agent output:**
```
SEVERITY: P1 — Critical (hypercare multiplier applied)

RATIONALE:
55-minute timeout in production hypercare = active service degradation.
Wave 3 go-live cannot proceed while Wave 2 has an unresolved P1.
Wave sequencing rule: no new go-live commitment while P1 is open in any live country.

IMMEDIATE ACTIONS (next 30 minutes):
1. Engage Temenos Level 3 support — reference OFS API timeout, production hypercare
2. Confirm whether issue is config, network, or T24 version-specific
3. Notify Programme Director and Wave 2 Country PM immediately
4. Freeze Wave 3 go-live decision until Wave 2 P1 is resolved
5. Activate Bank ICT incident response procedure

ESCALATION CHAIN:
Integration Architect → Programme Director (now)
Wave 2 Country PM → notified in parallel (not sequential)
Programme Director → Group CTO (if root cause unclear in 45 min)
Programme Director → COO (if unresolved in 60 min)
COO → Steering Committee (if Wave 3 go-live impact confirmed)

REGULATORY OBLIGATION:
DORA Art. 11 — ICT continuity must be maintained during hypercare.
If outage exceeds 2 hours: assess local central bank notification requirement.
Incident must be logged with full timeline for post-incident review.

WAVE SEQUENCING:
Wave 3 go-live date is NOT confirmed until Wave 2 P1 is fully resolved
and root cause is documented. No exceptions.

POST-INCIDENT:
Root cause analysis within 48h.
If T24 version is the cause: Group CTO + Programme Director assess
upgrade vs config path — agent does not recommend, escalates for decision.
```

**Action Agent output:**
- Email sent to: Programme Director, Integration Architect, Wave 2 Country PM, Group CTO (copied)
- Slack alert posted to: #bank-incidents and #wave2-hypercare channels
- Wave 3 go-live channel notified: freeze flag raised automatically
- Timestamp logged: 2026-05-02 11:32 UTC
- Acknowledgement tracking: active (15-minute follow-up if no response)

**Total time from alert to notifications sent: 9 seconds.**
Manual equivalent: 25–40 minutes, with risk of Wave 3 decision being made without full context.

---

## What This Is Not

This system does not make decisions that belong to humans:

| Decision | Owner |
|----------|-------|
| Go-live approval | Programme Director + Steering Committee |
| AML exception / SAR filing | MLRO |
| Architectural choice | Group CTO + Programme Director |
| Investor communication content | Programme Director + Legal PM |
| NCA regulatory notification | Programme Director (DORA ICT Risk Manager) |
| Budget impact decisions | CFO |
| Manual custody workaround | Not approvable — hard stop |

The agent presents options and escalates. It does not commit, approve, or override.

---

## Current Status & Roadmap

| Phase | Status | Description |
|-------|--------|-------------|
| Phase 1 — Core agent | ✅ Live | Vendor Risk & Escalation Agent with 10 scenarios |
| Phase 2 — Discovery agent | 🔧 In design | Input validation and routing layer |
| Phase 3 — Action agent | 🔧 In design | Automated email/Slack notification |
| Phase 4 — Monitoring integration | 📋 Planned | Webhook from Datadog / Azure Monitor |
| Phase 5 — Multi-programme orchestration | 📋 Planned | RWA + NLB unified orchestration layer |

---

## Live Demo

**Agent demo available to qualified enquiries.**
Contact via LinkedIn or email to request access.
biljana.obradovic@concept360.rs/biljana-obradovic-28390a8

---

## Access & Licensing

The agent system is proprietary. This repository documents the architecture and decision logic for transparency and professional reference.


---

*© Biljana Obradović · Concept360 · 2026*
