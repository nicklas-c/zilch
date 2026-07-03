<u>**DevOps**</u>

**Ephemeral Environments**
* Reactive fixes to Zephyr testing issues ongoing — this week:   
  * DynamoDB cache table provisioned for product-service
  * fee schedule seeding hardened
  * missing SNS topics added to customer-service
  * Redis host fixes for issuer-service and velocity-service
  * WAF IP allowlist updated for VGS Sandbox
  * OOM kill monitor added
  * toolbox deployed to all ephemeral environments.
* Posted announcement in #engineering
* **In Progress** Zephyr build gate (per-repo PR check that eventually blocks merge when a change breaks the zephyr build).
* **Planned** 
  * Automate set-up of routes for VGS
  * Continued break-fixes in Zephyr Zero with Payments
  * Open Bug-bash to remaining teams

**Dev Platform Rebuild**
* dev-cu test pass rate up to 81%. Multiple issues fixed including mock for expin token endpoint.
* Branch deploy and branch deploy test workflows validated for dev-unified cluster — done.

**New Web**
* **In Progress** Spike: design cloudfront-web-app Terraform module for marketing site infrastructure.

**DevEx / Tooling**
* @verify-test command completed — allows checking TestRail status without redeploying, unblocking branch merges after manual test verification.
* GitHub Actions cache issue causing intermittent build failures (customer-service, wallet-providers-service) — investigated and workaround applied.
* **In Progress** Mobile release concurrency issue — deploys to different environments cancelling each other due to overly broad concurrency group config.

**Intelligent Commerce**
* Still pending: IP whitelisting with Quidco and Experian, and product lines missing in TestRail. Expin token endpoint mocked to bypass Experian but will cause other test failures.

**Incidents**
* Incident 522 (SEV-2): 3DS Cardinal outage. Thredd-side root cause, resolved overnight.

**Security**
* Remove secret from Git history for data-analysis repo — in QA.
