# Pay Monthly

## Also Known As

Pay Monthly, Po6, Po12

## Slack
#pay-monthly-delivery

## Context

Pay Monthly allows customers to spread fees across monthly instalments, extending Zilch's BNPL model with longer-term payment options. The strategic goals are reducing voluntary churn and creating a new loan product to help acquisition.

**Launch plan:** Pay over 3–12 months with a rolling fee initially, with a repayment date to be added later. Minimum MVP design, with known room for improvement (e.g. transaction screen).

**Loan product codes:** Readable format settled on — e.g. `payIn7Over6m1of7dwn`. Proposed by Tomasz Michalski; refined with input from Arled Kola and Jan Michalak.

**Fee model:**
- Jacek Zanko (Merchant) proposed a "tranche" concept: fee-service returns a fee breakdown by instalment. Reviewed and approved across teams. Tomasz Surowiec requested the API be exposed in Stoplight for review first.
- Fee cap is based on the monthly fee amount and the customer's credit limit. No EHI changes required if fee-service only returns the monthly fee amount.

**Billing service:** Marek Chodak has proposed improvements: configurable multiple billing runs per day, faster and more scalable, decoupled from Customer Service. Andrzej noted A/B testing as a benefit. Impact of rolling fee on billing run is under discussion.

**Events Aggregator:** Tomasz Surowiec has asked Abhishek Chatterjee and Saeed Aghaee to produce an ADR for an Events Aggregator that aggregates three events using `purchaseId` or `correlationId` to generate a summary event. Flink identified as the leading option.

**Apple Checkout / Product Lineup:** Pay Monthly introduces a risk to the existing Po3 product on Apple Checkout. Tamara Quinn proposed temporarily removing Po3, Po6m, and Po12m from Apple Checkout for Pay Monthly customers, with a plan to restore quickly as a follow-up.

**Tracking:** Kevin Came set up a Jira board and dashboard to track progress across teams.

### Cross-team responsibilities (per Andrea Ponte)
- **Decisioning** — eligibility
- **Payments** — billing, recon API, loan product configuration
- **Merchant** — fee-service, retailer schema, admin changes
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
- Events Aggregator ADR tasked to Abhishek Chatterjee and Saeed Aghaee; Flink identified as leading option.
- Kevin Came set up Jira board and dashboard.
- Cross-team technical responsibilities mapped by Andrea Ponte.
- Credit limit work tracked by Michał Górny and Chris Walker (Onboarding).

### 2026-02-23

- Received Pay Monthly ticket links from Zac Barclay. Flagged as ready to work up ahead of sprint 11.4 planning.

### 2026-03-02

- ZILCH-49027 (fee service support for monthly instalment fees) added to the Merchant board while I was away. Accepted as additional scope in sprint 11.4 without dropping equivalent points — Jacek believes he has capacity.
- "Work up Zac's Pay Monthly tickets ahead of sprint 11.4 planning" remains an open task.
- Jacek updating tests to check for updated version; only expects updated DTOs in the appropriate version (ZILCH-48897 — in progress).
