# 7 Operational Layers — Quick Reference
## RWA Programme Delivery Framework

**© Biljana Obradović · Concept360 · 2026**

---

> Use this reference during programme reviews, go/no-go assessments, and stakeholder conversations. For each layer: entry question, key risks, PM responsibilities, and common failure pattern.

---

## Layer 0 — Economic Viability
*The gate before the gate*

**Entry question:** Is there a documented economic case showing sustainable investor demand, viable revenue model, and tokenisation adding genuine value over existing alternatives?

**What it covers:**
- Investor demand validation — documented evidence, not assumption
- Revenue model feasibility — bottom-up unit economics at projected volume
- Competitive positioning — why tokenisation vs. existing access mechanisms
- Minimum viable scale — AUM, investor count, secondary market volume thresholds

**Where programmes get stuck:** Teams fall in love with tokenisation and build technically perfect platforms with no investor demand. Layer 0 is skipped in the majority of failed programmes. The cause of failure is diagnosed as "market wasn't ready" — the real cause was never asking whether demand existed before building.

**PM responsibility:** Own the Layer 0 documentation. Ensure it is approved by the steering committee before Layer 1 work begins. This is not a background activity — it is a gate.

---

## Layer 1 — Asset
*What you are tokenising*

**Entry question:** Is the asset legally owned, free of undisclosed encumbrances, and independently valued by a qualified appraiser?

**What it covers:**
- Property due diligence — title search, ownership chain, encumbrance check
- Independent valuation — RICS or equivalent, by appraiser with tokenisation experience
- SPV assessment — is tokenisation economically viable for this asset value?
- Rights definition — what exactly does the token represent?

**Where programmes get stuck:** Hidden encumbrances and ownership irregularities discovered at the notarial stage — after technical work has started on the wrong assumptions. SPV costs make tokenisation economically unviable for smaller properties (below €200,000 EUR in most jurisdictions).

**PM responsibility:** Due diligence is a delivery gate, not a background activity. The technical team cannot make architecture decisions without knowing the full legal and financial profile of the asset. Do not let technical work begin before due diligence is complete.

**Key risk — banking:** Some banks refuse to open accounts for SPVs connected to blockchain activities. Validate banking acceptance explicitly in Phase 1 — not at the point of SPV registration.

---

## Layer 2 — Legal & Regulatory
*The slowest layer — must start Day 1*

**Entry question:** Is there a signed legal opinion for the target jurisdiction(s), a defined SPV structure, and a completed CASP licensing assessment?

**What it covers:**
- Token classification — security token, utility token, or hybrid? Determines which regulator has jurisdiction
- CASP licensing assessment — does the planned activity trigger CASP under MiCA?
- Jurisdictional analysis — for each target investor country
- Regulatory opinion — signed by qualified legal counsel
- SPV structure design — DOO or AD in Serbia? Which structure fits the asset?

**Where programmes get stuck:** Wrong token classification discovered post-development triggers complete architectural redesign. CASP licensing (3–6 months) not on the programme timeline because it was treated as a post-technical step.

**PM responsibility:** CASP assessment must begin in Week 1 of the programme — before platform development starts. VASP (Serbia) ≠ CASP (EU MiCA). Two separate assessments required for platforms serving EU investors.

**CASP Class Reference:**
| Class | Services | Minimum Capital |
|-------|----------|-----------------|
| 1 | Advisory, reception and transmission of orders | €50,000 EUR |
| 2 | Exchange, execution of orders, placing | €125,000 EUR |
| 3 | Custody, trading platform, portfolio management | €150,000 EUR |

---

## Layer 3 — Tokenisation
*Architecture decisions are compliance decisions*

**Entry question:** Is the token standard decision documented in an Architecture Decision Record, signed off by legal and compliance?

**What it covers:**
- Token standard selection — ERC-20 + whitelist layer, or ERC-3643 (T-REX)?
- Smart contract design and audit (4–8 weeks, €15,000–50,000 EUR)
- Security audit / penetration test — separate from smart contract audit (2–4 weeks, €10,000–30,000 EUR)
- Whitelist management — 24/7 operational process, not a one-time setup
- Oracle infrastructure — NAV feed, Proof of Reserves, rental income
- Proof of Reserves — MiCA Article 76 obligation for asset-referenced tokens

**Where programmes get stuck:** Audit finding post-code-freeze requires a new audit cycle (8–12 week buffer). PoR not in original architecture requires migration. Whitelist managed manually in a spreadsheet — does not scale and creates regulatory exposure.

**PM responsibility:** Two separate audit cycles, two separate budgets. Smart contract audit ≠ security audit. Whitelist management authority must be defined in the governance charter — who has the right to add or remove addresses, with what authorization level, and what the escalation path is for disputed removals.

**Whitelist SLA:** AML flag on investor wallet = removal within 24 hours. This is both a technical and a legal action. The exit mechanism for flagged investors must be legally documented before the first investor is onboarded.

---

## Layer 4 — Financial Infrastructure
*The most underestimated layer in every programme plan*

**Entry question:** Is the banking relationship confirmed, the custody model defined as an ADR, and the settlement mechanism agreed?

**What it covers:**
- SPV banking onboarding — account confirmed with blockchain-friendly bank
- Custody model — internal custody, licensed DASP, or multi-sig?
- Settlement mechanism — how investors fund purchases and receive distributions
- ISO 20022 integration — mapping all financial flows to MX message formats
- Yield distribution — tax treatment, reporting format, frequency

**Where programmes get stuck:** Bank refuses SPV — programme stops. No banking = no cash flows = no investor participation. Custody model decided too late to change without full architectural rebuild. Yield distribution agreed without checking whether tax reporting infrastructure can generate investor documents per jurisdiction.

**PM responsibility:** Custody decision is an architectural decision — must be made in Phase 1 and documented as an ADR. ISO 20022 is an architectural constraint, not a migration task. Every financial institution the platform interacts with uses MX messaging format.

**Custody options:**
| Model | Advantages | Risks | Regulatory status |
|-------|-----------|-------|------------------|
| Internal custody | Full control, lower cost | Single point of failure, full liability | NBS approval required in Serbia |
| Licensed DASP | Institutional standard, insurance, MPC | Higher cost, provider dependency | Compliant if provider is EU-authorized |
| Multi-sig | Eliminates single point of failure | Operational complexity, quorum recovery | Acceptable, must be documented with key ceremony protocol |

---

## Layer 5 — Identity & Compliance
*The hidden critical path of every RWA programme*

**Entry question:** Is the KYC/AML workflow end-to-end tested with real investors, and SLAs defined for each investor type?

**What it covers:**
- KYC/AML provider integration — before technical platform implementation
- Investor onboarding workflow — per investor tier with defined SLAs
- MLRO appointment — before platform development begins
- CASP licensing (if triggered) — 3–6 months, must be on critical path from Week 1
- Ongoing AML monitoring — continuous, not point-in-time

**Where programmes get stuck:** Onboarding bottleneck becomes go-live blocker. Revenue delayed 3–6 months. Teams that treat KYC/AML as a technical item systematically underestimate time and cost.

**PM responsibility:** KYC/AML infrastructure is not a feature — it determines when the platform can begin operations. Define onboarding SLAs before the first API call is written.

**Investor tier SLAs:**
| Tier | SLA | Additional requirements |
|------|-----|------------------------|
| Retail domestic | 2–3 days | Standard KYC |
| Retail diaspora | 5–10 days | EDD for cross-border, source of funds |
| HNW individual | 10–15 days | PEP screening mandatory |
| Institutional | 15–30 days | Entity verification, UBO, AML questionnaire |

---

## Layer 6 — Market & Liquidity
*Must be a Phase 1 deliverable — not a post-launch feature*

**Entry question:** Is there a liquidity plan, a minimum viable liquidity threshold, a secondary market strategy, and a market maker arrangement?

**What it covers:**
- Secondary market design — own DEX, external DEX integration, OTC, or licensed MTF
- Minimum viable liquidity threshold — defined before launch, not after
- Market maker arrangement — who provides starting liquidity?
- Yield distribution — frequency, automation, tax treatment per jurisdiction
- Pricing methodology — NAV vs. market price, fractional discount

**Where programmes get stuck:** Platform launches without buyers. Investors cannot exit. Trust collapses within weeks. Secondary market deferred to "post-launch" universally requires full architectural rebuild.

**PM responsibility:** Secondary market as architectural decision. Token standard selection, custody model, KYC integration, and governance model are all affected by secondary market design. The minimum viable liquidity threshold must be a go-live gate criterion — not a post-launch target.

**Key insight:** Liquidity is not the same as tradability. A token that can technically be transferred is not liquid if there are no active buyers at an acceptable price within an acceptable timeframe.

---

## Layer 7 — Governance & Reporting
*Runs horizontally across ALL layers from day one*

**Entry question:** Is the governance charter signed, decision rights matrix defined, escalation paths documented, and automated reporting tested?

**What it covers:**
- Governance charter — decision rights, meeting cadence, escalation framework
- Automated regulatory reporting — audit trail, on-chain logging
- Corporate actions — dividend process, voting, asset sales
- Incident response — who does what when things go wrong
- Regulatory change management — process for monitoring and responding to regulatory updates

**Where programmes get stuck:** Governance vacuum post-launch. No clear owner when things go wrong — and things always go wrong. Regulatory finding post-launch with no documented response procedure.

**PM responsibility:** Layer 7 is not a final step. It is active from the first programme decision. The three mandatory go-live sign-offs — Product Manager, Integration Architect, Compliance/Legal — must all be obtained before any gate opens.

**Governance forum cadence:**
| Forum | Frequency | Decisions owned |
|-------|-----------|-----------------|
| Steering committee | Monthly | Strategic decisions, budget, go/no-go gates |
| Programme core team | Weekly | Cross-workstream dependencies, escalations |
| Compliance committee | Bi-weekly | Regulatory updates, AML findings, policy changes |
| Technical review | Weekly during development | Architecture decisions, audit findings |

---

## The Cascade Principle — Quick Reference

A change in any layer cascades to others. Ask for every proposed change: *which other layers are affected, and what must be revisited?*

| Change in | Cascades to |
|-----------|-------------|
| Layer 2 (regulatory) | Layer 3 (token standard), Layer 5 (KYC rules), Layer 7 (reporting) |
| Layer 3 (token standard) | Layer 4 (custody), Layer 5 (transfer restrictions), Layer 6 (secondary market) |
| Layer 4 (banking rejection) | Layer 2 (SPV restructuring), Layer 3 (payout mechanism), Layer 5 (onboarding) |
| Layer 5 (KYC outage) | Layer 6 (onboarding halt), Layer 7 (governance escalation) |
| Layer 6 (liquidity failure) | Layer 7 (governance crisis), Layer 2 (regulatory review) |

---

## Programme Self-Assessment — Status Check

Use this for programme reviews. Mark each layer: **Green** (resolved and documented) / **Yellow** (in progress, unresolved dependencies) / **Red** (not started or blocked).

| Layer | Status | Critical dependency | Blocker? |
|-------|--------|--------------------|----|
| 0 — Economic Viability | | | |
| 1 — Asset | | | |
| 2 — Legal & Regulatory | | | |
| 3 — Tokenisation | | | |
| 4 — Financial Infrastructure | | | |
| 5 — Identity & Compliance | | | |
| 6 — Market & Liquidity | | | |
| 7 — Governance & Reporting | | | |

*If any layer is Red — identify the cascade impact before proceeding.*

---

*Full framework: [github.com/concept360/rwa-delivery-framework](https://github.com/concept360/rwa-delivery-framework)*  
*© Biljana Obradović · Concept360 · Belgrade, 2026 · CC BY 4.0*
