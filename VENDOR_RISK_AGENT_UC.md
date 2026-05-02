# Vendor Risk & Escalation Agent — Use Case Scenarios
**Multi-Agent Architecture · Concept360 · 2026**
*Built by Biljana Obradović — Senior Delivery Governance, RWA & Banking Programmes*

> This document presents two real-programme use cases demonstrating how the three-agent system (Discovery → Vendor Risk & Escalation → Action) handles critical vendor incidents in regulated fintech environments.
>

## How the Agent System Works — Quick Reference

```
Any input signal (monitoring alert / manual PM / webhook / scheduled scan)
        │
        ▼
[ DISCOVERY AGENT ]  — validates, identifies vendor & programme, routes
        │
        ▼
[ VENDOR RISK & ESCALATION AGENT ]  — classifies severity, maps regulation,
                                       builds escalation chain & actions
        │
        ▼
[ ACTION AGENT ]  — selects stakeholders, sends email/Slack, logs & tracks
```

**Severity levels:**
- **P1 — Critical:** production impact, regulatory exposure, or go-live blocker. Full escalation chain activated immediately.
- **P2 — High:** significant risk within 24–48h window. Targeted escalation, monitoring increased.

---

## Use Case 1 — RWA Tokenisation Programme
### Fireblocks API failure — 90 minutes before institutional token disbursement

**Programme context:**
Real-world asset tokenisation in production. Fireblocks is the custody and settlement layer (Layer 6). Three institutional investors are scheduled to receive token disbursements in 90 minutes.

**Incident input** *(received via webhook from Azure Monitor):*
> "Fireblocks API returning errors. Custody wallet inaccessible. Token disbursement to 3 institutional investors scheduled in 90 minutes. Layer 6. Production environment."

---

**Discovery Agent output:**
| Field | Value |
|-------|-------|
| Vendor | Fireblocks |
| Programme layer | Layer 6 — Custody & Settlement |
| Programme | RWA Tokenisation |
| Regulatory scope | MiCA Art. 70 (custody obligations) |
| Routing | → Vendor Risk & Escalation Agent |

---

**Vendor Risk & Escalation Agent output:**
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

**Why no manual workaround?**
MiCA Art. 70 requires that custody assets remain under the licensed custodian at all times. Any manual transfer outside Fireblocks during an API failure would constitute an unauthorised movement of client assets. The agent enforces this as a hard stop — it cannot be overridden by the PM. Only the Programme Director and Legal PM can authorise an exception, which itself requires documented regulatory justification.

---

**Action Agent output:**
| Action | Detail |
|--------|--------|
| Email sent to | Programme Director, Integration Architect, Compliance Lead |
| Slack alert | #rwa-incidents channel |
| Timestamp logged | 2026-05-02 09:14 UTC |
| Acknowledgement tracking | Active — 15-minute follow-up if no response |

**Total time from alert to notifications sent: 12 seconds.**
Manual equivalent: 20–35 minutes, with risk of incorrect escalation order or missed regulatory flag.

---

## Use Case 2 — Multi-Country Bank Core Banking Implementation
### T24 OFS API timeout — hypercare period, Wave 3 go-live in 48 hours

**Programme context:**
Multi-country core banking rollout. Wave 2 country went live recently and is in hypercare (active post-go-live support window). Wave 3 go-live is scheduled in 48 hours. T24 is the core banking platform (Layer 2).

**Incident input** *(received via manual PM input confirmed by Datadog alert):*
> "T24 OFS API returning intermittent timeout errors for the past 55 minutes. Affects payment processing and account inquiry modules. Wave 2 country currently in hypercare — 48 hours from Wave 3 go-live. Bank environment, production."

---

**Discovery Agent output:**
| Field | Value |
|-------|-------|
| Vendor | Temenos T24 |
| Programme layer | Layer 2 — Core Banking Platform |
| Programme | Multi-Country Bank Core Banking Implementation |
| Regulatory scope | DORA Art. 11 (ICT continuity), local central bank reporting |
| Context flags | Active hypercare · Adjacent wave go-live imminent |
| Routing | → Vendor Risk & Escalation Agent |

---

**Vendor Risk & Escalation Agent output:**
```
SEVERITY: P1 — Critical (hypercare multiplier applied)

RATIONALE:
55-minute timeout in production hypercare = active service degradation.
Wave 3 go-live cannot proceed while Wave 2 has an unresolved P1.
Wave sequencing rule: no new go-live commitment while P1 is open
in any live country.

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

**Why is Wave 3 frozen automatically?**
The agent applies the wave sequencing rule: a live country in P1 during hypercare is a direct signal that the platform is unstable. Allowing Wave 3 to proceed would multiply the blast radius — a second country going live on a platform with an unresolved critical failure. The freeze is automatic and is not a PM judgment call. It is lifted only when P1 is closed and root cause is documented.

**Why are Country PM notifications parallel, not sequential?**
In single-country incidents, escalation is sequential (IA → PD → COO). In multi-country incidents, each Country PM is notified simultaneously — they each have their own regulatory obligations and operational windows and cannot wait for the previous escalation step to complete.

---

**Action Agent output:**
| Action | Detail |
|--------|--------|
| Email sent to | Programme Director, Integration Architect, Wave 2 Country PM, Group CTO (cc) |
| Slack alerts | #bank-incidents · #wave2-hypercare channels |
| Wave 3 channel | Freeze flag raised automatically |
| Timestamp logged | 2026-05-02 11:32 UTC |
| Acknowledgement tracking | Active — 15-minute follow-up if no response |

**Total time from alert to notifications sent: 9 seconds.**
Manual equivalent: 25–40 minutes, with risk of Wave 3 go-live decision being made without full incident context.

---

## What the Agent Does Not Decide

In both scenarios above, the agent classifies, routes, and notifies. It does not make the following decisions — these remain with humans:

| Decision | Owner |
|----------|-------|
| Go-live approval or freeze confirmation | Programme Director + Steering Committee |
| AML exception / SAR filing | MLRO |
| Architectural choice (T24 upgrade vs config) | Group CTO + Programme Director |
| Investor communication content | Programme Director + Legal PM |
| NCA / central bank notification | Programme Director (DORA ICT Risk Manager) |
| Manual custody workaround approval | Not approvable — hard stop |
| Budget impact decisions | CFO |

---

## Knowledge Sources

These scenarios are not hypothetical. The agent's decision logic was derived from:

- DORA ICT Risk Framework (Arts. 11, 17)
- MiCA Arts. 70–76 (custody, continuity, investor obligations)
- AML / FATF monitoring continuity guidelines
- Temenos T24 OFS API operational runbook
- Fireblocks enterprise integration specifications
- Programme-specific wave sequencing and hypercare rules
- Vendor matrix: 10 critical vendors mapped across 6 programme layers

---

*© Biljana Obradović · Concept360 · 2026*
*Agent system is proprietary. This document is published for professional reference.*
*To request a demo: [your LinkedIn / contact]*
