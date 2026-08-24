<u>**DevOps**</u>

**Ephemeral Environments**
* Per-environment Plaid sandbox wallet provisioning.
* VGS automation for ephemeral environments.
* E2E test pass rate up to 89%, standard Zephyr now has test-pass parity with Zephyr Zero.
* Missing retailers identified and populated for e2e tests.
* **In Progress:** Postgres pod per ephemeral environment — solving RDS connection limit at scale.
* **In Progress:** Zephyr build gate deploying to retailer-service as first adopter — reporting only, not yet gating.

**New Web**
* Web cluster EKS configuration.
* **In Progress:** IAM Role for cloudfront-web-app.
* **In Progress:** marketing-web domain migration from payzilch.com to zilch.com.

**Datadog / Monitoring**
* Continued reduction in triggered monitors visible in event explorer trend.

**Risks / Concerns**
* Ongoing issues with GitHub stability