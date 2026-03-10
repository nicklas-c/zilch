# Activity

## 2026-02-24

- Resolved fee schedule ownership ambiguity for EWA/Extra with Andrzej — confirmed Spend Platform will handle it.

## 2026-02-23

- Led EWA/Extra impact assessment with the Merchant team. Concluded the team is broadly in the clear, with two caveats identified and documented (fee schedule ownership ambiguity, overlap with Pending Rewards/Blocking Rewards).
- Prepared Sprint 11.4 planning — reviewed all work streams, assessed capacity (14 BE / 7 FE), prepared agenda, and pre-triaged defect candidates.
- Escalated Rory Fielding's behaviour (bypassing me to pressure Ossie directly) to Mike Davis. Handled proportionately: handed over for Mike to manage.
- Closed Incident-417 — ZILCH-46517 (fee-change playbooks) was the last mitigation ticket.
- Designed the knowledge base restructure model: single main log with inline tagging and periodic compaction into per-entity digests.

## 2026-02-20

- Wrote and distributed the Merchant weekly flash report covering rewards, race condition fix, Pending Rewards design, Incident-452, Intelligent Commerce, feature flag audit, gateway service, and fee-service latency spike.
- Attended EWA/Extra product and planning meeting. Participated in whiteboard exercise to identify cross-team work allocation; confirmed no Merchant scope at this stage and flagged potential DevOps dependency on open banking.
- Interviewed candidate for L4 Back End Engineer role (Krakow).
- Led refinement meeting. Tamara Quinn joined to discuss Pay Monthly / rewards interaction.

## 2026-02-19

- Signed off three tickets (ZILCH-48355, ZILCH-43416, ZILCH-48222).
- Reviewed and gave feedback on Michal Baran's fee-service playbooks (ZILCH-46517).
- Led cross-dependency meeting with Merchant BE engineers on Pending Rewards — concluded feature-level events are the preferred approach and identified Decisioning as the dependency.
- Chased Aurora connectivity risk assessment across Merchant, Platform, and DevOps. Established that production is safe: issue is specific to JDBC driver v3; all current production services are on v2.
- Conducted 1:1 with Tom McKenzie — gave feedback on defect analysis presentation facilitation; reinforced his authority as QA gatekeeper; advanced the test policy document initiative.

## 2026-02-18

- Completed the DevOps operating model initiative: set up sprint planning, refinement, and retro meetings; rescheduled stand-ups; reviewed backlog track assignments with the team.
- Signed off six tickets in a batch (ZILCH-43742, ZILCH-48248, ZILCH-40343, ZILCH-46901, ZILCH-47687, ZILCH-48105).
- Created tech-zilch-pro Slack channel for cross-team Pro release coordination.
- Drafted Zilch Pro Release Plan for Confluence — seeded with feature list, roll-out plan, and key constraints.
- Set up DevOps firefighter tag in Slack and retired OpsGenie for the rotation.
- Scheduled regular DevOps retro and rota review meetings.
- Reviewed Nick Holt's Pending Rewards design and raised follow-up questions on expiry logic, late payment reversal triggers, and test readiness.
- Conducted 1:1 with Phil Stevenson — captured EWA sentiment concerns and three operational actions.
- Authored ZILCH-48608 — test policy document task for the Merchant team.

## 2026-02-17

- Authored three Jira stories (ZILCH-48444, ZILCH-48520, ZILCH-48543) and one epic (ZILCH-48546, Categories Banner) with improved descriptions and GWT acceptance criteria.
- Established backlog authoring standards: documented PBI types, epic conventions, and acceptance criteria formats.
- Published DevOps operating model announcement to engineering-wide Slack: hybrid Scrum/Kanban from Sprint 11.4.
- Participated in Engineering Leadership Sync — shared Alex Murphy exit interview feedback; discussed EWA strategic pivot and Spend Platform backfills.
- Conducted final 1:1 with Michal Baran ahead of his move to the new team. Shared Andrzej's feedback on why he was selected and discussed the transition.
- Led Merchant refinement meeting — refined and estimated three tickets; identified a questionable scope item (boost exclusion from rewards) and flagged it for product sense-check.

## 2026-02-16

- Set up Jira boards and sprint structure for the new DevOps hybrid Scrum/Kanban process. Created capacity spreadsheet.
- Met with DevOps team to refine ZILCH-47773 (customer-web-app environment prep). Added ZILCH-48449 to the New Web epic.
- Led Gateway Service next-steps meeting — decided on iterative approach: deploy authoriser Lambda first rather than building full gateway-service.
- Met with Decisioning re continuity of membership requirements. Pushed back on assumed Merchant ownership and clarified the onus is with Decisioning to provide new APIs.
- Agreed New Web prioritisation with Rob Nelson — target Sprint 11.4, ready by end of iteration.
- Conducted 1:1 with Andrzej Lorenz — discussed Michal backfill, Jacek rotation, new team leadership, and L5 FE role vision.

## 2026-02-13

- Reviewed fee-service backlog in Jira and identified 7 Merchant Team tickets in To Do.
- Prepared refinement candidates with descriptions for three tickets.
- Published Backlog Management page to Confluence and linked it as the single source of truth from the local playbook.
- Set up cross-team refinement with Decisioning and Merchant for continuity of membership work.
- Initiated test policy document idea with Tom McKenzie — proposed codifying testing expectations to reduce recurring stand-up debates.
- Conducted 1:1 with Lukasz Kowalczyk — shared appraisal feedback; discussed Piotr's ZOE work and Lukasz's development path.

## 2026-02-12

- Built and presented Sprint Report #11.2 — published as Confluence blog post covering sprint plan, scope changes, burndown, capacity planning, and defect cumulative flow.
- Conducted 1:1 with Nick Gilbert — discussed SSR pressure (aligned with Rob Nelson to treat as planned work), DevOps Scrum timing, appraisal feedback, and Piotr's ZOE code review patterns.
- Agreed Pro roll-out plan with Zac Barclay and Ethan: 4–6 week experimentation window, then BAU with hold-out group for 6 months.
- Agreed QA roll-out plan with Nikos Sofianos: two weeks internal testing, then 1% cohort for a week.

## 2026-02-11

- Conducted 1:1 with Nick Holt — delivered year-end appraisal feedback. Discussed communication growth areas; feedback landed well despite expectation of a difficult conversation.
- Conducted 1:1 with Abhishek Chatterjee.
- Identified LaunchDarkly flag discipline failure (ZILCH-46355 released without LD flag) and flagged as retro item.
- Started async conversation with Steve Rayko about vision for L5 FE role.
- Confirmed milestone rewards descoped from Zilch Pro — updated project records.

## 2026-02-10

- Led Sprint Planning for Merchant Sprint #11.3.
- Clarified FE competency lead role with Rob Nelson.

## 2026-02-09

- Wrote Incident-452 post-incident review. Raised mitigations epic ZILCH-48173. Updated DataDog record.
- Authored and published backlog management playbook to Confluence — defined ticket lifecycle states, field rules, and hygiene principles.
- Created Stefan Amarie onboarding project — captured key contacts, significant work to brief on, and tasked out onboarding preparation.
- Created On-Call Rota project — documented context, tooling, personnel, and open questions; started async conversation with DevOps team.
- Wrote detailed Tastecard project log from Jira and Confluence research.
- Informed Merchant team of Michal Baran's upcoming team move.
- Participated in Sprint 11.2 retro — four retro actions agreed including LD flag discipline and test evidence requirements.

## 2026-02-06

- Wrote flash reports for five teams (Merchant, DevOps, Payments, Issuer, Acquirer) — covering for two EMs on leave.
- Conducted 1:1 with Piotr Niebylski — delivered appraisal feedback; discussed hybrid Scrum/Kanban proposal; gave positive feedback on ZOE work.

## 2026-02-05

- Conducted 1:1 with Tom McKenzie — discussed Maestro handover readiness, defect analysis progress, Nick H testing tension, and Nikos's appraisal feedback.
