# Merchant Operations

## Also Known As
N/A

## Context
A personal workstream to develop hands-on operational knowledge of the Merchant team's software portfolio. Motivated by approximately 18 months of managing the team without having deeply understood the services from an operational perspective. The Merchant O11y Audit & Refresh epic (ZILCH-47400) provides a practical vehicle for this.

### Software Portfolio
The following components are owned by the Merchant team.

**Services**
- fee-service
- retailer-service
- rewards-service
- data-consistency-service
- offer-service
- affiliate-integration-service

**Lambdas** (in `zilchdev/lambdas` monorepo)
- webgains-ingestion-lambda — in `data/` subfolder; ownership confirmed by Jacek Zanko; nature and purpose unknown
- pz-lambda-content-cache-invalidation — in `product/` subfolder
- pz-lambda-mixpanel-integration — in `product/` subfolder
- pz-lambda-retailer-image-optimiser — in `product/` subfolder

**Crons**
- Dynamic Fees Activator (proper name TBC)

**UI / Front-end** (lower priority for observability purposes)
- Storefront
- Categories list page
- Promotion page
- Retailer filter results page
- Search page
- Stories
- retailer-admin-ui — status uncertain; last GitHub activity May 2024; possibly dormant

### Reference Sources
- [Confluence: Software Portfolio](https://payzilch.atlassian.net/wiki/spaces/Merch/pages/4458741954/Software+Portfolio) — incomplete as of 3 Mar 2026; missing offer-service and affiliate-integration-service
- DataDog software catalogue — incomplete as of 3 Mar 2026; lists fee-service, retailer-service, rewards-service, data-consistency-service, offer-service, and pz-lambda-retailer-image-optimiser only; missing five components

## Personnel

| Person | Role |
|---|---|
| Nicklas Chapman | Engineering Manager — leading this workstream |

## Running Notes

### 2026-03-03
First session. Objective established: develop genuine hands-on operational understanding of Merchant team services, using ZILCH-47400 as a vehicle.

Began by establishing the software portfolio, cross-referencing the Confluence Software Portfolio page, the DataDog software catalogue, and the GitHub org (`zilchdev`). Found meaningful discrepancies across all three sources:
- Confluence is missing offer-service and affiliate-integration-service
- DataDog catalogue is missing five components: affiliate-integration-service, webgains-ingestion-lambda, pz-lambda-content-cache-invalidation, pz-lambda-mixpanel-integration, and the Dynamic Fees Activator cron
- retailer-admin-ui exists in GitHub but appears dormant — status to be confirmed

webgains-ingestion-lambda sits in the `data/` subfolder of the lambdas monorepo, alongside data-team lambdas. Ownership attributed to Merchant team by Jacek Zanko, but the rationale for the placement is unclear and warrants investigation.

Did not begin the observability audit itself — this session was consumed by establishing the portfolio inventory.

Items surfaced that need addressing, likely as tasks under ZILCH-47400:
- Reconcile the Confluence Software Portfolio page — add offer-service and affiliate-integration-service; confirm retailer-admin-ui once its status is known
- Reconcile the DataDog software catalogue — add affiliate-integration-service, webgains-ingestion-lambda, pz-lambda-content-cache-invalidation, pz-lambda-mixpanel-integration, and the Dynamic Fees Activator
- Confirm the proper name of the Dynamic Fees Activator cron
- Investigate webgains-ingestion-lambda — understand its purpose and why it sits in the `data/` subfolder of the lambdas monorepo

Discussed the approach to defining 'what good looks like' for the audit. Two key sources: the Zilch Service Readiness document (https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/3465216052/Service+Readiness+WIP) and industry standards (Google's Four Golden Signals, RED, USE methods). The Service Readiness doc covers operational observability reasonably well (logging, metrics, tagging) but is still WIP and says nothing about dashboards, alerting, or Synthetic Tests.

Agreed on a clear separation between two types of health:
- **Operational health** — generic technical metrics applicable to any service: latency, CPU, memory, GC, connection pools, error rates, etc.
- **Functional health** — business-domain metrics specific to each service: e.g. total rewards applied, total fees calculated. These signal whether a service is doing the right thing, not just whether it is alive.

Proposed approach for the audit: enumerate functional health metrics per service as a task under ZILCH-47400, then determine appropriate alerting for each. This list should be produced collaboratively with the team, not inferred.

fee-service is being handed over to the new Spend Platform team, led by Andrzej Lorenz (VP of Engineering). Michal Baran has moved to that team. The handover makes fee-service observability a particular priority — it will be handed to the user's own manager. Timeline TBC.

Inspected the `terraform-datadog` repo (`zilchdev/terraform-datadog`) to understand what monitoring is currently configured. Key findings:

- A `service-defaults` module applies a standard set of operational monitors to each enrolled service: CPU, memory, JVM heap, container restarts, latency anomalies (inbound and outbound), error rate by endpoint, HTTP connection pool, disk space, load balancer targets, and SLOs. This is operational health monitoring only.
- Five Merchant services are enrolled: fee-service, retailer-service, rewards-service, data-consistency-service, offer-service. affiliate-integration-service is not enrolled at all.
- retailer-service is the only Merchant service with an API gateway health check synthetic configured. fee-service has a TODO in the Terraform noting the endpoint is missing.
- A `lambda-defaults` module covers pz-lambda-content-cache-invalidation and pz-lambda-retailer-image-optimiser (both owner: merchant). pz-lambda-mixpanel-integration is in the config but attributed to "onboarding" — ownership discrepancy vs the Confluence portfolio. webgains-ingestion-lambda and Dynamic Fees Activator are not enrolled.
- Apdex monitoring exists in the codebase but is entirely commented out — not active for any service.
- A fee calculation synthetic test exists and is detailed: it validates actual fee amounts for multiple fee codes and purchase amounts, running daily.
- No custom Merchant dashboards exist in Terraform. The Decisioning team has a custom dashboard; Merchant does not.
- No functional health monitoring exists anywhere in the Terraform config, with the sole exception of the fee calculation synthetic.

Audit findings are being tracked in `./audit.md` in this project folder, pre-populated with what's known from Terraform, with `?` for items requiring DataDog verification.

Audit scope and priority agreed:
- **Excluded:** affiliate-integration-service (not yet operational); data-consistency-service (is itself a form of observability)
- **Lambdas and crons:** lower priority; to be addressed after core services
- **Priority order for core services:** (1) fee-service, (2) rewards-service, (3) retailer-service, (4) offer-service

Fee-service is priority #1 due to the imminent handover to Spend Platform.

**Stopped here. Next step: go into DataDog and audit fee-service, populating the relevant section of `audit.md`. Specifically:**
- Whether an APM service page exists and what it shows
- Whether the operational monitors are active and in a healthy state
- Whether the fee calculation synthetics are passing consistently
- Whether any dashboards exist (custom or auto-generated)
- What functional metrics, if any, are currently visible

### 2026-03-03 (continued)

Second session. Continued the fee-service DataDog audit, working through the audit table item by item. Key findings:

- APM service page confirmed: comprehensive operational health data visible.
- 68 monitors across all environments; 15 in prod, all OK or No Data. Three No Data monitors in prod: HTTP connection pool, outbound latency anomalies (both `[TF]`, likely metric drift), and "Fee Schedule Not Found" (non-`[TF]`, possibly defunct).
- Apdex monitor is active in DataDog (P2, OK) despite being commented out in Terraform — Terraform drift risk.
- Fee calculation synthetics: 117 tests on prod matching "fee" in free text search. Significant tagging issues: not attributed to merchant team, and incorrectly tagged with `rewards`.
- Team tag inconsistency: one team in DataDog with slug `unicorn` and display name `merchant`; assets split between `team:unicorn` and `team:merchant` tags, so neither filter returns the full estate.
- Two custom dashboards found: "Fee Service" (Jacek Zanko, operational signals only) and "Unicorn Team Dashboard" (team-wide, heavily cluttered, no purpose, not focused on functional signals). Both need rationalisation.
- fee-service emits two custom Micrometer metrics: `fee.service.calculation.successful.counter` and `fee.service.schedule.not.found.counter`. Thin but present.
- **Significant finding:** fee-service has no prod logs. Debug logging was disabled as a cost optimisation (high log volume; requests/responses stored in DB). Confirmed by Jacek Zanko. The situation had come up before so wasn't a total surprise, but when the change was actually made wasn't known. Prod logging needs to be restored — action to be raised.

Audit split into per-service files. `audit.md` is now an index; fee-service audit is in `audit-fee-service.md`.

Also reviewed the ZILCH-47400 epic description in light of what the audit has revealed. Key issues identified: Out of Scope was blank (now populated); Success Criterion 2 was too absolute re: no observability outside DataDog (DCS carve-out needed); JSM alerting integration dropped from success criteria and deliverables (to be treated as a separate initiative, unblocked from ITOPS-14282 separately). Revised epic description drafted in `backlog-authoring/output/ZILCH-47400-revised.md` — ready to be pasted into Jira.

Agreed approach for documenting the observability work. Observability documentation will live in DataDog where DataDog supports it (dashboard descriptions, monitor messages, etc.). Functional metrics per service have no natural home in DataDog, so these will be documented in Confluence — one page per service under a new "Observability" parent page in the Merchant Confluence space, covering functional metrics, normal ranges, and associated context. fee-service first.

Tasked out the epic. Ten child tickets created under ZILCH-47400 (ZILCH-49114 through ZILCH-49123), covering: dashboard team tagging, functional metric definition, logging refactor, dashboard review and replacement, observability documentation, synthetic test tagging, Apdex Terraform drift, monitor estate review, and monitor implementation.

Aspiration noted: the Unicorn Team Dashboard should be completely replaced, not merely rationalised. The per-service functional dashboards created as part of this epic are the intended replacements. The Unicorn Team Dashboard should be retired once those are in place.

### 2026-03-03 (continued)

Third session. Completed ticket review cycle for ZILCH-47400 child tickets.

Reviewed all remaining tickets against Jira. Key changes made during review:

- ZILCH-49117 and ZILCH-49118 merged into a single ticket (ZILCH-49117, "Rebuild fee-service dashboard") — the review was preparatory work for the build, not a standalone deliverable.
- ZILCH-49119 (document fee-service observability) closed — documentation is covered by ZILCH-49115 (Confluence for functional metrics) and the dashboard description scope added to ZILCH-49117.
- ZILCH-49122 and ZILCH-49123 merged into a single ticket (ZILCH-49122, "Review fee-service monitors") — same rationale as 49117/49118.
- Remaining tickets (ZILCH-49120, ZILCH-49121) were minor changes only.

Net result: ten child tickets reduced to eight active tickets. Ticketing for ZILCH-47400 is not complete — further tickets remain to be written up, and the rewards-service audit (and subsequent services) will surface more.

Also discovered that the DataDog monitors list does not support OR logic in the search query, meaning the team tag split (`team:unicorn` vs `team:merchant`) prevents getting a unified view of the monitor estate. Further reinforces ZILCH-49114 as a prerequisite.

**Stopped here. Next steps when resuming:**
1. Continue writing up tickets for ZILCH-47400.
2. Continue the audit with rewards-service.

### 2026-03-04

- Checked Jira: eight child tickets confirmed under ZILCH-47400, all in Ready for Refinement except ZILCH-49130 (Created). ZILCH-49130 ("Migrate DCS tests to DataDog where possible") was not created in a previous session — origin unknown; to review.
- Created `audit-rewards-service.md` pre-populated with Terraform knowledge. DataDog verification is the next step.
