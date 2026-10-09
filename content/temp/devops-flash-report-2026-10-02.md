<u>DevOps</u>

*Ephemeral Environments*
* Zephyr launch announced for next week's eng townhall — team will demo features and discuss upcoming capabilities. 20+ raised hands in #engineering.
* Zero-debugging test pass rate reached 92%, up from 85% last week.
* Completed: ZOE demand-based pool scaling, PR/branch auto-resolution from claim/link, and GitHub PAT auth scope reduction (no longer requires extra scopes).
* Completed the VGS shared-gateway design. Cert provisioning still taking ~30 mins per env — shared gateway implementation now likely the next step.
* **In Progress**: Prod retailer and vector data seeding continues.
* **In Progress**: PostgreSQL pod per environment continues.
* **In Progress**: ZOE cache handling fixes (in QA). ZOE client library generation (Go + TypeScript) in dev.

*CI/CD & Tooling*
* Fixed staging promotion race condition — GitHub Actions concurrency group was cancelling queued promotions, causing services to silently skip staging/prod promotion when two released within minutes of each other.
* Release-please silent-drop bug resurfaced — nested parens in commit bodies break the parser, causing merged changes to ship unrecorded in later releases. Produced a fix (org ruleset rejecting the pattern at push time). Abhishek chasing legal to allow upstream contribution.
* Three services (loan, scheduler, offer) found missing the shared branch-deploy rollback workflow — PRs created to fix all three.
* Websocket-lambda duration alert resolved — cold starts had increased (likely AWS-side); fixed by increasing memory allocation.

*Observability Migration*
* Coralogix demo held at the office.

*Infrastructure*
* customer-web-app migration to the new *-web clusters now Ready for Release.
* **In Progress**: Aurora IAM auth grants fix continues.
* Cloudflare/CloudFront failover procedure at Ready for Sign Off.


