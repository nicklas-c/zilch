<u>**DevOps**</u>

**On-Call Rollout**
- Workshop delivered to help engineers better understand On-Call duties.  Recording shared.
- On-call reporting scheduled jobs done.

**Ephemeral Environments**
- Dynamic e2e config support done — tests can now run against any `eu-ew1-eph-*` namespace without per-env config files.
- ZOE API dev environment built.
- ZOE mobile config endpoint done — when supported in the app, it will allow devices to connect to a Zephyr backend.
- Shared Plaid webhook ingress done — webhooks fan out to all subscribed ephemeral environments.
- VGS automation for ephemeral environments — automating inbound route - **In Progress:**  Zephyr build gate deploying to retailer-service as first adopter (PRs won't merge unless a Zephyr builds).
- **In Progress:**  Posgres pod per ephemeral environment — solving RDS connection count limit at scale.
- **In Progress:**  Per-environment Plaid sandbox wallet provisioning.
setup per env.
- **Pending:**  Zephyr build gate rollout to further services.

**New Web**
- **In Progress:** Web cluster EKS configuration (CloudFront, DNS, security, observability).

**Datadog / Monitoring**
- Significant reduction in triggered monitors over recent months (visible trend in event explorer).
- Spotted missing CloudWatch logs for SDE environments (fargate-to-EC2 migration gap) — investigating.
