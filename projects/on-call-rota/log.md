# On Call Rota

## Also Known As

On Call, Incident Response Rota

## Context

24/7 incident response rota staffed by engineers from the DevOps and Platform teams. Has lacked managerial oversight since the Platform team manager left — currently self-organised with Matt Swirski (Platform) coordinating.

Nicklas is taking ownership as part of managing the DevOps team. The goal is to provide the managerial oversight that's been missing, not necessarily to change how the rota operates day-to-day.

### Tooling

- Rota is managed in Jira Ops: https://payzilch.atlassian.net/jira/ops/teams/og-1e258c57-ef25-4b34-9772-49388624ebf0/on-call

### Open Questions

- How are shifts decided — is it mostly self-organised?
- What does Matt Swirski's current coordination role involve?
- Why is Paul Batey (Platform) not on the rota?

## Personnel

### On the rota

- **Abdul Wahid** — Platform team
- **Matt Swirski** — Platform team, currently organising the rota
- **Charlie Hurst** — Platform team
- **Chris Prowse** — Platform team
- **Phil Stephenson** — DevOps Engineer (Level 4), de facto tech lead
- **Nick Gilbert** — DevOps Engineer (Level 3)
- **Piotr Niebylski** — DevOps Engineer (Level 4)
- **Lukasz Kowalczyk** — DevOps Engineer (Level 2)

### Not on the rota

- **Paul Batey** — Platform team (reason unknown)

## Running Notes

### 2026-03-02

First rota review meeting. Chris Prowse walked through the toolchain. Worked through most alerts from the fortnight to 2 March (three skipped due to time).

**Toolchain overview (Chris Prowse):**
- Rota is set up as `SRE_Team` in Jira Service Management.
- Integrations tab lists alert sources. Email supported, but only Datadog is realistically used.
- On-call tab shows routing, with separate configurations for in-hours and out-of-hours.
- Alert priorities are set at source (i.e. in Datadog).
- Datadog alerts flow into #platform-alerts-incidents on Slack. Not every message in that channel results in a call-out — look for Jira messages to identify actual incidents.
- Personal notification preferences (SMS, phone call, etc.) are set by each team member individually.

**Alerts reviewed:**

*Snooze Config requests anomaly*
- Has been silenced. Should alert the owning team directly, not the on-call channel.
- Action: Follow up with Phil Stephenson to identify which team should own this, then discuss handover with the relevant EM.

*Datadog Aurora Agent CrashloopBackOff*
- Datadog's DB monitoring agent is crashing and needs diagnosis.
- Sits with DevOps/Platform.
- Jira ticket raised: [PO-1676](https://payzilch.atlassian.net/browse/PO-1676).
- Action: Track PO-1676 to ensure it gets picked up.

*AWS Lambda throttling (overdue-outsystems)*
- Throttling is normally treated as an error (valid messages go to DLQ, risking data loss), so a generic alert fires.
- However, throttling has been intentionally enabled for this specific lambda. It is owned by the Retain team.
- Action: Catch up with Phil Stephenson async on how to handle this with Retain.

*product-service container restarts*
- Container crashed because the Datadog sidecar crashed. Not believed to be recurrent.
- Action: Monitor for recurrences in future rotations; no further action if one-off, as the service recovered.

*Cashflow latency anomaly*
- Seen a few times. Owned by the Acquirer team.
- Question raised: should this alert on an Acquirer team channel rather than on-call?
- Action: Monitor for recurrences. If it becomes recurring noise, discuss appropriate alert sensitivity and channel routing with the Acquirer team EM (Grzegorz Ziemiański).

*String/binary data truncation (P1/P2)*
- Generic monitor. Data is too large for a DB column.
- Primary culprit is `acquirer-service`. Significant due to risk of actual data loss or corruption.
- Acquirer team ticket [ZILCH-44139](https://payzilch.atlassian.net/browse/ZILCH-44139) exists to fix this.
- Action: Chase Grzegorz Ziemiański to ensure ZILCH-44139 is planned into a sprint.

**Skipped (ran out of time):** Three less frequent alerts not reviewed this session.

### 2026-02-18

Regular rota review meeting scheduled. First session on 2 March.

**Agenda for the first few sessions (information-gathering only):**
- Set the expectation upfront: no solutionising yet, just data gathering.
- Walk through every alert from the previous fortnight.
- For each alert, understand it well enough to reason about root cause.
- After a month or two of data points, shift to looking for patterns and solutions.

### 2026-02-09

Project created. Two immediate actions identified:
1. Find out from the DevOps team how the rota is captured in tools, how shifts are decided, and how self-organised it is.
2. Set up a regular meeting with on-call staff to review upcoming tickets.
