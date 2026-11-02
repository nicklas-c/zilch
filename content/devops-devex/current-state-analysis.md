# DevOps to DevEx: Current State Analysis

## 1. Slack Channel Analysis (#tech-devops)

### Overview

The #tech-devops channel is the primary interface between engineering teams and the DevOps team. Its stated purpose is: *"Channel for engineering to engage with DevOps support, ask ad-hoc questions and raise issues."* The channel topic directs engineers to the `@devops-firefighter` rotation for support requests.

Three months of message history (late July to late October 2026) were analysed, filtering out bot messages (GitHub Status, Datadog alerts, Jira notifications, rotation announcements) and categorising human-initiated requests.

### Volume

Over approximately 65 working days, the channel received **~341 human-initiated requests** — an average of **5.2 per working day**.

### Request breakdown

| Category | Aug | Sep | Early Oct | Late Oct | Total | % |
|---|---|---|---|---|---|---|
| PR review/approval | ~42 | ~65 | ~38 | ~55 | **~200** | **59%** |
| Deployment/pipeline problems | ~12 | ~14 | ~9 | ~16 | **~51** | **15%** |
| Terraform/infra config changes | ~5 | ~10 | ~6 | ~10 | **~31** | **9%** |
| Access/permission requests | ~4 | ~3 | ~2 | ~4 | **~13** | **4%** |
| Environment issues | ~3 | ~5 | ~3 | ~4 | **~15** | **4%** |
| Other (questions, guidance) | ~9 | ~10 | ~7 | ~5 | **~31** | **9%** |
| **Total** | **~75** | **~107** | **~65** | **~94** | **~341** | |

The distribution is remarkably stable across all four periods — this is the steady state, not a spike.

### Category detail

#### PR review/approval (~200 requests, 59%)

The dominant category by a wide margin. Engineers tag `@devops-firefighter` to request review or approval of PRs. Running at approximately **3 per working day**, each representing an engineer blocked until a DevOps team member responds.

Requests span dozens of repositories, including service repos (customer-service, acquirer-service, fee-service, etc.), frontend, e2e-test, lambdas, terraform repos, and deploy repos.

**Root cause: CODEOWNERS rules.** Analysis of CODEOWNERS files across a sample of repos reveals a consistent pattern. DevOps is a required reviewer for:

- `.github/` (CI/CD workflows)
- `helm/**/templates` and `helm/**/values.yaml`
- `Dockerfile`
- `app.sh`
- `skaffold.yaml`
- `release-please-config.json`

This pattern is replicated across service repos, frontend, e2e-test, and lambdas. Any PR that touches CI/CD config, Helm charts, Dockerfiles, or release config requires DevOps approval — regardless of how trivial the change.

This explains why experienced engineers (not just juniors) are the most frequent requesters: they do more infrastructure-adjacent work and hit these paths more often. The top requesters over the three-month period include Sam Whittaker (L5 backend), Tom McKenzie (QA), Radek Kachel (QA), Jakub Zrebiec, and Dariusz Chrząścik.

#### Deployment/pipeline problems (~51 requests, 15%)

The second largest category. Engineers blocked by deployment failures they cannot diagnose or resolve themselves: stuck runners, failed automation, missing deploy PRs, version mismatches, QG timeouts, ArgoCD sync failures.

These tend to be high-cost interactions — some threads run to dozens or even hundreds of replies (one Terraform error thread had 225 replies). Engineers cannot troubleshoot their own pipeline failures because they lack access to the underlying systems (Terraform Cloud, ArgoCD, runner infrastructure).

Representative examples:
- Deploy-test failing with version mismatches
- Production version bump PRs not being created by automation
- ArgoCD syncs stuck or showing wrong deployed code
- Runner pool exhaustion (k8s-runners-16 not available)
- Release-please automation failures

#### Terraform/infra config changes (~31 requests, 9%)

Mechanical operations that engineers cannot perform themselves due to access restrictions:
- Switching a Terraform workspace to track a feature branch for testing
- Resetting a workspace back to main after testing
- Creating new Terraform Cloud workspaces
- Applying Terraform runs that require confirmation

These requests require no DevOps judgement — they are access-gated, not expertise-gated.

#### Access/permission requests (~13 requests, 4%)

Engineers lacking access to systems they need:
- AWS role access for testing
- Read access to secrets or configs
- Repository admin permissions
- Database connectivity

#### Environment issues (~15 requests, 4%)

Problems in shared environments requiring DevOps intervention:
- Database disk space exhaustion
- Redis memory exhaustion
- Flink application scaling
- SQS DLQ inspection (engineers lack "godmode" access)

#### Other (~31 requests, 9%)

A mix of questions about tooling, requests for guidance, and ad-hoc asks. August showed a higher proportion of "how do I..." questions, suggesting a documentation/golden-path gap alongside the access and tooling gaps.

### Key findings

1. **The channel functions as a service desk.** Its name, description, and usage pattern all confirm this. The `@devops-firefighter` rotation is a support rota.

2. **PR approvals account for ~60% of all requests and are the single biggest tax on both DevOps capacity and engineering velocity.** They are driven by CODEOWNERS rules that require DevOps review for infrastructure-adjacent files across all repos.

3. **The pattern is structural, not situational.** The distribution is stable across three months. This is how the system works, not a temporary state.

4. **~85% of channel traffic is addressable by tooling and policy changes** — removing or automating PR approval gates (~60%), improving pipeline self-service and observability (~15%), and providing self-service Terraform operations (~9%).

5. **Top requesters are experienced engineers.** The dependency on DevOps is not a knowledge problem; it is an access and tooling problem.

---

## 2. Jira Analysis

### Overview

All DevOps team Jira tickets updated in the last 90 days were analysed (187 tickets), alongside a manual review of the "reactive" label and the team's active epics.

### Ticket volume

- **187 tickets** touched in the last 90 days
- **11 labelled "reactive"**
- **~37 labelled "devops_planned"**
- Many tickets carry no workflow label at all (a vestige of an older organisational approach, not a labelling discipline problem)

### The reactive label is accurate but incomplete

Only 11 tickets carry the "reactive" label in 90 days. The label itself is used with reasonable discipline — the tickets it appears on are genuinely reactive. But it only captures reactive work that is significant enough to warrant a Jira ticket.

The Slack analysis found **~341 human requests** in the same period, the vast majority of which — PR reviews, quick config changes, pipeline troubleshooting — are handled entirely in Slack without a Jira ticket ever being created. Jira captures the tip of the iceberg; the bulk of reactive demand is invisible to anyone looking at the board.

### The reactive tickets

| Key | Summary | Status |
|---|---|---|
| ZILCH-57374 | e2e-test runs should use IAM role instead of IAM user | Backlog |
| ZILCH-57335 | Upgrade cert-manager to 1.21.3 | In Dev |
| ZILCH-57334 | Upgrade karpenter to 1.15.1 | In Dev |
| ZILCH-57333 | Upgrade external-secrets to 2.14.0 | In Dev |
| ZILCH-56666 | Enable lambda deployments to eu-ew1-sde-dev | Done |
| ZILCH-56286 | Service releases silently skip promotion | Done |
| ZILCH-55346 | Add datadog agent config to ssr apps | Ready for Release |
| ZILCH-54455 | Provide read-only GitHub PAT for ai-plugin-marketplace | Created |
| ZILCH-54207 | Adjust JSM routing rules | Done |
| ZILCH-54180 | Set up MOBILE_TEST_DISPATCH_TOKEN secret in frontend | Done |
| ZILCH-53685 | Create on-call reporting scheduled jobs | Done |

### Planned work: what the team spends its project capacity on

The team's active epics and recent workstreams reveal where planned capacity goes. The picture is a mix of DevEx-oriented platform building and traditional DevOps infrastructure work.

**DevEx-oriented workstreams (building tools and platforms for engineers):**

- **Ephemeral Environments / ZOE** — The single largest investment over the past ~14 months. Multiple epics (Zephyr Zero, Basic Zoe API, Full Zoe API, Zoe Integration, Zephyr & ZOE Maintenance). Ongoing, with ~35 tickets touched in the last 90 days. This is squarely DevEx: building a self-service platform that makes engineers more productive.
- **Unified Dev Platform Buildout** (ZILCH-35664) — IDP initiative, actively in development.
- **Observability PoC** (ZILCH-57057) — Exploring OpenTelemetry, Grafana LGTM stack, and alternatives to the current Datadog-centric setup.

**Traditional DevOps workstreams (infrastructure builds, operational work):**

- **New Web platform** — Building EKS clusters, ArgoCD applicationsets, S3 caching, and Datadog config for server-side-rendered sites. Significant work by Lukasz Kowalczyk, spread across individual tickets without an epic. This is infrastructure buildout for other teams.
- **Fraud Detection Engine infrastructure** — Platform build for the FDE, consuming significant capacity from Phil Stevenson.
- **Incident alerting routes** — Configuring JSM routing rules, escalation policies, and on-call reporting. Planned work, but operational in character.
- **Observability cost reduction** (ZILCH-52090) — Reducing Datadog spend. Operational/financial rather than DevEx.
- **Quen deployment** — Making a new service deployable: Helm chart, Kubernetes, Aurora Postgres, Argo CD. Service onboarding work.
- **Cluster and infrastructure work** — EKS cluster creation, VPC migrations, cluster configuration.

### The work intake problem

The analysis reveals a structural gap in how work enters the DevOps team's backlog. Currently, when another team needs infrastructure work done (a new platform build, a service migration, a config change), the work flows in and gets done. There is no gate at which someone asks: *"Should we do this for them, or should we build something that allows them to do it for themselves?"*

This distinction is critical to the DevEx transition. Without an intake gate, the team will continue to absorb operational work from other teams as planned project work — even as the strategy aims to shift toward building self-service capabilities. Every "do it for them" ticket is capacity that could have been spent on "build it so they can do it themselves."

Examples from the current backlog that illustrate this tension:
- Seeding data into environments for other teams (vs. building self-service seeding tools)
- Enabling Terraform presync for a specific service (vs. making presync self-service)
- Configuring VPC egress for a specific team (vs. providing a self-service networking abstraction)

### Key findings

1. **Jira dramatically understates reactive work.** The "reactive" label is used with discipline, but most reactive work never reaches Jira. The Slack channel is the true signal.

2. **The team's largest planned investment (ZOE/ephemeral environments) is DevEx-oriented.** The team is already building in the right direction with its flagship workstream.

3. **Significant planned capacity goes to traditional infrastructure builds** (New Web, FDE, incident alerting, service onboarding) that are DevOps in character — doing things for other teams rather than enabling them to do things themselves.

4. **There is no intake gate** that evaluates whether incoming work should be done directly or used as a signal to build self-service capability. This is the mechanism that would shift the balance from DevOps to DevEx over time.

5. **Visibility is limited.** Work is not consistently structured into epics, and the team self-organises to a degree that makes it difficult to see the full portfolio from Jira alone. This limits the ability to manage the DevOps/DevEx balance strategically.

---

## 3. On-Call / SRE Analysis (#tech-on-call)

### Overview

Three months of #tech-on-call channel history (August–October 2026) were analysed to understand the incident response burden on the DevOps team. Messages were filtered to remove rotation announcements (JSM ChatOps), automated deployment notifications, and platform maintenance bot messages.

### Volume

| | Aug | Sep | Oct | 3-month total |
|---|---|---|---|---|
| Genuine incidents requiring response | ~15-18 | ~5-6 | ~6-8 | **~28-32** |
| Batch operation notifications (FYI) | ~10+ | ~9 | ~18 | **~37+** |
| False alarms / alert noise | Several | ~2-3 | ~2-3 | Persistent |

Actual incident volume is moderate — roughly **10 incidents per month** requiring human SRE response. Not trivial, especially when they hit out of hours, but not a team drowning in pages.

### Shared rotation

The SRE on-call rotation is **shared between DevOps and Platform teams**, not solely a DevOps responsibility.

- **DevOps engineers on rota:** Phil Stevenson, Piotr Niebylski, Nick Gilbert, Lukasz Kowalczyk
- **Platform engineers on rota:** Charlie Hurst, Abdul Wahid, Paul Batey, Chris Prowse, David Ramsay

Separate team-specific rotations also exist (Issuer, Acquirer, Decisioning, Retain) staffed by those teams' own engineers. The SRE rotation is the escalation path and covers infrastructure-level issues.

### Incident types

**Database-related incidents** are the most common category across all three months:
- Production read replica struggling under load (October — extended investigation, multi-team)
- MSSQL high logical reads (recurring across all months)
- DB connection pool exhaustion (October — multiple teams affected)
- DB filegroup growing / disk space (October)

**Billing run failures** were the standout pain point in August:
- Multiple failures in one month, including one requiring Nick Gilbert to work from midnight
- Follows a runbook but still requires manual intervention with production DB access
- Involves shedlock removal, cron rescheduling, and monitoring the next run
- High-toil, high-stress, out-of-hours work

**External service incidents** occur occasionally (Mastercard via Checkout.com, VGS circuit breaker, Thredd maintenance) but are outside Zilch's control.

**False alarms** are a persistent problem:
- Kubernetes Service Health alerts firing 8 times in 30 days (flagged by Steve Rayko as false positives)
- Recurring night-time P1s for Issuer team that self-resolve in 1-2 minutes
- Upwind pod failures triggered by image version updates (not service-affecting)

### Alert noise

Alert noise is a recognised and escalated problem. Key signals:

- **CTO intervention (September):** Sean Hederman raised concerns about P1/P2 alerts being left unacknowledged, referencing a previous incident (IR0-166) as a complacency risk. Steve Rayko agreed and took ownership.
- **Persistent unacknowledged P3s:** Weekly SRE digests consistently show 10+ unacknowledged out-of-hours P3 alerts. Recurring offenders include:
  - MSSQL logical reads/writes — fires multiple times per week, never acknowledged
  - Fee API latency p99 — fires nightly, never acknowledged
  - Merchant affiliate transaction drops — fires every weekend, never acknowledged
  - Fivetran connector errors — recurring, likely external/vendor issues
- **Request for alert tuning:** Łukasz Krauzowicz raised that repeated false P1s at night need to be tuned.

This pattern represents alert fatigue. Known false positives and low-priority recurring alerts are eroding trust in the monitoring system and creating the complacency risk the CTO flagged.

### Batch operation notifications

More than a third of human messages in the channel are operations teams notifying on-call before running large production data operations:
- RCA migrations (200k+ batches)
- Behaviour score adjustments (10-15k)
- Card deactivations (238k)
- Reward applications (up to 140k)
- Product level migrations (up to 107k)

These are not incidents — they're courtesy notifications so on-call knows not to react to alerts triggered by the batch load. They represent an implicit coupling between operations teams and SRE: teams notify because bulk operations *could* cause issues.

### Key findings

1. **Incident volume is moderate (~10/month)** but not negligible, especially out of hours. The SRE function is a real demand on DevOps capacity, shared with Platform.

2. **The SRE rotation is shared with Platform.** Any changes to the SRE function or on-call model need to be coordinated with Platform, since both teams staff the same rota.

3. **Alert noise is a recognised problem at CTO level.** Recurring false positives and unacknowledged P3s are creating alert fatigue and complacency risk. Tuning monitors and eliminating noise is foundational work — the team cannot shift to a DevEx model if it is fatigued by alert noise.

4. **Billing run failures are the highest-toil recurring incident.** Multiple failures per month in August, manual intervention with prod DB access, out-of-hours response. A strong candidate for automation.

5. **Batch operation notifications are a self-service opportunity.** If the monitoring system were smarter about expected batch load patterns (e.g. suppression windows or expected-load annotations), teams would not need to manually notify on-call before every run.
