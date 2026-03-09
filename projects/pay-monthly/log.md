# Pay Monthly

## Also Known As

Pay Monthly, Po6, Po12

## Slack
#pay-monthly-delivery

## Jira
**Initiative:** [ZILCH-48758 — Pay Monthly](https://payzilch.atlassian.net/browse/ZILCH-48758) (P1, reported by Kevin Came)

**Child epics:**
| Epic | Team | Status |
|---|---|---|
| [ZILCH-48609](https://payzilch.atlassian.net/browse/ZILCH-48609) — [Purchase] Pay Monthly – MVP | Purchase | In Dev |
| [ZILCH-48650](https://payzilch.atlassian.net/browse/ZILCH-48650) — [Payments] Pay Monthly 3m/6m/12m | Payments (Craig Main) | In Dev |
| [ZILCH-48762](https://payzilch.atlassian.net/browse/ZILCH-48762) — Decisioning - Pay Monthly | Decisioning | In Dev |
| [ZILCH-48764](https://payzilch.atlassian.net/browse/ZILCH-48764) — Onboarding - Pay Monthly | Onboarding | In Dev |
| [ZILCH-48859](https://payzilch.atlassian.net/browse/ZILCH-48859) — Merchant - Pay Monthly | Merchant | In Dev |
| [ZILCH-48896](https://payzilch.atlassian.net/browse/ZILCH-48896) — Issuer - Pay Monthly | Issuer | Proposed |
| [ZILCH-48898](https://payzilch.atlassian.net/browse/ZILCH-48898) — Acquirer - Pay Monthly | Acquirer | Proposed |
| [ZILCH-48945](https://payzilch.atlassian.net/browse/ZILCH-48945) — [Retain] Pay Monthly & Visa Flex | Retain | Proposed |
| [ZILCH-49153](https://payzilch.atlassian.net/browse/ZILCH-49153) — [Purchase] Pay Monthly – post-MVP | Purchase | Proposed |

**Merchant epic stories ([ZILCH-48859](https://payzilch.atlassian.net/browse/ZILCH-48859)):**
| Ticket | Summary | Status | Assignee |
|---|---|---|---|
| [ZILCH-48897](https://payzilch.atlassian.net/browse/ZILCH-48897) | Extend retailer schema to support credit rewards | Ready for Testing | Jacek |
| [ZILCH-48903](https://payzilch.atlassian.net/browse/ZILCH-48903) | Enhance Admin Portal: credit reward config & simplify debit rewards | In QA | Jacek |
| [ZILCH-48905](https://payzilch.atlassian.net/browse/ZILCH-48905) | Add static rewards for new Po6/Po12 credit purchases | Ready for Dev | Unassigned |
| [ZILCH-48906](https://payzilch.atlassian.net/browse/ZILCH-48906) | Add dynamic rewards for new Po6/Po12 credit purchases | Created | Unassigned |
| [ZILCH-49027](https://payzilch.atlassian.net/browse/ZILCH-49027) | Add distributed fee (tranches) support to fee calculation | In Dev | Jacek |
| [ZILCH-49087](https://payzilch.atlassian.net/browse/ZILCH-49087) | [Admin Portal] Update 360Profile for Pay Monthly products | Created | Unassigned |

## Context

Pay Monthly allows customers to spread fees across monthly instalments, extending Zilch's BNPL model with longer-term payment options. The strategic goals are reducing voluntary churn and creating a new loan product to help acquisition.

**Deadline:** End of March 2026 — shared with EWA/Extra and Visa Flex. Likely driven by the need to land these products before the start of the new financial year.

**Launch plan:** Pay over 3–12 months with a rolling fee initially, with a repayment date to be added later. Minimum MVP design, with known room for improvement (e.g. transaction screen).

**Loan product codes:** Readable format settled on — e.g. `payIn7Over6m1of7dwn`. Proposed by Tomasz Michalski; refined with input from Arled Kola and Jan Michalak.

**Fee model:**
- Jacek Zanko (Merchant) proposed a "tranche" concept: fee-service returns a fee breakdown by instalment. Reviewed and approved across teams. Tomasz Surowiec requested the API be exposed in Stoplight for review first.
- Fee cap is based on the monthly fee amount and the customer's credit limit. No EHI changes required if fee-service only returns the monthly fee amount.
- **Fee calculation decision (confirmed 2026-03-04):** The canonical rate is **1.6% per instalment** (Option B). The 20.8% total is an implied/derived figure. This matches how fees are communicated to customers across all surfaces. Tom Wood confirmed; Tamara Quinn documented; Andrzej Lorenz requested cross-team communication and acknowledgement (including Data and Finance).

**Billing service:** Marek Chodak has proposed improvements: configurable multiple billing runs per day, faster and more scalable, decoupled from Customer Service. Andrzej noted A/B testing as a benefit. Impact of rolling fee on billing run is under discussion.

**Events Aggregator:** Part of the Purchase Message Decomposition work, not a Merchant concern. Tomasz Surowiec asked Abhishek Chatterjee and Saeed Aghaee to produce an ADR for an Events Aggregator that aggregates three events using `purchaseId` or `correlationId` to generate a summary event for customer notifications. Kinesis + Flink agreed as the solution; Tomasz has written the ADR and design doc in Confluence. DEVOPS-42 (migrated to ZILCH-48712) was raised to create a monorepo for Flink apps — marked as Done.

**Apple Checkout / Product Lineup:** Pay Monthly introduces a risk to the existing Po3 product on Apple Checkout. Tamara Quinn proposed temporarily removing Po3, Po6m, and Po12m from Apple Checkout for Pay Monthly customers, with a plan to restore quickly as a follow-up.

**Tracking:** Kevin Came set up a Jira board and dashboard to track progress across teams.

### Cross-team responsibilities (per Andrea Ponte)
- **Decisioning** — eligibility
- **Payments** — billing, recon API, loan product configuration
- **Merchant** — fee-service, retailer schema, rewards enablement, admin portal changes (admin portal is not critical path — could go to market without it in a pinch)
- **Onboarding** — credit limit changes (Michał Górny, Chris Walker)

### Cross-team dependencies
- **Pending Rewards** — intersection raised by Tamara Quinn at a Merchant refinement meeting on 20 Feb. Implications not yet resolved.
- **EHI** — dependency on EHI supporting new fee response format from fee-service (Grzegorz Ziemiański).
- **Stoplight** — API to be exposed there for cross-team review before implementation.

## Personnel

- Tom Wood — Head of Product (sponsor / product definition)
- Andrea Ponte Martins — Product GM (cross-team coordination, stories)
- Kevin Came — Product Delivery Manager (Jira board, tracking)
- Zac Barclay — Product Manager (Merchant)
- Nicklas Chapman — Engineering Manager (Merchant)
- Jacek Zanko — Back End Engineer, Merchant (fee tranche approach)
- Craig Main — Payments (recon API)
- Marek Chodak — Payments (billing service)
- Tamara Quinn — Senior PM, Purchase (Apple Checkout / product lineup)
- Grzegorz Ziemiański — (EHI / fee capping)
- Tomasz Surowiec — (Events Aggregator lead, API review)
- Abhishek Chatterjee — (Events Aggregator ADR)
- Saeed Aghaee — (Events Aggregator ADR)
- Tomasz Michalski — (Loan product codes)
- Michał Górny — Onboarding (credit limit)
- Chris Walker — Onboarding (credit limit)
- Andrzej Lorenz — VP Engineering (billing run discussion)
- Mariusz Maciuszek — (fee tranche review)

## Running Notes

### 2026-01-14 – 2026-02-23 (from #pay-monthly-delivery digest)

- Tom Wood shared Miro board with the team.
- Product vision established: rolling fee for 3–12 months initially, repayment date to follow.
- Marek Chodak proposed billing service improvements; Andrzej noted A/B testing benefit.
- Loan product configuration concern raised — instalment calculation different for Pay Monthly; discussed whether it could come from loan-service.
- Loan product codes proposed by Tomasz Michalski; settled on readable format (e.g. `payIn7Over6m1of7dwn`).
- Fee capping approach agreed: based on monthly fee and credit limit; no EHI changes needed.
- Apple Checkout concern raised by Grzegorz Ziemiański around impact on Po3; Tamara Quinn proposed temporary removal for Pay Monthly customers.
- Jacek Zanko proposed tranche approach for fee-service API; approved across teams. Tomasz Surowiec requested Stoplight exposure first.
- Events Aggregator ADR tasked to Abhishek Chatterjee and Saeed Aghaee (Purchase domain / message decomposition — not a Merchant concern). Kinesis + Flink agreed; ADR written by Tomasz Surowiec. DEVOPS-42 raised for a Flink monorepo.
- Kevin Came set up Jira board and dashboard.
- Cross-team technical responsibilities mapped by Andrea Ponte.
- Credit limit work tracked by Michał Górny and Chris Walker (Onboarding).

### 2026-02-23

- Received Pay Monthly ticket links from Zac Barclay. Flagged as ready to work up ahead of sprint 11.4 planning.

### #pay-monthly-delivery Channel Digest (2026-02-23 to 2026-03-04)

**MVP product configuration (Acquirer):** Michał Górny / Acquirer team considering two options for the Pay Monthly MVP — no decision made. Open questions include: whether Po3 stays intact for existing customers while new customers get the new monthly configuration; and what happens to customers already on Po3 if migrated. Grzegorz Ziemiański also asked whether the plan is to add Po6/Po12 or remove Po3 from pay monthly eligible customers. Tamara Quinn updated the requirements document (https://payzilch.atlassian.net/wiki/spaces/ZP/pages/5100863491/Purchase+Pay+Monthly) to include both options.

**Credit limit on downgrade from Po12m:** If a customer loses access to Po12m, the credit limit decreases by the outstanding loan amount — same logic as the current Po3m product. Agreed by Tomasz Surowiec, Tamara Quinn, and Tom Wood. Tommy Kwok clarified that downgrades are only done manually by the risk team, typically when a customer enters a repayment plan.

**Fee presentation in the UI:** Jacek Zanko proposed that the fee service returns the total fee broken down into tranches, and the UI displays the effective rate of the first unpaid tranche rounded to 1 decimal place. Andrea Ponte and Craig Main agreed — the rounding difference should still result in a monthly fee of ≥ 1.6% when rounded to 1dp. Michał Ptaszek raised whether the first instalment percentage should be displayed even once it's been paid. (Note: this discussion preceded and informed the Option A/B decision confirmed later the same period — see below.)

**Ledger / accounting approach (MVP):** Tomasz Surowiec raised whether Pay Monthly fees should be stored as part of the purchase or as a separate loan fee. Decision: keep current approach for MVP — monthly fees (except the first) stored in the FEE column in the ledger, not split between purchase and loan. Rationale: minimise changes and risk.

### 2026-03-04

**Merchant team responsibilities clarified:**
1. Enable rewards for credit purchases with the Pay Monthly loan product
2. Enable fee-service to calculate fees on a monthly-instalment basis (as opposed to the single-instalment model used by other loan products)

**Fee calculation method confirmed (via Slack):**
Jacek Zanko asked for final confirmation on which fee calculation approach to implement. Two options were considered:
- **Option A:** Calculate total fee as `amount × 20.8%`, then split across tranches (already implemented)
- **Option B:** Calculate each instalment fee as `amount × 1.6%`, multiply by 13 tranches to derive total

Following discussion between Tamara Quinn, Nicklas Chapman, and Tom Wood, **Option B was confirmed as correct**. The reasoning: 1.6% is the rate communicated to customers in comms, the app, the calculator, and the ECJ — it is the de facto contractual commitment. 20.8% is an emergent total, not the stated figure. Tom Wood confirmed; Tamara Quinn documented. Andrzej Lorenz requested the decision be communicated to and acknowledged by all teams, including Data and Finance. Tamara Quinn has confirmed she will handle this broadcast.

### 2026-03-05

- **ZILCH-49027** (Jacek) — Requires further design conversations following yesterday's confirmation of Option B (1.6% per instalment) as the source of truth for fee calculation. The implementation approach needs to be validated against this decision before progressing.
- **ZILCH-48897 & ZILCH-48903** — Ossie tested on 4 March as planned. Found issues; Jacek fixed; returned to QA.

**fee-service API design debate (Slack, two parallel threads):**
Nicklas proposed replacing the tranche array with a single per-instalment fee value (1.6%), arguing: (1) all tranche values are identical given the source-of-truth decision, making the array redundant; (2) the tranche model encodes instalment-count domain knowledge into fee-service, creating poor separation of concerns; (3) retailer-level suppression is far simpler to configure with a scalar than with 13 tranches per retailer.

Andrzej pushed back: the Revolving Line project (on hold) has requirements for varying fee values per instalment. Pivoting now would close that door and require future cross-team rework. His position: retain tranches.

Tom Wood: reluctantly comfortable descoping per-instalment variation for now. Confirmed the immediate new requirement is retailer-level fee suppression (not per-instalment variation), and that Zac has confirmed this can be handled manually in the current setup.

Grzegorz Ziemiański: challenged whether the new requirements actually necessitate a payload change, arguing tranches can fulfil them. Raised the input question: fee-service currently receives `credit extended` (purchase amount after rewards deducted, accounting for 0 down) — not the instalment amount. Confirmed as correct by Nicklas.

Tomasz Surowiec: supportive of the simpler single-value approach; also removes work on his side and is supported out of the box for ECJ.

In a parallel thread, Craig Main joined and raised concern about the timing of any API change. He shared the existing agreed tranche JSON contract and flagged that Andrzej had previously instructed it be left unchanged. Nick Holt clarified the contract was still a proposal and not yet merged; Craig accepted this and asked for the final contract once agreed.

**Partial refund — new scope identified:** Tom Wood confirmed that if a partial refund is made, the fee for the remaining instalments must be recalculated based on the reduced principal (`principal - refund amount`). Andrzej noted this is new scope, not previously considered. A debate followed on how fee-service should handle this:
- Nicklas proposed either (1) calculate once at loan creation and recalculate on refund event, or (2) calculate per instalment on each billing run. Option 2 avoids a dedicated recalculation event but may require storing a fee calculation reference per instalment on the ledger.
- Andrzej raised audit concerns: the `fee_calculation_reference` field on the customer ledger is intended to tie a fee to its calculation. Multiple calculations mid-loan would produce multiple references, complicating the audit trail.
- Jacek proposed calling fee-service once per instalment so each gets its own clean `fee_calculation_id`.
- Nicklas proposed a further refinement: store the fee calc ID per instalment on the ledger, and leave it to Payments to decide whether to calculate once at loan creation and reuse the ID, or calculate afresh each time. This decouples fee-service API design from billing run implementation choices.

Thread ended with Nicklas asking Craig Main whether individual instalments are recorded as separate ledger entries — unanswered in the transcript.

**Late update (4:39–4:49 PM):** Andrzej confirmed there will be a FEE ledger entry for these fees, meaning the fee calculation reference can be stored there. Nicklas responded suggesting this indicates convergence towards a scalar value applied on a per-instalment basis, recalculated as needed to accommodate partial refunds. No explicit confirmation yet.

**Status:** Trending towards agreement. Scalar per-instalment model with recalculation on partial refund appears to be the emerging direction, with ledger storage of the fee calculation reference resolving the audit concern. Craig Main's input still outstanding — he works in South Africa and is done for the day. Thread resumes tomorrow.

### 2026-03-02

- ZILCH-49027 (fee service support for monthly instalment fees) added to the Merchant board while I was away. Accepted as additional scope in sprint 11.4 without dropping equivalent points — Jacek believes he has capacity.

### 2026-03-06

- **ZILCH-49027** rejected after considerable work. Rejection based on the new plan for fees (the evolving API design settled after the tranche/scalar debate of 2026-03-05). Asked Jacek to create a new Jira ticket for adding a new fee schedule, reflecting the agreed approach.
- **ZILCH-48897** (Jacek) — in review.
- **ZILCH-48873 & ZILCH-48954** (Tom) — in progress.
- Pay Monthly tickets worked up and in play for sprint 11.4.
- Jacek updating tests to check for updated version; only expects updated DTOs in the appropriate version (ZILCH-48897 — in progress).
- **April pricing changes impact:** Michał Górny confirmed that the Purchase team can complete the April pricing scope by end of next sprint, but this will delay PayMonthly work by approximately one sprint. Items deferred: Credit Multiplier, ECJ, Purchase Comms.
