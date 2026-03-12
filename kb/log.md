# Log

## 2026-03-12

* Actioned [EC-2182](https://payzilch.atlassian.net/browse/EC-2182) — LaunchDarkly change to enable the "Free Trial" CTA to 50% of customers (replacing "Upgrade" on the membership header). Reported by Zac Barclay. [Memberships](./projects/memberships)
* Rewrote `kb/CLAUDE.md` — restructured the Knowledge Base instructions to be clearer about the AI's role (reading, writing, compacting), introduced entity index files as a formal concept, and removed the "factual and concise" formatting constraint on log entries to keep the log open to richer content including opinions and commentary.
* Authored epic [ZILCH-49461](https://payzilch.atlassian.net/browse/ZILCH-49461) (On-Call Noise Reduction) — cross-team initiative to reduce noisy and unnecessary out-of-hours call-outs from Datadog monitors. Owned by DevOps, under the [On-Call Rota](./projects/on-call-rota) project.

### Merchant Stand-Up

* [ZILCH-49228](https://payzilch.atlassian.net/browse/ZILCH-49228) (ECJ pricing change update — mobile) — [Ossie Nwokedi](./people/ossie-nwokedi): missed some requirements in planning (notice needed on card active screen as well as other specified places). Now in review. [April Price Changes](./projects/april-price-changes)
* [ZILCH-42041](https://payzilch.atlassian.net/browse/ZILCH-42041) (Decommission fee-service MSSQL database) — [Jacek Zanko](./people/jacek-zanko): still waiting on [Charlie Hurst](./people/charlie-hurst). I will chase Charlie and escalate if necessary — want this closed off. [Fee Service](./projects/fee-service)
* [ZILCH-48536](https://payzilch.atlassian.net/browse/ZILCH-48536) (Calculate and store pending rewards for credit purchases) — [Nick Holt](./people/nick-holt): moved to In Review. Has questions about what we should be testing. [Pending Rewards](./projects/pending-rewards)
* [ZILCH-49269](https://payzilch.atlassian.net/browse/ZILCH-49269) (Setup fee code fc-extra-monthly for EWA) & [ZILCH-48793](https://payzilch.atlassian.net/browse/ZILCH-48793) (Fee-service: include fee type and percentage in fetch by calculationId response) — Jacek: will continue today. Set up in pre-prod, will include prod too. Needs changes to fee-service to handle maximum properly — will raise a new ticket for that. [EWA/Extra](./projects/ewa-extra)
* [ZILCH-48873](https://payzilch.atlassian.net/browse/ZILCH-48873) (Fix the receipt banner Maestro test) — [Tom McKenzie](./people/tom-mckenzie): talking to LambdaTest to establish a fix.
* Nick Holt: having successfully sent cancellation files to Ello last week, we should look at setting up the task on an automated schedule. [Tastecard](./projects/tastecard)
* Jacek: will be closing PRs relating to credit rewards — requirements have been simplified (rewards descoped from Pay Monthly). [Pay Monthly](./projects/pay-monthly)
* Tom McKenzie: fee-service timeouts on Prod. EHI service logged them; Lukasz Krauzowicz reported them to us. Jacek: not sure of the cause, but better logging will help diagnose. A ticket to improve logging is already in the sprint. [Fee Service](./projects/fee-service)

### DevOps Stand-Up

* [ZILCH-47773](https://payzilch.atlassian.net/browse/ZILCH-47773) (Prepare environments for customer-web-app deployments) — [Nick Gilbert](./people/nick-gilbert): now has K8s ACM Terraform config working to provision host certificates. [New Web](./projects/new-web)
* [ZILCH-49441](https://payzilch.atlassian.net/browse/ZILCH-49441) (Configure VGS credential secret for zephyrs — new vault) — Nick Gilbert: has the details he needs from [Julien Morvan](./people/julien-morvan), will pick it up today. [Ephemeral Environments](./projects/ephemeral-environments)
* [ZILCH-49315](https://payzilch.atlassian.net/browse/ZILCH-49315) (Diagnose and fix upwind-admission-webhook pulling incorrect image) — Nick Gilbert: stabilised in staging, moving to sign-off.
* [ZILCH-48463](https://payzilch.atlassian.net/browse/ZILCH-48463) (Enable AWS Gateway OpenAPI spec generation and deployment for retailer-service) — [Lukasz Kowalczyk](./people/lukasz-kowalczyk): in progress. His update was hard to follow — a recurring communication issue. Need to think about how to coach him to communicate in a way more appropriate for the audience. [Gateway Service](./projects/gateway-service)
* [ZILCH-47380](https://payzilch.atlassian.net/browse/ZILCH-47380) (Automate Auth0 resource creation) — Lukasz Kowalczyk: in review, will walk the team through it. Again, details were hard to follow.
* [ZILCH-48462](https://payzilch.atlassian.net/browse/ZILCH-48462) (Migrate retailer-service Terraform to use microservice module) — [Phil Stevenson](./people/phil-stevenson): in progress. Concerned about Terraform drift between environments — should raise a ticket for Platform to fix. Open question: why does Platform own this Terraform? It is service-specific, so feels like it belongs at the application level, not infrastructure level.
* [ZILCH-48604](https://payzilch.atlassian.net/browse/ZILCH-48604) (Move Flink app Terraform module to module repo) — Phil: in progress, should be done this morning.
* [ZILCH-49450](https://payzilch.atlassian.net/browse/ZILCH-49450) (New SNS topic for payouts service in SDE) — [Piotr Niebylski](./people/piotr-niebylski): got it working on Dev, now applying in staging and prod. [EWA/Extra](./projects/ewa-extra)
* [ZILCH-49221](https://payzilch.atlassian.net/browse/ZILCH-49221) (Update deployment dashboard to include sensitive services) — Piotr: will pick up as a 5-minute job. [Continuous Deployment](./projects/continuous-deployment)
* [ZILCH-49134](https://payzilch.atlassian.net/browse/ZILCH-49134) (Review number of cronjobs on product clusters) & [ZILCH-49455](https://payzilch.atlassian.net/browse/ZILCH-49455) (RBAC missing for dev to view Crossplane resources) — Piotr raised these into the reactive board.

## 2026-03-11

### [EWA/Extra](./projects/ewa-extra) — #ewa-delivery Channel Digest (4–11 Mar)

New information from Slack digest (179 messages, 30 participants):

**Fee code naming:**
* Agreed fee code for EWA disbursement fee: "ewa-advance" (preferred over "advance-fee" proposed by Marcin Żołna). [Tommy Kwok](./people/tommy-kwok) initially agreed with Marcin's suggestion; I overrode with "ewa-advance".

**Virtual wallet setup:**
* [Abhishek Chatterjee](./people/abhishek-chatterjee) working on virtual wallet setup for Finance, blocked on [PO-1694](https://payzilch.atlassian.net/browse/PO-1694). Handover to Jake Pickup once unblocked, to ensure it's tested and ready from a finance perspective.
* [Grzegorz Ziemiański](./people/grzegorz-ziemianski) needed to add someone as admin to the Plaid team — unsure who from Platform should be added.

**Eligibility and affordability:**
* [Alastair Gullan](./people/alastair-gullan) summarised the decision not to ask customers for their payday — Zilch will choose the day based on decisioning logic, accepting the risks of not aligning to actual payday.
* APR: the £25 Zilch Advance disbursement fee is considered an optional instant disbursal fee and not included in APR (confirmed by Alex Ivison).
* [John Strawhorne](./people/john-strawhorne) and [Tommy Kwok](./people/tommy-kwok) discussed capping logic — Zilch Advance amount based on customer affordability level and downpayment percentage.

**Customer research:**
* [Zac Barclay](./people/zac-barclay) shared survey results: probable unmet need for short-term cash advance, but PMF risks — low product awareness, demand for larger loan amounts than offered, and infrequent expected usage patterns. Controlled pilot planned to address.
* Thomas Peter Breakwell agreed to provide customer IDs for survey responses.

**Frequency cap:**
* [Andrea Ponte Martins](./people/andrea-ponte-martins) proposed basing the frequency cap on calendar month rather than subscription month. Agreed for MVP. Marcin Żołna preferred a lock-out period based on days since last advance, but calendar month accepted as simpler for now.
* Ozzie confirmed: once per calendar month per customer for MVP.

**Income and eligibility requirements:**
* [Tommy Kwok](./people/tommy-kwok) shared updated requirements: minimum £125 per deposit transaction to achieve the £25 Zilch Advance floor. Income source must have a deposit in the last month. Largest value deposit selected regardless of pay frequency.
* No frontend changes — decisioning logic only.

**RCA and customer notification:**
* [Alastair Gullan](./people/alastair-gullan) and John Moore aligned: customers will be notified about the new Zilch Advance feature being added to their existing RCA. No new RCA required. Template email wording from previous notifications to be reused.

**Mobile app release cadence:**
* [George Sharpe](./people/george-sharpe): v2.47.0 (containing Zilch Advance MVP) created from 24 March; testing and rollout from ~30 March; all customers on v2.47.0 by Zilch Advance launch on **13 April**.
* Pay Monthly MVP in v2.46.0. v2.48.0 (Pay Monthly fast-follows) timing TBD to avoid impacting Advance rollout.

**Data tracking:**
* Yasmin Lepech building Looker performance dashboard — three tabs: high-level performance, Extra performance, EWA performance. Meeting with [Rob Nelson](./people/rob-nelson) to scope data ingestion and modelling.

**Rollout planning:**
* ~30K control group alongside test group. Same auto-freeze logic for credit limits applied to both test and control for consistency.
* Zilch Advance and Pay Monthly rollout groups will be **mutually exclusive**.

### [Visa Flex](./projects/visa-flex) — #proj-visa-flex Channel Digest (3 Feb – 11 Mar)

New information from Slack digest (170 messages, 20 participants):

**Technical implementation:**
* [Saurabh Raman](./people/saurabh-raman) shared the team's thinking on changes to authorisation, reporting, and clearing.
* [Abhishek Chatterjee](./people/abhishek-chatterjee) and [Derek McCallum](./people/derek-mccallum) raised concerns around fraud and velocity checks in the proposed changes.
* [Sam Whittaker](./people/sam-whittaker) noted that adding new EHI fields may require Platform team effort.

**Single secondary commercial card proposal:**
* [Derek McCallum](./people/derek-mccallum) proposed using a single shared secondary commercial card for all customers rather than issuing individual cards, to simplify implementation.
* [Abhishek Chatterjee](./people/abhishek-chatterjee) and [Saurabh Raman](./people/saurabh-raman) discussed implications — need to ensure no negative outcomes.

**Certification and testing:**
* [Jakub Pałka](./people/jakub-palka) shared the Visa Flex test plan and approach, including documenting all certification scenarios.
* [Wojciech Mielczarek](./people/wojciech-mielczarek) outlined the customer migration approach — admin endpoints and LaunchDarkly toggles.
* [Sam Whittaker](./people/sam-whittaker) reported the first successful Visa Flex transaction on UAT.

**Retailer list and affiliate identification:**
* [Grzegorz Ziemiański](./people/grzegorz-ziemianski) requested an up-to-date list of in-network retailers from [Zac Barclay](./people/zac-barclay).
* [Saurabh Raman](./people/saurabh-raman) referenced a previous list from Antri and noted the need to validate and refresh it regularly.
* [Max Nicol](./people/max-nicol) clarified that the 'Has Affiliate' field is more accurate than 'Current Affiliate' for identifying currently affiliated retailers. This connects to the open question about whether all Affiliates in the database qualify for Visa Flex purposes.

**Merchant affiliate status:**
* [Andrea Ponte Martins](./people/andrea-ponte-martins) led a discussion on defining and identifying affiliated retailers — what changes are needed to align with Visa's requirements.

### [Pay Monthly](./projects/pay-monthly) — #pay-monthly-delivery Channel Digest (4–11 Mar)

New information not already captured elsewhere:

**Refunds:**
* Fees already paid at the point of refund are not refunded. For partial refunds that reduce the outstanding loan, future fees are calculated against the new loan balance. Confirmed by [Tamara Quinn](./people/tamara-quinn).

**Fee calculation ID:**
* [Craig Main](./people/craig-main) and Tomasz Surowiec agreed that the fee calculation ID used for the downpayment should be reused for remaining instalments — no recalculation. This resolves the open question from the 5 March design debate about whether to calculate once or per-instalment.

**Mobile release cadence:**
* [George Sharpe](./people/george-sharpe): release 2.47.0 (containing all MVP functionality for Zilch Advance/[EWA](./projects/ewa-extra)) to be rolled out by 13 March, before 2.48.0 for Pay Monthly features. [Tamara Quinn](./people/tamara-quinn) noted Pay Monthly should be rolled out before Advance.

**Apple Checkout:**
* Mariusz Kuligowski shared examples of Pay Monthly in Apple Checkout. [Grzegorz Ziemiański](./people/grzegorz-ziemianski) flagged that only the monthly fee should be displayed, not the total cost.

**Fee/instalment rounding:**
* [Grzegorz Ziemiański](./people/grzegorz-ziemianski) raised concern about ensuring the difference in instalment amounts is not greater than 1p.

**Fee events (potential risk):**
* [Mike Davis](./people/mike-davis) asked which events would include per-instalment fees or fee codes for Pay Monthly. Marek Chodak noted this is not in scope for MVP but may be problematic to exclude. Worth monitoring — could surface as a late blocker.

**Test environments:**
* Tomasz Michalski and Jan Michalak provided instructions for assigning users to the new product lines in dev-cu, dev-ci, and qa-sit.

**Fee schedule updates:**
* [Jacek Zanko](./people/jacek-zanko) confirmed he will update fee schedules in dev environments.

### DevOps Stand-up

* [Phil Stevenson](./people/phil-stevenson) raised out-of-hours call-outs for Decisioning alerts that don't require immediate action:
  * "Pre Approval (UK): Low percentage of 'PREAPPROVED' final outcome responses" (DataDog monitor 22219374)
  * "Credit Decision (UK): High Percentage of 'DECLINE' final outcome responses" (DataDog monitor 14209807)
* Phil's view: these are P3 alerts that can be reviewed in hours; they should not trigger OpsGenie pages overnight.
* Paul Batey (Decisioning) agreed — P3 should not be a call-out regardless of the specific alert.
* Wider context: all DevOps engineers report that overnight call-outs are so frequent they cannot share a bedroom with their partners during on-call rotations. This is a significant quality-of-life impact and needs addressing. [On-Call Rota](./projects/on-call-rota)
* **Follow-up needed:** Ensure these specific alerts are downgraded or have their notification routing changed so they don't page overnight. Escalate the broader call-out frequency issue.

### DataDog Monitor Noise — Initiative Launched [On-Call Rota](./projects/on-call-rota)

* Confirmed with DevOps team that the vast majority of call-outs originate from DataDog. Root cause: many teams own monitors and routinely add SRE integration without realising it results in OpsGenie pages. No standard approach to monitor ownership or notification routing.
* Initiated a project to define a standard approach to DD monitors to reduce noise. Plan:
  1. Ensure all DevOps-owned monitors are properly attributed to the DevOps team (own house in order first).
  2. Ensure every DD monitor has a team attribution, so non-compliant monitors can be traced to an owner.
  3. Define and roll out a standard approach to monitor configuration that reduces unnecessary call-outs.
* Current state: 465 DD monitors have no team attribution. Of those, all but 12 are managed by Terraform.
* Asked the team: (a) is there an easy way to identify Terraform-managed monitors that belong to DevOps and add the team tag? (b) what can be done with the remaining 12 non-Terraform monitors?

### [Pay Monthly](./projects/pay-monthly) — Sync Meeting

* Attended. Shared Merchant status. No significant new information.
* Items arising requiring follow-up with [Mike Davis](./people/mike-davis) and [Michał Górny](./people/michal-gorny) — meeting scheduled for 12 March.

### [Pay Monthly](./projects/pay-monthly) — Team Review Meeting

[Zac Barclay](./people/zac-barclay) clarified the latest requirements changes:

**Scope:**
* Changes apply to Pay Monthly only — no changes to other existing loan products.
* Two variants of Po3M will exist: standard (existing) and Pay Monthly (new).
* ExCo decided a stronger customer incentive is to reduce fees rather than offer rewards.

**Fee rates (confirmed):**
* 1.5% per month for ECJ (Online and In-store default)
* 1.8% per month for Anywhere and Express
* £80 cap on existing loan products (up from £40)
* No cap on new Pay Monthly products
* Arsenal pricing: no fees on Po6W; fees on Po3M, Po6M, Po12M (including existing Po3M product)

**Rewards — descoped entirely:**
* No additional rewards for retailers on any BNPL products, including new Pay Monthly.
* This means **no rewards work is required for Pay Monthly** — no code changes, no new configuration.
* ZILCH-48905 (static rewards) and ZILCH-48906 (dynamic rewards) are no longer needed.

**Fee service:**
* Confirmed no change to fee-service behaviour required.

**Remaining Merchant work:**
* Admin portal updates needed, especially 360 Profile — for customer success.
* [Tom McKenzie](./people/tom-mckenzie) to add test tickets for new loan products.

**Net impact on Merchant scope:** Significantly reduced. Rewards work eliminated entirely. Remaining work is admin portal (ZILCH-49087) and testing.

### Iteration Review Prep — DevOps Team

Compiled an achievement digest for the DevOps team covering Iteration 11 (13 Jan – 11 Mar 2026). Sources: weekly flash reports (intake/DevOps-i11.md), Jira (ZILCH project, Team = DevOps Team, Done + Ready for Release), and KB log entries.

Key stats: 45 tickets completed or effectively complete, 5 incidents responded to, 4 engineers.

Major workstreams: [Ephemeral Environments](./projects/ephemeral-environments) (ZOE to MVP, Zephyr Zero operational — 23 tickets), EWA/payout-service infrastructure on Sensitive Data Environment, fraud detection platform (AI agent, auto-scaling, Athena pipeline), Upwind to production, EKS cluster upgrades, GitHub runner optimisation, Flink Apps monorepo, and process adoption (hybrid Scrum/Kanban).

Suggested big-ticket highlights: ZOE MVP, EWA infrastructure delivery, Upwind to production, fraud detection platform, incident response load.

### [Pay Monthly](./projects/pay-monthly) — Requirements Changes (Slack, #pay-monthly-delivery)

[Zac Barclay](./people/zac-barclay) shared key requirement changes following ExCo discussions:

* **Fee rate change:** Pay Monthly fees now **1.8% monthly** on purchase amount for all term lengths (3, 6, 12 months). Previous rate was 1.6%.
* **Fee cap:** No fee cap on Pay Monthly (PO3M, PO6M, PO12M). Legacy PO3M will have an £80 fee cap.
* **Rewards change:** No dynamic rewards or base rewards on Pay Monthly loans. Only the incremental Plus rate of 1% will remain, applied to PO6W, PO3M, PO6M, PO12M. In effect: rewards only for Plus members, with different rates depending on loan product.
* **Fee rates table:** Updated in Confluence (https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4419354651/Fees+Rate+Table).

Nicklas pushed back on the instability of requirements — requested these changes be treated as final, and that stakeholders be informed any further changes will mean the 31 March deadline is missed. Zac acknowledged but noted he doesn't own the requirements for this project.

**Impact on Merchant epic:**
* ZILCH-48905 (static rewards for Po6/Po12) and ZILCH-48906 (dynamic rewards for Po6/Po12) — scope significantly reduced. Dynamic rewards (ZILCH-48906) may no longer be needed at all.
* The confirmed fee rate is now 1.8%, not 1.6% — the Option B decision from 4 March needs updating.

### Merchant Stand-up

* Missed the start of stand-up — [George Sharpe](./people/george-sharpe) caught me at my desk beforehand to discuss mobile releases for [EWA/Extra](./projects/ewa-extra) and [April Pricing Changes](./projects/april-price-changes).
* Mobile releases will need close management: time is needed for adoption of new app versions before features are switched on.
* George has specific requirements and will coordinate with [Ossie Nwokedi](./people/ossie-nwokedi).

### [Pay Monthly](./projects/pay-monthly) — Jira Review

* Reviewed Merchant epic ([ZILCH-48859](https://payzilch.atlassian.net/browse/ZILCH-48859)) live status ahead of status update meeting.
* ZILCH-48897 and ZILCH-48903 both now Ready for Release ([Jacek Zanko](./people/jacek-zanko)).
* ZILCH-48905 (static rewards for Po6/Po12) picked up by [Nick Holt](./people/nick-holt), In Dev.
* ZILCH-49027 (distributed fee/tranches) confirmed Rejected. No replacement needed — the scalar approach means fee-service already supports the required behaviour.
* Identified that the Merchant epic may be missing tickets for other work areas (e.g. fee code configuration). Scheduling a review meeting with the team this afternoon ahead of the status update.

### 1:1 — [Nick Holt](./people/nick-holt)

* **Michal's departure:** Nick thinks it's a shame — he was a good engineer. However, the dynamic with [Jacek Zanko](./people/jacek-zanko) has actually improved: previously, in-person conversations between Jacek and Michal in the Krakow office left Nick out of the loop. Now everything happens in Slack and he's involved.
* **[Pending Rewards](./projects/pending-rewards) / [Pay Monthly](./projects/pay-monthly):** Discussed how pending rewards work blocks rewards for Pay Monthly. Nick's explanation was hard to follow — stream of consciousness. Concern that this thread needs to be wrestled under control before it becomes a risk to 31 March deadlines. Scheduled an afternoon meeting to review.
* *Private note:* Merchant's responsibility on the 31 March projects is light compared to other teams. It would be very embarrassing if we were the ones who failed to meet the deadline.

### Task List Grooming

* Confirmed retailer-admin-ui is a defunct codebase — can be ignored or removed. [Merchant Operations](./projects/merchant-operations)
* Backlog hygiene on defect candidates completed as a byproduct of sprint planning activities.
* Dropped: Merchant retro (2026-03-09) notes — deprioritised.
* Dropped: conversation with [Grzegorz Ziemiański](./people/grzegorz-ziemianski) and [Nikos Sofianos](./people/nikos-sofianos) re friction with [Radek Kachel](./people/radek-kachel) on [EWA/Extra](./projects/ewa-extra) — window of opportunity passed.
* Dropped: chase on pen testing environment for [New Web](./projects/new-web) — completed through other activities.

## 2026-03-10

* Completed the KB Restructure project. First full compaction cycle finished: project digests, incident digests, people digests, and activity.md all populated from log entries up to 2026-02-24. Log entries for that period removed. Task closed.

### Sprint Planning — DevOps

- Sprint "DevOps #11.5" planned. [Ephemeral Environments](./projects/ephemeral-environments) and [DevOps Process](./projects/devops-process) relevant.
- Team largely guided the session themselves — they still know their backlog and priorities better than I do.
- Identified need for increased refinement sessions to redefine the [Ephemeral Environments](./projects/ephemeral-environments) project and better understand the backlog.

### Sprint Planning — Merchant

- Sprint "Merchant #11.Q" planned. [April Pricing Changes](./projects/april-price-changes), [EWA/Extra](./projects/ewa-extra), [Pay Monthly](./projects/pay-monthly) relevant.
- Managed to get all tickets required for 31 March deadline projects included.

### Engineering Leadership Sync

- Main topic: how to handle the upcoming iteration review and planning, given the department is struggling under the weight of three concurrent projects with 31 March deadlines.

### [Visa Flex](./projects/visa-flex) — Meeting Skipped

- Skipped the Visa Flex meeting — no critical responsibility in this project.

### [EWA/Extra](./projects/ewa-extra) — Extra Meeting

- Simple meeting. Updated that EWA/Extra work is underway.

### 1:1 — [Jacek Zanko](./people/jacek-zanko)

- Discussed how he's getting on since [Michal Baran](./people/michal-baran) left.
  - Would be nice to have someone else in the Krakow office to work with, but he's not too bothered.
  - Acknowledged that conversations with [Nick Holt](./people/nick-holt) can be challenging because of Nick's tendency to talk at length, unaware that he's not bringing others with him. Asked whether I'd given Nick that feedback — I hinted that I had.
- Discussed how the team can be better at raising and tracking tech debt.
  - Engineers need to do better at raising tech debt tickets at the point the debt is recognised.
  - Jacek thinks the habit has fallen away since the big bucket epic was banned.
  - Discussed mitigations. Agreed the team should continue raising tech debt tickets even without an epic to attach them to, and that we would review existing tech debt tickets and assign them to epics aligned with the iterations we intend to address them in.

## 2026-03-09

### DevOps Retro

- Two main themes: broken build/deploy pipelines, and delivery pressure and work intake.
- Pipeline failures: volume of failures has increased because CD adoption has driven a large increase in deploy frequency; failure *rate* is not necessarily higher. Team are often first port of call for diagnosis. Some structural problems (e.g. IP exhaustion) are solvable but the team rarely get time to make fixes. Team feel they are required to work at Platform level — boundary with Platform team remains unclear.
- Delivery pressure: multiple work streams all treating DevOps as top priority. Requests arrive via desk walk-ups and DMs, bypassing proper intake. Team cautious about over-formalising but recognise informal intake doesn't scale.
- Mitigations agreed for pipeline failures: use open questions to gently push diagnosis responsibility back to engineers; redirect DMs to #tech-devops; channel larger project requests through EM.
- Mitigations agreed for work intake: require Jira tickets for walk-up requests (immediate small tasks at discretion); move DM conversations to #tech-devops for visibility; large project requests to come through EM; be sensitive to delivery context and over-communicate during high-pressure periods.
- Personal actions: monitor #tech-devops more closely; respond to [Andrzej Lorenz](./people/andrzej-lorenz)'s pipeline concerns with appropriate context.
- [Phil Stevenson](./people/phil-stevenson) pushed back on the work intake formalisation proposal — expressed an emotional preference for informal, responsive working.
- Retro notes written up and shared with the DevOps team.
- Write-up reviewed and analysed with AI: insights generated on pipeline failure framing, CD project context, planned capacity model, work intake mitigations, and [Phil Stevenson](./people/phil-stevenson)'s pushback. Observations logged to devops-process project and people files.

### Merchant Retro

Merchant team retro held. Notes to be added.

### [April Pricing Changes](./projects/april-price-changes) — Cross-Team Refinement

Cross-team refinement session held for FE tickets under [ZILCH-49226](https://payzilch.atlassian.net/browse/ZILCH-49226) ([April Pricing Changes](./projects/april-price-changes) epic). This work is not normally Merchant's responsibility but is being picked up to allow other teams to remain focused on [EWA/Extra](./projects/ewa-extra) and [Pay Monthly](./projects/pay-monthly).

### EC-2083 — customer-web-legacy Production Deployment

[George Sharpe](./people/george-sharpe) confirmed release is proceeding, having obtained approval from [Rob Nelson](./people/rob-nelson) and [Andrzej Lorenz](./people/andrzej-lorenz).

### Stand-ups — Merchant and DevOps

Both stand-ups held. No notes taken.

### 1:1 — [Ossie Nwokedi](./people/ossie-nwokedi)

- EC-2083: updated [Ossie Nwokedi](./people/ossie-nwokedi). [George Sharpe](./people/george-sharpe) has been chased and is on it.
- [Stefan Amarie](./people/stefan-amarie) joining: [Ossie Nwokedi](./people/ossie-nwokedi) is interested to see how [Stefan Amarie](./people/stefan-amarie) works and is aware of the learning opportunity, but hasn't given it much thought yet.
- [Rory Fielding](./people/rory-fielding) situation: touched on briefly. Considered resolved and in the past.
- AI usage: [Ossie Nwokedi](./people/ossie-nwokedi) is getting significant value from AI tooling. Shared an example where he picked up a defect ticket, asked AI to analyse possible causes, and was told the defect had already been fixed a few hours earlier — highlighting a communication gap between engineers rather than an unresolved defect.

## 2026-03-06

### [New Web](./projects/new-web) — Pen Testing Scheduled

* [Oliver Hamilton](./people/oliver-hamilton) announced in Slack that pen testing is targeted for the week of 9 March.

### 1:1 — [Piotr Niebylski](./people/piotr-niebylski)

- Personal: his wife's operation was postponed. She is well in the meantime. [Piotr Niebylski](./people/piotr-niebylski) will need to work from home ahead of the operation to minimise pathogen exposure. Hans Zimmer concert still something they're looking forward to.
- ZOE spike (ZILCH-44576): last remaining blocker is that the customer verification service won't start. Cause unknown — configuration appears correct. Has asked the rest of the team for assistance.
- Zephyr Zero: up and running, except for a VGS issue. QAs continue to find issues for the team to work through.
- Off-piste pattern: gave feedback. [Piotr Niebylski](./people/piotr-niebylski) took it well. Acknowledged there may be adjustment needed to the new process and that he should get into the habit of raising Jira tickets for work.

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

- Fee-service rollout stats shared by [Grzegorz Ziemiański](./people/grzegorz-ziemianski): 23% EHI / 77% [fee-service](./projects/fee-service), 80 timeouts over 4 weeks, 99.997% success rate. [Andrzej Lorenz](./people/andrzej-lorenz) greenlit moving 100% to [fee-service](./projects/fee-service).
- Invited to Purchase refinement by [Tamara Quinn](./people/tamara-quinn); joined ~10 minutes late.
- [Michał Górny](./people/michal-gorny) confirmed Purchase scope: hardcoded fee values (FE web + mobile), ECJ pricing (FE web + mobile), PO3 calculator fee cap (£40 → £80), test updates.
- Dependency flagged: Storefront adaptive header is sourced from [fee-service](./projects/fee-service) on the Merchant side.
- Purchase scope achievable by end of next sprint but will delay PayMonthly work by approximately one sprint.
- [Andrzej Lorenz](./people/andrzej-lorenz) asked whether [Ossie Nwokedi](./people/ossie-nwokedi) could help Purchase with ECJ to protect PayMonthly timeline; [Michał Górny](./people/michal-gorny): workable if ECJ experience is there, but adds complexity.
- [Michał Górny](./people/michal-gorny) proposed FE-only alternative (no BE dependency on pricing changes): preserves PayMonthly timeline but introduces tech debt — no single source of truth for fee calculation. [Andrzej Lorenz](./people/andrzej-lorenz) acknowledged we are already in this situation; directed [Tamara Quinn](./people/tamara-quinn) to document it as a known system limitation and potential blocker for future pricing changes.
- Responded to [Andrzej Lorenz](./people/andrzej-lorenz) re: [Ossie Nwokedi](./people/ossie-nwokedi): [Ossie Nwokedi](./people/ossie-nwokedi) is currently on [Pay Monthly](./projects/pay-monthly) Admin Portal work; [Jacek Zanko](./people/jacek-zanko) could cover that, potentially freeing [Ossie Nwokedi](./people/ossie-nwokedi) for Purchase. Feasible given the [fee-service](./projects/fee-service) simplification. Committed to a definitive answer by end of day.
- [Michał Górny](./people/michal-gorny) to post an options summary to #april-pricing-changes.
- Confirmed: Merchant team will own the fee changes for April pricing.

### Slack — #merchant-firefighter

- [Tomasz Więckowski](./people/tomasz-wieckowski) (Decisioning) created [ZILCH-49269](https://payzilch.atlassian.net/browse/ZILCH-49269) — "Setup fee code fc-extra-monthly" — for the Merchant team, flagging it as needed for [EWA](./projects/ewa-extra) (Zilch Advance) and requesting prioritisation for the coming sprint.
- Responded confirming it would be pushed to the top of the backlog.

### Merchant Stand-Up

- **ZILCH-42041** ([Jacek Zanko](./people/jacek-zanko)) — Unblocked. Confirmation received that existing backups are sufficient.
- **ZILCH-48536** ([Nick Holt](./people/nick-holt)) — Listener set up for product change events. Deploying to pre-prod. Looking good.
- **ZILCH-45502** ([Ossie Nwokedi](./people/ossie-nwokedi)) — Brought back into sprint, having been dropped earlier to make way for another ticket. Ready for review.
- **ZILCH-49027** ([Jacek Zanko](./people/jacek-zanko)) — Rejected after considerable work. Decision based on new plan for fees. Asked [Jacek Zanko](./people/jacek-zanko) to create a Jira ticket for adding a new fee schedule.
- **ZILCH-48897** ([Jacek Zanko](./people/jacek-zanko)) — In review.
- **ZILCH-48873 & ZILCH-48954** ([Tom McKenzie](./people/tom-mckenzie)) — In progress.

## 2026-03-05

### DevOps Stand-Up

**Reactive board:**
- Security vulnerability tickets in To-Do — [Phil Stevenson](./people/phil-stevenson) does not think they should sit with DevOps. [Nick Gilbert](./people/nick-gilbert) has said he would handle them on his return ([Nick Gilbert](./people/nick-gilbert) is currently away).
- ZILCH-49091 — in progress with [Phil Stevenson](./people/phil-stevenson).
- ZILCH-41286 — unclear what it's for or whether [George Sharpe](./people/george-sharpe) is handling it; need to catch up with [George Sharpe](./people/george-sharpe). [Jira: "Create a fix version and apply it to tickets in release scope on merge of a release-please PR" — assigned to [George Sharpe](./people/george-sharpe), In Dev. Part of the CD automation work. [Phil Stevenson](./people/phil-stevenson) to confirm whether [George Sharpe](./people/george-sharpe) is actively progressing it.]
- ZILCH-45505 — on hold, low priority (consistent with decision at [Phil Stevenson](./people/phil-stevenson)'s 1:1 on 2026-03-04).
- Noted: ambiguity about what the Sign Off stage on the reactive Kanban board is for. Process needs clarifying.
- ZILCH-49094 — deployment already done but sitting in To-Do; moved to the correct column.

**Planned board:**
- ZILCH-48462 ([Phil Stevenson](./people/phil-stevenson)) — in progress but blocked by his duty rota rotation. Will return if reactive load allows.
- ZILCH-48446 — awaiting [Nick Gilbert](./people/nick-gilbert)'s return.
- ZILCH-47186 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk)) — moved to Done.
- ZILCH-48966 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk)) — needs final verification before closing. Blocked on staging; waiting on a role to be set up.
- ZILCH-48967 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk)) — moved to Done.
- ZILCH-48715 ([Lukasz Kowalczyk](./people/lukasz-kowalczyk)) — DevOps work done; Terraform merge still outstanding. Closed.
- ZILCH-44576 ([Piotr Niebylski](./people/piotr-niebylski)) — spike dragging; finding lots of issues. Expected to complete by end of day.

**[Piotr Niebylski](./people/piotr-niebylski) (ZILCH-44576):** Sense that [Piotr Niebylski](./people/piotr-niebylski) is using the spike as cover to do [Ephemeral Environments](./projects/ephemeral-environments) work he wants to do. Will push for better adherence to the new process — work he considers necessary should be raised as proper tickets and planned in. Aligns with existing appraisal observation that he goes off piste.

### EC-2083 — customer-web-legacy Production Deployment Blocked

Raised with [George Sharpe](./people/george-sharpe) that EC-2083 (Production Deployment — customer-web-legacy-1.176.0) has been sitting in Planning since 24 February — 9 days — despite containing merged work from six teams including Merchant (ZILCH-40343).

Pulled from Jira:
- **Ticket:** EC-2083 — auto-created by Jira automation on 24 Feb 2026
- **Status:** Planning (still open)
- **Assignee:** [Ossie Nwokedi](./people/ossie-nwokedi)
- **Teams affected:** Payments (ZILCH-48454), Purchase (ZILCH-47884, ZILCH-37894), Retain (ZILCH-46362), Onboarding (ZILCH-45932), Merchant (ZILCH-40343)

Reason for the stall is not yet established. Raised with [George Sharpe](./people/george-sharpe) to investigate.

### Merchant Stand-Up

Ticket updates:
- **ZILCH-42041** — [Jacek Zanko](./people/jacek-zanko) hasn't chased the platform ticket; still pending.
- **ZILCH-48536** ([Nick Holt](./people/nick-holt)) — Making do with a sub-optimal event requiring a callback to product-service rather than a fully enriched event. Putting tests around it. Wants to catch up with [Tom McKenzie](./people/tom-mckenzie) on test strategy, especially to cover both LD flag settings.
- **ZILCH-47174** — Should be unblocked now that [Tom McKenzie](./people/tom-mckenzie) is back at work. [Tom McKenzie](./people/tom-mckenzie) will review.
- **ZILCH-48897 & ZILCH-48903** ([Jacek Zanko](./people/jacek-zanko)) — [Ossie Nwokedi](./people/ossie-nwokedi) tested yesterday as planned. Found issues; [Jacek Zanko](./people/jacek-zanko) fixed; back for more testing.
- **ZILCH-49027** ([Jacek Zanko](./people/jacek-zanko)) — Requires further design conversations following yesterday's decision on source of truth for [Pay Monthly](./projects/pay-monthly) fees.
- **ZILCH-48954** — Requires another PR to be merged before it can be re-tested.
- **ZILCH-48873** — [Tom McKenzie](./people/tom-mckenzie) will look at it today.

Actions:
- Asked [Tom McKenzie](./people/tom-mckenzie) to ensure ZILCH-48954 and ZILCH-48873 both have parent epics (currently missing).
- Announced [Iteration 12](./projects/iteration-12-planning) planning will be a lightweight process, to avoid distracting from the March 31 deadline.
- Announced introduction of `@merchant-firefighter` for the Merchant duty rota.

Other notes:
- [Zac Barclay](./people/zac-barclay) briefly hinted at new requirements. [Nick Holt](./people/nick-holt) went straight into solutionising mode, well ahead of any clear requirements being established.
- [Jacek Zanko](./people/jacek-zanko) announced that affiliate-integration-service has made its **first production call to Partnerize** — a significant milestone; the service was still not operational as of 3 March.

### Merchant Firefighter Rota — Slack App Set Up

Set up a duty rota for the Merchant team in a Slack app. The person on duty can be tagged via `@merchant-firefighter`.

### 1:1 — [Tom McKenzie](./people/tom-mckenzie)

Meeting cut short — not much to discuss and I had not prepared.

**Defect backlog:**
The team's defect backlog is growing when it should be shrinking. The root issue identified: defects are not being properly triaged when they come in. Without triage, there is no mechanism to determine whether a defect requires urgent attention in a near sprint or can safely wait.

**Decision:** [Tom McKenzie](./people/tom-mckenzie) to own defect triage. He will be responsible for assessing incoming defects and advocating for their priority in pre-refinement meetings.

I have a Jira cumulative flow report for defects. Will monitor it and expect to see defect numbers begin to decline as a result of this change.

### DevOps Refinement Meeting

Attended but arrived late — pulled into other conversations beforehand. Struggled to maintain focus on the specific tickets being refined, but provided adequate facilitation of the process. Facilitation is still needed while the team beds in the new hybrid Scrum/Kanban approach.

### [fee-service](./projects/fee-service) Design — [Pay Monthly](./projects/pay-monthly) — Slack Discussion (Design Debate)

A design debate across two parallel Slack threads (cross-team, including [Andrzej Lorenz](./people/andrzej-lorenz), [Grzegorz Ziemiański](./people/grzegorz-ziemianski), [Tomasz Surowiec](./people/tomasz-surowiec), Tom Wood, [Mariusz Maciuszek](./people/mariusz-maciuszek), [Abhishek Chatterjee](./people/abhishek-chatterjee), [Marek Chodak](./people/marek-chodak), [Craig Main](./people/craig-main), [Sam Whittaker](./people/sam-whittaker), [Jacek Zanko](./people/jacek-zanko), [Nick Holt](./people/nick-holt)) around whether to change the [fee-service](./projects/fee-service) API design for [Pay Monthly](./projects/pay-monthly).

**Thread 1 — tranche vs. scalar**

**Proposal (Nicklas):** Replace the tranche array with a single per-instalment fee value (1.6%), with retailer-level overrides where suppression is needed. Rationale:
- With 1.6% as the source of truth, all values in the tranche array are identical by definition — the array is redundant.
- The tranche model builds in poor separation of concerns: it requires [fee-service](./projects/fee-service) to know the number of instalments, which is domain knowledge it shouldn't need.
- Retailer suppression is much cleaner to configure with a single value per retailer vs. 13 tranches per retailer.
- Callers would be responsible for applying the fee across each instalment rather than relying on [fee-service](./projects/fee-service) to return a pre-expanded array.

**Pushback ([Andrzej Lorenz](./people/andrzej-lorenz)):** Keep the original tranche model. Future requirements (specifically from the Revolving Line project, currently on hold) may need different fee values for different instalments. Pivoting now would close that door and require new cross-team development later.

**Tom Wood:** Reluctantly comfortable descoping per-instalment variation for now, but wants it noted that he is reluctant. Confirmed that the incoming requirement is specifically about being able to reduce the 1.6% for specific retailers and loan types — not about varying by instalment. [Zac Barclay](./people/zac-barclay) has confirmed retailer suppression can already be handled in the current setup (manually for now).

**[Grzegorz Ziemiański](./people/grzegorz-ziemianski):** Challenged the premise — argued the tranche model can fulfil all the stated requirements. Asked what the input to [fee-service](./projects/fee-service) should be: purchase amount or instalment amount?

**[Tomasz Surowiec](./people/tomasz-surowiec):** Supportive of the single-value approach; removing per-instalment complexity also removes work on his side, and the simpler response is supported out of the box for ECJ.

**Input clarification:** [Grzegorz Ziemiański](./people/grzegorz-ziemianski) confirmed that [fee-service](./projects/fee-service) currently receives `credit extended` (the purchase amount after deducting rewards, accounting for 0 down payment) — not the instalment amount. This was confirmed as correct by Nicklas (the whole loan principal, not just one instalment's share).

**Thread 2 — [Craig Main](./people/craig-main) joins; refund scope surfaces**

[Craig Main](./people/craig-main) joined the discussion expressing concern about the timing of a potential API change, requesting the new contract and risk mitigations as quickly as possible. He shared the existing agreed tranche JSON contract and noted that [Andrzej Lorenz](./people/andrzej-lorenz) had previously said to leave it unchanged.

[Nick Holt](./people/nick-holt) clarified that the tranche contract was still a proposal and had not yet been merged; [Craig Main](./people/craig-main) accepted this and reiterated his request for the final contract once agreed.

A new and material scope item emerged: **partial refunds**. Tom Wood confirmed that if a partial refund is made, the fee for the remaining instalments must be recalculated against the reduced principal (i.e. `principal - refund amount`). [Andrzej Lorenz](./people/andrzej-lorenz) flagged this as new scope — not previously considered.

**Debate on refund handling approach:**
- **Nicklas** proposed two options: (1) calculate the fee once at loan creation and recalculate if a refund event occurs; (2) calculate per instalment on each billing run, so each instalment naturally reflects the current principal. Nicklas noted that option 1 introduces a recalculation event, whereas option 2 avoids one — but option 2 may require storing a fee calculation reference per instalment on the ledger.
- **[Andrzej Lorenz](./people/andrzej-lorenz)** raised a concern about the audit trail: the `fee_calculation_reference` field on the customer ledger is intended to record which fee calculation produced a given fee. If fees are recalculated mid-loan, there would be multiple references — this creates ledger complexity.
- **[Jacek Zanko](./people/jacek-zanko)** proposed calling [fee-service](./projects/fee-service) once per instalment, so each instalment gets its own `fee_calculation_id`. This keeps the audit trail clean and is consistent with how the billing service already operates.
- **Nicklas** proposed a further clarification: store the fee calculation ID per instalment in the ledger, and leave it to Payments to decide whether to calculate once at loan creation and reuse that ID per instalment, or calculate fresh on each instalment. This separates [fee-service](./projects/fee-service) API concerns from billing run decisions.

The thread ended without resolution, with Nicklas putting a direct question to [Craig Main](./people/craig-main) about whether individual instalments are currently recorded as separate entries in the ledger. The question was unanswered in the transcript.

**Late update (4:39–4:49 PM):** [Andrzej Lorenz](./people/andrzej-lorenz) confirmed that there will be a FEE ledger entry for these fees, meaning the fee calculation reference can be stored there. Nicklas responded suggesting this points towards convergence: a scalar value applied on a per-instalment basis, recalculated as needed to accommodate partial refunds. No explicit confirmation yet — [Craig Main](./people/craig-main)'s input still awaited.

**Overall outcome:** Trending towards agreement on a scalar per-instalment model with recalculation on partial refund, with the ledger providing the audit trail. Pending [Craig Main](./people/craig-main)'s input (he is based in South Africa and has finished for the day — thread will resume tomorrow).

### [fee-service](./projects/fee-service) Design — [Pay Monthly](./projects/pay-monthly) (x2 meetings)

Two meetings today on [fee-service](./projects/fee-service) design in support of the [Pay Monthly](./projects/pay-monthly) project. Notes to follow.

### Pricing Structure Changes — [Steve Rayko](./people/steve-rayko) Conversations

Pulled into conversations by [Steve Rayko](./people/steve-rayko) (SVP Engineering) regarding planned pricing structure changes. [Steve Rayko](./people/steve-rayko) wanted to understand what would be involved in implementing them.

Key points established:
- **Deadline:** End of March 2026 — adding to the existing cluster of end-of-month P1 deliveries ([Pay Monthly](./projects/pay-monthly), [EWA/Extra](./projects/ewa-extra), [Visa Flex](./projects/visa-flex)).
- **Back-end:** Changes can be accommodated through configuration — no code changes required on the back end.
- **UX:** Some UX work may be required, but this would sit outside the Merchant team.
- **Team ownership — open question:** It is not yet decided whether Merchant would pick this work up or whether it would be handled by [Michal Baran](./people/michal-baran) and the new Spend Platform team.

The team ownership question has material implications for Merchant sprint capacity, which is already under significant pressure. The configuration-only back-end scope may appear lightweight, but landing anything at end of March — when three concurrent P1 initiatives are converging — adds risk. Worth monitoring closely.

## 2026-03-04

### March Delivery Pressure

[Pay Monthly](./projects/pay-monthly), [EWA/Extra](./projects/ewa-extra), and [Visa Flex](./projects/visa-flex) all share an end-of-March 2026 deadline — likely driven by the need to land all three before the start of the new financial year. Three concurrent P1 initiatives is significant delivery pressure across the organisation.

### [Pay Monthly](./projects/pay-monthly) — Channel Digest Ingested (2026-02-23 to 2026-03-04)

Key new information from #pay-monthly-delivery:
- **MVP product configuration still undecided** — Acquirer team (Michał Górny) considering two options; open questions around Po3 continuity for existing customers and migration scenarios
- **Credit limit on Po12m downgrade:** decreases by outstanding loan amount, same as Po3m; downgrades manual, done by risk team
- **Fee UI presentation:** fee service returns tranches; UI shows effective rate of first unpaid tranche, rounded to 1dp — agreed by Andrea Ponte and [Craig Main](./people/craig-main)
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
Following the ambiguity raised on 2026-02-23, [Andrzej Lorenz](./people/andrzej-lorenz) responded:
- Fee-service (and possibly rewards) move to Spend Platform will **not happen yet**
- New Spend Platform team **could** handle [EWA](./projects/ewa-extra)/[Pay Monthly](./projects/pay-monthly) fee schedules; [Andrzej Lorenz](./people/andrzej-lorenz) said to assume they would, pending planning discussion
- Rewards service ownership: **not decided yet**

Despite this steer, ZILCH-49156 ([EWA](./projects/ewa-extra) disbursement fee code) landed with Merchant, raised by [Tommy Kwok](./people/tommy-kwok) and [Oleksandr Tertyshnyi](./people/oleksandr-tertyshnyi). Nicklas has asked [Andrzej Lorenz](./people/andrzej-lorenz) to confirm whether Merchant or Spend Platform should own it. Awaiting response.

### [Lukasz Kowalczyk](./people/lukasz-kowalczyk) Promotion — Slack Discussion with [Andrzej Lorenz](./people/andrzej-lorenz)

[Andrzej Lorenz](./people/andrzej-lorenz) reviewed the L3 evidence document sent earlier today. Key outcomes from the discussion:

- **Growth Potential concern:** [Andrzej Lorenz](./people/andrzej-lorenz) pushed back on "Uses feedback to improve" being evidenced only by the annual appraisal response. He clarified the criterion relates to ongoing, day-to-day feedback responsiveness. Verbal examples provided: (1) reduction in handholding from [Piotr Niebylski](./people/piotr-niebylski) and [Phil Stevenson](./people/phil-stevenson) — [Lukasz Kowalczyk](./people/lukasz-kowalczyk) is now operating much more independently; (2) sustained improvement in speaking up during team meetings following feedback on this; (3) active engagement with recent Scrum/Kanban process formalisation following feedback to lean in to process more.

- **[Andrzej Lorenz](./people/andrzej-lorenz)'s conclusion:** [Lukasz Kowalczyk](./people/lukasz-kowalczyk) is performing at L3 level. The remaining unevidenced criteria in Growth Potential are not disqualifying. [Andrzej Lorenz](./people/andrzej-lorenz) will take the case to [Steve Rayko](./people/steve-rayko).

- **Action:** [Andrzej Lorenz](./people/andrzej-lorenz) requested an executive (TL;DR) summary of L3 performance. Summary authored and sent to [Andrzej Lorenz](./people/andrzej-lorenz).

- **Rating:** Target outcome is promotion to L3 with a rating of 3.

### [Pay Monthly](./projects/pay-monthly) — Fee Calculation Decision Confirmed

A decision was confirmed via Slack (originally raised by [Jacek Zanko](./people/jacek-zanko), resolved through discussion involving [Tamara Quinn](./people/tamara-quinn), Tom Wood, and Nicklas Chapman, with [Andrzej Lorenz](./people/andrzej-lorenz) requesting broadcast):

**Decision: Option B — 1.6% per instalment is the canonical fee rate.**

- The fee for each instalment is calculated as: `purchase amount × 1.6%`
- The total lifetime fee (20.8%) is an implied/derived figure, not the primary one
- This aligns with how fees are communicated to customers in-app, in emails, in the ECJ, and in the calculator
- Tom Wood confirmed; [Tamara Quinn](./people/tamara-quinn) documented
- [Andrzej Lorenz](./people/andrzej-lorenz) requested this be communicated to all teams (including Data and Finance) and acknowledged — [Tamara Quinn](./people/tamara-quinn) has confirmed she will own this broadcast

The earlier-implemented Option A (calculate 20.8% total, then split across tranches) is **not** the chosen approach. The [fee-service](./projects/fee-service) implementation should use 1.6%.

### [Pay Monthly](./projects/pay-monthly) — Refinement Complete (previously)

[Pay Monthly](./projects/pay-monthly) tickets (from [Zac Barclay](./people/zac-barclay)) were worked up prior to today and are in play for sprint 11.4.

Also noted: the Merchant team's responsibilities for [Pay Monthly](./projects/pay-monthly) span two areas:
1. Enable rewards for credit purchases with the [Pay Monthly](./projects/pay-monthly) loan product
2. Enable [fee-service](./projects/fee-service) to calculate fees on a monthly-instalment basis (rather than single-instalment as with other loan products)

### [Iteration 12](./projects/iteration-12-planning) — Chased [Zac Barclay](./people/zac-barclay) on Candidates

Chased [Zac Barclay](./people/zac-barclay) on candidate work streams for [Iteration 12](./projects/iteration-12-planning). Response suggests he doesn't yet know what the team will be pointed at.

### Tech Leadership Sync

Nothing significant to note.

### [Pay Monthly](./projects/pay-monthly) Tech Sync

Attended. Nothing significant to note.

### [Phil Stevenson](./people/phil-stevenson) 1:1

Largely a venting session — [Phil Stevenson](./people/phil-stevenson) needed to articulate his concerns more than he needed specific actions taken. The broad theme was pressure, process, and friction with cross-team engineers.

**Quality:** Less of an acute problem than it appeared. [Phil Stevenson](./people/phil-stevenson) was able to push back on [Radek Kachel](./people/radek-kachel)'s changes as a codeowner and got the outcome he wanted. Quality is in hand.

**[Radek Kachel](./people/radek-kachel) / [EWA](./projects/ewa-extra) pattern:** The real concern is a recurring pattern of poor communication and cooperation from [Radek Kachel](./people/radek-kachel) — unwillingness to engage through proper channels and reluctance to act on review feedback. Will raise with [Grzegorz Ziemiański](./people/grzegorz-ziemianski) and [Nikos Sofianos](./people/nikos-sofianos) framed as a light-touch question about whether they've observed any friction, rather than a direct escalation.

**Unrealistic expectations on DevOps:** [Phil Stevenson](./people/phil-stevenson) perceives a persistent belief — particularly in the [EWA](./projects/ewa-extra) project — that DevOps should do things on demand. This has some historical basis. Advised him to counter it by leaning into the newly formalised process: when work slips because higher-priority reactive items were pulled in, point to the sprint record and Jira evidence; when people expect immediate reactive delivery, point to the Kanban board and WIP limits to show them they're in a queue; and if anything genuinely needs reprioritising over in-flight work, requesters should come to me — that's an EM decision.

**Observation:** [Phil Stevenson](./people/phil-stevenson) gets frustrated when he's concerned quality may suffer or when he senses friction with other engineers. Some friction is inevitable: engineers are under pressure to deliver quickly; DevOps want things done properly. That tension is natural and can be productive. [Phil Stevenson](./people/phil-stevenson) is aware of this at an intellectual level but still finds it stressful in practice.

### Merchant Stand-up

[Tom McKenzie](./people/tom-mckenzie) remains off sick.

* ZILCH-48952 — Brought into sprint yesterday; awaiting build and release. Marked as done.
* ZILCH-46769 — With [Ossie Nwokedi](./people/ossie-nwokedi). [Nick Holt](./people/nick-holt) has reviewed. Needs test evidence before it can move forward.
* ZILCH-42041 — [Jacek Zanko](./people/jacek-zanko) assigned to himself and responded to [Charlie Hurst](./people/charlie-hurst) (Platform). Now awaiting action from Platform.
* ZILCH-46367 — Completed yesterday.
* ZILCH-49076 — With [Nick Holt](./people/nick-holt). Blocked on the Decisioning team's PR. Risk of slipping beyond the sprint. A workaround using a different event exists but could introduce a race condition. [Nick Holt](./people/nick-holt) will chase Decisioning on the PR's status. E2E testing will also be required. Assessed as at-risk.
* ZILCH-47174 — With [Ossie Nwokedi](./people/ossie-nwokedi). Awaiting sign-off from [Tom McKenzie](./people/tom-mckenzie), who is on sick leave.
* ZILCH-48897 — With [Jacek Zanko](./people/jacek-zanko). Also awaiting [Tom McKenzie](./people/tom-mckenzie).
* ZILCH-48903 — With [Jacek Zanko](./people/jacek-zanko). Also awaiting [Tom McKenzie](./people/tom-mckenzie). [Ossie Nwokedi](./people/ossie-nwokedi) offered to test in [Tom McKenzie](./people/tom-mckenzie)'s absence.
* ZILCH-49027 — Awaiting clarification from Product.
* ZILCH-48873 & ZILCH-48954 — With [Tom McKenzie](./people/tom-mckenzie); awaiting his return.

### DevOps Stand-up

[Nick Gilbert](./people/nick-gilbert) not mentioned; presumably still on leave.

**Planned:**
* ZILCH-48462 — [Phil Stevenson](./people/phil-stevenson); still in progress.
* ZILCH-44576 — Still in progress with [Piotr Niebylski](./people/piotr-niebylski).
* ZILCH-48966 & ZILCH-48967 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk) making good progress; expected to complete today.

**Reactive:**
* [Phil Stevenson](./people/phil-stevenson) occupied with support. Several issues with ZILCH-49113. ZILCH-49091 in progress.

### [New Web](./projects/new-web) — Pen Testing Requirements Discussion (Slack)

Slack exchange with [Chris Walker](./people/chris-walker) and [Phil Stevenson](./people/phil-stevenson) regarding the [New Web](./projects/new-web) sprint work and pen testing readiness.

**Background:** [New Web](./projects/new-web) sprint work (likely ZILCH-47773 or related) is at risk due to high-priority [EWA](./projects/ewa-extra) tasks being pulled in. [Chris Walker](./people/chris-walker) was informed proactively.

**[Chris Walker](./people/chris-walker)'s request:** That DevOps and the Security team (secteam) agree and document what needs to be done before pen testing can begin. [Chris Walker](./people/chris-walker) referenced that Julien (sec team) had said the environment should be "as close to prod as possible". [Chris Walker](./people/chris-walker) is concerned about ending up unable to get security sign-off because something wasn't tested.

**[Phil Stevenson](./people/phil-stevenson)'s view:** Testing in staging should be sufficient; DevOps are not planning major changes and any issues found would likely require changes anyway.

**Outcome:** [Chris Walker](./people/chris-walker) is comfortable with [Phil Stevenson](./people/phil-stevenson)'s position but wants it confirmed in writing by the Security team.

**Action required:** Arrange agreement — ideally written — between DevOps and the Security team on the pen testing environment requirements for [New Web](./projects/new-web) (staging acceptable vs. prod-like required).

## 2026-03-03

### [EWA](./projects/ewa-extra) Team — DevOps Engagement

[Phil Stevenson](./people/phil-stevenson) flagged via Slack that the [EWA](./projects/ewa-extra) project team (including [Radek Kachel](./people/radek-kachel)) are performing DevOps work themselves rather than engaging via the tech-devops channel, and are showing reluctance to take suggestions on PRs. [Phil Stevenson](./people/phil-stevenson) supports them doing the work but wants it done properly through the right channels. He attributes the behaviour to pressure from elsewhere.

Responded to [Phil Stevenson](./people/phil-stevenson) and agreed to discuss further at tomorrow's 1:1 (4 Mar).

[Phil Stevenson](./people/phil-stevenson) also forwarded a Slack exchange (17:37) in which [George Sharpe](./people/george-sharpe) (Change Manager) contacted [Phil Stevenson](./people/phil-stevenson) and [Lukasz Kowalczyk](./people/lukasz-kowalczyk) directly to chase progress on 4 [EWA](./projects/ewa-extra) tickets assigned to DevOps. [Phil Stevenson](./people/phil-stevenson)'s response: "blocked on number of hours in the day and devops engineers at zilch." [Lukasz Kowalczyk](./people/lukasz-kowalczyk) confirmed ZILCH-48967 is done and ZILCH-48966 will be done today. [Phil Stevenson](./people/phil-stevenson) noted that some of the work had only surfaced that day; [Lukasz Kowalczyk](./people/lukasz-kowalczyk) confirmed ZILCH-49094 and ZILCH-49091 are new additions. [Phil Stevenson](./people/phil-stevenson) shared this with Nicklas as evidence of undue pressure and concern about the impact on quality. To discuss at tomorrow's 1:1.

### [Merchant Operations](./projects/merchant-operations) — Observability Documentation Structure

Agreed approach for documenting observability work under ZILCH-47400. Observability documentation will live in DataDog where DataDog supports it (dashboard descriptions, monitor messages, etc.). Exception: functional metrics per service have no natural home in DataDog, so these will be documented in Confluence. Structure: one page per service under a new "Observability" parent page in the Merchant Confluence space, covering functional metrics, normal ranges, and associated context. [fee-service](./projects/fee-service) to be the first page created.

### [Merchant Operations](./projects/merchant-operations) — [fee-service](./projects/fee-service) Audit

Continued the [Merchant Operations](./projects/merchant-operations) workstream. Completed the DataDog audit of [fee-service](./projects/fee-service) — a significant time investment, constituting a large portion of the day. Key finding: [fee-service](./projects/fee-service) has no prod logs — debug logging was disabled as a cost optimisation without the EM's knowledge. Confirmed by [Jacek Zanko](./people/jacek-zanko). This is consistent with the pattern noted in his appraisal of things happening under the radar.

See `projects/merchant-operations/audit-fee-service.md` for full findings.

### Sprint Change — Merchant

* [Ossie Nwokedi](./people/ossie-nwokedi) requested to bring ZILCH-48952 ("Deeplinks to category pages aren't working") into the sprint. Approved on the condition that something was swapped out. ZILCH-45502 ("Large volume of error logs from featured tile query when product line not yet loaded") moved out to make room.

### Merchant Stand-up

* ZILCH-46769 — [Ossie Nwokedi](./people/ossie-nwokedi) picked up; now in PR.
* ZILCH-42041 — Response received from Platform via PO-1597. [Charlie Hurst](./people/charlie-hurst) can ensure backup is in place (see ticket comments). [Nick Holt](./people/nick-holt) suggests that however backup is implemented, it should be retained indefinitely.
* ZILCH-46367 — [Ossie Nwokedi](./people/ossie-nwokedi) has completed.
* ZILCH-48536 — Progressing with [Nick Holt](./people/nick-holt). Finance sign-off on the approach still outstanding. Decisioning not providing the events needed for feature changes; [Nick Holt](./people/nick-holt) has pointed them to the relevant part of the codebase. Decisioning's work is blocked by a refactor branch pending merge, and they are also occupied with [EWA](./projects/ewa-extra) work. Decisioning pushing back on the need for the change. Need to lean in to resolve this.
* ZILCH-47600 — [Ossie Nwokedi](./people/ossie-nwokedi) has in PR. Tests confirm working behaviour and are gated in CI. Issue was never reproduced. Ready to close off.
* ZILCH-48887 — [Jacek Zanko](./people/jacek-zanko) reports [Tom McKenzie](./people/tom-mckenzie) has started building tests. Ready from [Jacek Zanko](./people/jacek-zanko)'s perspective. [Tom McKenzie](./people/tom-mckenzie) is on sick leave.
* ZILCH-49027 — [Jacek Zanko](./people/jacek-zanko) just picking up.
* ZILCH-48954 — In progress with [Tom McKenzie](./people/tom-mckenzie); no update as [Tom McKenzie](./people/tom-mckenzie) is on sick leave.

### DevOps Stand-up

[Nick Gilbert](./people/nick-gilbert) still on leave.

**Planned:**
* ZILCH-44576 — [Piotr Niebylski](./people/piotr-niebylski) working through issues.
* ZILCH-48967 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk) fixed issues with Wm and added to helm chart.
* ZILCH-48966 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk) created RBAC permissions. Blocked by one missing secret.
* ZILCH-48715 — Discussion, details hard to follow. [Phil Stevenson](./people/phil-stevenson) making a point about the distinction between what the team owns and how they manage it: SNS/SQS should be managed through Crossplane, not Terraform.
* ZILCH-48462 — Not progressed; [Phil Stevenson](./people/phil-stevenson) is on rota duty.
* ZILCH-49042 — Not progressed; [Phil Stevenson](./people/phil-stevenson) is on rota duty.
* ZILCH-45505 — [Phil Stevenson](./people/phil-stevenson) has the script done; needs team review. [Lukasz Kowalczyk](./people/lukasz-kowalczyk) has reviewed. [Phil Stevenson](./people/phil-stevenson) subsequently shared the script ([tools PR #98](https://github.com/zilchdev/tools/pull/98)) and an example change ([customer-service PR #3759](https://github.com/zilchdev/customer-service/pull/3759)) in Slack, and asked for sign-off from [Piotr Niebylski](./people/piotr-niebylski) and Nicklas before running it across all repos. [Piotr Niebylski](./people/piotr-niebylski) approved. Nicklas deferred — needs more context before signing off; will discuss at tomorrow's 1:1 with [Phil Stevenson](./people/phil-stevenson).
* ZILCH-48446 — [Nick Gilbert](./people/nick-gilbert) dropped this when he went on leave. [Phil Stevenson](./people/phil-stevenson) to pick up where [Nick Gilbert](./people/nick-gilbert) got to.

**Process observation:** ZILCH-48446 highlights a gap in leave handover practice. [Phil Stevenson](./people/phil-stevenson) should not have to piece together where [Nick Gilbert](./people/nick-gilbert) got to — outgoing team members need to hand over in-progress work clearly before going on leave.

### Refinement Session — Merchant

Ran a refinement session with the Merchant team. One ticket discussed.

### Interviews

Two interviews were scheduled today. The first candidate was a no-show — interview scrapped. Later in the day, stood in for [Mike Davis](./people/mike-davis) at a second interview. Candidate was not suitable. Write-up pending.

### Merchant Support Rota — Hand-over

Attended the Merchant support rota hand-over meeting. Now on duty for the first week.

## 2026-03-02

* Returned to work after a few days off. Catching up via Slack.

* [Incident-467](./incidents/incident-467) — rewards comms/eligibility mismatch. See [Incident-467](./incidents/incident-467). Status: Stable. Root cause: `rewards-service` correctly skipped reward for ineligible customers, but `customer-service` missed the signal and published `Loan_OnLoanComplete_ENRICHED`, which `notification-service` consumed and acted on. Fix deployed 27 Feb by [Rory Fielding](./people/rory-fielding) (Retain) — comms turned off pending proper resolution. Root cause fix owned by Retain (ZILCH-48940). Retrospective to be jointly led by Merchant and Retain. Incident commander: Mark Reddington. [Tom McKenzie](./people/tom-mckenzie) tagged me in the channel this morning — reason unknown.

* [Stefan Amarie](./people/stefan-amarie) onboarding — drafted first 1:1 agenda ([content-authoring/output/stefan-first-1-1-agenda.md](content-authoring/output/stefan-first-1-1-agenda.md)). Ingested [Steve Rayko](./people/steve-rayko)'s informal L5 IC expectations document; logged [Rob Nelson](./people/rob-nelson)'s position on the FE competency lead question ([Chris Walker](./people/chris-walker) retains for now, review once [Stefan Amarie](./people/stefan-amarie) is settled). Created Incident-166 record ([Incident-166](./incidents/incident-166)) — background, significance, mitigations, and link to ZILCH-47400.

* [On-Call Rota](./projects/on-call-rota) review meeting. [Chris Prowse](./people/chris-prowse) walked through the toolchain; worked through most alerts from the fortnight to 2 March. Several actions identified — see [On-Call Rota](./projects/on-call-rota).

* [Andrzej Lorenz](./people/andrzej-lorenz) requested evidence to support the rating of 2 given to [Lukasz Kowalczyk](./people/lukasz-kowalczyk) in his appraisal. Responded via Slack with a structured justification covering all four dimensions of the staff levels framework, with Jira evidence drawn from ZILCH and DEVOPS projects across the full year, and a summary of his cross-team support activity. Working notes in [content-authoring/output/lukasz-appraisal-justification.md](content-authoring/output/lukasz-appraisal-justification.md).

### Slack catch-up (23 Feb – 2 Mar)

Relevant items extracted from AI channel summaries:

**[Incident-467](./incidents/incident-467) (engineering-application-support):**
* [Mike Davis](./people/mike-davis) requested [Nick Holt](./people/nick-holt) and [Jacek Zanko](./people/jacek-zanko) to raise the incident.
* Root cause confirmed as `onesignal-integration` lambda incorrectly triggering notifications for loan completion events where rewards were not applied.
* Mark Reddington: future incidents should be raised directly in Datadog, not via Slack. Incident record updated.

**DevOps / infrastructure (platypus, tech-on-call):**
* [Phil Stevenson](./people/phil-stevenson) removed the Upwind admission webhook from production — it was preventing new pods from starting. [Nick Gilbert](./people/nick-gilbert) to follow up with Arnar.
* EKS prod cluster upgrades to version 1.33 completed (issuer cluster done; customer cluster scheduled).
* Upwind deployed to production and working (confirmed across team).
* [Lukasz Kowalczyk](./people/lukasz-kowalczyk) sharing Terraform plans for staging/prod — reviewed and approved by [Matt Swirski](./people/matt-swirski) and [Charlie Hurst](./people/charlie-hurst).

**Infosec vulnerability tickets (infosec-vulnerability-remediation-tracking):**
* Vulnerable dependency findings in frontend and typescript-shared-library flagged by [Nandini Muraleedharan](./people/nandini-muraleedharan).
* Originally assigned to Payments team; [Nandini Muraleedharan](./people/nandini-muraleedharan) asking which team has capacity for the frontend ones.
* Connects to the DevOps stand-up concern about security vuln tickets landing on the wrong team.

**[EWA](./projects/ewa-extra) / Plaid (tech-ewa-plaid-open-banking):**
* [Rob Nelson](./people/rob-nelson) shared that Plaid will deliver their Income Insights product by 13 March — critical for [EWA](./projects/ewa-extra) short- and long-term plans. [Alastair Gullan](./people/alastair-gullan) flagged need for a quick decision on trusting that date.

**[New Web](./projects/new-web):**
* [Chris Walker](./people/chris-walker) sent a planning reminder tagging [Nick Gilbert](./people/nick-gilbert), [Phil Stevenson](./people/phil-stevenson), and me on 23 Feb (before I went on leave).

**dev-payments (today):**
* Deadlock issue blocking the payments team — [Craig Main](./people/craig-main) investigating; query optimised but still deadlocking. Ongoing.

**OTA errors / alert-mobile:**
* Elevated OTA errors on mobile-ui — caused by Expo free tier quota being exceeded. [Rory Fielding](./people/rory-fielding) and Jan Michalak resolving by re-enabling enterprise subscription.

### DevOps Flash Report — engineer contributions (full report not seen)

Captured from team channel week-notes. No [Lukasz Kowalczyk](./people/lukasz-kowalczyk) contribution visible in this snippet.

**[Phil Stevenson](./people/phil-stevenson):**
- GitHub runners: caching base container images (some performance issues to resolve)
- Ephemeral: database backup and restore improvements
- Fraud: initial fraud AI agent deployed

**[Nick Gilbert](./people/nick-gilbert):**
- Upwind deployed to production
- Initial work on certificate management for server-side web app (Crossplane deployed to dev cluster — ACM)
- VGS manually set up for zephyr-zero

**[Piotr Niebylski](./people/piotr-niebylski):**
- CI/CD ready deployment for payout-service
- Aggregation flink-apps Terraform ready
- GitHub runners: caching base container images (speeds up build time)
- Ephemeral: database backup/restore from qa-sit into zephyr-zero; new services added; all service versions updated to latest staging; VGS manually set up for zephyr-zero
- Fraud: initial fraud AI agent deployed
- Upwind deployed to production
- Crossplane deployed to dev cluster for server-side web app certificate management

### Merchant Flash Report (sent by [Tom McKenzie](./people/tom-mckenzie) in my absence)

[Tom McKenzie](./people/tom-mckenzie) sent the weekly Merchant flash report to [Andrzej Lorenz](./people/andrzej-lorenz) while I was away. [Andrzej Lorenz](./people/andrzej-lorenz) pushed back, characterising it as more of a sprint report than an end-of-week flash report. Report content:

> Morning [Andrzej Lorenz](./people/andrzej-lorenz), i've been given the honour of sending over the flash report. As is the case when you have a complete burn down in the previous sprint, this sprint isn't going to necessarily have any early quick wins. Evidenced by the fact that we don't have anything in Done.
> * We're still very much in the early stages of [Pending Rewards](./projects/pending-rewards) development.
> * [Pay Monthly](./projects/pay-monthly): Extending the retailer schema to incorporate credit rewards, as well as the respective admin changes are almost ready for testing.
> * Frontend LD flag audit is in review.
> * Working with Lambdatest to solve failing maestro tests.

### Merchant Stand-up

* ZILCH-46769 — still pending pickup.
* ZILCH-42041 — still blocked by PO-1597. [Charlie Hurst](./people/charlie-hurst) on leave; waiting on him.
* ZILCH-46367 — [Ossie Nwokedi](./people/ossie-nwokedi) absent from stand-up; no update.
* ZILCH-48536 — [Nick Holt](./people/nick-holt) in progress. Blocked: wants an event on feature changes. Considering doing the work himself and sending to Decisioning for review.
* ZILCH-48539 — pending pickup.
* ZILCH-47174 — [Ossie Nwokedi](./people/ossie-nwokedi) not present to comment.
* ZILCH-48897 — in progress with [Jacek Zanko](./people/jacek-zanko). Updated tests to check for updated version; only expects updated DTOs in the appropriate version.
* ZILCH-48873 — [Tom McKenzie](./people/tom-mckenzie) working to resolve with LambdaTest.
* ZILCH-49027 — added to board while I was away. Fee service to support fees split into monthly instalments ([Pay Monthly](./projects/pay-monthly) scope). Accepted as additional scope without dropping equivalent points; [Jacek Zanko](./people/jacek-zanko) believes he has capacity.

### DevOps Stand-up

[Nick Gilbert](./people/nick-gilbert) on leave.

**Reactive:**
* ZILCH-48881 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk): Done. Moved to Done column. [Phil Stevenson](./people/phil-stevenson) moved past Ready for Release.
* ZILCH-41286 — [George Sharpe](./people/george-sharpe) asked [Lukasz Kowalczyk](./people/lukasz-kowalczyk) about a fix. Ticket assigned to [George Sharpe](./people/george-sharpe) but should be with DevOps. [Phil Stevenson](./people/phil-stevenson) to catch up with [George Sharpe](./people/george-sharpe).
* ZILCH-48513, ZILCH-45505 — [Phil Stevenson](./people/phil-stevenson) to look at soon.
* Security vuln. tickets — [Phil Stevenson](./people/phil-stevenson) questions whether these should sit with DevOps; thinks they belong with the security team. To resolve.

**Planned:**
* ZILCH-47186 — [Lukasz Kowalczyk](./people/lukasz-kowalczyk) looking at it.
* ZILCH-48966, ZILCH-48967 — High priority, [EWA](./projects/ewa-extra) project. [Lukasz Kowalczyk](./people/lukasz-kowalczyk) has under way. Brought into sprint; ZILCH-47583 bumped to accommodate. Estimated at 1 point each.
* ZILCH-44567 — in progress with [Piotr Niebylski](./people/piotr-niebylski).
* ZILCH-48462 — [Phil Stevenson](./people/phil-stevenson): nearly ready for review; has a PR.
* ZILCH-48416 — Done ([Phil Stevenson](./people/phil-stevenson)).
* ZILCH-48075 — [Phil Stevenson](./people/phil-stevenson) has spoken to [Nikos Sofianos](./people/nikos-sofianos); agreed new approach for caching images. [Phil Stevenson](./people/phil-stevenson) to raise a ticket.
* ZILCH-48446 — [Phil Stevenson](./people/phil-stevenson) to find out where [Nick Gilbert](./people/nick-gilbert) got to and whether it needs progressing.
* ZILCH-47773 — blocked. Need to find out how to create certificates from the security team.

**General:**
* Handover policy agreed: if less than a day's work remains on an in-progress reactive ticket when rotation changes, the current owner can continue rather than handing over.
* Observation: unclear who is on duty for reactive work — [Lukasz Kowalczyk](./people/lukasz-kowalczyk) and [Phil Stevenson](./people/phil-stevenson) both across both boards. May need better discipline around the duty rota.

* Removed from Waiting On: [Piotr Niebylski](./people/piotr-niebylski) 1:1 reschedule — no reschedule materialised; decided not to chase.
* Removed from Waiting On: [Ethan Stockwell](./people/ethan-stockwell) data file (visa-flex).
* Removed from Waiting On: [Tom McKenzie](./people/tom-mckenzie) test policy document — a Jira task has been created; now a planning matter rather than a chase.

