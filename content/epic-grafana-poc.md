# Epic: Grafana Cloud PoC Evaluation

## Summary

Evaluate Grafana Cloud as a candidate observability platform by running a hands-on proof of concept across representative workloads, producing an evidence-based assessment for the vendor selection decision.

## Context

Zilch's Datadog contract expires 31 July 2027. The Observability Platform Migration initiative is evaluating alternative platforms to reduce cost and vendor lock-in. Two vendors have been shortlisted: Grafana Cloud and Coralogix. Each is being evaluated via a separate PoC run by a different team — this Epic covers the Grafana Cloud PoC, run by the Onboarding team.

A set of [PoC Success Criteria](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/5967675402/PoC+Success+Criteria) has been published and shared with both vendors. It defines hard gates (capabilities, coverage, constraints) and scored criteria (developer experience, operational experience, platform concerns) against which each candidate will be assessed.

The PoC depends on the vendor-agnostic OTel collection infrastructure being built in [ZILCH-57057](https://payzilch.atlassian.net/browse/ZILCH-57057) (Phase 1a), which delivers the collectors and instrumentation that get telemetry flowing into candidate platforms.

## Statement of Value

This PoC is one half of the evidence base for the vendor selection decision. Without it, the organisation is choosing a multi-year observability platform on the basis of vendor demonstrations and sales materials rather than first-hand operational experience. The PoC de-risks the decision by surfacing integration gaps, usability issues, and capability shortfalls before commitment.

## Description

Instrument representative workloads into Grafana Cloud and evaluate the platform through hands-on use against the published success criteria. The PoC should cover:

- **Workload onboarding:** At least one backend service, one Lambda function, the new web application, and the mobile application sending telemetry to Grafana Cloud.
- **Hard gate validation:** Each hard gate (capabilities, coverage, constraints) assessed as pass/fail with evidence.
- **Scored criteria evaluation:** Each scored criterion explored through hands-on use, with observations documented.
- **Simulated incident exercise:** A realistic incident scenario exercised end-to-end to evaluate signal correlation — navigating from alert to monitor to logs to traces.
- **Assessment write-up:** A written evaluation document produced for the stakeholder review group.

### Requires refinement

- **Specific workloads:** Which backend services, Lambda functions, and app versions will be instrumented. To be specified by the Onboarding team.

### Incident management and on-call evaluation

The PoC success criteria include on-call/notification integration and incident management. Mark Reddington owns the evaluation of these criteria. The Onboarding team may need to support this work (e.g. providing access to instrumented environments), but Mark drives the assessment.

## Out of Scope

- OTel collection infrastructure build — covered by [ZILCH-57057](https://payzilch.atlassian.net/browse/ZILCH-57057)
- Production-grade dual-ship OTel architecture (Phase 1c)
- Commercial negotiation with Grafana Labs — handled separately by business owners
- Vendor selection decision — dependent on both PoCs completing (Phase 2)
- Coralogix PoC — separate Epic, run by the Merchant team

## Success Criteria

- The PoC team can confidently recommend for or against Grafana Cloud, backed by first-hand evidence rather than vendor claims
- Hard gate failures, if any, are identified early enough to redirect effort
- The assessment document is sufficient for the stakeholder review group to make an informed vendor selection decision without needing to repeat the evaluation

## Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Mobile SDK immaturity | Grafana's React Native SDK is in beta. The PoC may be unable to evaluate mobile observability to a production-representative standard. | Assess what is available; document gaps clearly. Treat as a finding, not a blocker to completing the PoC. |
| SQL Server support in private preview | Database observability for SQL Server entering private preview ~16 Nov. Feature maturity may limit evaluation depth for Zilch's primary database. | Enrol in the private preview (David Ramsay requested inclusion). Document current state and roadmap commitments. |
| Trace-to-query linkage unavailable | Application-to-SQL-Server trace linkage estimated "a couple of quarters" away by Grafana. This is heavily used at Zilch for root cause analysis. | Document as a gap. Assess whether alternative workflows exist within Grafana. |

## Deliverables

- Representative workloads instrumented and sending telemetry to Grafana Cloud
- Written PoC assessment document evaluating Grafana Cloud against the success criteria, with evidence from hands-on use
- Hard gate pass/fail register with supporting evidence
- Simulated incident exercise findings

## Dependencies

| Dependency | Type | Detail |
|---|---|---|
| Phase 1a — OTel collection infrastructure | Blocks start | [ZILCH-57057](https://payzilch.atlassian.net/browse/ZILCH-57057) |
| Grafana Cloud org access | Blocks start | Created by Jack George; invites sent 28 Oct. Confirm access for all participants. |
| Grafana vendor support | Ongoing | Contacts: Charlie Lutterloch (account), Stephen Leddy, Jack George (SE). |

## Stakeholders

| Role | Who |
|---|---|
| PoC team | Onboarding (Rob Nelson) |
| Infrastructure support | DevOps |
| Platform support | David Ramsay |
| Incident management criteria | Mark Reddington |
| Security | Oliver Hamilton |
| Sponsor | Steve Rayko |

## Timeline

Target end date: TBD. Dependent on Phase 1a completion and scope refinement.

## Links

- [PoC Success Criteria](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/5967675402/PoC+Success+Criteria)
- Phase 1a: [ZILCH-57057](https://payzilch.atlassian.net/browse/ZILCH-57057)
