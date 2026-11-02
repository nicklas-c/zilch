<u>DevOps</u>

*Ephemeral Environments*
- New eu-central-1 EKS cluster provisioned in Terraform. RBAC and Secrets Manager access being resolved with Platform.
- Prod retailer and vector data seeding into ephemeral environments completed.
- Weekly MSSQL golden snapshot completed — new ephemeral envs now restore from a pre-migrated DB instead of running the full migration/seed pipeline.
- ZOE analytics now retains 30 days of zephyr and pool claim history.
- **In Progress**: OCI Helm chart pilot for customer-service to eliminate chart/image version skew in ephemeral envs.
- **In Progress**: ZOE logging, tracing, and metrics improvements.

*Infrastructure*
- Karpenter upgrade from 1.13.0 to 1.15.1 underway — IAM policy and module bumps applied; chart deploying to non-prod clusters today.
- External Secrets Operator upgrade towards 2.14.0 — upgraded to 0.16.2; v1beta1 → v1 manifest migration across 9 repos tested and merging.
- Cloudflare/CloudFront failover procedure remains at Ready for Sign Off.

*Observability Platform Migration*
- Grafana kick-off meeting held 28 Oct — Grafana Cloud org created and invites sent.
- PoC Success Criteria shared with both Grafana and Coralogix. Additional scored criteria added: Sensitive Data Protection, Performance Optimisation Recommendations, and Workflow Automation.
- **In Progress**: OTel operator deployment to dev/eph clusters.
