# fee-service — O11y Audit

Part of ZILCH-47400. See [audit.md](audit.md) for scope notes, legend, and index.

## Legend
- ✓ — confirmed in place
- ✗ — confirmed absent
- ~ — partial / mixed
- ? — unknown / not yet verified

---

| Item | Status | Notes |
|---|---|---|
| DataDog catalogue entry | ✓ | |
| Operational monitors (Terraform) | ✓ | Via `service-defaults` module: CPU, memory, JVM heap, container restarts, latency anomalies, error rate, HTTP connection pool, disk space, LB targets, SLOs |
| Operational monitors (DataDog verified) | ✓ | [Monitors](https://app.datadoghq.eu/monitors/manage?q=service%3Afee-service&p=1) — 68 total across all environments; filtering to prod gives 15. All showing OK or No Data — no active alerts. 3 No Data in prod: HTTP connection pool, outbound latency anomalies (both `[TF]` — likely metric drift), and "Fee Schedule Not Found" (non-`[TF]` — possibly defunct). |
| K8s health check synthetic | ✓ | |
| API gateway health check synthetic | ✗ | TODO noted in Terraform — service does not expose a health endpoint in API Gateway |
| Functional synthetic test | ✓ | Fee calculation schedule defined in `zilchdev/terraform-datadog` (specific file not recorded) — [117 synthetics on prod matching "fee"](https://app.datadoghq.eu/synthetics/tests?query=env%3Aeu-ew1-prod%20fee), almost all merchant-owned. Confirms the Terraform-described suite (multiple fee codes × purchase amounts) is substantial. Note: [filtering by merchant team attribution](https://app.datadoghq.eu/synthetics/tests?query=env%3Aeu-ew1-prod%20team%3Amerchant) returns only 6 tests (K8s health checks) — the fee synthetics are not attributed to the team, indicating a tagging gap across the estate. Additionally, the fee synthetics are incorrectly tagged with `rewards` — they have no relation to the rewards service. |
| APM service page | ✓ | [APM service page](https://app.datadoghq.eu/apm/entity/service%3Afee-service) — comprehensive operational health data visible; everything expected is present |
| Custom dashboard | ~ | Two dashboards exist: (1) ["Fee Service"](https://app.datadoghq.eu/dashboard/sdj-m79-tkv/fee-service) (created by Jacek Zanko) — largely duplicates the APM service page, operational signals only, no functional content; (2) ["Unicorn Team Dashboard"](https://app.datadoghq.eu/dashboard/dy7-3uy-s7x/unicorn-team-dashboard) — covers the whole team, heavily cluttered, no clear purpose, not focused on business domain signals. Neither is Terraform-managed. Both need significant rationalisation. |
| Production logging | ✗ | Debug logs disabled in prod as a cost optimisation — fee-service was generating a very high log volume. Justification: fee calculation requests/responses are stored in DB. Confirmed by Jacek Zanko (3 Mar 2026). No prod log visibility means no log-based metrics and no log investigation capability during prod incidents. Needs to be fixed — raise a task under ZILCH-47400. |
| Functional metrics | ~ | Two custom metrics emitted via Micrometer (`MetricsService.java`): `fee.service.calculation.successful.counter` (incremented on every successful fee calculation) and `fee.service.schedule.not.found.counter` (incremented when no fee schedule is found). Thin but meaningful. No metrics covering fee type distribution, dynamic fee events, or volume trends. Note: Micrometer metrics are emitted independently of logging and should still be active in prod. |
| Functional alerts | ~ | Two exist outside Terraform: "dynamic fee evaluation endpoint not triggered" (P3, OK) and "Fee Schedule Not Found" (No Data — possibly defunct). Broader functional alerting to be established once metrics defined. |
| Apdex monitoring | ✓ | Active in DataDog (P2, OK) despite being commented out in Terraform — Terraform drift risk. If `terraform apply` is run without restoring the config, this monitor could be silently deleted. |
