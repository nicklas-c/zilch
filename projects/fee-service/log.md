# Fee Service

## Also Known As

*To be added*

## Context

*To be populated as context arises.*

## Personnel

*To be added*

## Backlog (Merchant Team, To Do)

As of 13 Feb 2026, the following fee-service-related tickets are tagged to Merchant Team and in a "To Do" status category:

| Ticket | Summary | Status | Priority | Assignee |
|---|---|---|---|---|
| [ZILCH-48343](https://payzilch.atlassian.net/browse/ZILCH-48343) | Upgrade AWS JDBC Driver in fee-service | Created | — | Unassigned |
| [ZILCH-47989](https://payzilch.atlassian.net/browse/ZILCH-47989) | A/B Test Retailer Fees | Proposed | — | Unassigned |
| [ZILCH-47400](https://payzilch.atlassian.net/browse/ZILCH-47400) | Merchant O11y Audit & Refresh | Proposed | — | Unassigned |
| [ZILCH-45927](https://payzilch.atlassian.net/browse/ZILCH-45927) | Introduce pre-warm capability to fee-service | Created | — | Unassigned |
| [ZILCH-44714](https://payzilch.atlassian.net/browse/ZILCH-44714) | Add HTTP in DB transaction detection library to merchant team-owned services | Created | P3 Medium | Unassigned |
| [ZILCH-43416](https://payzilch.atlassian.net/browse/ZILCH-43416) | Fee service timeout causes sanity test failure | Ready for dev | P2 High | Unassigned |
| [ZILCH-42522](https://payzilch.atlassian.net/browse/ZILCH-42522) | Enable Reference ID Generator Post-Aurora Migration | Created | — | Unassigned |

## Running Notes

### 2026-02-19

Stand-up:
- **DataDog alert — noisy neighbour latency spike.** Gavin Dunn (Underwriting) ran a bulk upgrade of 22k customer product levels via Bulkify at 10/s, starting ~15:32. Michal noticed a significant latency increase on fee-service starting at 15:32 — p99 rose to ~50ms (vs usual baseline), well below the 100ms SLA, but ~3x above normal. Jacek identified a slow query and traced it to wallet-providers-service, which subscribes to product change events and was querying a table of 2 million rows without a required index. Jakub Zrebiec (wallet-providers-service) confirmed the missing index and will raise a ticket for Platform to create it. Latency returned to normal once the bulk job completed. Grzegorz Ziemiański (wallet-providers-service) raised a broader concern: the Aurora migration was partly motivated by preventing noisy neighbour problems, but this incident suggests the problem can still occur. Platform (Charlie Hurst / Benjamin Ibrulj) investigating. No timeouts on ehi-service; all loans processed with correct fees.
- **ZILCH-43416** (fee-service timeout causes sanity test failure): Michal analysed test failures and concludes the issue is no longer a problem. Moving to Ready for Sign-off.

### 2026-02-16

Stand-up:
- Michal: getting started with playbooks for fee changes.
- Michal: coordinating decommissioning of MSSQL fee database with Platform.

### 2026-02-12

- Confirmed in 1:1 with Abhishek Chatterjee that fee-service is moving to the new team with Michal Baran (effective 24 Feb). Abhishek hadn't been aware of the move.
