# Log

## 2026-02-17

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

* 1:1 with Nick G
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
