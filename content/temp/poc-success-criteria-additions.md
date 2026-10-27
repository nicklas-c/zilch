## Hard Gate — Constraints

#### Sensitive Data Protection

The platform must support detection and masking of sensitive data in observability pipelines. Zilch handles card numbers, secrets, and customer PII, all of which must be prevented from persisting in stored telemetry.

* [ ] Sensitive data can be detected and masked before logs are stored
* [ ] Card numbers, secrets, and customer PII are detected out of the box
* [ ] Custom detection rules can be defined
* [ ] Works for traces as well as logs

---

## Scored Criteria

#### Sensitive Data Protection Maturity

How mature and production-ready is the platform's sensitive data protection capability?

- Feature stability and GA status
- Track record in production environments
- Breadth of built-in detection patterns
- Configurability and operational overhead of detection rules

#### Performance Optimisation Recommendations

What automated performance insights does the platform surface?

- Detection of inefficient queries and missing indexes
- Application-level recommendations (e.g. JVM tuning, code hotspots)
- Breadth of supported runtimes and data stores
- Actionability — are recommendations specific enough to act on?

#### Workflow Automation

What support does the platform offer for building automated workflows on top of observability data?

- Ability to define multi-step automations triggered by conditions
- Data collection, aggregation, and analysis within workflows
- Integration with external systems (e.g. Slack, ticketing)
- Complexity and variety of workflows that can be expressed
