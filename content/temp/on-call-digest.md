# On-Call Rollout — Digest for Merchant Team Conversation

## Background

Zilch is moving to a "You Build It, You Run It" model. Service-owning teams take operational responsibility for the services they build, including monitoring and responding to alerts. SRE (DevOps and Platform) shifts to building a reliable platform, improving observability, and providing tooling.

This has been phased over several months:

| Phase | What | Status |
|---|---|---|
| 0 — Pilot | Payments and Retain teams ran engineering-owned on-call to validate the model | Complete |
| 1 — Visibility | Alert visibility increased across all teams (intentionally noisy) | Complete |
| 2 — EM Paging | P1/P2 alerts routed to EMs 24/7 to drive ownership of noisy alerts | Complete |
| 3 — Operational Readiness | Teams set up rotations; alerts route to teams during working hours; escalation paths active | **Now** |
| 4 — Full Ownership | All teams operating 24/7 on-call | **Target: 3 August** |

## Setup Requirements

- **Primary and Secondary on-call rotations** in JSM for the Merchant team.
- All SWEs and QAs participate. EM participation is encouraged but optional.
- Ensure all on-callers have correct JSM notification settings and phone config for paging.

### How to Configure in JSM

1. Go to https://payzilch.atlassian.net/jira/ops/who-is-on-call (or click "On-call schedules" in the left sidebar)
2. Click on a rota (e.g., "Acquirer Primary")
3. Click "View Schedule"
4. On the rota, click `...` → Edit
5. Under Rotations, click `...` → Edit
6. Configure participants, rotation type, handover time, etc.

## Escalation Policy

| Priority | When paged |
|---|---|
| P1 | Always (24/7) |
| P2 | Always (24/7) |
| P3 | Business hours only |
| P4 | Not paged |

EMs are on the escalation path (configurable per team) but not required on primary/secondary.

## Compensation

### Standby Stipend

- Approved. Paid for being available on standby, regardless of whether you're paged.
- Rates were shared as an attachment on Steve's EM post (9 Jul). I need to check the exact figures.
- **B2B contractors are included** (confirmed by Steve, shared with DevOps on 16 Jul).

### Call-out Compensation

- Mechanism is **TOIL** (Time Off In Lieu).
- Exact policy details still being finalised by the People team.

### Contracts

- Andrzej believes existing contracts already cover on-call. HR is verifying.

## Incident Response — What Are We Responding To?

An incident is:

> An unplanned disruption or degradation of service that is actively affecting customers' ability to use the product and should be addressed immediately.

"Customers" includes internal customers.

### Incident vs Defect

The key distinction is **immediacy**:

- **Incident** = requires immediate response, interrupts normal delivery, triggers incident response process.
- **Defect** = prioritised into sprint backlogs, handled through normal SDLC.

Incidents are expensive (context switch + post-mortem). If over-used, they grind teams to a halt.

### Severity vs Priority

- **Severity** determines the *response* (how urgently we act, how much risk we accept in the fix).
- **Priority** determines how urgently the *Jira ticket* must be delivered (not always correlated).

Example: A SEV2 might be mitigated operationally, with the root-cause fix delivered as a P3 in a future sprint. A SEV3 with no workaround might need a P1 hotfix immediately.

### Declaring Incidents

Incidents are declared in Datadog: https://app.datadoghq.eu/incidents/new

### Severity Levels

> If you are unsure which level an incident is (e.g. not sure if SEV-1 or SEV-2), **treat it as the higher one**. During an incident is not the time to discuss severities — assume the highest and review during a post-mortem.

| Severity | Description | Typical Response |
|---|---|---|
| SEV-1 | **Critical issue warranting public notification and executive liaison.** System in critical state, actively impacting a large number of customers. Functionality severely impaired for a long time, breaking SLA. Customer-data-exposing security vulnerability. | Major incident response. Raise in DataDog, post to #zilchops, notify stakeholders, public notification. |
| SEV-2 | **Critical system issue actively impacting many customers' ability to use the product.** Purchases severely impaired. Data loss/corruption. Web app unavailable or severely degraded. Monitoring of major incident conditions impaired. | Major incident response. Raise in DataDog, post to #zilchops, notify stakeholders. |
| — | **Anything above this line is a "Major Incident" and triggers full incident response.** | — |
| SEV-3 | **Stability or minor customer-impacting issues requiring immediate attention from service owners.** Partial loss of functionality (not majority of customers). Likely to become SEV-2 if left. No redundancy in a service. | High-urgency page to service team. Top priority. Rollback if deployment-related. Trigger incident response if it escalates. |
| SEV-4 | **Minor issues requiring action but not affecting customer ability to use the product.** Performance issues, individual host failure, delayed job failure, cron failure. | Low-urgency page to service team. First priority above normal tasks. Monitor for escalation. |
| SEV-5 | **Cosmetic issues or bugs, not affecting customer ability to use the product.** | Jira ticket. Assign to owner of affected system. |

**Key points:**
- All SEV-2s are major incidents, but not all major incidents need to be SEV-2s. If you need coordinated response even for lower severity, trigger the process.
- SEV-1 and SEV-2 incidents that meet security incident criteria (ZP03) or exceed Important Business Service impact thresholds require FCA reporting. Compliance team handles submission.

### Further Reading

- Incident Response: https://payzilch.atlassian.net/wiki/spaces/ZO/pages/427720705/Incident+Response
- Severity Definitions: https://payzilch.atlassian.net/wiki/spaces/ZO/pages/746586134

## Questions Raised by Other Teams

These came up in the #eng-management thread and are useful context for anticipating my team's questions:

| Question | Answer |
|---|---|
| Do I have to be on-call? | Yes. Everyone participates. |
| Do I need the Jira app on my phone? | No. Can acknowledge via laptop, Slack, or phone call. |
| What if I get paged overnight — do I still work a full day? | TOIL applies. Policy details TBC from People team. |
| Are rates fair? | Rates are what they are — previously there was no stipend at all. |
| Do B2B contractors get the stipend? | Yes (confirmed). |
| What if my team is too small? | Merge rotas with a compatible team. Rule of thumb: <5 people = too small. |

## Team-Specific Considerations

### Merchant Team

- Large enough for its own rota (currently ~6-7 engineers + QA).
- Jacek goes on leave 26 Jul — factor into rotation when building the schedule.
- Amr starts 27 Jul — too new for on-call immediately; exempt initially, bring in after settling.
- The team hasn't been on primary on-call before (only the EM paging phase). Expect questions.

### DevOps Team

- Already on the SRE rota, so this is less of a change for them.
- The stipend is new and welcome.
- B2B inclusion was the key question — now answered.

## Open Actions

- [ ] Check the stipend rates attachment from Steve's 9 Jul post
- [ ] Decide on EM participation in the Merchant primary/secondary rotation
- [ ] Build the Merchant rota in JSM (accounting for Jacek's leave and Amr's onboarding)
- [ ] Prepare talking points for Monday's team conversation
