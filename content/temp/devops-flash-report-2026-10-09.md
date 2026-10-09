<u>DevOps</u>

*Ephemeral Environments*
* ZOE and Zephyrs launched at Engineering Townhall. Good reception — strong questions from the audience showing genuine interest and intent to adopt.
* ZOE access opened to all engineering teams. Build check gating enabled on retailer repo. 12 concurrent environment limit.
* ZOE cache handling fixed, Go and TypeScript client libraries done, human-readable time format and UX improvements shipped.
* VGS creation jobs moved to earlier sync wave — 5 mins off environment build time (cert provisioning now parallel with DB setup).
* VGS mobile blocker: shared inbound route won't work for mobile — still needs per-env branded domain cert. Under investigation with VGS.
* **In Progress**: ZOE command palette, saved views, and security/observability fixes. Test-as-a-Service DB setup. Prod retailer and vector data seeding continues. Weekly MSSQL golden snapshot. PostgreSQL pod per environment continues.

*CI/CD & Tooling*
* Release Please silent-drop bug fixed — org ruleset now rejects the problematic commit-message pattern at push time.
* MSSQL password reveal RBAC fix for ZOE (ClusterRole scoped to global-passwords secret).

*Infrastructure*
* IDV table synonyms changeset added for customer-verification-service.
* **In Progress**: Aurora IAM auth grants fix continues.
* Cloudflare/CloudFront failover procedure at Ready for Sign Off.
