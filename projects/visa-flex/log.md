# Visa Flex

## Also Known As
* Zilch Flex

## Context

### Overview
Strategic project leveraging **Visa's Flexible Credentials (VFC)** to dynamically route transactions between consumer and commercial BINs. Allows Zilch to optimise interchange revenue while simplifying the customer experience to a single consumer credential.

### Business Case
**Hypothesis:** If we integrate with Visa's Flexible Credential solution, we will increase in-store interchange revenue, because we can seamlessly route transactions between consumer and commercial BINs, earning commercial interchange rates on eligible in-store transactions from affiliate merchants.

**Problems being solved:**
- Lower interchange on in-store transactions (~30bps consumer vs ~185bps commercial)
- Intra-EEA volume risk (Visa plans to restrict commercial BINs for non-affiliated EEA merchants)
- Complex card infrastructure (different credentials for online vs in-store)

**Financial impact:**
| Metric | Current | With Visa Flex |
|--------|---------|----------------|
| Blended Interchange Rate | 93bps | 110bps |
| Monthly GMV Uplift | - | **£300K** |

### Technical Approach
**Self-Serve model:**
- Consumer cards become **primary credentials** (exposed to customers)
- Each primary links to a **secondary commercial credential** (hidden)
- Zilch dynamically routes "in-network" (affiliate merchant) transactions to commercial credential during authorisation

**BIN Configuration:**
| BIN Type | BIN | Flex Role | Use Case |
|----------|-----|-----------|----------|
| Consumer Credit | 44135387 | Primary | Mobile wallets, in-app, physical card |
| Commercial Corporate (C) | 44136916 | Secondary | Hidden credential for in-network transactions |
| Commercial Purchasing (P) | 44135388 | Not Flex-compatible | Legacy COF transactions only |

### Timeline
| Phase | Timeline | Status |
|-------|----------|--------|
| Exploration & Discovery | Jul - Sep 2025 | ✅ Completed |
| Planning | Oct 2025 | ✅ Completed |
| Solution Design | Oct - Dec 2025 | ✅ Completed |
| Contractuals | Oct - Nov 2025 | 🔄 In Progress |
| Build & Development | Dec 2025 - Mar 2026 | 🔄 In Progress |
| Visa Testing | Mar 2026 | ⏳ Planned |
| Certification | Apr 2026 | ⏳ Planned |
| Launch + Migration | May 2026 | ⏳ Target: 30 Apr 2026 |

**Effort estimate:** 4 sprints (1 iteration)
**Team dependencies:** Issuer, Purchase, Retain, **Merchant**

### Pending Items
- EHI Interface changes from Thredd
- PEI details
- Reporting changes for Zilch
- VFC eligibility indicator behaviour (sticky vs per-transaction)
- Refund/reversal handling when secondary credential is blocked

### Costs (TBC)
- Visa Flexible Credential product utilisation cost
- Visa Project Resource: ~$30K ($5K/month)
- Thredd Project Resource costs
- FIME Apple certification cost
- New BIN costs

### Key Confluence Pages
- [PRD: Visa Flex (Draft)](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4971888685/PRD+Visa+Flex+Draft)
- [Zilch Flex - Project Charter](https://payzilch.atlassian.net/wiki/spaces/BCP/pages/4628250690/Zilch+Flex)
- [Visa Flex Credentials](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4687855684/Visa+Flex+Credentials)
- [Visa Flex - Outstanding Questions](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/5027725355/Visa+Flex+-+Outstanding+questions)

## Personnel

- Sean Hederman (ExCo Sponsor)
- Saurabh Raman (Project Owner)
- Andrea Ponte Martins (Product GM)
- Kevin Came (Engineering Lead)
- External partners: Visa, Thredd, Apple, Google, Samsung, Fime

## Running Notes

### 2026-02-05

Project log created.

**Affiliate definition query** — responded to question on how to identify affiliated retailers:
- No simple binary flag exists
- Model uses Retailers linked to Affiliates
- A Retailer is "affiliated" if:
  - Linked to an Affiliate
  - Link is marked active (not inactive or blocked)
  - Not linked to the 'No Affiliate' placeholder
- **Open question**: Do all Affiliates in the database qualify for Visa Flex purposes? E.g. Amazon is linked to its own 'Amazon' Affiliate — may not meet the commercial interchange definition.
