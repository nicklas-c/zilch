<u>DevOps</u>

*Ephemeral Environments*
* Zephyr build gate deployed and enabled on customer-service (non-blocking).
* Dedicated Payout wallet per ephemeral environment done.
* ZOE mobile config metadata envelope done.
* PR-tracking Zephyrs done — users can now request a Zephyr that tracks a PR.
* Pooled Zephyr pre-claim and auto PR comments done.
* Found customer reference character length bugs during Zephyr testing with unique IDs — purchase-service hardcoded to 8 digits, funding_model column too narrow. Cross-team issue; checking for similar problems in other services.
* **In Progress**: PostgreSQL pod per ephemeral environment — resolving RDS connection limit at scale.
* **In Progress**: Cross-repo deployment to Zephyr using PR labels.
* **In Progress**: E2E test pipeline against Zephyrs, including IP whitelisting.
* **In Progress**: Zephyr cleanup job, including removal of environments from LD.

*New Web*
* SSR assets cache behaviour for S3 bucket done.
* Staging marketing-web environment working and under test. 2 small Terraform fixes remaining (assets bucket policy + CloudFront origin path). Close to production.
* **In Progress**: Terraform microservice module cleanup following dev-unified migration.

*Operations / Tooling*
* GitHub Copilot billing changed this month — credits per user halved (7000→3900). Disabled auto AI review and expensive models to manage cost. Exploring Bedrock as a cheaper alternative.
* Refinement cadence changing — moving to the off-week from the planning session.

*Issues*
* Karpenter producing elevated prod error logs — investigating.
* ArgoCD Redis CPU utilisation alerts over the weekend (self-recovered).
