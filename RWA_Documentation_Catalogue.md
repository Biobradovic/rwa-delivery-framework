# RWA Programme Documentation Catalogue
## 68 Documents Required Across a Regulated RWA Programme

**© Biljana Obradović · Concept360 · 2026**

---

> This catalogue lists the documents required to run a regulated RWA programme from inception to institutional scale. It is organised by delivery phase. Titles and descriptions only — this is the map. The documents are the territory.
>
> A programme that cannot produce any of these documents on request is not institutionally ready. Use this catalogue to identify gaps before a regulatory review, investor due diligence, or go-live gate finds them for you.

---

## Phase 1 — Foundation Documents (18 documents)

| # | Document | Owner | Purpose |
|---|----------|-------|---------|
| 01 | Economic Viability Assessment | Programme Director | Documents investor demand validation, revenue model feasibility, competitive positioning, and minimum viable scale thresholds. Gate for starting Layer 1 work. |
| 02 | Programme Charter | Programme Director | Defines programme scope, objectives, governance structure, and initial budget. Approved by steering committee before any workstream begins. |
| 03 | Stakeholder Map and Communication Plan | Programme Director | Identifies all internal and external stakeholders, their influence and interest level, and the communication strategy for each. |
| 04 | Regulatory Opinion | Legal PM | Signed legal opinion from qualified counsel covering token classification, applicable regulatory framework, and CASP licensing assessment. Without this — do not proceed. |
| 05 | Token Classification Decision Record | Legal PM + Compliance PM | Documents the token classification decision (security, utility, or hybrid), the legal basis, and the regulatory implications for the target jurisdictions. |
| 06 | CASP Licensing Assessment | Compliance PM | Assesses whether planned activities trigger CASP authorization under MiCA. If yes: authorization process initiated immediately. Timeline: 3–6 months. |
| 07 | SPV Feasibility Assessment | Legal PM | Documents whether SPV structure is economically viable for the asset value, which SPV type (DOO or AD), and estimated formation costs and timeline. |
| 08 | Asset Due Diligence Report | Asset PM + Legal PM | Covers property title search, ownership chain verification, encumbrance status, outstanding legal issues, and cadastral registration status. |
| 09 | Independent Valuation Report | Asset PM | RICS or equivalent standard valuation by qualified appraiser with tokenisation experience. Includes liquidity discount methodology for fractional stakes. |
| 10 | Bank Screening Results | Operations PM | Documents which banks were approached, their position on blockchain-connected SPVs, and which bank was selected for SPV account. |
| 11 | Token Standard Decision Record (ADR-001) | Technical PM + Legal PM | Architecture Decision Record documenting token standard selection (ERC-20 or ERC-3643), rationale, compliance implications, and sign-off by legal and compliance. |
| 12 | Blockchain Network Decision Record (ADR-002) | Technical PM | ADR documenting blockchain network selection, Layer 2 strategy if applicable, rationale, and infrastructure implications. |
| 13 | Custody Model Decision Record (ADR-003) | Technical PM + Compliance PM | ADR documenting custody model (internal, licensed DASP, or multi-sig), rationale, regulatory status, and key ceremony protocol. |
| 14 | Oracle Provider Decision Record (ADR-004) | Technical PM | ADR documenting oracle provider selection for NAV feed and Proof of Reserves, integration approach, and fallback mechanism. |
| 15 | Secondary Market Design Document (ADR-005) | Product PM + Legal PM | ADR documenting secondary market architecture (own DEX, external DEX, OTC, or MTF), minimum viable liquidity threshold, and market maker strategy. |
| 16 | Governance Charter (v1) | Programme Director | Initial governance framework: steering committee composition, decision rights matrix, meeting cadence, escalation framework. Updated throughout programme. |
| 17 | Programme Risk Register (v1) | Programme Director | Initial risk register covering regulatory, technical, operational, financial, and soft risks. Updated weekly throughout programme. |
| 18 | Programme Plan (v1) | Programme Director | Full programme timeline with milestones, dependencies, resource allocation, and phase gate criteria. Updated as programme evolves. |

---

## Phase 2 — Regulatory Preparation Documents (14 documents)

| # | Document | Owner | Purpose |
|---|----------|-------|---------|
| 19 | AML/CFT Policy | Compliance PM + MLRO | Comprehensive anti-money laundering policy covering investor onboarding, transaction monitoring, suspicious activity reporting, and record-keeping obligations. |
| 20 | KYC Procedure Manual | Compliance PM | Step-by-step procedure for investor identity verification, document requirements per investor tier, EDD triggers, and ongoing monitoring obligations. |
| 21 | Investor Onboarding SLA Matrix | Compliance PM | Defines onboarding time commitments per investor tier (retail domestic, diaspora, HNW, institutional) with escalation triggers. |
| 22 | Whitelist Operational Procedure | Compliance PM + Technical PM | Documents process for adding and removing wallet addresses from whitelist, responsible roles, authorization requirements, 24-hour AML flag SLA, and on-chain logging requirements. |
| 23 | Token White Paper | Legal PM + Product PM | Prepared in accordance with applicable law (MiCA and/or local Digital Assets Act). Covers asset description, token structure, rights, risks, and issuer information. |
| 24 | CASP Authorization Application | Compliance PM + Legal PM | Complete application package for CASP authorization with the relevant National Competent Authority. Includes all supporting documentation. |
| 25 | Bridging Architecture Document (ADR-006) | Technical PM + Legal PM | Documents the on-chain/off-chain bridging model: which off-chain document controls the on-chain token in case of conflict, oracle failure procedures, and regulatory audit trail. |
| 26 | Smart Contract Audit Plan | Technical PM | Documents audit scope, selected auditor, timeline, cost, and post-audit change freeze protocol. |
| 27 | Security Audit Plan | Technical PM | Documents pentest scope (APIs, admin panel, infrastructure, wallet integrations), selected firm, timeline, and remediation process. |
| 28 | Proof of Reserves Integration Plan | Technical PM | Documents Chainlink PoR integration design, audit frequency, automatic trading suspension trigger mechanism, and oracle failure fallback. |
| 29 | ISO 20022 Message Mapping | Technical PM + Operations | Maps all financial flows to MX message formats for banking integration and regulatory reporting. |
| 30 | Regulatory Change Management Procedure | Compliance PM | Process for monitoring regulatory updates (MiCA, local law, FATF) and translating them into programme actions within defined response timeframes. |
| 31 | Regulatory Change Log (v1) | Compliance PM | Living document tracking all relevant regulatory changes, their programme impact, and actions taken. Updated at minimum monthly. |
| 32 | VoP Compliance Assessment | Compliance PM | For programmes targeting EU investors: assessment of Verification of Payee obligations and SPV registration requirements with target EU banks. |

---

## Phase 3 — Technical Implementation Documents (11 documents)

| # | Document | Owner | Purpose |
|---|----------|-------|---------|
| 33 | Smart Contract Specification | Technical PM | Full functional specification of all smart contract logic, including token mechanics, whitelist integration, oracle feeds, and governance functions. |
| 34 | Smart Contract Audit Report | Technical PM | Completed audit report from qualified auditor (Trail of Bits, OpenZeppelin, CertiK, or equivalent). All findings documented and remediated or accepted. |
| 35 | Security Audit Report | Technical PM | Completed penetration test report. All critical and high findings remediated before go-live. |
| 36 | Key Ceremony Protocol | Technical PM + Compliance PM | Formal documented procedure for private key generation, witnessed and signed by legal and compliance team members present. |
| 37 | KYC/AML Integration Test Report | Compliance PM + Technical PM | Documents end-to-end testing of investor onboarding workflow with real users across all investor tiers. |
| 38 | Oracle Integration Test Report | Technical PM | Documents testing of NAV feed, PoR verification, rental income oracle, and all fallback mechanisms under simulated failure conditions. |
| 39 | Whitelist Test Report | Technical PM + Compliance PM | Documents testing of add/remove flows, AML flag simulation, 24-hour SLA compliance, and on-chain logging verification. |
| 40 | Secondary Market Test Report | Product PM + Technical PM | Documents testing of KYC-restricted transfer, matching engine, pricing mechanism, and liquidity scenarios with real users. |
| 41 | User Acceptance Testing Report | Product PM | Sign-off document from all workstream leads confirming platform meets requirements before go-live gate. |
| 42 | Integration Architecture Document | Technical PM | Complete documentation of all system integrations: KYC provider, oracle, banking, custody, reporting. Includes API specifications and failover procedures. |
| 43 | Bug Bounty Programme Design | Technical PM | Scope, reward structure (€20,000–50,000 EUR pool recommended for retail-facing platforms), responsible disclosure process, and remediation SLAs. |

---

## Phase 4 — Go-Live Readiness Documents (9 documents)

| # | Document | Owner | Purpose |
|---|----------|-------|---------|
| 44 | Go/No-Go Assessment Report | Programme Director | Structured assessment against all gate criteria. Three mandatory sign-offs: Product Manager, Integration Architect, Compliance/Legal. Without all three — gate does not open. |
| 45 | Go-Live Communication Plan | Product PM + Compliance PM | Investor communication strategy explaining the difference between tokens and direct asset ownership, go-live timeline, and onboarding process. |
| 46 | Incident Response Procedure | Operations PM | Step-by-step response procedure for defined incident types: smart contract vulnerability, oracle failure, AML flag escalation, banking disruption, regulatory inquiry. |
| 47 | Minimum Viable Liquidity Confirmation | Operations PM | Documented confirmation that MVL threshold has been met: capital committed, market maker arrangement signed, starting liquidity pool established. |
| 48 | CASP Authorization Certificate | Compliance PM | Confirmation of CASP authorization from NCA (if applicable). Or documented regulatory sandbox arrangement. |
| 49 | Governance Charter (final) | Programme Director | Final version of governance charter with all workstream sign-offs, decision rights matrix, and post-launch operational governance framework. |
| 50 | Vendor Governance Framework | Operations PM | SLA management, performance review cadence, escalation procedures, and exit protocols for all critical vendors (KYC provider, oracle, custody, legal). |
| 51 | Business Continuity Plan | Operations PM | Operating continuity procedures under defined disruption scenarios: platform outage, banking disruption, oracle failure, key person dependency. |
| 52 | Programme Closure Report | Programme Director | Documents programme delivery against original business case, outstanding items, transition to operational management, and lessons learned. |

---

## Phase 4 — Institutional Scale Documents (16 documents)

| # | Document | Owner | Purpose |
|---|----------|-------|---------|
| 53 | PMO Operating Model | Programme Director | PMO structure, cadence, reporting framework, escalation procedures, and team responsibilities for ongoing programme governance. |
| 54 | Ongoing Compliance Monitoring Procedure | Compliance PM + MLRO | Procedure for continuous AML monitoring, periodic re-KYC, sanctions screening, and suspicious activity reporting post-launch. |
| 55 | Investor Reporting Standard | Operations PM + Compliance PM | Standard for material disclosures, routine investor communications, and annual reporting. Approved by board. |
| 56 | Corporate Actions Procedure | Operations PM + Legal PM | Process for asset sales, refinancing, distributions, disputes, and extraordinary events. Covers both on-chain and off-chain components. |
| 57 | Secondary Market Risk Assessment | Risk PM + Operations PM | Assessment of liquidity, settlement, and operational risk for secondary market operations. Updated quarterly. |
| 58 | Cross-Border Compliance Matrix | Legal PM + Compliance PM | Jurisdiction-by-jurisdiction compliance requirements for all target investor countries. Updated as new jurisdictions are added. |
| 59 | Tax Reporting Framework | Compliance PM + Legal PM | Investor tax document types by jurisdiction, generation process, and distribution timeline. |
| 60 | Multi-Jurisdiction Compliance Architecture | Legal PM | Formal multi-jurisdiction compliance framework for platforms operating across multiple countries simultaneously. |
| 61 | Key Person Dependency Register | Programme Director | Critical function dependencies, backup arrangements, and succession protocols for all key roles. |
| 62 | Institutional Investor Due Diligence Package | Programme Director | Governance, audit, compliance evidence package prepared for institutional investor due diligence. Includes all ADRs, audit reports, and regulatory authorizations. |
| 63 | Board Reporting Pack (RWA Segment) | Programme Director | Quarterly board reporting framework covering programme performance, risk status, regulatory updates, and financial metrics. |
| 64 | Operating Model Stress Test Report | Operations PM + Risk PM | Results of volume and scenario stress testing under defined load conditions and disruption scenarios. |
| 65 | Regulatory Examination Preparation Guide | Compliance PM | Internal preparation document for National Competent Authority examinations. Covers evidence organization, staff preparation, and response protocols. |
| 66 | Institutional Distribution Agreement Template | Legal PM | Standard terms for institutional distribution partners, including KYC obligations, reporting requirements, and liability allocation. |
| 67 | Annual Compliance Review Report | Compliance PM | Annual assessment of compliance architecture against current regulatory requirements. Identifies gaps and remediation plan. |
| 68 | Programme Performance Review | Programme Director | Post-implementation review against original business case, documenting actual vs. planned performance across all seven operational layers. |

---

## Document Status Tracking Template

Use this for programme governance reviews:

| Phase | Total documents | Completed | In progress | Not started | Overdue |
|-------|----------------|-----------|-------------|-------------|---------|
| Phase 1 — Foundation | 18 | | | | |
| Phase 2 — Regulatory | 14 | | | | |
| Phase 3 — Technical | 11 | | | | |
| Phase 4 — Go-Live | 9 | | | | |
| Phase 4 — Institutional | 16 | | | | |
| **Total** | **68** | | | | |

*A document not planned in advance does not exist — and will be discovered as a gap at the worst possible moment, usually before a regulatory review or go-live.*

---

*Full framework: [github.com/concept360/rwa-delivery-framework](https://github.com/concept360/rwa-delivery-framework)*  
*© Biljana Obradović · Concept360 · Belgrade, 2026 · CC BY 4.0*
