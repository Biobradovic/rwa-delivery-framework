# RWA Delivery Team Architecture

**Concept360 · Biljana Obradović · 2026**

> *"No single PM covers all seven layers. The Programme Director is the only role present in all three phases and all eight layers — from the first business case decision to the last audit."*

---

## Key Role Definitions

**Program Director** — Orchestrates all workstreams. Sequences dependencies. Owns escalation. The only role in all three phases and all eight layers.

**SC Engineer** — Writes Solidity/Rust/Vyper. Implements ERC-3643, ERC-20, or ERC-7518. Builds whitelist, PoR integration, pause/upgrade mechanisms, admin wallet multi-sig. Must understand reentrancy, access control, flash loan vectors.

**MLRO** — Named individual. NCA-notified before first investor. Owns all SAR/STR decisions. Key ceremony participant. Cannot be delegated. NCA approval for replacement: 4–8 weeks.

**IAM Engineer** — Role-based access for operational systems. Privileged access for key holders (SC admin, custody multi-sig). Audit trail for every privileged action.

**Key Ceremony Coordinator** — Convenes all multi-sig key holders. Tests signing authority. Documents protocol. Custodian present. Owned by CISO on Small/Medium.

**Exchange Reporting Officer** — Trade reports per CEX rulebook. Suspicious trading escalation to MLRO. Monthly market maker SLA review.

**Regulatory Reporting Manager** *(Large)* — Owns regulatory calendar. Coordinates NCA, DORA, FATCA/CRS, SAR, exchange reporting. Reports to CCO.

---

## PM Profiles — What RWA Programs Need

| Profile | What makes them effective |
|---------|--------------------------|
| **Governance PM** | Designs how the program works. Holds the line under commercial pressure. |
| **Regulatory PM** | Reads MiCA and translates it into a delivery artefact. Compliance as dependency, not checkpoint. |
| **Integration PM** | Operates in the gaps between legal, compliance, tech, and banking. Owns contested outcomes. |
| **Operations PM** | Runs reporting calendar, wallet reconciliation, vendor SLAs without PD involvement. |

---

## Three Phases

| Phase | Layers | Core Team |
|-------|--------|-----------|
| **Pre-Programme** | Layer 0 | Programme Director + Solution Architect + C-suite + external advisors |
| **Implementation** | Layers 1–6 | Full delivery team — scale depends on TVL |
| **Post-Implementation** | Layer 7 (ongoing) | Operations team — PD hands over to Operations PM at Day 30 |

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

## How Teams Scale — Small / Medium / Large

### Small — < €10M TVL
*Using existing platform or white label solution*

| Role | What they cover |
|------|----------------|
| **Program Director** | All 4 PM streams — Legal + Compliance + Technical + Banking |
| **Legal Counsel** *(external)* | Token classification, SPV, regulatory opinion, vendor contracts |
| **Regulatory Advisor** *(external)* | CASP/VASP strategy, NCA engagement |
| **SC Engineer / Full-stack Dev** | Smart contract + backend + basic DevOps — one person |
| **MLRO** *(named)* | AML program, SAR, NCA notification, key ceremony participant |
| **KYC/AML Provider** *(vendor)* | Jumio, Sumsub, or platform-provided |
| **SC Audit Firms x2** *(external)* | Two independent audits — non-negotiable at any scale |
| **Pen Test Firm** *(external)* | Full platform pentest before go-live |
| **Custodian** *(vendor)* | Fireblocks or BitGo — SPV and treasury wallets, key ceremony |
| **Banking Partner** *(crypto-native)* | Sygnum or AMINA — 4–8 week onboarding, API-native |

### Medium — €10M–€100M TVL
*Building custom or significantly customizing white label*

| Role | What they cover |
|------|----------------|
| **Program Director** | Program governance, gate reviews, escalation |
| **Legal PM** | SPV, token classification, vendor contracts |
| **Compliance PM** | KYC/AML, MLRO coordination, regulatory reporting calendar |
| **Technical PM** | SC audit coordination, custody integration, ADR |
| **Banking PM** | Banking screening Week 1, custody model, settlement |
| **MLRO** *(dedicated)* | AML decisions, SAR, NCA, investor wallet risk scoring |
| **Solution Architect** | System architecture, integration design, ADR |
| **SC Engineers (1–2)** | Smart contract, whitelist, PoR integration, admin wallet multi-sig |
| **Full-stack Developers (1–2)** | Investor portal, API integrations, wallet onboarding flow |
| **DevOps / Cloud Engineer** | CI/CD, cloud infrastructure, DORA compliance |
| **CISO** *(fractional)* | ISO 27001, IAM, key ceremony governance |
| **Investor Support Specialist** | Wallet troubleshooting, KYC queries, transfer agent |
| **Exchange Reporting Officer** | Exchange compliance obligations, trade surveillance |
| **Community PM** | Investor comms, Discord/Telegram, incident communications |
| **Operations PM** *(from Layer 7)* | Post go-live operations, reporting calendar |

### Large — €100M+ TVL
*Full custom build or platform operator*

| Function | Roles |
|----------|-------|
| **Program Governance** | Program Director · Operations PM · Community PM |
| **Legal & Regulatory** | Legal PM · Legal Counsel · Regulatory PM · Regulatory Advisor · Notary *(RE)* |
| **Compliance & AML** | Compliance PM · CCO · MLRO · DPO · Exchange Reporting Officer · Regulatory Reporting Manager · Compliance Assurance Officer |
| **Technology** | Technical PM · CTO · Solution/Integration Architect · SC Engineers (3–5) · Blockchain Devs (2–3) · Full-stack Devs (3–5) · Frontend Dev (1–2) |
| **Infrastructure & Security** | Cloud Architect · DevOps/Cloud Engineers (2–3) · CISO · Cloud Security Specialist · IAM Engineer |
| **Wallet & Custody** | Custody Specialist · Key Ceremony Coordinator · Wallet Policy Owner |
| **Audit** | SC Audit Firms x2 · Pen Test Firm · ISO 27001 Auditor · Internal Audit · External Auditor / Big 4 |
| **Finance & Banking** | Banking PM · CFO · COO · CRO · Banking Partners (primary + backup) · Custodian · Market Maker |
| **Asset & Valuation** | RICS Valuator *(RE)* · ESG Verifier/Verra *(carbon)* · Oracle Provider |
| **Investor Operations** | Investor Support Specialists (2–3) · Transfer Agent · Onboarding PM |
| **Growth & Sales** | BizDev Director · Liquidity/Growth Manager · Placement Agent · Growth Partner |
| **Governance & Data** | DPO · DORA ICT Risk Manager · HR |

---

## Wallet & Reporting

Wallet governance is defined in Layer 2 and Layer 3. Five wallet types — investor, SPV operational, treasury, smart contract admin, and market maker — each require different custody model, signing authority, and team ownership.

RWA programs run 12+ parallel reporting streams simultaneously across regulatory, investor, board, exchange, and banking obligations — each with a named owner and hard deadline where applicable.

*Full wallet policy, custody model per type, signing authority matrix, and reporting matrix available in the private repository.*

---

*Full RACI matrix, integration register, and engagement model available upon qualified engagement.*
Biljana Obradović, Concept360, 2026"*

