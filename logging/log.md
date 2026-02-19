# Log

## 2026-02-19

### Merchant Stand-up

* **ZILCH-40366** (Lambda authorizer / public retailer gateway, In Dev) — Jacek cleaned up Terraform; asked Phil to review. Michal writing E2E tests ahead of deployment while waiting for DevOps.
* **Partnerize** — Jacek. Tested service sending test data to Partnerize successfully. One URL parameter remaining; should be done.
* **ZILCH-42041** (Decommission fee-service MSSQL database, In Dev) — Michal. Charlie (Platform) about to drop the MSSQL tables; progress at Platform (PO-1597). Still waiting.
* **ZILCH-46517** (Fee-change playbooks, In PR) — Michal. Playbooks written and in PR; Jacek reviewed and added comments on 18 Feb. Michal will share Confluence links in Slack. Confluence page already carries a production-use disclaimer (tested in QA-SIT only) — asked Michal to note this in the docs, which he has done.
* **ZILCH-48222 and ZILCH-43416** — both ready for my sign-off.
* **ZILCH-48355** (Bottom rail hidden on online/storefront tabs, In PR) — Ossie. Bug vs Defect debate resolved: Ossie downgraded to Bug — introduced during development, not in the current production release (2.44.0).
* **ZILCH-43416** (Fee-service timeout causes sanity test failure) — Michal. Analysed test failures; concludes the issue is no longer a problem. Moving to Ready for Sign-off.
* **ZILCH-35883** (Storefront rails clip right edge, In Dev) — Ossie. Brought into sprint on spare capacity; cannot recreate. Asked Tom to try on a physical device. May be closeable.
* **DataDog alert** — Michal spotted a latency spike on fee-service. Root cause: wallet-providers-service was consuming product change events from Underwriting's bulk upgrade job (22k records at 10/s) and was missing a database index — causing slow queries on the Aurora issuer cluster. No SLA breach (p99 ~50ms vs 100ms limit). Grzegorz Ziemiański raised a broader concern: Aurora was partly adopted to prevent noisy neighbour problems, but this suggests that hasn't fully been achieved. Platform (Charlie Hurst / Benjamin Ibrulj) investigating.
* **Pending Rewards** — Nick Holt chasing what events are available to drive cancellation of pending rewards, and what event signals loss of a feature.

## 2026-02-18

* Promoted three devops-process tasks to Next priority: review backlog track assignments, set up refinement and backlog prioritisation meetings, and extend Merchant stand-up timing. Aim is to close off the devops-process initiative today.
* Chased Tom McKenzie on test policy document.
* Authored ZILCH-48608 — task for the Merchant team to define a test policy document, to be published to Confluence under Unicorn Operating Processes and reviewed in a team session.
* Wrote up Nick Gilbert's 1:1 notes from 12th Feb.
* Set up new series of sprint planning meetings for the DevOps team.
* Rescheduled Merchant and DevOps stand-ups — more time for Merchant stand-up and better chance of making the DevOps one on time.
* Scheduled regular refinement meetings for the DevOps team.

* Reviewed Memberships Strategy presentation from Zac — feels out of date given EWA/Extra pivot.
* Reviewed backlog track assignments with the DevOps team in a meeting. Almost everything ended up in the 'planned work' track. This likely means the team isn't creating tickets for reactive work rather than there being less of it than expected — reinforces the need for the Slack-to-ticket automation investigation.
* Checked in with Nikos on Zephyr Zero testing progress. Two blockers being worked on: a VGS issue and work on the test lambda (which allows test state management via direct DB SQL queries) — both prevent test users from acting as customers signing up on the environments. Radek Kachel is working on the lambda.
* Rory Fielding's query answered by Kieren Messenger and Tom McKenzie. Rory picking up ZILCH-48181 (storefront tabs/search don't fit on Android with max display size). ZILCH-48355 (bottom rail hidden on online/storefront tabs) is In PR and ready for peer review.
* Pinged Nikos to confirm who's working on the test lambda for Zephyr Zero.
* Ossie out of tickets — suggested he pick up ZILCH-35883 (storefront rails right-edge clipping), already In Dev and previously started. Bias towards finishing in-progress work before starting new.
* Worked through ticket sign-offs. Signed off six tickets: ZILCH-43742 (remove fetchRecentlyPurchasedRetailers query), ZILCH-48248 (race condition fix), ZILCH-40343 (refresh token session renewal), ZILCH-46901 (Partnerize integration), ZILCH-47687 (Pro rewards label on purchases page), ZILCH-48105 (WebSocket/IDV deadlock fix). All moved to Ready for Release.
* Created `tech-zilch-pro` Slack channel for coordination on the Pro project, especially roll-out planning. Public channel; starting with a focussed list and expecting it to grow organically.
* Drafted Zilch Pro Release Plan page for Confluence. Collaborative document for cross-team contributors to capture release steps per feature. Seeded with feature list from the product overview, roll-out plan from discussions with Nikos/Zac/Ethan, and the key constraint that customer availability is gated on partnership delivery. Remaining work: add Confluence-specific macros directly in Confluence.

* Read Nick Holt's Pending Rewards design overview (Confluence: https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5112201230/Pending+Rewards+Design+Overview+V2). Straightforward read. Shared observations in the team Slack channel.
* Posted to Slack that the imminent blocker on pending rewards is Kieren producing designs for how pending rewards should be displayed.
* Raised question in Slack for Zac Barclay: should expiry logic extend to pending rewards? Outlined a scenario where rewards could legitimately stay pending for a long time (e.g. referral rewards that realise only when a referral is made).
* Raised question for Tom McKenzie: whether he's familiar enough with Nick's proposal to define the tests required.
* Raised question for Nick Holt: need to define what triggers reversal of a pending reward on late payment. Expectation is immediate removal, requiring a listener on payment events.

### Slack Digest — 18 Feb

#### Merchant Team
* Tom McKenzie raised concerns in support-merchant that velocity limits may prevent users from fully redeeming rewards before an upcoming deadline — potential customer experience issue.
* Paweł Wasielewski plans to release Mixpanel Lambda v1.113.0 (switching purchase_successful event source from customer-service to purchase-service). EC ticket approved.
* Paweł Pęcikiewicz requested review of PR for My Plan screen rework — extracting logic into custom hooks, modular components, parallax/fade animations.

#### DevOps Team
* Phil Stephenson and Nick Gilbert worked through deployment issues: IP exhaustion and RBAC permission problems blocking releases for various services.
* Lukasz Kowalczyk resolved IP pool issue that was causing Argo deployment failures.
* Nick Holt requested review for a logging configuration change in prod.
* Piotr Niebylski questioned why credit-risk-service accesses other services' DynamoDB tables and SQS queues directly. Marcin Żołna explained it's temporary — part of graduation logic migration from decisioning-service to credit-risk-service; may refactor direct SQS to private API gateway.

#### EWA / Open Banking
* Rob Nelson pushing hard on open banking integration for EWA. Wants a BE engineer to start immediately. Martin Thorlby-Witham suggested reusing existing open banking service (already has Plaid US components). Rob agreed. Confirms EWA/Extra reprioritisation pressure.

#### Other
* Rory Fielding noted in eol-device-restrictions that Expo 56 (expected ~May) will increase minimum iOS version — another comms exercise later this year.
* Chris Walker confirmed new web app flag active in staging; showed it during scoping call with third party.
* Marcin Żołna's product-1.49.0 deployment passed 395 tests but failed 32.

### EWA/Extra Meeting
- Zac Barclay briefed on the feature. Nothing substantially new.
- No work identified for Merchant at this stage — I flagged this and nobody challenged.
- Possible work for DevOps on the open banking side. I flagged this and asked to be told of any requests ASAP.
  - Rob Nelson thinks the work would be minimal: an OpenBanking integration capability already exists in production, built for earlier initiatives that were mothballed. The capability itself was never decommissioned.
  - I was surprised — I'd assumed the previous OpenBanking work had been fully mothballed, but only the initiatives were, not the underlying integration.
- Significant product complexity and edge cases still unresolved:
  - Free trials for membership tiers: want to withhold EWA benefit until first payment taken (not available on free trial).
  - Given Extra only gives you EWA, a free trial has questionable value.
  - But then why wouldn't customers just get a free Plus trial? Except they wouldn't have access to EWA until after payment either.
  - Would customers lose EWA benefit if a membership payment is late? Only regain when caught up?
  - Lots of product refinement still to go.
- Pro not being dropped but is lower priority than EWA/Extra.
- Cross-team lead roles:
  - Product: Zac on Extra, Michael Charash on EWA.
  - Tech: not confirmed yet. Rob thinks it will be him and Andrzej.
- Rob is very concerned about front-end capacity across the department.
- Target delivery by end of March confirmed — very aggressive.

* 1:1 with Phil Stephenson. Generally OK but frustrated by the pace of pivots and concerned about quality erosion. Busy with FinCrime fraud work. Optimistic about the new DevOps operating model. Three actions: automate Slack-to-ticket flow for reactive work, set up rotation tag and retire OpsGenie, and lean in on Zephyr Zero debugging.
* EWA sentiment: Phil's discomfort with the EWA pivot is not isolated. Anecdotal evidence that similar concerns are shared by other ICs and at least one manager. Worth monitoring — this is a values-based concern, not just a workload one.
* Deferred review of Nick H's pending rewards design write-up (ZILCH-48222) — not a blocker (he's seeking peer reviews from other engineers); will pick up tomorrow.
* Set up firefighter tag in tech-devops channel and retired OpsGenie for the rotation. Explored auto-response via Slack Workflow Builder to nudge people away from the team user group, but Slack doesn't support triggers based on user group mentions. Settled on updating the channel topic as a low-tech alternative for now.
* Scheduled regular DevOps retro.
* Scheduled regular rota review meeting — first session on 2 March. Plan for the first few sessions: information-gathering only, walking through each alert from the previous fortnight to understand root causes. No solutionising until there's a month or two of data.
* Prioritised task list — moved LaunchDarkly playbook and retro rota update from Later to Next. Reframed Aurora JDBC failover plugin task as a binary risk assessment (are any other services exposed?) and elevated to Next given escalation potential.
* Rory Fielding chasing for sign-off comments on four tickets: ZILCH-47654, ZILCH-48181, ZILCH-48183, ZILCH-48195. All need a comment confirming whether happy for app to go live. Rory has capacity to pick one up today if any are not approved, but needs a response urgently.

### Merchant Stand-up
- Plenty of tickets at 'ready for review' — need to work through sign-offs.
- ZILCH-40366 (gateway service authoriser): ready to go to prod. Tom's concerns satisfied on the basis that it won't be in active use yet — just available in production.
- ZILCH-42041: Platform only just picked up their part. Michal continues to track.
- ZILCH-46517 (fee service playbooks): Michal done, in review with Jacek. Michal wants to 'test' the playbooks by running through them in dev.
- ZILCH-48222 (pending rewards design): Nick H basically done. Wants review.
- ZILCH-48355 (bottom rail hidden on online/storefront tabs): in progress with Ossie. Looks like it might be Android only. Trying to recreate.

## 2026-02-17

* Sent a message to the DevOps team yesterday (16 Feb) outlining the new Jira board setup — Reactive (Kanban) and Planned (Scrum) boards, filter-based routing, and sprint structure through the end of the next iteration. The message promised to use the next day's planning meeting to sort through tickets and talk through backlog management approach. However, the planning meeting had already been cancelled, and this was forgotten when sending the message. The promised follow-up conversation never happened. Self-assessed as poor form — particularly given the team needs focused attention right now.
* Backlog authoring session: worked up three stories (ZILCH-48444, ZILCH-48520, ZILCH-48543) with improved descriptions and GWT acceptance criteria. Also authored an epic (ZILCH-48546, "Categories Banner") for the ZILCH-48543 feature. Established and documented backlog authoring standards across three files: CLAUDE.md (workspace instructions, PBI type table, folder structure), epics.md (title conventions, required/optional sections), and acceptance-criteria.md (GWT and checklist formats, general principle on verifiable outcomes).
* Final 1:1 with Michal Baran before his move to Andrzej's new team on 24 Feb. Discussed his appraisal, shared Andrzej's feedback on why he was selected, and talked through how he's feeling about the transition — excited but anxious.
* Michal Baran active in dev-payments: reported duplicate loan completion messages for a single loan, and created a Jira task to implement an API endpoint to track membership feature changes history. The latter likely relates to the continuity of membership work for Decisioning.
* Pre-refinement meeting with Tom McKenzie and Zac Barclay — discussed the three tickets (ZILCH-48444, ZILCH-48520, ZILCH-48543) subsequently worked up in the backlog authoring session.
* Engineering Leadership Sync meeting:
  - Marcin Zolna shared his team's KPIs for the last five sprints.
  - Shared feedback from Alex Murphy's exit interview.
  - Discussed a strategic pivot: new ask to deliver an EWA tied to a new membership tier by end of March.
  - Discussion about backfills for staff moved to the new Spend Platform team.
* Merchant team Ops hand-off — regular rotation handover meeting. Discussed ZILCH-48542 (add DB-level unique constraint to prevent duplicate rewards on LoanCompleted events), which ties to the duplicate loan completion messages Michal flagged in dev-payments.
* Merchant refinement meeting — refined and estimated ZILCH-48520 (Correct banner copy for Anywhere unlock) and ZILCH-48543 (Add rotating banner to Categories page), plus the defect ZILCH-48542. Left ZILCH-48444 (Exclude boost from rewards calculation) unestimated — Zac wants to sense-check it with Tom Wood first. Good call: the ask seems odd — offering rewards only on the loan portion doesn't make sense given that we normally only offer rewards on debit purchases (effectively 100% boost) and not credit purchases. Attempted to story out epic ZILCH-47121 (Pending Rewards) but didn't get far — the epic went to "In Dev" before being storied out (not great practice but not unusual at Zilch); the first task was to produce a design that would inform the remaining tickets.
* Continued working on backlog-authoring standards and tooling within this knowledge base system, including authoring the Categories Banner epic (ZILCH-48546).

## 2026-02-16

* Met with DevOps team to refine and task out ZILCH-47773 (prepare environments for customer-web-app deployments). Also added ZILCH-48449 (infrastructure remediation for pen test findings) to the new-web epic. Estimated effort suggests ZILCH-47773 could take the full sprint.
* Gateway service next-steps meeting. Decided to take the iterative approach: deploy the new authoriser Lambda for authorisation while continuing to use customer-service for other gateway functions, rather than building a full gateway-service before going to production.
* Met with Decisioning (Tomasz Więckowski, John Strawhorne) and Michal re continuity of membership requirements. Decisioning seemed to assume Merchant would already be cracking on with the work based on previous conversations — similar attitude to Tommy recently. In reality, there are still gaps in the definition that need filling from their side. After discussion, agreed an approach: Decisioning need to provide new APIs for understanding longevity of features per customer. Onus is with them, not Merchant. Michal to write up a Jira ticket for Decisioning to refine and estimate.
* 1:1 with Andrzej Lorenz
* Published DevOps operating model announcement to engineering-wide Slack channel: hybrid Scrum/Kanban from Sprint 11.4, with fixed capacity reserved for reactive work.
* Tom presented defect analysis findings to the Merchant team (with Nikos). Stats and insights were reasonable. Follow-up workshop on common root causes was unstructured and unhelpful — Tom picked on people randomly with oddly specific questions, not necessarily related to their function or domain. Little gained from it.
* Approved EC-2001 and EC-1999.
* Slack conversation with Rob Nelson re new-web prioritisation. Rob raised concern that dev/staging setup vs productionised could be significantly more work. Agreed to prioritise for Sprint 11.4, starting next week. Target: ready by end of the iteration, giving 11.5 to finalise. Rob happy with the plan.

### Completed tasks
- Wrote up Nick H's 1:1 notes from 11th Feb.
- Cleared down Slack messages. Rationalised Slack organisation, recap tool usage, and channel notification settings to reduce missed messages.
- Set up Jira to support the new DevOps hybrid Scrum/Kanban process.
- First pass on DevOps backlog — assigned existing tickets to planned/reactive tracks.
- Created DevOps capacity spreadsheet (adapted from Merchant).

### Stand-up
- Jacek: affiliate integration service (ZILCH-46901, Partnerize) — found and resolved concurrency problems at higher volumes during testing. Thinks it's ready for production. Will move to sign-off. Platform blockers removed with temporary solution.
- Jacek: gateway service — authoriser ready for review. Has doubts about how to go to production. Will organise a meeting with stakeholders to take forward.
- Michal: toggle backfill done and in sign-off.
- Michal: getting started with playbooks for fee changes.
- Michal: coordinating decommissioning of MSSQL fee database with Platform.
- Nick H: on leave.
- Ossie: fixed ZILCH-48105 (which caused an incident). Yorkor will test.
- Ossie: will bring ZILCH-48355 (bottom rail hidden on online/storefront tabs) into sprint — everything else now in review or QA.

## 2026-02-13

### Stand-up
- ZILCH-43742: Tom will add a QA comment, then I can sign off.
- ZILCH-46368: Jacek will review.
- ZILCH-46901 (Partnerize): solution found on blocker. Platform side has a lot of work for the proper solution — Jacek will create a bucket independently for now. Focusing on it today to get it signed off.
- ZILCH-47687: in QA with Tom. He wants to add proof to the ticket before moving it forward.
- ZILCH-48222: Nick H has scheduled a meeting to review the design with the team.
- ZILCH-48084: now fixed. Needs QA sign-off — Tom will look at it today.
- ZILCH-43416: not yet picked up. May no longer be a problem — may be possible to just close it.
- ZILCH-48105: in progress with Ossie.
- ZILCH-48303: engineering done, ready for testing. Tom wanted tests for both toggle-on and toggle-off cases. Discussed — he's satisfied the automated tests cover this and it can move forward.

### PM
- Reviewed fee-service backlog in Jira — identified 7 Merchant Team tickets in "To Do" state; logged to fee-service project file.
- Refinement prep — prepared descriptions for ZILCH-48355, ZILCH-48181, ZILCH-48195 (plus others done manually). Notified team of refinement candidates.
- Published Backlog Management page to Confluence; updated local playbook to point there as single source of truth.

### Completed tasks
- Set up cross-team refinement with Decisioning and Merchant (continuity of membership, Zilch Pro).

### Observations
- Testing discussions at stand-up are perennial — what types/levels of testing are appropriate for a given ticket. Suggested Tom work on a test policy document that the team can collectively sign up to.
- Stand-ups tend to overrun. Problem for me as DevOps stand-up follows immediately. Suggested extending from 15 to 20 minutes but committing to finishing strictly on time.

## 2026-02-12

* 1:1 with Nick Gilbert. Topics: pressure from Chris Walker on server-side rendering delivery (agreed with Rob Nelson to treat as planned work); timing for starting DevOps Scrum process (Nick suggested next iteration, I pushed for sooner); tech-devops channel noise (action to set up firefighter tag); his appraisal (feels fair and accurate, noted perception of pace — attributes to not communicating blockers); Piotr's ZOE presentation (good implementation, but large code submission without iterative review — pattern of working independently); feedback for me (lean in on on-call rota); uncertainty about Platform team leadership.
* Meeting with Zac and Ethan re Pro roll-out planning — agreed 4–6 week experimentation window post-launch, then BAU with hold-out group for 6 months.
* Catch-up with Nikos re QA perspective on Pro roll-out — wants two weeks internal testing then 1% cohort for a week before experiments begin.
* Time spent refining personal knowledge management system.
* Wrote up Abhishek Chatterjee's 1:1 notes from 11th Feb.
* Built and presented Sprint Report #11.2 — published as a Confluence blog post in the Merchant space. Covers sprint plan, scope changes, carried-forward items, burndown, capacity planning, and defect cumulative flow. Nick H demoed the expiring rewards piece; Michal demoed the blocked rewards piece. Observations:
  - Including a sprint report in the demo was experimental. Polarised reaction: a couple of FE devs pushed back on seeing it; Ossie was very positive. Suggests there isn't a shared understanding of what the demo meeting is for.
  - Kieren Messenger announced in meeting chat that the Merchant team would pick up a specific piece of work in an upcoming sprint. This is outside his remit as a product designer — planning and scope commitments are my responsibility. Part of a pattern of stepping outside his lane.

### Stand-up
- ZILCH-39822: ready for sign-off.
- ZILCH-40366: in progress with Jacek.
- ZILCH-42041: still awaiting Platform to pick up a blocking task. Michal chased — situation unclear.
- ZILCH-43742: Jacek reviewed Nick H's PR. Found a place where removed code might still be called from FE. Back with Nick H to check with Ossie.
- ZILCH-46368: in progress with Michal — should be moving forward today.
- ZILCH-46517: awaiting pick-up.
- ZILCH-46901: in progress with Jacek. Reacts on Snowflake workspace bucket update event. Bucket not created in dev environments, blocking work. Jacek and Platform agreed on hosting a bucket across all environments — still deciding where. Should resolve soon.
- ZILCH-47687: test working, evidence added to ticket. Available for QA review.
- ZILCH-48084: in progress with Nick H. Related to Aurora connectivity issue. Way forward: downgrade JDBC driver for now. New ticket created for proper fix.
- ZILCH-48105: in progress with Ossie. Might need to be down-prioritised in favour of RN new Architecture bugs.
- ZILCH-48222: in progress with Nick H. Design task, but he's talking about tests — seems to be validating ideas.
- ZILCH-48248: was with Nick H. Can be moved to QA sign-off.
- ZILCH-48303: in progress with Michal. Would like to release today.
- ZILCH-40343: Tom ran complete regression — all passed. Tried to mimic 401 for retry test. Needs to work with Ossie to verify test.

## 2026-02-11

* Merchant stand-up
* 1:1 with Abhishek Chatterjee (Architect)
* Scheduled Iteration 12 initiative review meeting with Zac for 12th Feb
* Sent Kieren Messenger money owed for Alex Murphy's leaving gift
* ZILCH-46355 (Block Rewards on Late Payments, Michal Baran) released without a LaunchDarkly feature flag. **Retro item** — this is the second time in recent sprints that LD flag discipline has come up. Previous retro action was to require full LD flag enablement for minimum 3 days with regression and tests. Need to discuss why process wasn't followed.
* Confirmed with Zac that milestone rewards has been descoped from Zilch Pro — dropped early due to insufficient value vs effort. May return as a separate initiative. Updated project log.
* Clarified upgrade/downgrade status with Payments and Decisioning (Pro tier migration)
* Checked higher rewards rate configuration for Pro — confirmed done
* Started async conversation with Steve Rayko about vision for L5 FE role
* Wrote up Jacek's 1:1 notes from 10th Feb
* Updated Nick H's file with year-end appraisal notes
* Chased Marcin Żołna and Tommy Kwok on ZILCH-46727 (only apply additional rewards for loans in continuous subscription) — no Merchant backlog items for this, concerned it's gone stale. Got a response pointing to a Slack thread — need to follow up with Jacek and Michal on what was agreed with Decisioning and capture as tickets.

## 2026-02-10

* Sprint planning — Merchant #11.3
* Checked where 23 March falls in the sprint cycle — last day of Iteration 11 and last day of a sprint. Stefan arrives in time for retro, starts fresh on day two.
* Clarified thinking on FE competency lead role with Rob Nelson
* Understood On Call Rota setup from DevOps team

## 2026-02-09

* Updated ADR for offer-service on Confluence — added "Notes and Corrections" section acknowledging pre-approval creation and naming issue
* Wrote detailed Tastecard project log from Jira and Confluence research — context, architecture, personnel, full timeline, and open items
* Wrote Incident-452 post-incident review
* Raised epic ZILCH-48173 for Incident-452 mitigations
* Updated Incident-452 record in Datadog
* Informed Merchant team that Michal Baran is moving to a new team on 24 Feb
* Created on-call rota project — documented context, tooling, personnel, and open questions
* Organised task list — added Waiting On section, reorganised priorities
* Started async conversation with DevOps team about on-call rota setup
* Authored backlog management playbook — defined ticket lifecycle states, field rules, activities, and backlog hygiene principles; created team-facing Confluence draft; published to Confluence
* Created Stefan onboarding project — captured key contacts, significant work to brief on, Chris Walker/competency lead dynamic, and tasked out onboarding preparation
* Retro (Tom hosting) — sprint 11.2 digest:
  * **Liked:** Plus launched to all customers; adaptive header at 20%; rewards refunding live; Alex's handover documentation praised; Maestro epic closed; improved incident reaction — Incident-452 caught early because we kept LD flags aligned between prod and pre-prod
  * **Learnt:** LD flag interactions not tested in combination (+2); capacity pressure over coming weeks with two engineers leaving (+2); need better test evidence in tickets (+2); rewards expiry scope grew outside normal process; cross-team dependencies likely to block without strong coordination
  * **Lacked:** Running out of BE tickets, again (+3); lack of informal collaboration — "where are the water cooler chats?" (+3); continued lack of clarity on Pro partnerships (+1); unpredictable waits on platform tickets; insufficient communication about fee service staging changes
  * **Actions:** Stricter test evidence requirements; full LD flag enablement for minimum 3 days with full regression and tests for each user state; create a playbook for enabling LaunchDarkly flags

## 2026-02-06

* Wrote flash report for Merchant team
* Wrote flash report for Payments team (covering for EM on leave; content from Marek Chodak)
* Wrote flash report for DevOps team
* 1:1 with Piotr
* Wrote flash report for Issuer team (covering for EM on leave)
* Wrote flash report for Acquirer team (covering for EM on leave)

## 2026-02-05

* Attended Zilch Pro sync meeting
* 1:1 with Tom McKenzie
