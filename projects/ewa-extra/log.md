# EWA Extra

## Context
New strategic initiative raised at the Engineering Leadership Sync on 17 Feb 2026. The ask is to deliver an Earned Wage Access (EWA) product tied to a new membership tier called "Extra", by end of March 2026.

Merchant team is unlikely to be heavily involved, but tracking for awareness given it emerged as a strategic pivot.

## Log

### 2026-02-17
* Initiative surfaced at Engineering Leadership Sync meeting. End-of-March deadline. Details on scope and ownership TBC.

### 2026-02-19
* Extra tier confirmed at £2.99/month. EWA will only be available within the Membership structure — not as a standalone product.
* Plaid products to be used: Auth, Assets, and Bank Income Verification.
* Rob Nelson proposed an "ewa-7day" loan product to be created and added to all product-lines, configured as a feature inside the Plus and Extra membership tiers.
* Radek Kachel's move to the Spend Platform team has been postponed until end of March specifically to help de-risk EWA delivery (Payouts component). Decision proposed by Grzegorz Ziemiański; Steve Rayko and Andrzej Lorenz asked for approval.
* Steve Rayko asserted that Pay Monthly is higher priority than EWA. Potentially significant given the EWA urgency — may indicate a limit to how much can be disrupted in service of the EWA deadline.

### 2026-02-20

* Product and planning meeting attended. Project on a tight schedule; tech planning session requested ASAP, before product understanding is fully settled. Tight iteration loop expected.
* ExCo has requested a project plan by end of today, including an engineering plan.
* Zac Barclay delivered a product overview with the following confirmed details:
  * EWA = Earned Wage Access; a monthly salary advance product.
  * Maximum advance: £100 or 20% of net monthly salary — whichever is lower.
  * Tied exclusively to the new "Extra" membership tier at £2.99/month.
  * Not available in the Plus tier. No free trial for Extra.
  * Customers can borrow up to a week before their salary date.
  * £3 disbursement fee on each use.
  * Customer care constraints require demonstrable evidence that the £3 fee is proportionate to handling costs.
  * Open banking required — used to verify evidence of regular salary income.
* Whiteboard exercise conducted to divide work across teams. Outcome for Merchant: no confirmed work, with only the possibility of light UI involvement.
* Confirmed project leadership: Kevin Came (project/delivery), Steve Rayko (engineering), Zac Barclay (product). My role is that of an interested observer — no active ownership.
* The strategic pivot to EWA/Extra caused disruption to the DevOps team this week.

### 2026-02-18
* EWA/Extra meeting. Zac Barclay briefed on the feature — nothing substantially new.
* No work identified for Merchant. I flagged this explicitly and nobody challenged.
* Possible work for DevOps on the open banking side. I asked to be told of any requests ASAP.
  - Rob Nelson thinks the work would be minimal: an OpenBanking integration capability already exists in production, built for earlier initiatives that were mothballed. The capability was never decommissioned.
* Significant product complexity and edge cases still unresolved — particularly around free trials, EWA withholding until first payment, and membership payment lateness. Lots of product refinement still to go.
* Pro not being dropped but is lower priority than EWA/Extra.
* Cross-team lead roles: Product — Zac on Extra, Michael Charash on EWA. Tech — not confirmed; Rob thinks it will be him and Andrzej.
* Rob very concerned about front-end capacity across the department.
* End-of-March delivery target confirmed. Very aggressive.
