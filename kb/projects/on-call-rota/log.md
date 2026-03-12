# On Call Rota

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
- **Phil Stevenson** — DevOps Engineer (Level 4), de facto tech lead
- **Nick Gilbert** — DevOps Engineer (Level 3)
- **Piotr Niebylski** — DevOps Engineer (Level 4)
- **Lukasz Kowalczyk** — DevOps Engineer (Level 2)

### Not on the rota

- **Paul Batey** — Platform team (reason unknown)

## Digest

### 2026-02-09

Project created. Two immediate actions: (1) find out from DevOps how the rota is captured, how shifts are decided, and how self-organised it is; (2) set up a regular meeting with on-call staff to review upcoming tickets. Started async conversation with DevOps team.

### 2026-02-10

Received information from DevOps team on how the on-call rota is set up.

### 2026-02-12

Nick Gilbert (1:1 feedback) suggested leaning in more on the on-call rota.

### 2026-02-18

Regular rota review meeting scheduled — first session on 2 March.

**Agenda for the first few sessions (information-gathering only):**
- No solutionising yet — just data gathering.
- Walk through every alert from the previous fortnight.
- For each alert, understand root cause.
- After a month or two of data, shift to patterns and solutions.

### 2026-03-02

First rota review meeting. Chris Prowse walked through the toolchain. Worked through most alerts from the fortnight to 2 March (three skipped due to time).

**Toolchain overview (Chris Prowse):**
- Rota set up as `SRE_Team` in Jira Service Management.
- Integrations tab lists alert sources; only Datadog is realistically used.
- On-call tab shows routing with separate in-hours and out-of-hours configs.
- Alert priorities set at source (Datadog).
- Datadog alerts flow into #platform-alerts-incidents on Slack; look for Jira messages to identify actual incidents.
- Personal notification preferences set individually by each team member.

**Alerts reviewed:**

*Snooze Config requests anomaly*
- Silenced. Should alert owning team directly. Action: follow up with Phil Stevenson to identify owner, then discuss handover with relevant EM.

*Datadog Aurora Agent CrashloopBackOff*
- DB monitoring agent crashing. Sits with DevOps/Platform. Ticket PO-1676 raised. Action: track to ensure pickup.

*AWS Lambda throttling (overdue-outsystems)*
- Throttling intentionally enabled for this lambda (Retain team). Generic alert fires because throttling normally means DLQ risk. Action: discuss handling with Phil Stevenson and Retain.

*product-service container restarts*
- Crashed due to Datadog sidecar crash. Not believed recurrent. Action: monitor.

*Cashflow latency anomaly*
- Owned by Acquirer team. Action: monitor; if recurring, discuss routing with Acquirer EM (Grzegorz Ziemiański).

*String/binary data truncation (P1/P2)*
- Generic monitor. Data too large for a DB column; primary culprit is acquirer-service. Risk of data loss. Ticket ZILCH-44139 exists. Action: chase Grzegorz to ensure it's sprint-planned.

**Skipped:** Three less frequent alerts not reviewed this session.
