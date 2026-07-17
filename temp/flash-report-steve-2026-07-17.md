<u>HIGHLIGHTS</u>

**DEVOPS**
* **Ephemeral / Zephyr Zero:** Continued stabilising with reactive fixes (collections-service, loan-service). Build gate still in active development. VISA sanity tests at 44%; full API test suite approaching 50%.
* **New Web:** Terraform module for new web infrastructure designed and signed off; now building. Incident-530: AWS CloudFront VPC origins outage briefly took down the new customer-web-app — rerouted to legacy app, now resolved.
* **Dev Platform Rebuild:** Ongoing remediation of issues on dev-cu.
* **Operations:** Production read-replica latency spike caused by ad-hoc DBA query — identified and resolved same day. GitHub REST API degraded overnight (GitHub-side) — minor build disruption.
* **DevEx:** `zilchctl` installer broken for Mac users without admin privileges — fix being investigated.
* **Security:** Secret removal from Git history (data-analysis repo) — in QA.

**MERCHANT**
* **Search:** Sponsored Retailer Search launching next week (5% rollout then A/B at 50%). Semantic search UX updates complete, ready for release.
* **Intelligent Commerce:** Automated ingestion failure alerting now live — posts to #intelligent-commerce with links to affected advertisers. Awin backdating for Currys completed.
* **Incident-523 (Fee Cap):** Production fix deployed — fee cap raised from £40 to £80 for Pay Over 3 Months. Monitoring confirms new cap in place. PIR meeting scheduled.
* **Service Handovers:** rewards-service and offer-service formally handed over to Loyalty. Knowledge transfer held with Spend Platform — they will support fee-service from next sprint.
* **Quality Sprint:** Swapped sprint 4 with Quality sprint. Focus on LD flag clean-ups, security vulnerabilities, and tech debt.

**PEOPLE / RECRUITMENT**
* **LT:**
  * SWE (L4 BE, Vilnius) — 4 CVs reviewed, 1 progressed to interview, 3 dropped.

**RISKS**
* Onboarding new back-end engineer next sprint, just as the team's only backend engineer goes on leave. Will mitigate with support from other backend engineers.
* New web app ingress architecture may need rethinking — current private VPC origin design leaves limited remediation options during CloudFront outages.
