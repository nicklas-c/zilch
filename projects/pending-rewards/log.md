# Pending Rewards

## Also Known As

Component: Pending Rewards

## Context

Pending Rewards introduces a "Pending" state into the Rewards lifecycle. When a customer makes a qualifying action (e.g. a purchase as a member), rewards are issued immediately in a pending state rather than waiting until maturity. They become realised (spendable) only once maturity conditions are met — e.g. the customer completes a loan on time while remaining a member.

The rewards rate is locked at the time of purchase, enabling time-limited promotions. Pending rewards values update dynamically on partial refunds, membership downgrades, full refunds, and other adjustments. Pending rewards are retained between subscription instances.

UX touchpoints include: receipt drawer, purchases page, app notifications, Rewards Hub (with pending total), cancellation flow (showing what the customer would lose), CRM, sign-up journey, and referrals. Scope is iOS, iPad, and Android — web is out of scope.

Future considerations (not MVP): delayed debit rewards during the payment failure grace period; delayed rewards for Standard members with early release on upgrade to Plus.

Status is In Discovery. Confluence spec: https://payzilch.atlassian.net/wiki/spaces/ZP/pages/5099585537

## Personnel

- Zac Barclay — Product Manager / Document Owner
- Nicklas Chapman — Engineering Manager
- Kieren Messenger — Product Designer

## Running Notes

### 2026-02-12

- Briefed Abhishek Chatterjee in 1:1. Discussed purpose (incentivising on-time repayment via visible pending rewards) and edge cases. He was relieved scope doesn't include holding rewards in pending state for months on debit purchases. Nick H and Michal Baran partnering on implementation. Committed to producing an ADR — Abhishek questioned whether a detailed ADR is needed for every small change, but this introduces a lifecycle concept to rewards and is an opportunity to reinforce ADR discipline.

### 2026-02-11

- PRD review meeting held. Discussion got derailed when engineers (Nick H in particular) pulled the conversation into solution design rather than staying focused on clarifying and challenging requirements. Other engineers followed, but Nick initiated it.

### 2026-02-10

- Project log created from Confluence spec (Component: Pending Rewards, version 3, ZP space).
- Wrote up epic description for ZILCH-47121 — context, description, statement of value, implementation notes, out of scope, risks, test plan, roll-out plan, and deliverables. Success criteria and business/product risks left TBC for Product. Linked Confluence spec to the epic.
- Rewrote ZILCH-48222 (Pending Rewards Technical Discovery & Design) — structured as a discovery spike with clear deliverable (ADR) and acceptance criteria. Architectural review expected but not a blocker.
