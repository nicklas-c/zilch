# Observability Migration — Project Plan

**Status:** Work in progress

---

## Overview

**Objective:** Reduce Zilch's dependency on Datadog by evaluating alternative observability platforms and executing a migration.

**End-state model:** Open question — single replacement, multi-vendor, or hybrid.

**Design principle:** Front-load DevOps effort so the team can move on to other priorities once the infrastructure work is done.

---

## Phases

### Phase 1 — Evaluation & Foundation

Four workstreams, partially parallelised.

#### 1a: PoC Instrumentation

OTel collection infrastructure sufficient to get representative telemetry flowing into each candidate platform. Vendor-agnostic — both candidates accept standard OTLP.

Tracked as [ZILCH-57057](https://payzilch.atlassian.net/browse/ZILCH-57057) — in progress. Scope:

- Explore and select tooling to orchestrate OTel agents and collectors
- Agents and collectors deployed to at least one cluster (unified dev, zephyr, or both)
- Collection proven via a simple deployment of an open-source Grafana instance
- Explore zero-code instrumentation
- Covers metrics, logs, and traces
- At least one Onboarding service switched from DD-native SDK to an OTel equivalent

**Estimated duration:** 4 weeks.
**Depends on:** Nothing — already underway.

#### 1b: PoC Evaluation

Two PoCs in parallel, assessed against the published [PoC Success Criteria](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/5967675402/PoC+Success+Criteria):

| Vendor | PoC Team |
|---|---|
| Grafana Cloud | Onboarding |
| Coralogix | Merchant |

**PoC scope:** At least one backend service, one Lambda function, the new web application, and the mobile application.

**Assessment:** Representative stakeholder group — PoC teams, DevOps, Platform, and senior engineering leadership.

**Depends on:** Phase 1a.

#### 1c: Production OTel Build

Full production-grade dual-ship OTel Collector architecture. Collectors deployed alongside the existing Datadog agent, exporting to both Datadog (`datadogexporter`) and a placeholder OTLP endpoint for the eventual chosen platform.

This is the largest single block of DevOps work on the project. Builds on Phase 1a; runs in parallel with the PoC evaluations.

**Node-based workloads (EC2):**
- DaemonSet OTel Collector via `opentelemetry-operator`: `filelogreceiver` (logs, carrying over current exclusions), `hostmetricsreceiver`, `kubeletstatsreceiver`
- Gateway/Deployment OTel Collector: `k8s_cluster` receiver, `prometheusreceiver` (scraping existing custom KSM), OTLP receiver on 4317/4318 (traces), `statsdreceiver` (DogStatsD compatibility)

**Fargate workloads:**
- Metrics and traces: OTel Collector sidecar-mode via `opentelemetry-operator`, scraping kubelet cAdvisor through the API server proxy
- Logs: Custom in-house OTel receiver using `client-go`'s pod log-stream API. No off-the-shelf OTel Collector Contrib receiver exists. Fallback: Fluent Bit + CloudWatch. Fargate-to-EC2 migration was considered as an alternative but ruled out (significant effort, cross-team dependencies).

**Admission controller:**
- Sidecar-mode `OpenTelemetryCollector` CR with `sidecar.opentelemetry.io/inject` annotation, replacing Datadog's Fargate sidecar injection profile

**Sizing:**
- Determined fresh per role via sizing/load-test pass — not mirrored from existing Datadog agent config.

**Depends on:** Phase 1a.

#### 1d: Application SDK Audit

Survey the service estate for direct Datadog SDK usage: `dd-trace`, custom metrics clients, RUM SDKs (mobile and web), log correlation tied to Datadog trace IDs. Findings determine the scope of service-team migration work in later phases.

**Depends on:** Nothing — can start immediately.
**Open question:** Who owns this?

#### Commercial Negotiation

Runs on its own track throughout Phase 1. Not in scope of the DevOps migration project — sits with business owners. Must conclude before Phase 3.

#### Phase 1 Dependencies

```
1a (PoC Instrumentation) ──→ 1b (PoC Evaluation)
                           └──→ 1c (Production OTel Build)

1d (Application SDK Audit) runs independently
Commercial negotiation runs independently
```

---

### Phase 2 — Vendor Selection

PoC results converge into a recommendation. Single-vendor is the default assumption; multi-vendor only if there is a compelling case and total cost remains within bounds.

**Depends on:** Phase 1b complete. Commercial negotiation sufficiently advanced to assess cost.

**Open questions:**
- Where does decision authority sit and what does the sign-off process look like?

---

### Phase 3 — Configuration Migration

Migrate the Datadog configuration estate — dashboards, monitors, SLOs, synthetic tests — into the chosen platform. High volume: 2,309 monitors, 835 integration-based.

Contractor support has been suggested as an option to reduce the demand on DevOps capacity. No commitment made.

Also: scope the service-team SDK migration work identified by the audit (Phase 1d). Where services use Datadog SDKs directly, teams will need application-level changes.

**Depends on:** Phase 2 (vendor selected). Phase 1d (SDK audit complete). Commercial negotiations concluded.

**Open questions:**
- Delivery model — in-house (DevOps), contracted out, or a mix?
- How much can be automated vs. manual?
- Lift-and-shift, or an opportunity to rationalise the monitor/dashboard estate?

---

### Phase 4 — Completeness & Confidence Check

OTel infrastructure (Phase 1c) pointed at the chosen vendor. Datadog and the new platform run side by side against the full production estate. Purpose: confirm everything is wired up correctly and nothing has been missed at full scale. Not proving parity — that is the PoC's job.

**Depends on:** Phase 1c (production OTel infrastructure deployed). Phase 3 (configuration migration at least partially complete).

**Open questions:**
- What constitutes sufficient confidence to proceed to cutover?
- How long does the dual-running period need to be?
- Who validates — DevOps, service teams, or both?

---

### Phase 5 — Cutover

Hard cut at or near Datadog contract expiry (July/August 2027). Dual-running in Phase 4 proves equivalence; cutover disables Datadog features and strips back the agent configuration.

#### Residual Tail

Two capabilities have no clean OTel replacement and will remain on the Datadog agent after cutover:

| Capability | Description | Candidate replacement |
|---|---|---|
| Orchestrator Explorer | Kubernetes cluster visibility | `k8s_cluster` receiver — needs separate evaluation |
| NPM | Network-level service visibility | Cilium/Hubble — needs separate evaluation |

**Key question:** Can these be lived without while alternatives are assessed, or do they require ongoing Datadog spend?

#### Service-Team SDK Migration

The existing `dd-trace` libraries can speak OTLP-compatible wire format into the OTel Collector, so SDK migration is not a blocker for cutover. However, without an operational forcing function, migration tasks are likely to sit on service-team backlogs indefinitely.

**Potential mitigation:** AI-agent-driven migration PRs — reduce the effort from "do the work" to "review and merge." Needs prototyping before scaling.

**Depends on:** Phase 4 (confidence check passed).

**Open questions:**
- Commercial implications of a residual Datadog footprint?
- Rollback plan if confidence is not achieved by contract expiry — extend the Datadog contract?

---

## Timeline

### Hard Backstop

Datadog contract expiry. Precise date pending (procurement contact on leave; expected w/c 27 October). Working assumption: **late July / early August 2027**.

### Estimates

| Phase | Duration | Start | Notes |
|---|---|---|---|
| 1a — PoC Instrumentation | **4 weeks** | In progress ([ZILCH-57057](https://payzilch.atlassian.net/browse/ZILCH-57057)) | Critical path. Unblocks 1b and 1c. |
| 1b — PoC Evaluation | _TBD_ | After 1a | |
| 1c — Production OTel Build | _TBD_ | After 1a; parallel with 1b | Largest DevOps work item. |
| 1d — Application SDK Audit | _TBD_ | Independent | No owner assigned. |
| 2 — Vendor Selection | _TBD_ | After 1b + commercial negotiation | |
| 3 — Configuration Migration | _TBD_ | After Phase 2 | |
| 4 — Confidence Check | _TBD_ | After 1c + Phase 3 partially complete | |
| 5 — Cutover | At contract expiry | Late July / early August 2027 | |

### Upcoming Milestones

- **28 October** — Grafana meeting. Set PoC kick-off date.
- **w/c 27 October** — Datadog contract expiry date confirmed.
- **5 November** — Coralogix demo.

### Slack Assessment

_Pending Phase 1a start date and contract expiry confirmation._ Roughly nine months from now to cutover. Whether that is comfortable depends on the outstanding estimates — particularly 1b (PoC duration) and 1c (production OTel build).

---

## Risk Register

### Technical

| # | Risk | Impact | Mitigation |
|---|---|---|---|
| T1 | **Fargate custom receiver** — no off-the-shelf OTel equivalent for Fargate log collection. | Delays Phase 1c. If build stalls, no OTel path for Fargate logs. | Fluent Bit + CloudWatch fallback documented. Fargate-to-EC2 ruled out (scope, cross-team dependencies). |
| T2 | **Residual Datadog tail** — Orchestrator Explorer and NPM have no OTel replacement. | May require ongoing Datadog spend or a separate replatforming effort. | Assess whether these can be lived without. Evaluate alternatives (`k8s_cluster` receiver, Cilium/Hubble) as follow-up. |
| T3 | **SDK cleanup stalls** — `dd-trace` works over OTLP with no forcing function for teams to migrate. | Indefinite tech debt. | AI-agent-driven migration PRs as potential mitigation. |
| T4 | **Production continuity** — monitoring and alerting must not regress during migration. | Missed alerts or degraded observability during a live incident. | Dual-ship architecture ensures both platforms receive signals throughout. Phase 4 validates completeness before cutover. |

### Delivery

| # | Risk | Impact | Mitigation |
|---|---|---|---|
| D1 | **DevOps capacity** — OTel infrastructure build is substantial; DevOps has concurrent commitments. | Phase 1c overruns, compressing later phases. | Front-load DevOps effort. Phase 3 delivery model to be decided with capacity in mind. |
| D2 | **Phase 3 delivery model undecided** — high-volume work. In-house competes with DevOps commitments; contracted introduces sourcing lead time and quality risk. | Compresses DevOps capacity or introduces external dependency. | Decision as part of Phase 3 planning. |

### Commercial / Organisational

| # | Risk | Impact | Mitigation |
|---|---|---|---|
| C1 | **Commercial negotiation timing** — must conclude before Phase 3. Outside project scope. | Delays Phase 3 regardless of technical readiness. | Noted as external dependency. Business owners aware. |
| C2 | **Contract expiry as deadline** — if confidence not achieved by July/August 2027, choice is: extend Datadog (cost) or cut over without full confidence (operational risk). | Unplanned cost or elevated production risk. | Front-load work; start Phase 4 early to maximise confidence-check window. |
| C3 | **Decision authority undefined** — sign-off process for vendor selection not established. | Delays at Phase 2 if approvals take longer than expected. | Clarify governance path early. |

### Compliance

| # | Risk | Impact | Mitigation |
|---|---|---|---|
| R1 | **Data residency** — Zilch is expanding into Lithuania. New platform must handle data residency obligations. | Late-stage blocker if not validated during PoC — could disqualify chosen vendor. | Data residency is a hard gate in the PoC Success Criteria. Must be explicitly tested during PoC. |
