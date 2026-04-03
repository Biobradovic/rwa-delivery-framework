# RWA Delivery Framework
### The 7 Operational Layers of Real World Asset Programmes

**By Biljana Obradović** · CEBP™ · CBPM™ · PRINCE2® · Fintech Expert™  
Founder, [Concept360](https://concept360.my.canva.site/) · 101 Blockchains Advisory Council · Belgrade, Serbia

---

## What This Is

This repository contains the public reference materials for the **RWA Delivery Framework** — an original analytical framework for programme managers, delivery leads, and senior practitioners responsible for taking Real World Asset tokenisation initiatives from concept to institutional-grade operation.

The central thesis:

> **RWA programmes do not fail because blockchain is hard. They fail because governance is introduced too late, compliance is treated as a gate rather than a dependency, and the programme is managed as a project.**

This framework supports ongoing research and consulting work in regulated RWA programme delivery.
---

## The 7 Operational Layers

All seven layers must be active **simultaneously**. A change in one cascades to all others. This is why sequential thinking — build first, add compliance later — fails every time.

| # | Layer | Key Delivery Responsibility | Where Programmes Get Stuck |
|---|-------|----------------------------|---------------------------|
| 0 | **Economic Viability** | Does this asset actually need to be tokenised? Sustainable economics? | Teams skip Layer 0 and discover there is no investor demand post-launch |
| 1 | **Asset** | Due diligence, legal ownership, SPV formation, independent valuation | Hidden encumbrances discovered at notarial stage — after technical work has started |
| 2 | **Legal & Regulatory** | Token classification, CASP assessment, regulatory opinion, jurisdictional analysis | Wrong token class = full architectural redesign. CASP: 3–6 month timeline, never on the plan |
| 3 | **Tokenisation** | Smart contract design & audit, token standard, whitelist, oracle, Proof of Reserves | Audit finding post-code-freeze = new audit cycle. PoR not in original architecture = migration |
| 4 | **Financial Infrastructure** | SPV banking, custody model, settlement, ISO 20022 integration | Bank refuses SPV — programme stops. Custody model decided too late to change |
| 5 | **Identity & Compliance** | KYC/AML workflow, investor onboarding, CASP licensing, ongoing monitoring | Onboarding bottleneck becomes go-live blocker. Revenue delayed 3–6 months |
| 6 | **Market & Liquidity** | Secondary market architecture, minimum viable liquidity threshold, yield distribution | Platform launches without buyers. Investors cannot exit. Trust collapses |
| 7 | **Governance & Reporting** | Decision rights, governance charter, audit trail — **runs across ALL layers from day one** | Governance vacuum post-launch. Regulatory finding. No clear owner when things go wrong |

**Layer 7 is not a final step.** It is a horizontal layer — present in every phase, from the first programme decision to the last audit.

---

## Contents of This Repository

### 📋 [RWA Delivery Checklist](./RWA_Delivery_Checklist.md)
A structured activity sequence for RWA programme managers — organised by delivery phase (Pre-Delivery, Regulatory Preparation, Technical Implementation, Go-Live). Based on real delivery experience, not theory.

### 📊 [Documentation Catalogue](./RWA_Documentation_Catalogue.md)
A reference list of the 53 documents required across a regulated RWA programme — organised by delivery phase and layer. Titles and descriptions only. This is the map; the documents are the territory.

### 📊 [7 Layers Quick Reference](./Seven_Layers_Quick_Reference1.md)
One-page reference for each of the seven operational layers: entry question, key risks, PM responsibilities, and common failure patterns. Use this during programme reviews and go/no-go assessments.

---

## Three Risks Every PM Must Know

**CASP Licensing — The Hidden Timeline**  
CASP authorization under MiCA takes 3–6 months. It must be on the programme critical path from Week 1. Most platforms start this process after the platform is built. By then, they cannot legally serve EU investors.

**Whitelist Management — The Operational Surprise**  
Whitelist is not a one-time setup. It is a 24/7 operational process. An AML flag on an investor's wallet requires whitelist removal within 24 hours. The exit mechanism for flagged investors must be legally documented before the first investor is onboarded.

**Proof of Reserves — The Regulatory Obligation**  
Under MiCA Article 76, reserve transparency is a regulatory obligation for asset-referenced tokens. Chainlink PoR is the standard. PoR failure must trigger automatic trading suspension — built into the smart contract from day one, not added post-launch.

---

## POC vs MVP — The Structural Gap

The most consistently misunderstood transition in RWA delivery.

| Proof of Concept | Minimum Viable Product |
|-----------------|----------------------|
| Technology works | System operates under real constraints |
| Internal / network investors only | Real KYC/AML end-to-end live |
| Regulatory assumptions documented | External audit trail validated |
| Minimal external dependencies | Banking confirmed and active |
| No formal compliance process | Three mandatory sign-offs obtained |

> The gap between POC and MVP is not technical. It is operational.

---

## The Four PM Profiles

No single PM covers all seven layers. The language, risks, and stakeholder sets are too different.

| Profile | Layers | Cost of Absence |
|---------|--------|-----------------|
| **Legal / Asset PM** | 0–2 | 3–6 months delay per asset. Every jurisdiction reinvents SPV structure |
| **Technical PM** | 3–4 | Integration failures discovered in UAT. New audit cycle required |
| **Compliance PM** | 5 | KYC is the hidden critical path. Missing in 90% of regional programmes |
| **Delivery Lead** | 6–7 + cross | Scope creep absorbs the programme. Commercial pressure overrides delivery gates |

---

## Soft Risks That Do Not Appear in the Risk Register

Standard risk registers cover regulatory, technical, and financial risks. These four categories are consistently missed — and consistently cause delays:

- **Stakeholder conflicts hidden behind alignment meetings** — consensus that proves to be pseudo-consensus
- **Slow decision-making between legal, product, and compliance** — everyone waits for someone else to take responsibility
- **Unclear ownership of cross-functional deliverables** — everyone is responsible, no one is accountable
- **Regulatory fear culture** — better not to decide than to make a mistake, especially in domestic financial institutions
- **Knowledge gap between blockchain and banking teams** — different languages, different assumptions, misunderstandings discovered at go-live

---

## About This Framework

The 7 Operational Layers of RWA Programmes is an original analytical framework developed by Biljana Obradović based on analysis of documented delivery failures, platform architectures, and 20+ years of experience delivering complex programmes in regulated environments.

**If you use this framework in your work, attribution is required:**  
*"7 Operational Layers of RWA Programmes — Biljana Obradović, Concept360, 2026"*

---

## Want to Go Deeper?

**💼 Consulting**  
**Concept360 supports organisations entering regulated RWA programmes.  
**[Concept360](https://concept360.my.canva.site/)
--**-

## Licence

Published under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.  
You may use, adapt, and share this material — with attribution:  
*"Biljana Obradović, Concept360, 2026 — [https://github.com/Biobradovic/rwa-delivery-framework]*

---

*© Biljana Obradović · Concept360 · Belgrade, 2026*  
*[linkedin.com/in/biljanaobradovic](https://www.linkedin.com/in/biljana-obradovic-28390a8/) · [concept360.rs](https://concept360.my.canva.site/)*
