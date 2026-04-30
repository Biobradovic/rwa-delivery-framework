# RWA Framework — What Exists

**Concept360 · Biljana Obradović · 2026**

> This file describes the full framework scope. Detailed materials are available upon qualified engagement.
> For the 7 layers, see README.md. For team structure, see delivery-team.md. For layer-by-layer depth, see Seven_Layers_Quick_Reference.md.

---

## The 25 Delivery Plans — by Layer

Every RWA programme requires 25 distinct delivery plans. The critical insight is not what each plan contains — it is **when it must be initiated**.

| Layer | Plans |
|-------|-------|
| **L0** | Programme Delivery Plan · Token Strategy · Risk Management Plan · Investor Acquisition Strategy · Communication Strategy · Security Strategy & Wallet Policy · Key Person Succession Plan |
| **L1** | Regulatory Strategy · **Banking Strategy** · Exchange & Liquidity Strategy · Regulatory Engagement Plan · Stakeholder Engagement Plan · Vendor Management Plan |
| **L1–2** | Crisis Communication Plan |
| **L2** | **Exit & Wind-Down Strategy** · Data Management Plan |
| **L3** | Business Continuity Plan · Disaster Recovery Plan · Incident Response Plan · Change Management Plan · Training Plan |
| **L5** | Token Issuance Plan |
| **L6** | Banking Operations Plan |
| **L7** | Continuous Audit Plan · Secondary Market Development Plan · **Hypercare Plan (Days 1–30)** · Post-Launch Plan (Days 31–90) |

**Three plans consistently started too late:**
- **Banking Strategy** (L1) — banking screening takes 8–20 weeks. Clock starts from Week 1, not after the platform is built.
- **Exit & Wind-Down Strategy** (L2) — must be disclosed in the Offering Memorandum before any investor subscribes.
- **Key Person Succession Plan** (L0) — NCA approval for MLRO replacement: 4–8 weeks. Must exist before departure.

**The Programme Director owns the gate — not every document. Each plan has a named owner and approver. Full ownership matrix in the private repository.**
---

## Risk Management — 11 Categories

Standard risk registers miss the categories that actually cause delays. An RWA programme requires all 11.

| # | Category | Note |
|---|----------|------|
| 1 | Documentation & Compliance | |
| 2 | Legal & Regulatory | |
| 3 | Governance | |
| 4 | Delivery | |
| 5 | Protocol & Smart Contract | |
| 6 | Technology & Infrastructure | |
| 7 | Solvency & Liquidity | |
| 8 | Security | |
| 9 | Vendor & Oracle | |
| 10 | KYC/AML | |
| 11 | **Soft Risks** | ← not in standard registers |

**Soft risks that consistently cause delays without appearing in RAG reports:**
Stakeholder pseudo-consensus · Slow cross-functional decisions · Unclear ownership at function boundaries · Regulatory fear culture · Blockchain/banking knowledge gap between teams.

Full risk register: 60+ risks, each with trigger condition, mitigation, owner, layer, and KPI.

---

## Wallet Architecture — Five Types

Wallet governance is defined in Layer 2 (policy) 
and Layer 3 (specification). Each wallet type has 
a different custody model, signing authority, and 
compliance obligation.

Five types: Investor wallets · SPV operational wallet 
· Treasury/reserve wallet · Smart contract admin wallet 
· Market maker wallet

Key Ceremony — mandatory before go-live. All key holders convened. CISO owns. Annual repeat.
---

## Reporting Architecture — 12 Streams

RWA programmes run multiple parallel reporting obligations. Each stream has a named owner and a hard deadline where applicable.

| Stream | Owner | Deadline |
|--------|-------|----------|
| NCA — DORA major incident | Compliance PM | 4h initial · 24h detailed |
| NCA — periodic supervisory | Compliance PM | Per NCA calendar (quarterly) |
| SAR / STR to FIU | MLRO | Promptly — national rules |
| FATCA / CRS | Compliance PM + Legal PM | Annual |
| Investors — NAV update | Operations PM + CFO | Quarterly minimum |
| Investors — material incident | Community PM | Within 24h |
| Board — programme status | Programme Director | Monthly |
| Board — risk review | CRO | Quarterly |
| Exchange — trade reports | Exchange Reporting Officer | Per CEX rulebook |
| Exchange — suspicious activity | Exchange Reporting Officer + MLRO | Per exchange rulebook |
| Banking — reconciliation | Banking PM | Monthly |
| Market maker — SLA | Banking PM | Monthly |

---

## Vendor Ecosystem — 20 Categories

| Category | Key vendors | Layer | Lead time |
|----------|------------|-------|-----------|
| Oracle | Chainlink, API3, Pyth, RedStone | L2–L3 | 2–4 weeks |
| SC Audit | Halborn, Certik, Trail of Bits, ConsenSys | L3 | 4–8 weeks — **book in L1** |
| Security / Pentest | NCC Group, Bishop Fox | L3 | 2–4 weeks |
| Blockchain Monitoring | Chainalysis, Elliptic, TRM Labs | L4 | 2–3 weeks |
| On-chain Monitoring | Forta, OpenZeppelin Defender, Tenderly | L3–L4 | 1–2 weeks |
| KYC / AML | Jumio, Onfido, Sumsub, ComplyCube | L4–L5 | 3–6 weeks |
| Sanctions Screening | ComplyAdvantage, Refinitiv | L4 | 2–4 weeks |
| Travel Rule | Notabene, Sygna Bridge | L4 | 4–6 weeks |
| Custody | Fireblocks (MPC), Copper, BitGo | L4–L6 | 4–8 weeks |
| Crypto-native Banking | Sygnum, AMINA, InCore, SEBA, Bank Frick | L6 | 4–8 weeks |
| Traditional Banking *(backup)* | Erste, Unicredit, OTP | L6 | 10–20 weeks |
| Exchange | SDX, Archax, INX, Boerse Stuttgart Digital, MERJ | L6 | 8–16 weeks |
| Market Maker | GSR, Wintermute, B2C2, Keyrock | L6 | 4–8 weeks |
| Valuation *(Real Estate)* | RICS-certified appraiser | L1–L7 | Quarterly |
| Valuation *(ESG/Carbon)* | Verra, Gold Standard, Xpansiv | L1–L7 | Quarterly |
| Legal Counsel | RWA-specialist per jurisdiction | L1 | 2–4 weeks |
| Regulatory Advisor | CASP/MiCA specialist | L0–L2 | Engage L0 |
| RegTech / Reporting | ComplyAdvantage, Rulefinder | L4–L7 | 3–5 weeks |
| Cloud Infrastructure | AWS, Azure, GCP — multi-region | L3 | 1–2 weeks |
| Token Platform *(Model 1/2)* | Tokeny, Securitize, DigiShares, Blocksquare | L0 decision | — |

**Three vendor rules:**
1. Book SC audit firms in Layer 1 — slots fill fast
2. Screen minimum 3 banks simultaneously from Week 1 — never a single banking relationship
3. Every vendor has a named PM owner — vendors without a named owner fail silently

Full vendor RACI, SLA register, and selection criteria per operating model available in the private repository.

---

## What the Full Framework Contains

The private repository includes:

- **Consulting deck** — complete delivery architecture across all 7 layers with KPIs, RACI, strategies
- **Integration register** — 15 integrations with vendor, API type, lead time, SLA, escalation procedure
- **Banking onboarding scenarios** — crypto-native vs neo vs traditional bank requirements
- **Risk register** — 60+ risks, 11 categories, scoring system, trigger conditions
- **KPI & milestones by layer** — gate criteria, red flags, go/no-go conditions per layer
- **Asset type architecture** — Real Estate vs US Treasuries vs ESG delivery differences
*Access by qualified engagement only.*

---

## About

→ [biljana.obradovic@concept360.rs](mailto:biljana.obradovic@concept360.rs)
→ [linkedin.com/in/biljana-obradovic-28390a8](https://linkedin.com/in/biljana-obradovic-28390a8)

*© Biljana Obradović · Concept360 · 2026*
*Attribution required: "7 Operational Layers of RWA Programmes — Biljana Obradović, Concept360, 2026"*
