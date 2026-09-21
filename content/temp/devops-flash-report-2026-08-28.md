<u>**DevOps**</u>

**Ephemeral Environments**
* Zoe now surfaces an environment access summary (API endpoints, UIs, DB creds) as a PR comment and on the Zoe env page.
* VGS ephemeral automation documented — covers lifecycle, design notes, and the outbound proxy routes per service.
* E2E test pass rate up to 91% (from 89%).
* Plaid `client_user_id` cross-environment collision identified and fixed — ephemeral environments share a global Plaid sandbox namespace, so two Zephyrs creating the same customer ID would collide. Resolved with per-environment customer ID reseeding, mirroring the existing Thredd WSID approach.
* **In Progress**: PostgreSQL pod per ephemeral environment — resolving RDS connection limit at scale. Tickets raised for engineering teams to address connection configurability.
* **In Progress**: Zephyr build gate — optimisation work started.
* **In Progress**: Dedicated Payout wallet per ephemeral environment.
* **In Progress**: ZOE enhancements — mobile config metadata envelope; pending state until build artifact is available from a PR.

**New Web**
* IAM Role for cloudfront-web-app created.
* marketing-web domain migration from payzilch.com to zilch.com — Ready for Release.
* **In Progress**: SSR Assets Cache Behavior for S3 Bucket.
* **In Progress**: Terraform microservice module cleanup following dev-unified migration.

**Operations**
* Alert escalation rules being updated — EMs to be notified on P1/P2 via a Management on-call schedule.
* Thredd maintenance window (23 Aug, 1–3am) — coordinated with Issuer on-call to manage status page, alerting suppression, and monitoring. Completed without incident.
* AWS SSM Run Command deprecation notice received — action required by 30 Sep.
