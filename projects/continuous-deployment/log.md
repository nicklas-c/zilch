# Continuous Deployment

## Also Known As

CD, Streamline Release and Deployment

## Context

A cross-team initiative to move Zilch from batch releases (deploying everything at once) to independent, continuous deployment of individual microservices. The goals are to reduce release risk, shorten delivery time, increase deployment frequency, and give engineering teams more autonomy.

### Background

The original problem: Zilch was releasing multiple services at once with many moving parts, making rollback difficult and confidence low. The initiative was phased:

- **Phase 0**: Tool analysis and selection
- **Phase 1**: Implementation — automation, Helm standardisation, config consolidation, cultural change

### Architecture & Tooling

- **ArgoCD** (self-hosted): Selected as the CD platform after evaluating FluxCD, Tekton, Spinnaker, and GitHub Actions. Chosen for GitOps principles, advanced deployment strategies (canary, A/B), efficient rollback, state management, and drift prevention. Self-hosted was preferred over managed (Akuity.io) for cost (~$795/month self-hosted vs ~$1,800/month managed) and flexibility (216 deployed applications across 9 environments).
- **DevOps EKS Cluster**: Purpose-built cluster to host ArgoCD, self-managed GitHub Actions runners, and other DevOps tooling. Also serves as a testing ground for EC2 node groups (replacing Fargate).
- **Helm**: Individual Helm charts per service, referencing a shared chart library (`microservice_lib`). New features behind flags before being added to the library.
- **GitHub Packages / GHCR**: Consolidated VCS, CI, and artefact storage (NPM, Maven, container images) onto GitHub, moving away from AWS ECR and CodeArtifact.
- **Config simplification**: Aim to reduce config providers (currently AWS Secrets Manager, Parameter Store, env vars, multiple config files) and make greater use of Kubernetes ConfigMaps and Secrets.

### Key Repositories

- **deploy-zilch**: Product deployment configuration. Services deployed via Argo ApplicationSets. Helm values cascade from service repo → environment level → specific environment → service environment → final override.
- **deploy-tools**: Kubernetes and environment tooling deployments (ArgoCD itself, external-dns, external-secrets, Karpenter, Gatekeeper, Datadog agents, wiremock, GitHub Actions runner controller, etc.).
- **helm-charts**: Shared Helm chart library including the `microservice_lib`.

### Current State

ArgoCD is operational and in use for Kubernetes deployments. The current model is **continuous delivery** — code is automatically built and pushed to environments, but production deployment requires a manual sync step via ArgoCD (merge a deploy PR in deploy-zilch, then sync in ArgoCD UI). This is documented in the "Deploying via ArgoCD" guide on Confluence.

Marcin Zolna (EM, Onboarding team) is now driving a further push towards **true continuous deployment** — removing the remaining manual steps so that production deployment happens automatically without explicit approval. Marcin has created a [Jira dashboard](https://payzilch.atlassian.net/jira/software/c/projects/ZILCH/boards/2843) to track progress.

### Jira Epic

**ZILCH-40937** — "Create CI/CD pipeline for Product service" (Epic, In Dev). Assigned to Marcin Zolna, reported by Rob Nelson. Parent initiative: ZILCH-34712 (Decisioning Engineering Roadmap). Confluence tracking doc: [Use CI/CD to accelerate delivery](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/4463067409/Use+CI+CD+to+accelerate+delivery).

The epic describes the target CI/CD flow:
- **On PR**: auto build and deploy to lower env (QA SIT), regression pack runs, if pass then released for team approval, merge allowed after regression pass + 2 reviews.
- **On merge to main**: new release version created, auto release to staging, auto regression, then either auto deploy to prod or alert to trigger. If tests fail: alert, pause pipeline, further merges re-trigger.
- Changes should be behind feature toggles; if not, additional approvals required (VPoE or VPoE + CTO).

#### Ticket Status (20 tickets, as at 11 Feb 2026)

**Done (15):**
- ZILCH-40893: Quality gate for product-service (John Strawhorne)
- ZILCH-40979: Identify and tag crucial e2e tests
- ZILCH-41226: Quality gate for decisioning-service (John Strawhorne)
- ZILCH-41376: Conditions for release self assessment (Marcin)
- ZILCH-42079: Switch to release-per-user-story process (Marcin)
- ZILCH-42080: Adjust Jira workflow to allow testing before merge (Marcin)
- ZILCH-42199: Create EC ticket after feature branch merge (George Sharpe)
- ZILCH-42200: Auto-merge release-please PRs (Phil Stevenson)
- ZILCH-42201: Auto deploy to staging after release-please PR merge (Phil Stevenson)
- ZILCH-42204: Trigger regression/sanity suite after staging deploy (Phil Stevenson)
- ZILCH-42205: GitHub check for QA phase
- ZILCH-42207: GitHub check for sign-off (Lukasz Kowalczyk)
- ZILCH-42241: Bypass EC ticket approvals on certain conditions (George Sharpe)
- ZILCH-44144: deploy-zilch to only require 1 approval for prod version PRs (Nick Gilbert)
- ZILCH-44798: Extend auto-merge release-please to decisioning-service

**In QA (1):**
- ZILCH-44143: Merge deploy-zilch PR when change request is approved (Unassigned)

**To Do (2):**
- ZILCH-42237: Create e2e-test check on production deployment branch (Unassigned)
- ZILCH-42238: EC ticket approval check (Unassigned)

**Rejected (2):**
- ZILCH-41820: Create new GitHub workflow for product-service CICD
- ZILCH-42198: Trigger release-please PR creation after feature branch merge

### Current Workstreams (from #proj-continuous-deployment)

The channel shows active work across several areas:

1. **End-to-end PR-to-Production pipeline**: Sean H is driving the goal of fully automated PR-to-prod deployments, framing it as "what needs to be true" (pre-deployment gates) and "what needs to stay true" (post-deployment validation).
2. **Identifying deployment readiness blockers**: Sam led a discussion identifying why changes aren't ready for deployment after PR merge — bugs, incomplete E2E tests, lack of approval, late redesigns, lightweight PR reviews. Nikos Sofianos suggested automating these checks earlier in the process.
3. **Automated merge workflows**: Phil Stephenson created a workflow to auto-merge release-please PRs for product-service. George Sharpe extended this to decisioning-service. George also proposed auto-merging PRs when tickets reach "Ready for Release" status.
4. **Automated regression testing**: Phil Stephenson and Radek Kachel are working on automatically triggering regression tests after staging deployments and integrating with TestRail for tracking results.
5. **Flaky test mitigation**: Sam and the team are tackling flaky tests — exploring automated retries, caching test results, and prioritising critical tests.
6. **Tracking**: Sam created a "Use CI/CD to accelerate delivery" tracking document.

### Future Goals

1. **Deploy without change in functionality** — automated regression testing, post-deployment release via feature flags (LaunchDarkly), deployments that don't require CAB approval.
2. **Canary deployments** — especially for changes requiring CAB approval and for larger/monolithic services like customer-service.
3. **Automated deployments** — trigger automatically on CAB approval, progressive rollout across regions (e.g. USA first, then UK), time-based scheduling, automated rollback based on Datadog metrics/logs/events.

### Channels

- Slack: #proj-continuous-deployment

### Key Confluence References

- [Streamline Release and Deployment (CD) [draft]](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/3031367681) — original project brief
- [CD Platform - ArgoCD Proposal](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/3549429869) — detailed technical proposal
- [Deploying via ArgoCD](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/4128505876) — how-to guide for production deployments
- [Developing ArgoCD](https://payzilch.atlassian.net/wiki/spaces/devops/pages/3843031080) — DevOps operational guide for tooling setup

## Personnel

- **Marcin Zolna** — EM, Onboarding team. Driving the initiative and tracking via Jira dashboard.
- **Sean H** — Framing the end-to-end PR-to-prod goal.
- **Sam** — Leading discussions on deployment readiness blockers, flaky tests, and tracking delivery progress.
- **Phil Stephenson** — Creating auto-merge workflows and automated regression testing pipelines.
- **George Sharpe** — Extending auto-merge workflows, proposing ticket-status-based PR merging.
- **Radek Kachel** — Working on automated regression testing and TestRail integration.
- **Nikos Sofianos** — QA Manager. Suggesting earlier automation of quality checks.
- **Mike Davis** — Involved in PR-to-prod discussions.
- **DevOps team** — Owns the underlying infrastructure (ArgoCD, EKS clusters, Helm charts, deploy-tools, deploy-zilch).

## Running Notes

### 2026-02-11

Project log populated from Confluence research. Key pages: Streamline Release and Deployment brief, ArgoCD proposal, Deploying via ArgoCD guide, Developing ArgoCD DevOps guide.
