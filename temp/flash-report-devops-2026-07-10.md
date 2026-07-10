**DevOps**

**Ephemeral Environments**
* **In Progress**: Zephyr build gate (per-repo PR check to block merge on broken builds) still in active development.
* Reactive fixes ongoing — this week: cross-service IAM for customer-service → credit-risk-service SQS in ephemerals.
* Debugging workshops announced — team-specific sessions starting next week, requesting at least one BE + QA per team.

**Dev Platform Rebuild**
* Remediating issues on dev-cu continues. Test pass rate improving.
* Identified multiline log ingestion issue on unified dev environment.  Planned fix at application layer.

**New Web**
* cloudfront-web-app Terraform module spike in PR.
* **In Progress** marketing-web workspace setup in progress.

**DevEx / Tooling**
* Actuator /info version-reporting rollout complete — all 30 deployed backend services now report running version at their /info endpoint. New services covered by default.
* Acquirer Datadog terraform now auto-applies after merge to main.

**Operations**
* Thredd maintenance (5 Jul) — banner raised overnight, no issues observed.

**Incidents**
* Brief Datadog API outage on Mon 7 Jul caused metric delivery errors across multiple services. Root cause DD-side; recovered within ~2 hours.
