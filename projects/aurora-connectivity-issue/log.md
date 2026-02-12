# Aurora Connectivity Issue

## Also Known As

Aurora cluster endpoint issue; globalClusterInstanceHostPatterns issue.

## Context

The Platform team made a change to Aurora infrastructure to support regional failover (Aurora Global Database). This change introduced a hard requirement for services to include a `globalClusterInstanceHostPatterns` configuration property in their JDBC connection setup, via the AWS Advanced JDBC Wrapper's failover plugin.

The change appears to have been deployed to production first, without staging validation. Services that hadn't been restarted since the change continued to run fine, but any service attempting to start (e.g. during a release) would fail to connect to the database.

Fee-service was the first Merchant-owned service to hit this. ehi-service reportedly hit the same issue. It's unclear how many other services are silently affected — they'll break on next restart.

The Platform team currently has no manager (Ali Aziz left the company), which may be contributing to the lack of visibility and accountability around this change.

Potentially related to ZILCH-48084 and ZILCH-48248.

## Personnel

- **Nick H** — reported the issue, investigating from the Merchant side. Engaging with Platform in #platform-ops.
- **Michal Baran** — reported the issue alongside Nick H.
- **Phil Stephenson** — identified the specific config change needed and confirmed the change was deployed prod-first.
- **Nick Gilbert** — confirmed Platform made the change for regional failover; DevOps were not informed.
- **Charlie Hurst** (Platform) — investigating a related DB init script failure (`create_user.sql` erroring in Argo). Partially engaged but distracted by other priorities.
- **Abdul Wahid** (Platform) — flagged the `create_user.sql` error.

## Key Technical Detail

The fix for affected services is to add `global-cluster-instance-host-patterns` to the service's deploy config, e.g.:

```
global-cluster-instance-host-patterns: "eu-ew1-staging-storage-issuer-?.cunscjbmv8ve.eu-west-1.rds.amazonaws.com,eu-ew2-staging-storage-issuer-?.cik9zyi8spqq.eu-west-2.rds.amazonaws.com"
```

Phil's view is that this should be wildcarded rather than requiring environment-specific config per service.

Reference: [AWS Advanced JDBC Wrapper — Failover2 Plugin](https://github.com/aws/aws-advanced-jdbc-wrapper/blob/main/docs/using-the-jdbc-driver/using-plugins/UsingTheFailover2Plugin.md#host-pattern)

## Open Questions

1. **Scope of impact** — how many other services are silently broken (will fail on next restart)?
2. **Why prod first?** — was there a reason staging was skipped, or was it simply an oversight?
3. **DB init script failure** — ~~Charlie is investigating a separate `create_user.sql` error. He says it's benign (only needs to run once), but acknowledges it could indicate another issue.~~ Resolved: root cause is re-running a schema ownership command that's already been applied. Charlie has a v2 idempotent script and an AWS support ticket open.
4. **Communication gap** — no announcement or heads-up was given about this change. How do we prevent this happening again?
5. **Test coverage gap** — how did regression/sanity tests pass if the JDBC driver update broke DB connectivity on staging? Suggests DB configuration differs between lower environments and staging/prod, which is a systemic risk.
6. **Release-please configuration** — the Dependabot PR for the AWS JDBC driver didn't result in a release-please minor version bump. Why not?

## Running Notes

### 2026-02-11

Project log created. Issue reported by Nick H and Michal Baran.

**Slack thread summary (from three threads):**

- **Nick H → #platform-ops:** Reported fee-service DB init script error in Argo staging. `create_user.sql` failing with "column is not in index". Charlie Hurst investigating — same script works from pgAdmin. Phil questioned why the init script was being run again. Nick H clarified he was following the Confluence doc on Aurora setup and seeing `globalClusterInstanceHostPatterns` errors in staging.

- **Me → Charlie Hurst (DM):** Tried to understand what changed. Charlie pointed to the failover plugin config doc and a DB init script issue. Conversation was at cross-purposes — Charlie seemed focused on the init script; I was asking about the root cause of the connectivity breakage. Agreed to set up a call with Nick H and Charlie to align.

- **Me → Nick Gilbert & Phil Stephenson (DevOps):** Nick G confirmed Platform made a change for regional failover without informing anyone. ehi-service had the same issue. Phil identified the specific config (`global-cluster-instance-host-patterns`) and confirmed it was deployed to prod first. Phil's view: the config requirement is unfortunate but the lack of staging-first testing is the real problem.

### 2026-02-12

**Charlie Hurst — update on DB init script issue:**

Charlie completed his investigation. The root cause of the `create_user.sql` failure is that the script tries to set the owner of the public schema, but this was already done during initial database setup. On re-run, the command fails because ownership is already set. This is an Aurora-internal behaviour that can't be fixed from our side.

Actions taken:
- Charlie has written a v2 of the setup script that only sets ownership when it's currently incorrect (idempotent).
- He's opened an AWS support ticket for the underlying Aurora behaviour.
- He'll roll out the new script, which will fix the `init-db` task.

**Nick H — Dependabot AWS JDBC driver regression (fee-service):**

Separate from the `globalClusterInstanceHostPatterns` issue: a Dependabot update to the AWS JDBC driver broke fee-service connectivity on staging. Michal Baran's hunch that the driver update was the cause proved correct. Nick downgraded the driver and staging came back up.

Actions taken:
- Nick excluded the AWS JDBC driver from Dependabot ([PR #336](https://github.com/zilchdev/fee-service/pull/336)).
- A separate ticket will be raised to figure out how to safely upgrade the driver.

Open questions raised by the team:
- **Tom McKenzie:** How did regression/sanity tests pass if the driver broke DB connectivity? Michal suspects DB configuration differs between lower environments and staging/prod.
- **Michal Baran:** Why didn't the Dependabot PR result in a release-please minor version bump? Worth investigating the release-please configuration.

**Stand-up — 2026-02-12:**
- ZILCH-48084 confirmed related to this issue. Nick H has a way forward: downgrading the JDBC driver for now and has created a new ticket to implement a proper fix for the updated driver.
