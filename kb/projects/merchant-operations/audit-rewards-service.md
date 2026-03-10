# rewards-service — O11y Audit

Part of ZILCH-47400. See [audit.md](audit.md) for scope notes, legend, and index.

## Legend
- ✓ — confirmed in place
- ✗ — confirmed absent
- ~ — partial / mixed
- ? — unknown / not yet verified

---

| Item | Status | Notes |
|---|---|---|
| DataDog catalogue entry | ✓ | Listed in DataDog software catalogue (confirmed during portfolio inventory, 3 Mar 2026) |
| Operational monitors (Terraform) | ✓ | Enrolled in `service-defaults` module in `zilchdev/terraform-datadog`: CPU, memory, JVM heap, container restarts, latency anomalies (inbound and outbound), error rate by endpoint, HTTP connection pool, disk space, LB targets, and SLOs |
| Operational monitors (DataDog verified) | ? | To verify: how many monitors exist across environments; how many in prod; any in alert or No Data state |
| K8s health check synthetic | ? | To verify |
| API gateway health check synthetic | ? | Likely absent — only retailer-service is confirmed to have one in Terraform; to verify |
| Functional synthetic test | ? | Nothing found in Terraform for rewards-service; to verify whether anything exists outside Terraform |
| APM service page | ? | To verify: whether the page exists and what it shows |
| Custom dashboard | ? | To verify: no rewards-specific dashboard identified during portfolio scan, but not exhaustively checked |
| Production logging | ? | To verify: fee-service had logging disabled as a cost optimisation — worth checking whether any similar decision was made for rewards-service |
| Functional metrics | ? | To verify: does rewards-service emit any custom Micrometer metrics? Check `MetricsService.java` or equivalent |
| Functional alerts | ? | To verify |
| Apdex monitoring | ? | Likely affected by the same Terraform drift issue as fee-service — to verify |
