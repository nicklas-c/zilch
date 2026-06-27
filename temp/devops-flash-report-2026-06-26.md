<u>**DevOps**</u>

**Observability Cost Reduction**
* Removed Datadog security tools now covered by Upwind (ASM, CSM, CWS). Projected saving ~$19k/month. 
   * Code Security retained pending security team review.

**Making Call-Outs Rare**
* P3 alerts now delay out of hours until start of working day instead of paging on-call.
* Automated weekly SRE alert report (escalated alerts + out-of-hours P3s) now delivered to Slack every Monday.
* Created Datadog monitor notification rules for the new Loyalty and Spend Platform teams.
* Above items now close out this project as complete

**Dev Platform Rebuild**
* API Gateway ingress migration completed — dev-unified cluster now reachable via API Gateways.
* Cluster-level RBAC and e2e IAM user access implemented for the dev-unified Kubernetes cluster.
* `dev-cu` now fully migrated and operational.
    * Pending new IPs being white-listed with GPS/Thread

**Zephyr Zero**
* E2E test pipeline against Zephyr environments in development.
* Reactive fixes to issues found during Zephyr testing.

**DevEx / Tooling**
* Propagating copilot-setup-steps.yml workflow to all Java services (in progress).
* @verify-test command (check TestRail status without redeploying) ready for testing.
* Copilot PR summarisation workflow in development.
