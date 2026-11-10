<u>DevOps</u>

*Ephemeral Environments*
- ZOE logging, tracing, and metrics improvements completed.
- PostgreSQL password now surfaced in ZOE for easier debugging.
- Initial provisioned user with linked card now available on zephyr builds — access button moved to a more prominent location.
- OCI Helm chart pilot for customer-service ready for release — eliminates chart/image version skew in ephemeral envs.
- Zephyr `!deploy-test` rollback fix merged — resolves PermissionDenied failures that were marking zephyr runs as failed even when tests pass.
- VGS cert provisioning remains broken, blocking some ephemeral builds. Chasing with VGS via Mark Reddington.

*Infrastructure*
- Spacelift cutover completed. Terraform-presync issue caused disruption early in the week (broken syncing for recent artefacts, manual Spacelift runs required). Fix deployed; auto-apply being re-enabled for dev/QA environments today.
- Karpenter upgrade to 1.15.1 continues — rolling out across clusters.
- External Secrets Operator upgrade towards 2.14.0 continues — v1beta1 → v1 manifest migration across repos in progress.

*Observability Platform Migration*
- OTel operator deployed to dev/eph EKS clusters. Required collectors for logs, metrics, traces, and kubestate identified.
- Grafana PoC continuing.

*Reactive*
- Supporting Quen (QA platform) test environment deployment prerequisites — WAF, certificates, secrets, and ArgoCD access for the DevOps EKS cluster.
