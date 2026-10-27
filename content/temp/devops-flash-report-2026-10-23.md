<u>DevOps</u>

*Ephemeral Environments*
* ZOE Logs viewer fix completed — inconsistent, missing, and jumping log lines resolved.
* Individual PostgreSQL per Zephyr environment completed — each ephemeral env now gets its own database, addressing RDS connection count limits. E2E tests being updated.
* Test-as-a-Service DB provisioning completed for all dev, ephemeral, staging, and sit environments.
* ZOE scale permission, GitHub reference validation, and shared GitHub directory permission shipped.
* **In Progress**: New eu-central-1 EKS cluster being provisioned in Terraform.
* **In Progress**: Prod retailer and vector data seeding into ephemeral environments continues.
* **In Progress**: Weekly MSSQL golden snapshot.

*Infrastructure*
* App-link association files under Terraform management (prod only) at Ready for Release.
* VGS identified the cause of slow certificate provisioning and confirmed a fix is underway.
* **In Progress**: Aurora IAM auth grants fix continues (Platform).
* Cloudflare/CloudFront failover procedure remains at Ready for Sign Off.

*Observability Platform Migration*
* PoC Success Criteria document published.
* **In Progress**: Initial prep work — mapping required OTel collectors (logs, metrics, traces, kube-state) and deploying the OTel operator in dev/ephemeral clusters.

*SSR Web*
* Customer-web-app migration to new cluster pending —  aiming for next week.
