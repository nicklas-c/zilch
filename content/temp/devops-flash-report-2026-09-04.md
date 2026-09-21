<u>DevOps</u>

*Ephemeral Environments*
* ZOE "pending until build artifact" feature completed — Zephyr now waits in a pending state until a valid build is published before deploying.
* ZOE "building" lifecycle status implemented and ready for sign-off.
* Proposed combining the branch-deploy quality gate with E2E test execution against ephemeral environments — would unify the two workflows.
* 2 cross-team postgres compatibility tickets completed. Zephyr update posted to #engineering calling on remaining teams to prioritise; S&R committed their services for next sprint.
* *In Progress*: PostgreSQL pod per ephemeral environment — resolving RDS connection limit at scale.
* *In Progress*: Zephyr build gate deployment.
* *In Progress*: Dedicated Payout wallet per ephemeral environment.
* *In Progress*: ZOE mobile config metadata envelope.

*New Web*
* Datadog agent config added to SSR apps.
* AppSets for QA/staging created and marketing-web deployed on QA-SIT.
* *In Progress*: SSR assets cache behaviour for S3 bucket.
* *In Progress*: Terraform microservice module cleanup following dev-unified migration.


*Operations*
* Billing run incident (29 Aug): afternoon run stuck at 94% due to shedlock. Resolved overnight — shedlock released, cron rescheduled, subsequent runs verified.
* Release-please v4 dropped `always-bump-patch` for release branches — caused mobile-ui version to bump incorrectly (2.59.0 instead of 2.58.3). Version corrected; working on a rule to prevent `feat:` commits on release branches.
* Fixed fraud-agent GitHub action bug — AWS CLI pagination appending `None` to RUNTIME_ID. Resolved with `--no-paginate`.

*Datadog Cost Optimisation*
* August cost confirmed at $82,964.75 — approximately 17.4% reduction vs June baseline.
* Committed spend now appearing correctly in cloud cost data.

*Issues*
* Multi-tier CDN structure tripping loop detection — investigating potential solutions with Chris W.