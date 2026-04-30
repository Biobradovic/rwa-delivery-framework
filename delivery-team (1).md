# RWA Delivery Team Architecture

**Concept360 · Biljana Obradović · 2026**

> *"No single PM covers all seven layers. The Programme Director is the only role present in all three phases and all eight layers — from the first business case decision to the last audit."*

---

## Three Phases

| Phase | Layers | Core Team |
|-------|--------|-----------|
| **Pre-Programme** | Layer 0 | Programme Director + Solution Architect + C-suite + external advisors |
| **Implementation** | Layers 1–6 | Full delivery team — scale depends on TVL and operating model (see README) |
| **Post-Implementation** | Layer 7 (ongoing) | Operations team — PD hands over to Operations PM at Day 30 |

---

## How Teams Scale — Small / Medium / Large

The operating model chosen in Layer 0 determines which roles are needed in-house and which stay external.

### Small — < €10M TVL · Operating Model 1 or 2

| Role | What they cover |
|------|----------------|
| **Programme Director** | All 4 PM streams — Legal + Compliance + Technical + Banking |
| **Legal Counsel** *(external)* | Token classification, SPV, regulatory opinion, vendor contracts |
| **Regulatory Advisor** *(external)* | CASP/VASP strategy, NCA engagement |
| **SC Engineer / Full-stack Dev** | Smart contract + backend + basic DevOps — one person |
| **MLRO** *(named)* | AML programme, SAR, NCA notification, key ceremony participant |
| **KYC/AML Provider** *(vendor)* | Jumio, Sumsub, or platform-provided |
| **SC Audit Firms x2** *(external)* | Two independent audits — non-negotiable at any scale |
| **Pen Test Firm** *(external)* | Full platform pentest before go-live |
| **Custodian** *(vendor)* | Fireblocks or BitGo — manages SPV and treasury wallets, key ceremony |
| **Banking Partner** *(crypto-native)* | Sygnum or AMINA — 4–8 week onboarding, API-native |

### Medium — €10M–€100M TVL · Operating Model 2 or 3

| Role | What they cover |
|------|----------------|
| **Programme Director** | Programme governance, gate reviews, escalation |
| **Legal PM** | SPV, token classification, vendor contracts |
| **Compliance PM** | KYC/AML, MLRO coordination, regulatory reporting calendar |
| **Technical PM** | SC audit coordination, custody integration, ADR, wallet architecture |
| **Banking PM** | Banking screening Week 1, custody model, settlement, treasury wallet governance |
| **MLRO** *(dedicated)* | AML decisions, SAR, NCA, investor wallet risk scoring |
| **Solution Architect** | System architecture, integration design, ADR, wallet policy |
| **SC Engineers (1–2)** | Smart contract, whitelist, PoR integration, admin wallet multi-sig |
| **Full-stack Developers (1–2)** | Investor portal, API integrations, investor wallet onboarding flow |
| **DevOps / Cloud Engineer** | CI/CD, cloud infrastructure, DORA compliance |
| **CISO** *(fractional)* | ISO 27001, IAM, key ceremony governance, privileged access |
| **Investor Support Specialist** | Wallet troubleshooting, KYC queries, whitelist support, transfer agent |
| **Exchange Reporting Officer** | Exchange compliance obligations, trade surveillance |
| **Community PM** | Investor comms, Discord/Telegram, incident communications |
| **Operations PM** *(from Layer 7)* | Post go-live operations, reporting calendar, wallet reconciliation |

### Large — €100M+ TVL · Operating Model 3 or 4

| Function | Roles |
|----------|-------|
| **Programme Governance** | Programme Director · Operations PM · Community PM |
| **Legal & Regulatory** | Legal PM · Legal Counsel · Regulatory PM · Regulatory Advisor · Notary *(RE)* |
| **Compliance & AML** | Compliance PM · CCO · MLRO · DPO · Exchange Reporting Officer · Regulatory Reporting Manager · Compliance Assurance Officer |
| **Technology** | Technical PM · CTO · Solution/Integration Architect · SC Engineers (3–5) · Blockchain Devs (2–3) · Full-stack Devs (3–5) · Frontend Dev (1–2) |
| **Infrastructure & Security** | Cloud Architect · DevOps/Cloud Engineers (2–3) · CISO · Cloud Security Specialist · IAM Engineer |
| **Wallet & Custody** | Custody Specialist *(Fireblocks/Copper)* · Key Ceremony Coordinator · Wallet Policy Owner *(CISO or Technical PM)* |
| **Audit** | SC Audit Firms x2 · Pen Test Firm · ISO 27001 Auditor · Internal Audit · External Auditor / Big 4 |
| **Finance & Banking** | Banking PM · CFO · COO · CRO · Banking Partners (primary + backup) · Custodian · Market Maker |
| **Asset & Valuation** | RICS Valuator *(RE)* · ESG Verifier/Verra *(carbon)* · Oracle Provider |
| **Investor Operations** | Investor Support Specialists (2–3) · Transfer Agent · Onboarding PM |
| **Growth & Sales** | BizDev Director · Liquidity/Growth Manager · Placement Agent · Growth Partner |
| **Governance & Data** | DPO · DORA ICT Risk Manager · HR |

---

## Wallet Architecture — Who Owns What

Wallet governance is defined in Layer 2 (policy) and Layer 3 (specification). Operational from Layer 4 onwards.

| Wallet type | Layer | Custody | Owner | Compliance requirement |
|-------------|-------|---------|-------|------------------------|
| **Investor wallets** | L4–L5 | Self-custody by investor | Compliance PM + MLRO | Whitelisted (ERC-3643). KYC complete before adding. 24h removal on AML flag. |
| **SPV operational wallet** | L2, L6 | Qualified custodian (Fireblocks/Copper) | Banking PM + CFO | Multi-sig M-of-N. Named key holders. Key ceremony documented. Annual check. |
| **Treasury / reserve wallet** | L6 | Custodian — segregated | CFO + COO | Segregated from operational. Insurance confirmed. Included in PoR scope. |
| **Smart contract admin wallet** | L3, L5 | Hardware wallet + multi-sig | Technical PM + CTO + PD | Board resolution for admin actions. Timelock on upgrades. Publicly disclosed. |
| **Market maker wallet** | L6 | Market maker internal | Banking PM | Disclosed in exchange listing agreement. Monthly performance review. |

**Key Ceremony** — mandatory before go-live. All key holders convened. Signing authorities tested. Protocol documented. CISO owns. Repeated annually and on key holder change.

---

## Reporting Architecture — Who Reports What

| Reporting stream | Owner | Frequency | Hard deadline |
|-----------------|-------|-----------|---------------|
| **NCA — DORA major incident** | Compliance PM + Technical PM | Ad hoc | 4h initial · 24h detailed |
| **NCA — periodic supervisory** | Compliance PM | Quarterly | Per NCA calendar |
| **SAR / STR to FIU** | MLRO | Ad hoc | Promptly — national FIU rules |
| **FATCA / CRS** | Compliance PM + Legal PM | Annual | Per jurisdiction |
| **Investors — NAV update** | Operations PM + CFO | Quarterly minimum | Per Offering Memorandum |
| **Investors — material incident** | Community PM + Ops PM | Ad hoc | Within 24h |
| **Board — programme status** | Programme Director | Monthly | — |
| **Board — risk review** | CRO + Programme Director | Quarterly | — |
| **Exchange — trade reports** | Exchange Reporting Officer | Per CEX rulebook | Exchange SLA |
| **Exchange — suspicious activity** | Exchange Reporting Officer + MLRO | Ad hoc | Exchange rulebook |
| **Banking — reconciliation** | Banking PM + Operations PM | Monthly | — |
| **Market maker — SLA performance** | Banking PM | Monthly | — |

**Regulatory Reporting Manager** *(Large only)* — owns the full reporting calendar across all streams. Small/Medium: owned by Compliance PM.

---

## Key Role Definitions

**Programme Director** — Orchestrates all workstreams. Sequences dependencies. Owns escalation. The only role in all three phases and all eight layers.

**SC Engineer** — Writes Solidity/Rust/Vyper. Implements ERC-3643, ERC-20, or ERC-7518. Builds whitelist, PoR integration, pause/upgrade mechanisms, admin wallet multi-sig. Must understand reentrancy, access control, flash loan vectors.

**MLRO** — Named individual. NCA-notified before first investor. Owns all SAR/STR decisions. Key ceremony participant. Cannot be delegated. NCA approval for replacement: 4–8 weeks.

**IAM Engineer** — Role-based access for operational systems. Privileged access for key holders (SC admin, custody multi-sig). Audit trail for every privileged action.

**Key Ceremony Coordinator** — Convenes all multi-sig key holders. Tests signing authority. Documents protocol. Custodian present. Owned by CISO on Small/Medium.

**Exchange Reporting Officer** — Trade reports per CEX rulebook. Suspicious trading escalation to MLRO. Monthly market maker SLA review.

**Regulatory Reporting Manager** *(Large)* — Owns regulatory calendar. Coordinates NCA, DORA, FATCA/CRS, SAR, exchange reporting. Reports to CCO.

---

## PM Profiles — What RWA Programmes Need

| Profile | What makes them effective |
|---------|--------------------------|
| **Governance PM** | Designs how the programme works. Holds the line under commercial pressure. |
| **Regulatory PM** | Reads MiCA and translates it into a delivery artefact. Compliance as dependency, not checkpoint. |
| **Integration PM** | Operates in the gaps between legal, compliance, tech, and banking. Owns contested outcomes. |
| **Operations PM** | Runs reporting calendar, wallet reconciliation, vendor SLAs without PD involvement. |

---

## Roles by Layer — Who Must Be Present

| Layer | Cannot proceed without |
|-------|------------------------|
| **L0** | Programme Director · CEO · CFO · CTO · Legal Counsel · Regulatory Advisor · CRO |
| **L1** | + Legal PM · Banking PM · Regulatory PM · CCO · BizDev Director |
| **L2** | + Notary *(RE)* · RICS Valuator *(RE)* · ESG Verifier *(carbon)* · Oracle contracted · Wallet policy drafted |
| **L3** | + Technical PM · CISO · SC Engineers · Cloud/DevOps · SC Audit Firms x2 · Pen Test Firm · Internal Audit · IAM Engineer · DPO · Key Ceremony planned |
| **L4** | + MLRO *(named, NCA-notified)* · Compliance PM · Blockchain Monitoring · KYC/AML Vendor · Custodian · Investor wallet onboarding live |
| **L5** | + Community PM · Investor Support · Exchange Reporting Officer · Key Ceremony completed |
| **L6** | + Banking Partner *(live)* · Market Maker · Liquidity Manager · Transfer Agent · Treasury wallet live · PoR confirmed |
| **L7** | + Operations PM · Regulatory Reporting Manager *(Large)* · ISO 27001 Auditor *(annual)* · External Auditor *(annual)* |

---

*© Biljana Obradović · Concept360 · 2026*
*Full RACI matrix, AI tools by role, integration register, and engagement model available upon qualified engagement.*
*Attribution required: "RWA Delivery Team Architecture — Biljana Obradović, Concept360, 2026"*
