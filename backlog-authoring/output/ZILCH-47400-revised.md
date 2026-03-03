# ZILCH-47400 — Merchant O11y Audit & Refresh (Revised)

Revised description for copy/paste into Jira. Changes from original:
- Out of Scope populated (previously blank)
- Success Criterion 2 reworded to reflect DCS carve-out
- Success Criterion 6 and all JSM references removed
- JSM alerting integration removed from Deliverables

---

## Context / Background

The last observability audit was conducted approximately 18 months ago following a major incident. Since then, new services and capabilities have been introduced. While care has been taken to introduce appropriate monitoring along the way, an audit and review is now due.

Additionally, there is a department-wide initiative requiring all teams to undertake an observability review.

## Description

A review and refresh of observability for Merchant Team services. This includes assessing current monitoring, alerting, and dashboarding; implementing immediate improvements where criteria are met; and documenting deferred improvements as Jira tickets.

## Statement of Value

Reducing the risk of future incidents by ensuring comprehensive, consistent observability across Merchant Team services. Secondary benefits may include improved business and operational insights, and identification of opportunities to reduce running costs.

## Implementation Notes

Current observability is spread across DataDog, Looker, and the Data Consistency Service (DCS), with alerting via Slack. This epic will consolidate engineer-facing observability into DataDog, including better use of Synthetic Tests.

Dashboards will be restructured to separate operational health (e.g. liveness, heap size, latency) from functional health (e.g. rewards applied, fees calculated).

## Out of Scope

- **Data Consistency Service (DCS)** — DCS is itself a form of functional observability and is not subject to this audit. Longer-term migration away from DCS is a separate initiative.
- **affiliate-integration-service** — not yet operational; observability to be addressed separately once the service is live.
- **Lambdas and Dynamic Fees Activator** — lower priority; to be addressed as a follow-on phase if not completed within this epic.

## Success Criteria

1. All Merchant Team services have engineer-facing observability consolidated in DataDog
2. Synthetic Tests implemented where appropriate
3. Dashboards restructured with clear separation between operational health and functional health
4. Deferred improvements documented as Jira tickets with sufficient context for future implementation
5. Alerting routed via Slack

## Test Plan

Not required for this epic.

## Deliverables

- Observability audit findings
- Implemented improvements (per agreed criteria)
- Jira tickets for deferred improvements
- Consolidated DataDog dashboards (operational and functional health)
