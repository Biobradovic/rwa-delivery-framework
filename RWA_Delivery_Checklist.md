# RWA Delivery Checklist
## Activity Sequence for RWA Programme Managers

**© Biljana Obradović · Concept360 · 2026**  
*From: RWA Is Not a Tech Project — A Programme Manager's Guide to Real World Asset Delivery*

---

> This checklist is organised by delivery phase. Each item represents a documented deliverable — not a task to tick, but a gate criterion. If the answer is not documented, the phase should not proceed.

---

## Phase 1 — Pre-Delivery (Weeks 0–8)

### Layer 0 — Economic Viability
- [ ] Investor demand validation — documented evidence of real investor interest (not assumption)
- [ ] Revenue model feasibility — bottom-up model showing viable unit economics at projected volume
- [ ] Competitive positioning — clear articulation of why tokenisation adds value over existing alternatives
- [ ] Minimum viable scale definition — AUM threshold, investor count, secondary market volume required for sustainability

### Layer 1 — Asset
- [ ] Token classification confirmed: security token, utility token, or hybrid? Which regulator has jurisdiction?
- [ ] Regulatory opinion — signed legal opinion from firm with Digital Assets Act experience. Without written opinion — do not proceed
- [ ] Independent asset valuation — RICS or equivalent standard, by appraiser with tokenisation experience
- [ ] Title search completed — ownership chain clear, no undisclosed encumbrances

### Layer 2 — Legal & Regulatory
- [ ] CASP licensing assessment — does the planned activity trigger CASP authorization under MiCA? Begin immediately if required: 3–6 month timeline
- [ ] SPV assessment — is the SPV structure economically justified for the asset value? Below €200,000 EUR, SPV costs may be unviable
- [ ] SPV formation initiated — DOO or AD? Legal fees, notary, registration planned
- [ ] Bank screening — contact minimum three banks, verify whether they accept SPVs connected to blockchain activities

### Layer 3 — Tokenisation
- [ ] Token standard decision — ERC-20 (+ whitelist layer) or ERC-3643 (T-REX)? Documented as Architecture Decision Record
- [ ] Blockchain network selection — Ethereum mainnet, Layer 2, or alternative? ADR signed by legal and compliance
- [ ] Oracle provider identified — Chainlink or equivalent, for NAV feed and Proof of Reserves. Contract before go-live
- [ ] Smart contract audit planned — reputable auditor contracted. Waiting lists: 4–8 weeks. Cost: €15,000–50,000 EUR

### Layer 4 — Financial Infrastructure
- [ ] Custody model defined — internal custody, licensed DASP, or multi-sig? Documented as ADR. Must be decided before technical design
- [ ] Settlement mechanism agreed — how do investors fund purchases and receive distributions?
- [ ] Proof of Reserves setup — Chainlink PoR integration contracted. Define audit frequency and automatic trading suspension trigger

### Layer 5 — Identity & Compliance
- [ ] MLRO appointed — Money Laundering Reporting Officer role defined before platform development
- [ ] KYC/AML provider selected and contracted — Sumsub, Onfido, or equivalent. Before technical implementation
- [ ] Investor onboarding tiers defined — SLAs per investor type: retail domestic, retail diaspora, HNW, institutional
- [ ] AML/CFT policy drafted — reviewed by MLRO before platform onboarding begins

### Layer 6 — Market & Liquidity
- [ ] Secondary market model decided — own DEX, integration with external DEX, OTC, or licensed MTF? Documented as ADR
- [ ] Minimum viable liquidity threshold defined — what AUM, investor count, and market maker arrangement is required?

### Layer 7 — Governance & Reporting
- [ ] Governance charter drafted — decision rights matrix, escalation framework, steering committee composition
- [ ] Programme steering committee formed — at minimum: Programme Director, Legal PM, Technical PM, Compliance PM

---

## Phase 2 — Regulatory Preparation (Weeks 4–16)

- [ ] Bridging architecture documented — on-chain/off-chain bridging model as Architecture Decision Record
- [ ] Whitelist operational procedure — process for adding/removing addresses, responsible roles, escalation for AML flags, 24-hour SLA
- [ ] Whitelist authority defined in governance charter — who has the right to add or remove wallet addresses, and what the escalation path is
- [ ] Secondary market architecture finalised — minimum viable liquidity threshold and source of starting liquidity defined
- [ ] White paper drafted — in accordance with applicable law. Securities Commission: 30-day decision deadline from complete application
- [ ] AML/KYC system — provider contracted before technical platform implementation
- [ ] Smart contract audit — auditor contracted. Do not wait until development is complete
- [ ] Security audit planned separately — penetration test of full platform stack. Separate from smart contract audit. 2–4 weeks, €10,000–30,000 EUR
- [ ] Proof of Reserves integration — Chainlink PoR setup contracted. Audit frequency defined. Automatic suspension trigger designed
- [ ] Verification of Payee compliance — for EU investor targets, verify VoP compliance for EUR transfers
- [ ] CASP application submitted — if required. 3–6 month process from submission
- [ ] SPV banking onboarding — account opened, blockchain activities explicitly confirmed acceptable
- [ ] Regulatory change log established — living document tracking MiCA, local law, and FATF changes

---

## Phase 3 — Technical Implementation (Weeks 8–20)

- [ ] Smart contract deployment to testnet — with full whitelist and transfer restriction logic
- [ ] Oracle integration and testing — end-to-end testing of NAV feed, PoR verification, and fallback mechanism
- [ ] Whitelist smart contract deployed and tested — test add/remove flows with simulated KYC status changes
- [ ] Security audit (pentest) completed — full platform: APIs, admin panel, infrastructure, wallet integrations
- [ ] Smart contract audit completed — before any mainnet deployment
- [ ] KYC/AML integration end-to-end tested — with real users, not just technical testing
- [ ] Secondary market tested with real users — KYC-restricted transfer, matching engine, pricing mechanism
- [ ] Investor onboarding pipeline live — full flow from registration to first token receipt tested
- [ ] ISO 20022 mapping complete — all financial flows mapped to MX message formats
- [ ] Architecture Decision Records complete — all major decisions documented with rationale and sign-offs

---

## Phase 4 — Go-Live Preparation (2–4 Weeks Before Launch)

- [ ] Minimum viable liquidity confirmed — capital committed, market maker arrangement in place
- [ ] Three mandatory sign-offs obtained:
  - [ ] Product Manager sign-off: functional alignment with business requirements
  - [ ] Integration Architect sign-off: all technical dependencies resolved
  - [ ] Compliance / Legal sign-off: regulatory compliance confirmed for all target jurisdictions
- [ ] Go/no-go criteria defined and documented — explicit criteria for launch, who signs off, what triggers postponement
- [ ] Investor communication strategy finalised — clear explanation of difference between tokens and direct asset ownership
- [ ] Regulatory change log active — process established for monitoring and responding to regulatory updates
- [ ] Bug bounty programme established (optional but recommended for retail-facing platforms) — €20,000–50,000 EUR reward pool
- [ ] Incident response procedure documented — who does what if a critical issue arises post-launch
- [ ] Business continuity plan approved — operating continuity under disruption scenarios

---

## Post Go-Live — Ongoing Operations

- [ ] Whitelist monitoring — 24/7 process. AML flag = removal within 24 hours. On-chain logging of every change
- [ ] Proof of Reserves — oracle verification per agreed schedule (monthly minimum for retail-facing platforms)
- [ ] KYC re-verification — ongoing monitoring, re-KYC per investor tier SLA
- [ ] Regulatory change log — reviewed and updated at minimum monthly
- [ ] Governance forums — steering committee, risk committee, compliance committee cadence maintained
- [ ] Annual compliance review — compliance architecture assessed against current regulation
- [ ] Investor annual report — disclosure to token holders per regulatory requirements

---

## Key Time and Cost References

| Activity | Duration | Cost (2026) |
|----------|----------|-------------|
| CASP authorization (MiCA) | 3–6 months | €150,000 EUR minimum capital (Class 3) |
| SPV formation (Serbia) | 4–8 weeks legal + 2–6 weeks banking | €3,000–8,000 EUR legal fees |
| Smart contract audit | 4–8 weeks | €15,000–50,000 EUR |
| Security audit (pentest) | 2–4 weeks | €10,000–30,000 EUR |
| Chainlink PoR setup | 2–4 weeks | €5,000–15,000 EUR + ongoing fees |
| KYC onboarding — institutional | 15–30 days per investor | Varies by provider |
| Regulatory opinion (legal) | 4–8 weeks | €5,000–20,000 EUR |

---

*Full framework and context: [github.com/concept360/rwa-delivery-framework](https://github.com/concept360/rwa-delivery-framework)*  
*Book: RWA Is Not a Tech Project — Amazon KDP, 2026*  
*© Biljana Obradović · Concept360 · Belgrade, 2026*  
*CC BY 4.0 — use with attribution*
