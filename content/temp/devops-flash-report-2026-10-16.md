<u>DevOps</u>

*Ephemeral Environments*
* Branch-deploy to Zephyrs now live — `!deploy-test zephyr` claims or creates a Zephyr linked to a PR. Responses suggest positive reception from engineers.
* First quality gate run on Zephyr (customer-service): 83% passed (126 tests).
* First cloudnative-pg test run: 81% passed (286 tests). Liquibase AWS driver issue found and fixed; hitting Aurora connection limits - under investigation.
* ZOE command palette, saved views, and security/observability fixes shipped. Owner permissions, type scale, dashboard user limits, and multi-pod scaling per Zephyr all completed.
* *In Progress*: ZOE Logs viewer fix — investigating inconsistent, missing, and jumping log lines.
* *In Progress*: Test-as-a-Service DB setup (In PR).
* *In Progress*: Prod retailer and vector data seeding continues.
* *In Progress*: Weekly MSSQL golden snapshot.
* *In Progress*: PostgreSQL pod per environment — addressing RDS connection count limits.

*CI/CD & Tooling*
* Lambda deployments (release + branch-deploy) enabled for `eu-ew1-sde-dev`.

*Infrastructure*
* Cloudflare/CloudFront failover procedure at Ready for Sign Off.
* App-link association files being brought under Terraform management (prod only).
* Issuer VPC unified migration: velocity valkey/elasticache and fraud-case-handler identified as still in issuer VPC — to be addressed.
* **In Progress**: Aurora IAM auth grants fix continues.

*Quen*
* Quen deployment tickets received from Spend Platform — epic covering Helm charts, CI/CD pipelines, Postgres provisioning, and local dev setup. Scoping underway.
