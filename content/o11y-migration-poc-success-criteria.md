# Observability Platform PoC — Success Criteria

## Purpose

This document defines the success criteria for evaluating candidate observability platforms as replacements for Datadog. It is structured in two parts:

- **Hard Gates** — binary pass/fail criteria. A candidate that fails any hard gate is eliminated regardless of how well it scores elsewhere.
- **Scored Criteria** — qualitative evaluation areas. These are not weighted or scored numerically. They provide a structured framework for hands-on assessment and comparison, with the final decision remaining a judgement call.

This document is intended to be shared with candidate vendors to make explicit what we are evaluating and what we expect to see demonstrated.

---

## Hard Gates

Hard gates are grouped into three categories: **Capabilities** (does the platform support this?), **Coverage** (can it observe what we need it to observe?), and **Constraints** (business requirements that must be met).

### Capabilities

The platform must natively support the following pillars of observability.

#### Logs

- [ ] Querying
- [ ] Structured and unstructured logs
- [ ] Parsing pipelines

#### Metrics

- [ ] Collection and storage
- [ ] Discovery, exploration, and search

#### Traces

- [ ] Click-through and drill-down
- [ ] Distributed traces

#### Monitoring

The ability to define conditions on which alerts will trigger. This is distinct from Alerting (see Scored Criteria), which covers the routing and escalation of those alerts.

The platform must support the following monitor types, all of which are in active use:

- [ ] Threshold / metric monitors
- [ ] Anomaly detection monitors
- [ ] Composite monitors (combining conditions from multiple monitors)
- [ ] Forecast monitors (alerting on projected trends)
- [ ] SLO-based monitors
- [ ] Error tracking monitors
- [ ] Real User Monitoring (RUM)

### Coverage

Coverage is evaluated as an inventory exercise against the current Datadog monitor estate. The candidate platform must be able to ingest equivalent signals across the following areas.

#### Kubernetes

- [ ] Pod, node, and cluster-level metrics
- [ ] Events and state

#### AWS Services

- [ ] ALB
- [ ] SQS
- [ ] Lambda
- [ ] SNS
- [ ] RDS
- [ ] API Gateway
- [ ] SageMaker
- [ ] EC2
- [ ] Kinesis / Kinesis Analytics
- [ ] NLB
- [ ] ElastiCache
- [ ] MWAA
- [ ] Step Functions
- [ ] AppFlow
- [ ] CodeDeploy

#### Databases

- [ ] MSSQL (SQL Server)
- [ ] PostgreSQL / Aurora
- [ ] OpenSearch
- [ ] Redis / Val-key

#### Application Runtimes

- [ ] JVM (heap, GC, thread pools, etc.)
- [ ] Node.js

### Constraints

#### Compliance

The platform must support compliance with regulatory requirements, including data residency obligations.

Zilch is expanding into foreign jurisdictions (Lithuania first, followed by other European countries). The platform must support multi-region observation and any data residency implications that follow. This applies as a cross-cutting concern across Coverage, Cost, and Signal Correlation criteria as well.

- [ ] Data residency requirements can be met
- [ ] Multi-region deployment is supported

#### Cost

- [ ] Cheaper than the current Datadog solution

---

## Scored Criteria

These criteria are evaluated qualitatively during the PoC. There is no fixed scoring methodology or weighting — they provide a structured checklist of what to explore and what we expect vendors to demonstrate.

### Build-Time Experience

#### Developer Experience

How easy is it for engineers to adopt the new platform?

- Learning curve for engineers moving from Datadog
- Quality and completeness of documentation
- Community size and activity
- Time to productivity for a new user

#### Configuration

How well does the platform support infrastructure-as-code and programmatic management?

- Integration with IaC tooling already in use at Zilch (Spacelift, Crossplane)
- Programmatic configuration of dashboards, monitors, and pipelines
- Support for GitOps workflows

#### Extensibility

What integration points does the platform offer for building on top of it?

- Webhooks
- SDKs
- Open APIs

### Operate-Time Experience

#### Dashboards

What is the day-to-day operational experience like?

- Available controls and visualisation types
- Ease of use for operational workflows
- Configurability and customisation

#### Signal Correlation

In a live incident scenario, how easy is it to navigate from an alert to the relevant monitor, logs, and traces?

This should be evaluated via a simulated incident exercise during the PoC, not solely through a vendor demonstration.

#### Alerting

How are triggered alerts routed and escalated? This is the delivery side of monitoring — what happens after a monitor fires.

- Delivery mechanisms (email, Slack, webhook, etc.)
- Integration with existing incident management tooling
- Ease of configuring and managing routing rules
- Escalation policies

#### Anomaly Detection

What support does the platform have for anomaly detection beyond simple threshold monitors?

- Richness and sophistication of detection algorithms
- Configurability and tuning
- False positive and false negative rates

#### Synthetic Testing

What support does the platform offer for synthetic monitoring?

- Types of synthetic tests supported
- Configurability
- Geographic coverage of test locations

### Platform Concerns

#### SLO / SLI Support

Does the platform support service level objectives and indicators as first-class concepts?

- Defining and tracking SLOs
- SLO-based alerting
- Burn-rate alerts and error budget tracking

#### Access Control and Multi-Tenancy

Can dashboards, monitors, and data be scoped by team?

- Role-based access control
- Team-based data scoping
- Granularity of permissions

#### Data Retention and Queryability

How far back can data be queried, at what granularity, and at what cost?

- Hot vs cold storage tiers
- Retention periods by data type (logs, metrics, traces)
- Query performance across retention tiers
- Cost implications of retention policies

#### Cost Monitoring

What visibility does the platform provide over costs?

- Visibility of spend on the observability platform itself
- Ability to forecast future platform costs
- Ability to monitor infrastructure costs across the estate

#### Ecosystem Lock-In

How well does the platform support open technologies as an abstraction layer?

- OpenTelemetry support
- Use of open standards and formats
- Portability of configuration, dashboards, and queries
- Ease of future migration away from this platform

#### Migration

How easy is it to migrate existing Datadog configuration into the new platform?

- Automated migration tooling
- Manual effort required for monitors, dashboards, and pipelines
- Expected timeline and resource commitment

#### On-Call and Notification Integration

*Owner: Mark Reddington*

What does the platform offer for on-call management and alert notification?

- Native on-call and rota management capabilities
- Integration with existing tooling (currently Jira Service Management)
- Potential to consolidate or replace existing on-call tooling

#### Incident Management

*Owner: Mark Reddington*

What does the platform offer for incident management workflows?

- Native incident management capabilities
- Integration with existing incident management tools

#### Integrated AI

What AI-driven capabilities does the platform offer?

- Automated root cause analysis
- AI-assisted querying and exploration
- Predictive capabilities beyond forecast monitors

#### Fargate Monitoring

What support does the platform have for monitoring Fargate workloads?

- Metric collection without direct host access
- Sidecar or CloudWatch-based approaches
- Parity with standard container monitoring capabilities

#### Argo Rollout Integration

What integration does the platform offer with Argo Rollouts for progressive delivery?

- Canary analysis
- Automated rollback triggers based on observability signals
