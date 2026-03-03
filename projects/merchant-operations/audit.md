# Merchant O11y Audit

Audit findings for ZILCH-47400. One file per component.

## Scope Notes
- **affiliate-integration-service** — excluded from initial audit; service is new and not yet operational
- **data-consistency-service** — excluded from initial audit; the service is itself a form of observability (functional sanity testing), so treating it as an audit subject creates unhelpful circularity
- **Lambdas and Dynamic Fees Activator** — lower priority; to be addressed after core services

## Legend
- ✓ — confirmed in place
- ✗ — confirmed absent
- ~ — partial / mixed
- ? — unknown / not yet verified

---

## Cross-Cutting Findings

Issues observed during the audit that apply across the estate rather than to a single service.

| Finding | Detail |
|---|---|
| Team tag inconsistency | There is one team in DataDog with slug `unicorn` and display name `merchant`. Assets have been tagged inconsistently — some with `team:unicorn`, some with `team:merchant` — so neither filter returns the full estate. Needs investigation to understand which tag value DataDog treats as canonical, and a remediation pass to standardise all assets onto one value. |
| Synthetic test tagging | Multiple tagging errors identified on fee synthetics: (1) not attributed to the merchant team, so filtering by `team:merchant` returns only the 6 K8s health checks rather than the full estate; (2) incorrectly tagged with `rewards`, despite having no relation to the rewards service. Likely indicative of wider tag hygiene issues across the synthetic estate. |
| Apdex Terraform drift | Apdex monitors exist in DataDog with `[TF]` prefix but are commented out in Terraform. Active monitors are therefore unmanaged — a `terraform apply` could silently delete them. Applies to all enrolled services. |
| No Data monitors | Several Terraform-managed monitors are in a "No Data" state, likely due to metric or tag changes over time. Affects at least fee-service (HTTP connection pool, outbound latency anomalies). Likely present across other services too. |
| No functional dashboards | Two manually-created dashboards exist: "Fee Service" (by Jacek Zanko, operational signals only, largely duplicates APM page) and "Unicorn Team Dashboard" (team-wide, heavily cluttered, no clear purpose, not focused on business domain signals). Neither is Terraform-managed. No dashboards surface functional health. Both need significant rationalisation. |
| Thin functional health monitoring | fee-service emits two custom metrics (`fee.service.calculation.successful.counter` and `fee.service.schedule.not.found.counter`) and has two functional monitors. Beyond this, functional health monitoring across the Merchant estate is absent. |

---

## Core Services (priority order)

| Service | Audit file | Status |
|---|---|---|
| fee-service | [audit-fee-service.md](audit-fee-service.md) | Audit complete — tasking pending |
| rewards-service | — | Not started |
| retailer-service | — | Not started |
| offer-service | — | Not started |

---

## Other Components (lower priority)

| Component | Notes |
|---|---|
| affiliate-integration-service | Excluded from initial audit — not yet operational |
| data-consistency-service | Excluded from initial audit — service is itself a form of observability |
| pz-lambda-content-cache-invalidation | To be addressed after core services |
| pz-lambda-mixpanel-integration | To be addressed after core services; ownership discrepancy vs Terraform (`onboarding` vs Merchant) |
| pz-lambda-retailer-image-optimiser | To be addressed after core services |
| webgains-ingestion-lambda | To be addressed after core services; purpose and ownership rationale not yet understood |
| Dynamic Fees Activator | To be addressed after core services; proper name TBC |
