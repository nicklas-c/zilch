# EWA Extra

## Also Known As

Earned Wage Access; Zilch Extra; EWA/Extra

## Context
New strategic initiative raised at the Engineering Leadership Sync on 17 Feb 2026. The ask is to deliver an Earned Wage Access (EWA) product tied to a new membership tier called "Extra", by end of March 2026. The deadline is shared with Pay Monthly and Visa Flex — likely driven by the need to land all three products before the start of the new financial year.

Merchant team is unlikely to be heavily involved, but tracking for awareness given it emerged as a strategic pivot.

## References

### Jira

**Initiative:** [ZILCH-48756 — Earned Wage Access and Zilch Extra](https://payzilch.atlassian.net/browse/ZILCH-48756) (P1, In Dev)

**Child epics:**
| Epic | Team | Status |
|---|---|---|
| [ZILCH-48581](https://payzilch.atlassian.net/browse/ZILCH-48581) — Decisioning - EWA via Plaid Open Banking | Decisioning | In Dev |
| [ZILCH-48598](https://payzilch.atlassian.net/browse/ZILCH-48598) — EWA - Bank Payouts MVP | Payments | In Dev |
| [ZILCH-48681](https://payzilch.atlassian.net/browse/ZILCH-48681) — [Payments] Zilch Advance | Payments | In Dev |
| [ZILCH-48810](https://payzilch.atlassian.net/browse/ZILCH-48810) — Create new membership tier for Zilch "Extra" | Unknown | In Dev |
| [ZILCH-48812](https://payzilch.atlassian.net/browse/ZILCH-48812) — [Retain] Memberships - Zilch Extra & EWA | Retain | In Dev |
| [ZILCH-48913](https://payzilch.atlassian.net/browse/ZILCH-48913) — Onboarding - Link Journey - Open Banking Auth & SDK | Onboarding | In Dev |
| [ZILCH-48921](https://payzilch.atlassian.net/browse/ZILCH-48921) — Onboarding - Token Exchange - Open Banking | Onboarding | In Dev |

No Merchant epic — Merchant's involvement is limited to UI component testing for the new Extra membership tier.

## Personnel

*To be populated.*

## Digest

### #ewa-extra Channel Digest (pre-2026-03-04)

**Product requirements areas** (per Michael Charash): Plaid integration, EWA product mechanics, front-end UX, new membership tiers, pricing, finance, data analytics, admin portal, decisioning and fraud. ITAM to cover manual activities (e.g. database updates). A Tier 2 customer care team identified as a need for anything beyond the admin portal.

**Engineering scoping:** Michael Charash asked Andrzej and Rob Nelson to progress with engineering scoping while product discovery was still ramping up. Kevin Came created a delivery document and proposed a workshop for the technical delivery plan (2–3 sprints). Steve Rayko requested high-level wireframes from Michael to inform the plan.

**Plaid / Open Banking:** Steve Rayko shared a response from Plaid's Auth endpoint (tested with his Monzo account). Abhishek Chatterjee provided an overview of Open Banking services: AIS (Account Information Services) and Payouts. Decision: Plaid API keys for AIS and Payouts to be segregated for security.

**Delivery tracking:** Kevin Came created a Jira board and dashboard for EWA/Extra scope and issues (also noted in 2026-02-20 entry). Ozzie Yuce provided an overview of roles and responsibilities, emphasising cross-team alignment and dependency unblocking.

**EWA eligibility (Decisioning):** Alastair Gullan and Tommy Kwok discussed criteria: Plaid confidence score for name matching; income sources limited to monthly salary-based; largest income source selected. Plaid responses to be stored in S3 for auditing. "Crinan" raised questions about what information will be visible to customers and agents regarding the EWA decision.

**Initial rollout criteria** (per Zoe Chen): Active customers with no hard blocks. Excludes current Plus members and customers in the Pay Monthly test. Ozzie confirmed overdue customers handled by the app's blocks logic (no need to exclude explicitly).

**Pricing and compliance:** John Moore and Ozzie confirmed the £3 EWA disbursement fee will **not** be included in the APR calculation. An APR assessment is still required across all product lines, even though no changes are expected. Ozzie raised whether the disbursement fee should be capped — not resolved in this digest.

**App release deadline:** Steve Rayko confirmed deadline extended to end of March to align with the UK monthly pay cycle. Target: submission to Apple and Google on **31 March 2026**.

### 2026-02-17
* Initiative surfaced at Engineering Leadership Sync meeting. End-of-March deadline. Details on scope and ownership TBC.

### 2026-02-18
* EWA/Extra meeting. Zac Barclay briefed on the feature — nothing substantially new.
* No work identified for Merchant. I flagged this explicitly and nobody challenged.
* Possible work for DevOps on the open banking side. I asked to be told of any requests ASAP.
  - Rob Nelson thinks the work would be minimal: an OpenBanking integration capability already exists in production, built for earlier initiatives that were mothballed. The capability was never decommissioned.
* Rob Nelson pushing hard on OB integration — wants a BE engineer to start immediately. Martin Thorlby-Witham suggested reusing the existing open banking service (already has Plaid US components). Rob agreed.
* Significant product complexity and edge cases still unresolved — particularly around free trials, EWA withholding until first payment, and membership payment lateness.
* Pro not being dropped but is lower priority than EWA/Extra.
* Cross-team lead roles: Product — Zac on Extra, Michael Charash on EWA. Tech — not confirmed; Rob thinks it will be him and Andrzej.
* Rob very concerned about front-end capacity across the department.
* End-of-March delivery target confirmed. Very aggressive.
* Phil Stevenson's discomfort with the EWA pivot is not isolated — anecdotal evidence of similar concerns from other ICs and at least one manager. Values-based concern, not just workload.

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

### 2026-02-23

* Sprint retrospective cancelled; time used to work through EWA/Extra with the Merchant team in detail. Assessment: broadly in the clear, with two caveats.
* **Caveat 1 — Fee schedule ownership ambiguity.** With the fee-service migration to the new team running in parallel, it is unclear whether fee schedule changes fall to Merchant or Spend Platform. Working assumption is Spend Platform, but ambiguity needs to be derisked. Messaged Andrzej after CoP Poland; reply expected 24 Feb.
* **Caveat 2 — Overlap with Pending Rewards / Blocking Rewards for Continuity of Memberships.** These are lower priority than EWA/Extra and could be held back to let EWA proceed. However, the new tier and new loan product may need to be accommodated in Merchant systems, with a dependency on the Decisioning team.

### 2026-02-24

* Andrzej responded on fee schedule ownership: still undecided in general, but for EWA/Extra his team (Spend Platform) will handle it.

### 2026-03-04

**Merchant's scope confirmed:** UI component testing for the new Extra membership tier only. No delivery responsibility beyond that.

**Fee schedule ownership — update:**
Following the ambiguity flagged on 2026-02-23, Andrzej replied via Slack. Key points:
- The move of fee-service (and possibly rewards service) to Spend Platform **will not happen just yet**
- Andrzej indicated the new Spend Platform team **could** handle new fee schedules for EWA/Extra and Pay Monthly, and said he'd discuss in planning. Initial steer was to assume Spend Platform would do it.
- Separately, Nicklas raised whether rewards service might also move — Andrzej confirmed **nothing has been decided yet** on that front.

Despite Andrzej's steer, **ZILCH-49156** (Define a fee code for EWA Disbursement Fee) was subsequently raised by Tommy Kwok and Oleksandr Tertyshnyi and landed with Merchant. Nicklas has asked Andrzej to confirm whether Merchant or Spend Platform should own it — **confirmed 2026-03-06: Merchant will own all fee changes**.

The playbook-based ITAM handoff (with Michal Baran supervising initial uses) was also floated as an option by Nicklas.

### 2026-03-06

* Tomasz Więckowski (Decisioning) created [ZILCH-49269](https://payzilch.atlassian.net/browse/ZILCH-49269) — "Setup fee code fc-extra-monthly" — via the #merchant-firefighter channel, with a request to prioritise for the coming sprint. Committed to pushing to the top of Merchant's backlog.
* Fee code ownership confirmed: Merchant will own all fee changes, including ZILCH-49156 and ZILCH-49269.
