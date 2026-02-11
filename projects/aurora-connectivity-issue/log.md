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
3. **DB init script failure** — Charlie is investigating a separate `create_user.sql` error. He says it's benign (only needs to run once), but acknowledges it could indicate another issue.
4. **Communication gap** — no announcement or heads-up was given about this change. How do we prevent this happening again?

## Running Notes

### 2026-02-11

Project log created. Issue reported by Nick H and Michal Baran.

**Slack thread summary (from three threads):**

- **Nick H → #platform-ops:** Reported fee-service DB init script error in Argo staging. `create_user.sql` failing with "column is not in index". Charlie Hurst investigating — same script works from pgAdmin. Phil questioned why the init script was being run again. Nick H clarified he was following the Confluence doc on Aurora setup and seeing `globalClusterInstanceHostPatterns` errors in staging.

- **Me → Charlie Hurst (DM):** Tried to understand what changed. Charlie pointed to the failover plugin config doc and a DB init script issue. Conversation was at cross-purposes — Charlie seemed focused on the init script; I was asking about the root cause of the connectivity breakage. Agreed to set up a call with Nick H and Charlie to align.

- **Me → Nick Gilbert & Phil Stephenson (DevOps):** Nick G confirmed Platform made a change for regional failover without informing anyone. ehi-service had the same issue. Phil identified the specific config (`global-cluster-instance-host-patterns`) and confirmed it was deployed to prod first. Phil's view: the config requirement is unfortunate but the lack of staging-first testing is the real problem.
