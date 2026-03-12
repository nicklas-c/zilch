# Fee Service

## Context

*To be populated as context arises.*

## Personnel

*To be added*

## Digest

### 2026-02-12

- Confirmed in 1:1 with Abhishek Chatterjee that fee-service is moving to the new team with Michal Baran (effective 24 Feb). Abhishek hadn't been aware of the move.

### 2026-02-13

- Reviewed fee-service backlog in Jira — identified 7 Merchant Team tickets in "To Do" state.

### 2026-02-16

- Michal Baran getting started with playbooks for fee changes.
- Michal Baran coordinating decommissioning of MSSQL fee database with Platform.

### 2026-02-18

- ZILCH-42041 (decommission MSSQL database): Platform only just picked up their part. Michal Baran continues to track.
- ZILCH-46517 (fee-change playbooks): Michal Baran done, in review with Jacek Zanko.

### 2026-02-19

- Signed off ZILCH-43416 (fee-service timeout causes sanity test failure) — Michal analysed and concludes it's no longer a problem.
- Reviewed and commented on Michal Baran's fee-change playbooks (ZILCH-46517).
- **Noisy neighbour latency spike.** Underwriting bulk upgrade (22k customers at 10/s) caused fee-service p99 to rise to ~50ms (~3x normal), still below 100ms SLA. Root cause: wallet-providers-service querying a 2M-row table without a required index. Grzegorz Ziemiański raised a broader concern — Aurora was partly adopted to prevent noisy neighbour problems. Platform investigating.

### 2026-02-20

- Flash report: latency spike noted. ZILCH-42041 still waiting on Platform (PO-1597).

### 2026-02-23

- ZILCH-46517 (fee-change playbooks) closed off — the last mitigation ticket for Incident-417. Incident now closed.
