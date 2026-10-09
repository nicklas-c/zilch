<u>DevOps</u>

*Ephemeral Environments*
* Completed the Zephyr cleanup job — safety net for orphaned resources after teardown.
* Completed exploration of asset-exposure options for ephemeral environments.
* ZOE now creates a GitHub check run on PRs showing zephyr build/deploy state.
* **In Progress**: VGS shared-gateway approach under development to solve the Let's Encrypt cert rate limit. VGS confirmed no wildcard or alternate CA support, so per-env routing is being moved into our own cluster via a shared ALB.
* **In Progress**: Prod retailer and vector data seeding into ephemeral environments in progress — enables Data Science to reproduce production search relevance in zephyrs.
* **In Progress**: Weekly MSSQL golden snapshot in progress — will restore from a pre-migrated DB image rather than running full migration/seed on every env build.
* **In Progress**: PostgreSQL pod per environment continues — resolving the shared RDS Aurora connection limit.

*Infrastructure*
* Enabled External Secrets to use AWS Systems Manager Parameter Store.
* Terraform microservice module cleanup completed following the dev-unified migration.
* **In Progress**: Migrating customer-web-app to the new *-web clusters, continuing the pattern set by marketing-web.
* **In Progress**: Aurora IAM auth grants being fixed — instance resource IDs were omitted from policies, causing JDBC wrapper topology monitoring failures during failover.


