# Log

## 2026-03-10

* Completed the KB Restructure project. First full compaction cycle finished: project digests, incident digests, people digests, and activity.md all populated from log entries up to 2026-02-24. Log entries for that period removed. Task closed.

## 2026-03-09

### DevOps Retro

- Two main themes: broken build/deploy pipelines, and delivery pressure and work intake.
- Pipeline failures: volume of failures has increased because CD adoption has driven a large increase in deploy frequency; failure *rate* is not necessarily higher. Team are often first port of call for diagnosis. Some structural problems (e.g. IP exhaustion) are solvable but the team rarely get time to make fixes. Team feel they are required to work at Platform level — boundary with Platform team remains unclear.
- Delivery pressure: multiple work streams all treating DevOps as top priority. Requests arrive via desk walk-ups and DMs, bypassing proper intake. Team cautious about over-formalising but recognise informal intake doesn't scale.
- Mitigations agreed for pipeline failures: use open questions to gently push diagnosis responsibility back to engineers; redirect DMs to #tech-devops; channel larger project requests through EM.
- Mitigations agreed for work intake: require Jira tickets for walk-up requests (immediate small tasks at discretion); move DM conversations to #tech-devops for visibility; large project requests to come through EM; be sensitive to delivery context and over-communicate during high-pressure periods.
- Personal actions: monitor #tech-devops more closely; respond to [Andrzej Lorenz](./people/andrzej-lorenz.md)'s pipeline concerns with appropriate context.
- [Phil Stevenson](./people/phil-stevenson.md) pushed back on the work intake formalisation proposal — expressed an emotional preference for informal, responsive working.
- Retro notes written up and shared with the DevOps team.
- Write-up reviewed and analysed with AI: insights generated on pipeline failure framing, CD project context, planned capacity model, work intake mitigations, and [Phil Stevenson](./people/phil-stevenson.md)'s pushback. Observations logged to devops-process project and people files.

### Merchant Retro

Merchant team retro held. Notes to be added.

### [April Pricing Changes](./projects/april-price-changes) — Cross-Team Refinement

Cross-team refinement session held for FE tickets under [ZILCH-49226](https://payzilch.atlassian.net/browse/ZILCH-49226) ([April Pricing Changes](./projects/april-price-changes) epic). This work is not normally Merchant's responsibility but is being picked up to allow other teams to remain focused on [EWA/Extra](./projects/ewa-extra) and [Pay Monthly](./projects/pay-monthly).

### EC-2083 — customer-web-legacy Production Deployment

[George Sharpe](./people/george-sharpe.md) confirmed release is proceeding, having obtained approval from [Rob Nelson](./people/rob-nelson.md) and [Andrzej Lorenz](./people/andrzej-lorenz.md).

### Stand-ups — Merchant and DevOps

Both stand-ups held. No notes taken.

### 1:1 — [Ossie Nwokedi](./people/ossie-nwokedi.md)

- EC-2083: updated [Ossie Nwokedi](./people/ossie-nwokedi.md). [George Sharpe](./people/george-sharpe.md) has been chased and is on it.
- [Stefan Amarie](./people/stefan-amarie.md) joining: [Ossie Nwokedi](./people/ossie-nwokedi.md) is interested to see how [Stefan Amarie](./people/stefan-amarie.md) works and is aware of the learning opportunity, but hasn't given it much thought yet.
- [Rory Fielding](./people/rory-fielding.md) situation: touched on briefly. Considered resolved and in the past.
- AI usage: [Ossie Nwokedi](./people/ossie-nwokedi.md) is getting significant value from AI tooling. Shared an example where he picked up a defect ticket, asked AI to analyse possible causes, and was told the defect had already been fixed a few hours earlier — highlighting a communication gap between engineers rather than an unresolved defect.

## 2026-03-06

### 1:1 — [Piotr Niebylski](./people/piotr-niebylski.md)

- Personal: his wife's operation was postponed. She is well in the meantime. [Piotr Niebylski](./people/piotr-niebylski.md) will need to work from home ahead of the operation to minimise pathogen exposure. Hans Zimmer concert still something they're looking forward to.
- ZOE spike (ZILCH-44576): last remaining blocker is that the customer verification service won't start. Cause unknown — configuration appears correct. Has asked the rest of the team for assistance.
- Zephyr Zero: up and running, except for a VGS issue. QAs continue to find issues for the team to work through.
- Off-piste pattern: gave feedback. [Piotr Niebylski](./people/piotr-niebylski.md) took it well. Acknowledged there may be adjustment needed to the new process and that he should get into the habit of raising Jira tickets for work.

### Flash Report — Merchant Team

- First [Tastecard](./projects/tastecard) membership cancellation files sent to Ello via automated system.
- First set of transaction data sent to Partnerize for [Intelligent Commerce](./projects/intelligent-commerce) via automated system.
- Defects fixed: broken deeplinks to category pages; status banner not showing consistently; upstream vulnerability on mixpanel integration lambda.
- Audited front-end codebase for merchant-owned feature flags to tidy up.

### Flash Report — DevOps Team

- [EWA](./projects/ewa-extra) (payout-service): Crossplane configured on Sensitive Data Environment for SNS/SQS deployment; RDS proxy deployed to SDE staging and dev; WireMock deployed and configured on SDE staging and dev; SDE cluster RBAC updated to grant QA access to dev and staging; payout-service deployed.
- Flink Apps repository and infrastructure configuration (event aggregation).
- Resolved question with AWS regarding shortcode for SMS.
- [Ephemeral Environments](./projects/ephemeral-environments): E2E test config added.

### DevOps Stand-Up

- Skipped. Three hours of back-to-back meetings made attendance impractical.

### Slack — #april-pricing-changes / Purchase Refinement

- Fee-service rollout stats shared by [Grzegorz Ziemiański](./people/grzegorz-ziemianski.md): 23% EHI / 77% [fee-service](./projects/fee-service), 80 timeouts over 4 weeks, 99.997% success rate. [Andrzej Lorenz](./people/andrzej-lorenz.md) greenlit moving 100% to [fee-service](./projects/fee-service).
- Invited to Purchase refinement by [Tamara Quinn](./people/tamara-quinn.md); joined ~10 minutes late.
- [Michał Górny](./people/michal-gorny.md) confirmed Purchase scope: hardcoded fee values (FE web + mobile), ECJ pricing (FE web + mobile), PO3 calculator fee cap (£40 → £80), test updates.
- Dependency flagged: Storefront adaptive header is sourced from [fee-service](./projects/fee-service) on the Merchant side.
- Purchase scope achievable by end of next sprint but will delay PayMonthly work by approximately one sprint.
- [Andrzej Lorenz](./people/andrzej-lorenz.md) asked whether [Ossie Nwokedi](./people/ossie-nwokedi.md) could help Purchase with ECJ to protect PayMonthly timeline; [Michał Górny](./people/michal-gorny.md): workable if ECJ experience is there, but adds complexity.
- [Michał Górny](./people/michal-gorny.md) proposed FE-only alternative (no BE dependency on pricing changes): preserves PayMonthly timeline but introduces tech debt — no single source of truth for fee calculation. [Andrzej Lorenz](./people/andrzej-lorenz.md) acknowledged we are already in this situation; directed [Tamara Quinn](./people/tamara-quinn.md) to document it as a known system limitation and potential blocker for future pricing changes.
- Responded to [Andrzej Lorenz](./people/andrzej-lorenz.md) re: [Ossie Nwokedi](./people/ossie-nwokedi.md): [Ossie Nwokedi](./people/ossie-nwokedi.md) is currently on [Pay Monthly](./projects/pay-monthly) Admin Portal work; [Jacek Zanko](./people/jacek-zanko.md) could cover that, potentially freeing [Ossie Nwokedi](./people/ossie-nwokedi.md) for Purchase. Feasible given the [fee-service](./projects/fee-service) simplification. Committed to a definitive answer by end of day.
- [Michał Górny](./people/michal-gorny.md) to post an options summary to #april-pricing-changes.
- Confirmed: Merchant team will own the fee changes for April pricing.

### Slack — #merchant-firefighter

- [Tomasz Więckowski](./people/tomasz-wieckowski.md) (Decisioning) created [ZILCH-49269](https://payzilch.atlassian.net/browse/ZILCH-49269) — "Setup fee code fc-extra-monthly" — for the Merchant team, flagging it as needed for [EWA](./projects/ewa-extra) (Zilch Advance) and requesting prioritisation for the coming sprint.
- Responded confirming it would be pushed to the top of the backlog.

### Merchant Stand-Up

- **ZILCH-42041** ([Jacek Zanko](./people/jacek-zanko.md)) — Unblocked. Confirmation received that existing backups are sufficient.
- **ZILCH-48536** ([Nick Holt](./people/nick-holt.md)) — Listener set up for product change events. Deploying to pre-prod. Looking good.
- **ZILCH-45502** ([Ossie Nwokedi](./people/ossie-nwokedi.md)) — Brought back into sprint, having been dropped earlier to make way for another ticket. Ready for review.
- **ZILCH-49027** ([Jacek Zanko](./people/jacek-zanko.md)) — Rejected after considerable work. Decision based on new plan for fees. Asked [Jacek Zanko](./people/jacek-zanko.md) to create a Jira ticket for adding a new fee schedule.
- **ZILCH-48897** ([Jacek Zanko](./people/jacek-zanko.md)) — In review.
- **ZILCH-48873 & ZILCH-48954** ([Tom McKenzie](./people/tom-mckenzie.md)) — In progress.

## 2026-03-05

### DevOps Stand-Up

**Reactive board:**
- Security vulnerability tickets in To-Do — [Phil Stevenson](./people/phil-stevenson.md) does not think they should sit with DevOps. [Nick Gilbert](./people/nick-gilbert.md) has said he would handle them on his return ([Nick Gilbert](./people/nick-gilbert.md) is currently away).
- ZILCH-49091 — in progress with [Phil Stevenson](./people/phil-stevenson.md).
- ZILCH-41286 — unclear what it's for or whether [George Sharpe](./people/george-sharpe.md) is handling it; need to catch up with [George Sharpe](./people/george-sharpe.md). [Jira: "Create a fix version and apply it to tickets in release scope on merge of a release-please PR" — assigned to [George Sharpe](./people/george-sharpe.md), In Dev. Part of the CD automation work. [Phil Stevenson](./people/phil-stevenson.md) to confirm whether [George Sharpe](./people/george-sharpe.md) is actively progressing it.]
- ZILCH-45505 — on hold, low priority (consistent with decision at [Phil Stevenson](./people/phil-stevenson.md)'s 1:1 on 2026-03-04).
- Noted: ambiguity about what the Sign Off stage on the reactive Kanban board is for. Process needs clarifying.
- ZILCH-49094 — deployment already done but sitting in To-Do; moved to the correct column.

**Planned board:**
- ZILCH-48462 ([Phil Stevenson](./people/phil-stevenson.md)) — in progress but blocked by his duty rota rotation. Will return if reactive load allows.
- ZILCH-48446 — awaiting [Nick Gilbert](./people/nick-gilbert.md)'s return.
- ZILCH-47186 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk.md)) — moved to Done.
- ZILCH-48966 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk.md)) — needs final verification before closing. Blocked on staging; waiting on a role to be set up.
- ZILCH-48967 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk.md)) — moved to Done.
- ZILCH-48715 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk.md)) — DevOps work done; Terraform merge still outstanding. Closed.
- ZILCH-44576 ([Piotr Niebylski](./people/piotr-niebylski.md)) — spike dragging; finding lots of issues. Expected to complete by end of day.

**[Piotr Niebylski](./people/piotr-niebylski.md) (ZILCH-44576):** Sense that [Piotr Niebylski](./people/piotr-niebylski.md) is using the spike as cover to do [Ephemeral Environments](./projects/ephemeral-environments) work he wants to do. Will push for better adherence to the new process — work he considers necessary should be raised as proper tickets and planned in. Aligns with existing appraisal observation that he goes off piste.

### EC-2083 — customer-web-legacy Production Deployment Blocked

Raised with [George Sharpe](./people/george-sharpe.md) that EC-2083 (Production Deployment — customer-web-legacy-1.176.0) has been sitting in Planning since 24 February — 9 days — despite containing merged work from six teams including Merchant (ZILCH-40343).

Pulled from Jira:
- **Ticket:** EC-2083 — auto-created by Jira automation on 24 Feb 2026
- **Status:** Planning (still open)
- **Assignee:** [Ossie Nwokedi](./people/ossie-nwokedi.md)
- **Teams affected:** Payments (ZILCH-48454), Purchase (ZILCH-47884, ZILCH-37894), Retain (ZILCH-46362), Onboarding (ZILCH-45932), Merchant (ZILCH-40343)

Reason for the stall is not yet established. Raised with [George Sharpe](./people/george-sharpe.md) to investigate.

### Merchant Stand-Up

Ticket updates:
- **ZILCH-42041** — [Jacek Zanko](./people/jacek-zanko.md) hasn't chased the platform ticket; still pending.
- **ZILCH-48536** ([Nick Holt](./people/nick-holt.md)) — Making do with a sub-optimal event requiring a callback to product-service rather than a fully enriched event. Putting tests around it. Wants to catch up with [Tom McKenzie](./people/tom-mckenzie.md) on test strategy, especially to cover both LD flag settings.
- **ZILCH-47174** — Should be unblocked now that [Tom McKenzie](./people/tom-mckenzie.md) is back at work. [Tom McKenzie](./people/tom-mckenzie.md) will review.
- **ZILCH-48897 & ZILCH-48903** ([Jacek Zanko](./people/jacek-zanko.md)) — [Ossie Nwokedi](./people/ossie-nwokedi.md) tested yesterday as planned. Found issues; [Jacek Zanko](./people/jacek-zanko.md) fixed; back for more testing.
- **ZILCH-49027** ([Jacek Zanko](./people/jacek-zanko.md)) — Requires further design conversations following yesterday's decision on source of truth for [Pay Monthly](./projects/pay-monthly) fees.
- **ZILCH-48954** — Requires another PR to be merged before it can be re-tested.
- **ZILCH-48873** — [Tom McKenzie](./people/tom-mckenzie.md) will look at it today.

Actions:
- Asked [Tom McKenzie](./people/tom-mckenzie.md) to ensure ZILCH-48954 and ZILCH-48873 both have parent epics (currently missing).
- Announced [Iteration 12](./projects/iteration-12-planning) planning will be a lightweight process, to avoid distracting from the March 31 deadline.
- Announced introduction of `@merchant-firefighter` for the Merchant duty rota.

Other notes:
- [Zac Barclay](./people/zac-barclay.md) briefly hinted at new requirements. [Nick Holt](./people/nick-holt.md) went straight into solutionising mode, well ahead of any clear requirements being established.
- [Jacek Zanko](./people/jacek-zanko.md) announced that affiliate-integration-service has made its **first production call to Partnerize** — a significant milestone; the service was still not operational as of 3 March.

### Merchant Firefighter Rota — Slack App Set Up

Set up a duty rota for the Merchant team in a Slack app. The person on duty can be tagged via `@merchant-firefighter`.

### 1:1 — [Tom McKenzie](./people/tom-mckenzie.md)

Meeting cut short — not much to discuss and I had not prepared.

**Defect backlog:**
The team's defect backlog is growing when it should be shrinking. The root issue identified: defects are not being properly triaged when they come in. Without triage, there is no mechanism to determine whether a defect requires urgent attention in a near sprint or can safely wait.

**Decision:** [Tom McKenzie](./people/tom-mckenzie.md) to own defect triage. He will be responsible for assessing incoming defects and advocating for their priority in pre-refinement meetings.

I have a Jira cumulative flow report for defects. Will monitor it and expect to see defect numbers begin to decline as a result of this change.

### DevOps Refinement Meeting

Attended but arrived late — pulled into other conversations beforehand. Struggled to maintain focus on the specific tickets being refined, but provided adequate facilitation of the process. Facilitation is still needed while the team beds in the new hybrid Scrum/Kanban approach.

### [fee-service](./projects/fee-service) Design — [Pay Monthly](./projects/pay-monthly) — Slack Discussion (Design Debate)

A design debate across two parallel Slack threads (cross-team, including [Andrzej Lorenz](./people/andrzej-lorenz.md), [Grzegorz Ziemiański](./people/grzegorz-ziemianski.md), [Tomasz Surowiec](./people/tomasz-surowiec.md), Tom Wood, [Mariusz Maciuszek](./people/mariusz-maciuszek.md), [Abhishek Chatterjee](./people/abhishek-chatterjee.md), [Marek Chodak](./people/marek-chodak.md), [Craig Main](./people/craig-main.md), [Sam Whittaker](./people/sam-whittaker.md), [Jacek Zanko](./people/jacek-zanko.md), [Nick Holt](./people/nick-holt.md)) around whether to change the [fee-service](./projects/fee-service) API design for [Pay Monthly](./projects/pay-monthly).

**Thread 1 — tranche vs. scalar**

**Proposal (Nicklas):** Replace the tranche array with a single per-instalment fee value (1.6%), with retailer-level overrides where suppression is needed. Rationale:
- With 1.6% as the source of truth, all values in the tranche array are identical by definition — the array is redundant.
- The tranche model builds in poor separation of concerns: it requires [fee-service](./projects/fee-service) to know the number of instalments, which is domain knowledge it shouldn't need.
- Retailer suppression is much cleaner to configure with a single value per retailer vs. 13 tranches per retailer.
- Callers would be responsible for applying the fee across each instalment rather than relying on [fee-service](./projects/fee-service) to return a pre-expanded array.

**Pushback ([Andrzej Lorenz](./people/andrzej-lorenz.md)):** Keep the original tranche model. Future requirements (specifically from the Revolving Line project, currently on hold) may need different fee values for different instalments. Pivoting now would close that door and require new cross-team development later.

**Tom Wood:** Reluctantly comfortable descoping per-instalment variation for now, but wants it noted that he is reluctant. Confirmed that the incoming requirement is specifically about being able to reduce the 1.6% for specific retailers and loan types — not about varying by instalment. [Zac Barclay](./people/zac-barclay.md) has confirmed retailer suppression can already be handled in the current setup (manually for now).

**[Grzegorz Ziemiański](./people/grzegorz-ziemianski.md):** Challenged the premise — argued the tranche model can fulfil all the stated requirements. Asked what the input to [fee-service](./projects/fee-service) should be: purchase amount or instalment amount?

**[Tomasz Surowiec](./people/tomasz-surowiec.md):** Supportive of the single-value approach; removing per-instalment complexity also removes work on his side, and the simpler response is supported out of the box for ECJ.

**Input clarification:** [Grzegorz Ziemiański](./people/grzegorz-ziemianski.md) confirmed that [fee-service](./projects/fee-service) currently receives `credit extended` (the purchase amount after deducting rewards, accounting for 0 down payment) — not the instalment amount. This was confirmed as correct by Nicklas (the whole loan principal, not just one instalment's share).

**Thread 2 — [Craig Main](./people/craig-main.md) joins; refund scope surfaces**

[Craig Main](./people/craig-main.md) joined the discussion expressing concern about the timing of a potential API change, requesting the new contract and risk mitigations as quickly as possible. He shared the existing agreed tranche JSON contract and noted that [Andrzej Lorenz](./people/andrzej-lorenz.md) had previously said to leave it unchanged.

[Nick Holt](./people/nick-holt.md) clarified that the tranche contract was still a proposal and had not yet been merged; [Craig Main](./people/craig-main.md) accepted this and reiterated his request for the final contract once agreed.

A new and material scope item emerged: **partial refunds**. Tom Wood confirmed that if a partial refund is made, the fee for the remaining instalments must be recalculated against the reduced principal (i.e. `principal - refund amount`). [Andrzej Lorenz](./people/andrzej-lorenz.md) flagged this as new scope — not previously considered.

**Debate on refund handling approach:**
- **Nicklas** proposed two options: (1) calculate the fee once at loan creation and recalculate if a refund event occurs; (2) calculate per instalment on each billing run, so each instalment naturally reflects the current principal. Nicklas noted that option 1 introduces a recalculation event, whereas option 2 avoids one — but option 2 may require storing a fee calculation reference per instalment on the ledger.
- **[Andrzej Lorenz](./people/andrzej-lorenz.md)** raised a concern about the audit trail: the `fee_calculation_reference` field on the customer ledger is intended to record which fee calculation produced a given fee. If fees are recalculated mid-loan, there would be multiple references — this creates ledger complexity.
- **[Jacek Zanko](./people/jacek-zanko.md)** proposed calling [fee-service](./projects/fee-service) once per instalment, so each instalment gets its own `fee_calculation_id`. This keeps the audit trail clean and is consistent with how the billing service already operates.
- **Nicklas** proposed a further clarification: store the fee calculation ID per instalment in the ledger, and leave it to Payments to decide whether to calculate once at loan creation and reuse that ID per instalment, or calculate fresh on each instalment. This separates [fee-service](./projects/fee-service) API concerns from billing run decisions.

The thread ended without resolution, with Nicklas putting a direct question to [Craig Main](./people/craig-main.md) about whether individual instalments are currently recorded as separate entries in the ledger. The question was unanswered in the transcript.

**Late update (4:39–4:49 PM):** [Andrzej Lorenz](./people/andrzej-lorenz.md) confirmed that there will be a FEE ledger entry for these fees, meaning the fee calculation reference can be stored there. Nicklas responded suggesting this points towards convergence: a scalar value applied on a per-instalment basis, recalculated as needed to accommodate partial refunds. No explicit confirmation yet — [Craig Main](./people/craig-main.md)'s input still awaited.

**Overall outcome:** Trending towards agreement on a scalar per-instalment model with recalculation on partial refund, with the ledger providing the audit trail. Pending [Craig Main](./people/craig-main.md)'s input (he is based in South Africa and has finished for the day — thread will resume tomorrow).

### [fee-service](./projects/fee-service) Design — [Pay Monthly](./projects/pay-monthly) (x2 meetings)

Two meetings today on [fee-service](./projects/fee-service) design in support of the [Pay Monthly](./projects/pay-monthly) project. Notes to follow.

### Pricing Structure Changes — [Steve Rayko](./people/steve-rayko.md) Conversations

Pulled into conversations by [Steve Rayko](./people/steve-rayko.md) (SVP Engineering) regarding planned pricing structure changes. [Steve Rayko](./people/steve-rayko.md) wanted to understand what would be involved in implementing them.

Key points established:
- **Deadline:** End of March 2026 — adding to the existing cluster of end-of-month P1 deliveries ([Pay Monthly](./projects/pay-monthly), [EWA/Extra](./projects/ewa-extra), [Visa Flex](./projects/visa-flex)).
- **Back-end:** Changes can be accommodated through configuration — no code changes required on the back end.
- **UX:** Some UX work may be required, but this would sit outside the Merchant team.
- **Team ownership — open question:** It is not yet decided whether Merchant would pick this work up or whether it would be handled by [Michal Baran](./people/michal-baran.md) and the new Spend Platform team.

The team ownership question has material implications for Merchant sprint capacity, which is already under significant pressure. The configuration-only back-end scope may appear lightweight, but landing anything at end of March — when three concurrent P1 initiatives are converging — adds risk. Worth monitoring closely.

## 2026-03-04

### March Delivery Pressure

[Pay Monthly](./projects/pay-monthly), [EWA/Extra](./projects/ewa-extra), and [Visa Flex](./projects/visa-flex) all share an end-of-March 2026 deadline — likely driven by the need to land all three before the start of the new financial year. Three concurrent P1 initiatives is significant delivery pressure across the organisation.

### [Pay Monthly](./projects/pay-monthly) — Channel Digest Ingested (2026-02-23 to 2026-03-04)

Key new information from #pay-monthly-delivery:
- **MVP product configuration still undecided** — Acquirer team (Michał Górny) considering two options; open questions around Po3 continuity for existing customers and migration scenarios
- **Credit limit on Po12m downgrade:** decreases by outstanding loan amount, same as Po3m; downgrades manual, done by risk team
- **Fee UI presentation:** fee service returns tranches; UI shows effective rate of first unpaid tranche, rounded to 1dp — agreed by Andrea Ponte and [Craig Main](./people/craig-main.md)
- **Ledger approach (MVP):** monthly fees (except the first) stored in the FEE column; not split between purchase and loan

### [EWA/Extra](./projects/ewa-extra) — Channel Digest Ingested

Ingested a summary of the #ewa-extra Slack channel. Key new information (beyond what was previously logged):
- ITAM to cover manual activities; a Tier 2 customer care team identified as needed for admin portal gaps
- Plaid API keys for AIS and Payouts to be segregated for security
- [EWA](./projects/ewa-extra) eligibility: Plaid confidence score for name matching; monthly salary-based income sources only; largest source selected; Plaid responses stored in S3
- Initial rollout: active customers, no hard blocks; excludes Plus members and [Pay Monthly](./projects/pay-monthly) test customers
- £3 disbursement fee confirmed as **not** included in APR; APR assessment still required across all product lines; whether fee should be capped is unresolved
- App submission to Apple and Google targeted for **31 March 2026**

### [EWA/Extra](./projects/ewa-extra) — Fee Schedule Ownership and Merchant Scope

Merchant's involvement in [EWA/Extra](./projects/ewa-extra) is confirmed as minimal: UI component testing to verify components work correctly for the new Extra membership tier. No delivery responsibility beyond that.

**Fee schedule ownership (via Slack):**
Following the ambiguity raised on 2026-02-23, [Andrzej Lorenz](./people/andrzej-lorenz.md) responded:
- Fee-service (and possibly rewards) move to Spend Platform will **not happen yet**
- New Spend Platform team **could** handle [EWA](./projects/ewa-extra)/[Pay Monthly](./projects/pay-monthly) fee schedules; [Andrzej Lorenz](./people/andrzej-lorenz.md) said to assume they would, pending planning discussion
- Rewards service ownership: **not decided yet**

Despite this steer, ZILCH-49156 ([EWA](./projects/ewa-extra) disbursement fee code) landed with Merchant, raised by [Tommy Kwok](./people/tommy-kwok.md) and [Oleksandr Tertyshnyi](./people/oleksandr-tertyshnyi.md). Nicklas has asked [Andrzej Lorenz](./people/andrzej-lorenz.md) to confirm whether Merchant or Spend Platform should own it. Awaiting response.

### [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) Promotion — Slack Discussion with [Andrzej Lorenz](./people/andrzej-lorenz.md)

[Andrzej Lorenz](./people/andrzej-lorenz.md) reviewed the L3 evidence document sent earlier today. Key outcomes from the discussion:

- **Growth Potential concern:** [Andrzej Lorenz](./people/andrzej-lorenz.md) pushed back on "Uses feedback to improve" being evidenced only by the annual appraisal response. He clarified the criterion relates to ongoing, day-to-day feedback responsiveness. Verbal examples provided: (1) reduction in handholding from [Piotr Niebylski](./people/piotr-niebylski.md) and [Phil Stevenson](./people/phil-stevenson.md) — [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) is now operating much more independently; (2) sustained improvement in speaking up during team meetings following feedback on this; (3) active engagement with recent Scrum/Kanban process formalisation following feedback to lean in to process more.

- **[Andrzej Lorenz](./people/andrzej-lorenz.md)'s conclusion:** [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) is performing at L3 level. The remaining unevidenced criteria in Growth Potential are not disqualifying. [Andrzej Lorenz](./people/andrzej-lorenz.md) will take the case to [Steve Rayko](./people/steve-rayko.md).

- **Action:** [Andrzej Lorenz](./people/andrzej-lorenz.md) requested an executive (TL;DR) summary of L3 performance. Summary authored and sent to [Andrzej Lorenz](./people/andrzej-lorenz.md).

- **Rating:** Target outcome is promotion to L3 with a rating of 3.

### [Pay Monthly](./projects/pay-monthly) — Fee Calculation Decision Confirmed

A decision was confirmed via Slack (originally raised by [Jacek Zanko](./people/jacek-zanko.md), resolved through discussion involving [Tamara Quinn](./people/tamara-quinn.md), Tom Wood, and Nicklas Chapman, with [Andrzej Lorenz](./people/andrzej-lorenz.md) requesting broadcast):

**Decision: Option B — 1.6% per instalment is the canonical fee rate.**

- The fee for each instalment is calculated as: `purchase amount × 1.6%`
- The total lifetime fee (20.8%) is an implied/derived figure, not the primary one
- This aligns with how fees are communicated to customers in-app, in emails, in the ECJ, and in the calculator
- Tom Wood confirmed; [Tamara Quinn](./people/tamara-quinn.md) documented
- [Andrzej Lorenz](./people/andrzej-lorenz.md) requested this be communicated to all teams (including Data and Finance) and acknowledged — [Tamara Quinn](./people/tamara-quinn.md) has confirmed she will own this broadcast

The earlier-implemented Option A (calculate 20.8% total, then split across tranches) is **not** the chosen approach. The [fee-service](./projects/fee-service) implementation should use 1.6%.

### [Pay Monthly](./projects/pay-monthly) — Refinement Complete (previously)

[Pay Monthly](./projects/pay-monthly) tickets (from [Zac Barclay](./people/zac-barclay.md)) were worked up prior to today and are in play for sprint 11.4.

Also noted: the Merchant team's responsibilities for [Pay Monthly](./projects/pay-monthly) span two areas:
1. Enable rewards for credit purchases with the [Pay Monthly](./projects/pay-monthly) loan product
2. Enable [fee-service](./projects/fee-service) to calculate fees on a monthly-instalment basis (rather than single-instalment as with other loan products)

### [Iteration 12](./projects/iteration-12-planning) — Chased [Zac Barclay](./people/zac-barclay.md) on Candidates

Chased [Zac Barclay](./people/zac-barclay.md) on candidate work streams for [Iteration 12](./projects/iteration-12-planning). Response suggests he doesn't yet know what the team will be pointed at.

### Tech Leadership Sync

Nothing significant to note.

### [Pay Monthly](./projects/pay-monthly) Tech Sync

Attended. Nothing significant to note.

### [Phil Stevenson](./people/phil-stevenson.md) 1:1

Largely a venting session — [Phil Stevenson](./people/phil-stevenson.md) needed to articulate his concerns more than he needed specific actions taken. The broad theme was pressure, process, and friction with cross-team engineers.

**Quality:** Less of an acute problem than it appeared. [Phil Stevenson](./people/phil-stevenson.md) was able to push back on [Radek Kachel](./people/radek-kachel.md)'s changes as a codeowner and got the outcome he wanted. Quality is in hand.

**[Radek Kachel](./people/radek-kachel.md) / [EWA](./projects/ewa-extra) pattern:** The real concern is a recurring pattern of poor communication and cooperation from [Radek Kachel](./people/radek-kachel.md) — unwillingness to engage through proper channels and reluctance to act on review feedback. Will raise with [Grzegorz Ziemiański](./people/grzegorz-ziemianski.md) and [Nikos Sofianos](./people/nikos-sofianos.md) framed as a light-touch question about whether they've observed any friction, rather than a direct escalation.

**Unrealistic expectations on DevOps:** [Phil Stevenson](./people/phil-stevenson.md) perceives a persistent belief — particularly in the [EWA](./projects/ewa-extra) project — that DevOps should do things on demand. This has some historical basis. Advised him to counter it by leaning into the newly formalised process: when work slips because higher-priority reactive items were pulled in, point to the sprint record and Jira evidence; when people expect immediate reactive delivery, point to the Kanban board and WIP limits to show them they're in a queue; and if anything genuinely needs reprioritising over in-flight work, requesters should come to me — that's an EM decision.

**Observation:** [Phil Stevenson](./people/phil-stevenson.md) gets frustrated when he's concerned quality may suffer or when he senses friction with other engineers. Some friction is inevitable: engineers are under pressure to deliver quickly; DevOps want things done properly. That tension is natural and can be productive. [Phil Stevenson](./people/phil-stevenson.md) is aware of this at an intellectual level but still finds it stressful in practice.

### Merchant Stand-up

[Tom McKenzie](./people/tom-mckenzie.md) remains off sick.

* ZILCH-48952 — Brought into sprint yesterday; awaiting build and release. Marked as done.
* ZILCH-46769 — With [Ossie Nwokedi](./people/ossie-nwokedi.md). [Nick Holt](./people/nick-holt.md) has reviewed. Needs test evidence before it can move forward.
* ZILCH-42041 — [Jacek Zanko](./people/jacek-zanko.md) assigned to himself and responded to [Charlie Hurst](./people/charlie-hurst.md) (Platform). Now awaiting action from Platform.
* ZILCH-46367 — Completed yesterday.
* ZILCH-49076 — With [Nick Holt](./people/nick-holt.md). Blocked on the Decisioning team's PR. Risk of slipping beyond the sprint. A workaround using a different event exists but could introduce a race condition. [Nick Holt](./people/nick-holt.md) will chase Decisioning on the PR's status. E2E testing will also be required. Assessed as at-risk.
* ZILCH-47174 — With [Ossie Nwokedi](./people/ossie-nwokedi.md). Awaiting sign-off from [Tom McKenzie](./people/tom-mckenzie.md), who is on sick leave.
* ZILCH-48897 — With [Jacek Zanko](./people/jacek-zanko.md). Also awaiting [Tom McKenzie](./people/tom-mckenzie.md).
* ZILCH-48903 — With [Jacek Zanko](./people/jacek-zanko.md). Also awaiting [Tom McKenzie](./people/tom-mckenzie.md). [Ossie Nwokedi](./people/ossie-nwokedi.md) offered to test in [Tom McKenzie](./people/tom-mckenzie.md)'s absence.
* ZILCH-49027 — Awaiting clarification from Product.
* ZILCH-48873 & ZILCH-48954 — With [Tom McKenzie](./people/tom-mckenzie.md); awaiting his return.

### DevOps Stand-up

[Nick Gilbert](./people/nick-gilbert.md) not mentioned; presumably still on leave.

**Planned:**
* ZILCH-48462 — [Phil Stevenson](./people/phil-stevenson.md); still in progress.
* ZILCH-44576 — Still in progress with [Piotr Niebylski](./people/piotr-niebylski.md).
* ZILCH-48966 & ZILCH-48967 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) making good progress; expected to complete today.

**Reactive:**
* [Phil Stevenson](./people/phil-stevenson.md) occupied with support. Several issues with ZILCH-49113. ZILCH-49091 in progress.

### [New Web](./projects/new-web) — Pen Testing Requirements Discussion (Slack)

Slack exchange with [Chris Walker](./people/chris-walker.md) and [Phil Stevenson](./people/phil-stevenson.md) regarding the [New Web](./projects/new-web) sprint work and pen testing readiness.

**Background:** [New Web](./projects/new-web) sprint work (likely ZILCH-47773 or related) is at risk due to high-priority [EWA](./projects/ewa-extra) tasks being pulled in. [Chris Walker](./people/chris-walker.md) was informed proactively.

**[Chris Walker](./people/chris-walker.md)'s request:** That DevOps and the Security team (secteam) agree and document what needs to be done before pen testing can begin. [Chris Walker](./people/chris-walker.md) referenced that Julien (sec team) had said the environment should be "as close to prod as possible". [Chris Walker](./people/chris-walker.md) is concerned about ending up unable to get security sign-off because something wasn't tested.

**[Phil Stevenson](./people/phil-stevenson.md)'s view:** Testing in staging should be sufficient; DevOps are not planning major changes and any issues found would likely require changes anyway.

**Outcome:** [Chris Walker](./people/chris-walker.md) is comfortable with [Phil Stevenson](./people/phil-stevenson.md)'s position but wants it confirmed in writing by the Security team.

**Action required:** Arrange agreement — ideally written — between DevOps and the Security team on the pen testing environment requirements for [New Web](./projects/new-web) (staging acceptable vs. prod-like required).

## 2026-03-03

### [EWA](./projects/ewa-extra) Team — DevOps Engagement

[Phil Stevenson](./people/phil-stevenson.md) flagged via Slack that the [EWA](./projects/ewa-extra) project team (including [Radek Kachel](./people/radek-kachel.md)) are performing DevOps work themselves rather than engaging via the tech-devops channel, and are showing reluctance to take suggestions on PRs. [Phil Stevenson](./people/phil-stevenson.md) supports them doing the work but wants it done properly through the right channels. He attributes the behaviour to pressure from elsewhere.

Responded to [Phil Stevenson](./people/phil-stevenson.md) and agreed to discuss further at tomorrow's 1:1 (4 Mar).

[Phil Stevenson](./people/phil-stevenson.md) also forwarded a Slack exchange (17:37) in which [George Sharpe](./people/george-sharpe.md) (Change Manager) contacted [Phil Stevenson](./people/phil-stevenson.md) and [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) directly to chase progress on 4 [EWA](./projects/ewa-extra) tickets assigned to DevOps. [Phil Stevenson](./people/phil-stevenson.md)'s response: "blocked on number of hours in the day and devops engineers at zilch." [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) confirmed ZILCH-48967 is done and ZILCH-48966 will be done today. [Phil Stevenson](./people/phil-stevenson.md) noted that some of the work had only surfaced that day; [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) confirmed ZILCH-49094 and ZILCH-49091 are new additions. [Phil Stevenson](./people/phil-stevenson.md) shared this with Nicklas as evidence of undue pressure and concern about the impact on quality. To discuss at tomorrow's 1:1.

### [Merchant Operations](./projects/merchant-operations) — Observability Documentation Structure

Agreed approach for documenting observability work under ZILCH-47400. Observability documentation will live in DataDog where DataDog supports it (dashboard descriptions, monitor messages, etc.). Exception: functional metrics per service have no natural home in DataDog, so these will be documented in Confluence. Structure: one page per service under a new "Observability" parent page in the Merchant Confluence space, covering functional metrics, normal ranges, and associated context. [fee-service](./projects/fee-service) to be the first page created.

### [Merchant Operations](./projects/merchant-operations) — [fee-service](./projects/fee-service) Audit

Continued the [Merchant Operations](./projects/merchant-operations) workstream. Completed the DataDog audit of [fee-service](./projects/fee-service) — a significant time investment, constituting a large portion of the day. Key finding: [fee-service](./projects/fee-service) has no prod logs — debug logging was disabled as a cost optimisation without the EM's knowledge. Confirmed by [Jacek Zanko](./people/jacek-zanko.md). This is consistent with the pattern noted in his appraisal of things happening under the radar.

See `projects/merchant-operations/audit-fee-service.md` for full findings.

### Sprint Change — Merchant

* [Ossie Nwokedi](./people/ossie-nwokedi.md) requested to bring ZILCH-48952 ("Deeplinks to category pages aren't working") into the sprint. Approved on the condition that something was swapped out. ZILCH-45502 ("Large volume of error logs from featured tile query when product line not yet loaded") moved out to make room.

### Merchant Stand-up

* ZILCH-46769 — [Ossie Nwokedi](./people/ossie-nwokedi.md) picked up; now in PR.
* ZILCH-42041 — Response received from Platform via PO-1597. [Charlie Hurst](./people/charlie-hurst.md) can ensure backup is in place (see ticket comments). [Nick Holt](./people/nick-holt.md) suggests that however backup is implemented, it should be retained indefinitely.
* ZILCH-46367 — [Ossie Nwokedi](./people/ossie-nwokedi.md) has completed.
* ZILCH-48536 — Progressing with [Nick Holt](./people/nick-holt.md). Finance sign-off on the approach still outstanding. Decisioning not providing the events needed for feature changes; [Nick Holt](./people/nick-holt.md) has pointed them to the relevant part of the codebase. Decisioning's work is blocked by a refactor branch pending merge, and they are also occupied with [EWA](./projects/ewa-extra) work. Decisioning pushing back on the need for the change. Need to lean in to resolve this.
* ZILCH-47600 — [Ossie Nwokedi](./people/ossie-nwokedi.md) has in PR. Tests confirm working behaviour and are gated in CI. Issue was never reproduced. Ready to close off.
* ZILCH-48887 — [Jacek Zanko](./people/jacek-zanko.md) reports [Tom McKenzie](./people/tom-mckenzie.md) has started building tests. Ready from [Jacek Zanko](./people/jacek-zanko.md)'s perspective. [Tom McKenzie](./people/tom-mckenzie.md) is on sick leave.
* ZILCH-49027 — [Jacek Zanko](./people/jacek-zanko.md) just picking up.
* ZILCH-48954 — In progress with [Tom McKenzie](./people/tom-mckenzie.md); no update as [Tom McKenzie](./people/tom-mckenzie.md) is on sick leave.

### DevOps Stand-up

[Nick Gilbert](./people/nick-gilbert.md) still on leave.

**Planned:**
* ZILCH-44576 — [Piotr Niebylski](./people/piotr-niebylski.md) working through issues.
* ZILCH-48967 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) fixed issues with Wm and added to helm chart.
* ZILCH-48966 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) created RBAC permissions. Blocked by one missing secret.
* ZILCH-48715 — Discussion, details hard to follow. [Phil Stevenson](./people/phil-stevenson.md) making a point about the distinction between what the team owns and how they manage it: SNS/SQS should be managed through Crossplane, not Terraform.
* ZILCH-48462 — Not progressed; [Phil Stevenson](./people/phil-stevenson.md) is on rota duty.
* ZILCH-49042 — Not progressed; [Phil Stevenson](./people/phil-stevenson.md) is on rota duty.
* ZILCH-45505 — [Phil Stevenson](./people/phil-stevenson.md) has the script done; needs team review. [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) has reviewed. [Phil Stevenson](./people/phil-stevenson.md) subsequently shared the script ([tools PR #98](https://github.com/zilchdev/tools/pull/98)) and an example change ([customer-service PR #3759](https://github.com/zilchdev/customer-service/pull/3759)) in Slack, and asked for sign-off from [Piotr Niebylski](./people/piotr-niebylski.md) and Nicklas before running it across all repos. [Piotr Niebylski](./people/piotr-niebylski.md) approved. Nicklas deferred — needs more context before signing off; will discuss at tomorrow's 1:1 with [Phil Stevenson](./people/phil-stevenson.md).
* ZILCH-48446 — [Nick Gilbert](./people/nick-gilbert.md) dropped this when he went on leave. [Phil Stevenson](./people/phil-stevenson.md) to pick up where [Nick Gilbert](./people/nick-gilbert.md) got to.

**Process observation:** ZILCH-48446 highlights a gap in leave handover practice. [Phil Stevenson](./people/phil-stevenson.md) should not have to piece together where [Nick Gilbert](./people/nick-gilbert.md) got to — outgoing team members need to hand over in-progress work clearly before going on leave.

### Refinement Session — Merchant

Ran a refinement session with the Merchant team. One ticket discussed.

### Interviews

Two interviews were scheduled today. The first candidate was a no-show — interview scrapped. Later in the day, stood in for [Mike Davis](./people/mike-davis.md) at a second interview. Candidate was not suitable. Write-up pending.

### Merchant Support Rota — Hand-over

Attended the Merchant support rota hand-over meeting. Now on duty for the first week.

## 2026-03-02

* Returned to work after a few days off. Catching up via Slack.

* [Incident-467](./incidents/incident-467.md) — rewards comms/eligibility mismatch. See [Incident-467](./incidents/incident-467.md). Status: Stable. Root cause: `rewards-service` correctly skipped reward for ineligible customers, but `customer-service` missed the signal and published `Loan_OnLoanComplete_ENRICHED`, which `notification-service` consumed and acted on. Fix deployed 27 Feb by [Rory Fielding](./people/rory-fielding.md) (Retain) — comms turned off pending proper resolution. Root cause fix owned by Retain (ZILCH-48940). Retrospective to be jointly led by Merchant and Retain. Incident commander: Mark Reddington. [Tom McKenzie](./people/tom-mckenzie.md) tagged me in the channel this morning — reason unknown.

* [Stefan Amarie](./people/stefan-amarie.md) onboarding — drafted first 1:1 agenda ([content-authoring/output/stefan-first-1-1-agenda.md](content-authoring/output/stefan-first-1-1-agenda.md)). Ingested [Steve Rayko](./people/steve-rayko.md)'s informal L5 IC expectations document; logged [Rob Nelson](./people/rob-nelson.md)'s position on the FE competency lead question ([Chris Walker](./people/chris-walker.md) retains for now, review once [Stefan Amarie](./people/stefan-amarie.md) is settled). Created Incident-166 record ([Incident-166](./incidents/incident-166.md)) — background, significance, mitigations, and link to ZILCH-47400.

* [On-Call Rota](./projects/on-call-rota) review meeting. [Chris Prowse](./people/chris-prowse.md) walked through the toolchain; worked through most alerts from the fortnight to 2 March. Several actions identified — see [On-Call Rota](./projects/on-call-rota).

* [Andrzej Lorenz](./people/andrzej-lorenz.md) requested evidence to support the rating of 2 given to [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) in his appraisal. Responded via Slack with a structured justification covering all four dimensions of the staff levels framework, with Jira evidence drawn from ZILCH and DEVOPS projects across the full year, and a summary of his cross-team support activity. Working notes in [content-authoring/output/lukasz-appraisal-justification.md](content-authoring/output/lukasz-appraisal-justification.md).

### Slack catch-up (23 Feb – 2 Mar)

Relevant items extracted from AI channel summaries:

**[Incident-467](./incidents/incident-467.md) (engineering-application-support):**
* [Mike Davis](./people/mike-davis.md) requested [Nick Holt](./people/nick-holt.md) and [Jacek Zanko](./people/jacek-zanko.md) to raise the incident.
* Root cause confirmed as `onesignal-integration` lambda incorrectly triggering notifications for loan completion events where rewards were not applied.
* Mark Reddington: future incidents should be raised directly in Datadog, not via Slack. Incident record updated.

**DevOps / infrastructure (platypus, tech-on-call):**
* [Phil Stevenson](./people/phil-stevenson.md) removed the Upwind admission webhook from production — it was preventing new pods from starting. [Nick Gilbert](./people/nick-gilbert.md) to follow up with Arnar.
* EKS prod cluster upgrades to version 1.33 completed (issuer cluster done; customer cluster scheduled).
* Upwind deployed to production and working (confirmed across team).
* [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) sharing Terraform plans for staging/prod — reviewed and approved by [Matt Swirski](./people/matt-swirski.md) and [Charlie Hurst](./people/charlie-hurst.md).

**Infosec vulnerability tickets (infosec-vulnerability-remediation-tracking):**
* Vulnerable dependency findings in frontend and typescript-shared-library flagged by [Nandini Muraleedharan](./people/nandini-muraleedharan.md).
* Originally assigned to Payments team; [Nandini Muraleedharan](./people/nandini-muraleedharan.md) asking which team has capacity for the frontend ones.
* Connects to the DevOps stand-up concern about security vuln tickets landing on the wrong team.

**[EWA](./projects/ewa-extra) / Plaid (tech-ewa-plaid-open-banking):**
* [Rob Nelson](./people/rob-nelson.md) shared that Plaid will deliver their Income Insights product by 13 March — critical for [EWA](./projects/ewa-extra) short- and long-term plans. [Alastair Gullan](./people/alastair-gullan.md) flagged need for a quick decision on trusting that date.

**[New Web](./projects/new-web):**
* [Chris Walker](./people/chris-walker.md) sent a planning reminder tagging [Nick Gilbert](./people/nick-gilbert.md), [Phil Stevenson](./people/phil-stevenson.md), and me on 23 Feb (before I went on leave).

**dev-payments (today):**
* Deadlock issue blocking the payments team — [Craig Main](./people/craig-main.md) investigating; query optimised but still deadlocking. Ongoing.

**OTA errors / alert-mobile:**
* Elevated OTA errors on mobile-ui — caused by Expo free tier quota being exceeded. [Rory Fielding](./people/rory-fielding.md) and Jan Michalak resolving by re-enabling enterprise subscription.

### DevOps Flash Report — engineer contributions (full report not seen)

Captured from team channel week-notes. No [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) contribution visible in this snippet.

**[Phil Stevenson](./people/phil-stevenson.md):**
- GitHub runners: caching base container images (some performance issues to resolve)
- Ephemeral: database backup and restore improvements
- Fraud: initial fraud AI agent deployed

**[Nick Gilbert](./people/nick-gilbert.md):**
- Upwind deployed to production
- Initial work on certificate management for server-side web app (Crossplane deployed to dev cluster — ACM)
- VGS manually set up for zephyr-zero

**[Piotr Niebylski](./people/piotr-niebylski.md):**
- CI/CD ready deployment for payout-service
- Aggregation flink-apps Terraform ready
- GitHub runners: caching base container images (speeds up build time)
- Ephemeral: database backup/restore from qa-sit into zephyr-zero; new services added; all service versions updated to latest staging; VGS manually set up for zephyr-zero
- Fraud: initial fraud AI agent deployed
- Upwind deployed to production
- Crossplane deployed to dev cluster for server-side web app certificate management

### Merchant Flash Report (sent by [Tom McKenzie](./people/tom-mckenzie.md) in my absence)

[Tom McKenzie](./people/tom-mckenzie.md) sent the weekly Merchant flash report to [Andrzej Lorenz](./people/andrzej-lorenz.md) while I was away. [Andrzej Lorenz](./people/andrzej-lorenz.md) pushed back, characterising it as more of a sprint report than an end-of-week flash report. Report content:

> Morning [Andrzej Lorenz](./people/andrzej-lorenz.md), i've been given the honour of sending over the flash report. As is the case when you have a complete burn down in the previous sprint, this sprint isn't going to necessarily have any early quick wins. Evidenced by the fact that we don't have anything in Done.
> * We're still very much in the early stages of [Pending Rewards](./projects/pending-rewards) development.
> * [Pay Monthly](./projects/pay-monthly): Extending the retailer schema to incorporate credit rewards, as well as the respective admin changes are almost ready for testing.
> * Frontend LD flag audit is in review.
> * Working with Lambdatest to solve failing maestro tests.

### Merchant Stand-up

* ZILCH-46769 — still pending pickup.
* ZILCH-42041 — still blocked by PO-1597. [Charlie Hurst](./people/charlie-hurst.md) on leave; waiting on him.
* ZILCH-46367 — [Ossie Nwokedi](./people/ossie-nwokedi.md) absent from stand-up; no update.
* ZILCH-48536 — [Nick Holt](./people/nick-holt.md) in progress. Blocked: wants an event on feature changes. Considering doing the work himself and sending to Decisioning for review.
* ZILCH-48539 — pending pickup.
* ZILCH-47174 — [Ossie Nwokedi](./people/ossie-nwokedi.md) not present to comment.
* ZILCH-48897 — in progress with [Jacek Zanko](./people/jacek-zanko.md). Updated tests to check for updated version; only expects updated DTOs in the appropriate version.
* ZILCH-48873 — [Tom McKenzie](./people/tom-mckenzie.md) working to resolve with LambdaTest.
* ZILCH-49027 — added to board while I was away. Fee service to support fees split into monthly instalments ([Pay Monthly](./projects/pay-monthly) scope). Accepted as additional scope without dropping equivalent points; [Jacek Zanko](./people/jacek-zanko.md) believes he has capacity.

### DevOps Stand-up

[Nick Gilbert](./people/nick-gilbert.md) on leave.

**Reactive:**
* ZILCH-48881 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md): Done. Moved to Done column. [Phil Stevenson](./people/phil-stevenson.md) moved past Ready for Release.
* ZILCH-41286 — [George Sharpe](./people/george-sharpe.md) asked [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) about a fix. Ticket assigned to [George Sharpe](./people/george-sharpe.md) but should be with DevOps. [Phil Stevenson](./people/phil-stevenson.md) to catch up with [George Sharpe](./people/george-sharpe.md).
* ZILCH-48513, ZILCH-45505 — [Phil Stevenson](./people/phil-stevenson.md) to look at soon.
* Security vuln. tickets — [Phil Stevenson](./people/phil-stevenson.md) questions whether these should sit with DevOps; thinks they belong with the security team. To resolve.

**Planned:**
* ZILCH-47186 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) looking at it.
* ZILCH-48966, ZILCH-48967 — High priority, [EWA](./projects/ewa-extra) project. [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) has under way. Brought into sprint; ZILCH-47583 bumped to accommodate. Estimated at 1 point each.
* ZILCH-44567 — in progress with [Piotr Niebylski](./people/piotr-niebylski.md).
* ZILCH-48462 — [Phil Stevenson](./people/phil-stevenson.md): nearly ready for review; has a PR.
* ZILCH-48416 — Done ([Phil Stevenson](./people/phil-stevenson.md)).
* ZILCH-48075 — [Phil Stevenson](./people/phil-stevenson.md) has spoken to [Nikos Sofianos](./people/nikos-sofianos.md); agreed new approach for caching images. [Phil Stevenson](./people/phil-stevenson.md) to raise a ticket.
* ZILCH-48446 — [Phil Stevenson](./people/phil-stevenson.md) to find out where [Nick Gilbert](./people/nick-gilbert.md) got to and whether it needs progressing.
* ZILCH-47773 — blocked. Need to find out how to create certificates from the security team.

**General:**
* Handover policy agreed: if less than a day's work remains on an in-progress reactive ticket when rotation changes, the current owner can continue rather than handing over.
* Observation: unclear who is on duty for reactive work — [Lukasz Kowalczyk](./people/lukasz-kowalczyk.md) and [Phil Stevenson](./people/phil-stevenson.md) both across both boards. May need better discipline around the duty rota.

* Removed from Waiting On: [Piotr Niebylski](./people/piotr-niebylski.md) 1:1 reschedule — no reschedule materialised; decided not to chase.
* Removed from Waiting On: [Ethan Stockwell](./people/ethan-stockwell.md) data file (visa-flex).
* Removed from Waiting On: [Tom McKenzie](./people/tom-mckenzie.md) test policy document — a Jira task has been created; now a planning matter rather than a chase.

