<u>**DevOps**</u>

**Ephemeral Environments**
* Milestone: sanity and customer-smoke quality gates now passing repeatably on zephyrs. Admin-service and some api-gateway features still missing.
* ArgoCD downgraded on ephemeral after a recent upgrade caused significant zephyr sync time degradation. Upstream fix identified.
* Zephyr AI skills published to the plugin marketplace — four harness-agnostic skills covering overview, operations, debugging, and development.

**Infrastructure**
* Karpenter upgrade completed across all clusters.
* **In Progress:** External Secrets Operator upgrade — manifest migration across repos in progress.
* Quen test environment prerequisites completed — WAF, certificate, secrets, ESO trust, StorageClass, and ArgoCD repo access.
* **In Progress:** Terraform workspace fix for qa-sit.

**Observability Platform Migration**
* **In Progress:** Investigating zero-code instrumentation for Spring services via OTel Injector.
* **In Progress:** Exploring alternative tools for orchestrating agents and collectors.
* Grafana Cloud PoC Workshop confirmed for Monday.  Sessions: kick-off, Adaptive Telemetry, Notebooks & Workflows, AI demo, Q&A.
* Coralogix PoC planning meeting held — technical feasibility workshop being scheduled.

**Black Friday**
* DevOps support coverage confirmed — standard SRE rota stands.
* Scaling dashboard reviewed — all services within reasonable limits. Customer-service at 50% of scaling headroom but currently max-scaled for an ITAM product migration.
* **In Progress:** INC-601: Upwind tracer preventing graceful JVM shutdown since Feb. Fix merged but takes effect per-service on next deployment — ~20 services still to pick it up ahead of BFCM.

**Recruitment**
* Phil backfill
  * BJF submitted; formal approval expected but pending.
  * Sourcing starting.
