<u>**DevOps**</u>

**Ephemeral Environments**
* **In Progress**: Continued reactive fixes to Zephyr Zero and ephemerals (collections-service, loan-service).
* **In Progress** Zephyr build gate (per-repo PR check to block merge on broken builds) still in active development.
* VISA sanity tests at 44%; full API test suite approaching 50%.

**New Web**
* `cloudfront-web-app` Terraform module spike completed — design signed off.
* Module build now in progress; marketing-web workspace setup ready for release.
* Frontend WebApp migration to unified cluster in progress.
* Incident-530: Global AWS CloudFront VPC origins issue caused connectivity loss to new customer-web-app. Traffic rerouted to legacy app; now resolved. Reviewing ingress implementation to reduce exposure to similar outages.

**Dev Platform Rebuild**
* Ongoing remediation of issues emerging on dev-cu.

**Operations**
* Production read-replica latency spike caused by an ad-hoc DBA query scanning a large table — identified and resolved same day.
* GitHub REST API degraded overnight (resolved by GitHub) — minor build disruption.

**DevEx / Tooling**
* `zilchctl` installer flagged as broken for Mac users without admin privileges (Homebrew, Docker, SDKMAN all fail). Fix being investigated.

**Security**
* Secret removal from Git history (data-analysis repo) — in QA.
