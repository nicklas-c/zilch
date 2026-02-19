# Pending Rewards

## Also Known As

Component: Pending Rewards

## Context

Pending Rewards introduces a "Pending" state into the Rewards lifecycle, applying specifically to credit rewards, which are conditional by nature. When a customer makes a qualifying action (e.g. a purchase as a member), rewards are issued immediately in a pending state rather than waiting until maturity. They become realised (spendable) only once maturity conditions are met — e.g. the customer completes a loan on time while remaining a member. Pending rewards are forfeited if conditions are not met, for example due to late payment.

The technical approach uses an immutable, additive ledger: no reward entries are mutated; instead, reversals are recorded as negative entries and new entries are created when values change. The rewards rate is locked (and stored) at the time of purchase, enabling both time-limited promotions and re-calculation of pending rewards following events such as partial refunds. Pending rewards values update dynamically on partial refunds, membership downgrades, full refunds, and other adjustments. Pending rewards are retained between subscription instances.

Existing reward API endpoints (summary and history, at the customer and purchase levels) are extended to return pending and realised values separately, rather than a single aggregate.

UX touchpoints include: receipt drawer, purchases page, app notifications, Rewards Hub (with pending total), cancellation flow (showing what the customer would lose), CRM, sign-up journey, and referrals. Scope is iOS, iPad, and Android — web is out of scope.

Future considerations (not MVP): delayed debit rewards during the payment failure grace period; delayed rewards for Standard members with early release on upgrade to Plus.

Status is In Discovery. Confluence spec: https://payzilch.atlassian.net/wiki/spaces/ZP/pages/5099585537. Design overview: https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5112201230

## Personnel

- Zac Barclay — Product Manager / Document Owner
- Nicklas Chapman — Engineering Manager
- Kieren Messenger — Product Designer

## Running Notes

### 2026-02-19

- Stand-up: Nick Holt chasing what events are available to drive cancellation of pending rewards, and what event signals loss of a feature (e.g. membership downgrade). Connects to the open question raised on 18 Feb about the trigger for reversing a pending reward on late payment.
- ZILCH-48222 (Pending Rewards Technical Discovery & Design) ready for sign-off.

### 2026-02-18

- Read Nick Holt's design overview (Confluence: https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5112201230/Pending+Rewards+Design+Overview+V2). Straightforward — no major concerns.
- Shared observations in team Slack:
  - Imminent blocker is designs from Kieren Messenger for how pending rewards will be displayed.
  - Open question to Zac: should expiry logic be extended to pending rewards? Flagged a plausible edge case — referral rewards issued in a pending state could legitimately sit there for a long time before a referral is made. Current MVP spec doesn't address this.
  - Asked Tom McKenzie to confirm he's across Nick's proposal enough to define tests.
  - Asked Nick to define the trigger for reversing a pending reward on a late payment — expectation is immediate removal, likely via a listener on payment events.

### 2026-02-12

- Briefed Abhishek Chatterjee in 1:1. Discussed purpose (incentivising on-time repayment via visible pending rewards) and edge cases. He was relieved scope doesn't include holding rewards in pending state for months on debit purchases. Nick H and Michal Baran partnering on implementation. Committed to producing an ADR — Abhishek questioned whether a detailed ADR is needed for every small change, but this introduces a lifecycle concept to rewards and is an opportunity to reinforce ADR discipline.

### 2026-02-11

- PRD review meeting held. Discussion got derailed when engineers (Nick H in particular) pulled the conversation into solution design rather than staying focused on clarifying and challenging requirements. Other engineers followed, but Nick initiated it.

### 2026-02-10

- Project log created from Confluence spec (Component: Pending Rewards, version 3, ZP space).
- Wrote up epic description for ZILCH-47121 — context, description, statement of value, implementation notes, out of scope, risks, test plan, roll-out plan, and deliverables. Success criteria and business/product risks left TBC for Product. Linked Confluence spec to the epic.
- Rewrote ZILCH-48222 (Pending Rewards Technical Discovery & Design) — structured as a discovery spike with clear deliverable (ADR) and acceptance criteria. Architectural review expected but not a blocker.
