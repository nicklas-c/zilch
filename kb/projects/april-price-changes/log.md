# April Price Changes

## Context

Pricing structure changes planned for April 2026, requiring 30 days' notice to customers. The channel was created on 5 March 2026; comms to customers began going out from the morning of 6 March.

**Go live date:** 7 April 2026

**Scope of changes:**
1. Po6 pricing for all product lines (Anywhere & Express +£25p)
2. Po6 pricing for OV >£75:
   - Anywhere ECJ +£1
   - Retailer ECJ +£1 (caveat: 0£ fee retailers remain at 0£)
3. App purchases in non-GBP: 3% FX fee
4. Po3 fee cap: increase from £40 to £80 (decided same day as channel creation)

**Detailed pricing table (from Confluence brief):**

| Journey | Up | Classic V2 | X |
|---|---|---|---|
| Outside app / Tier 1 (<£75) | £3.75 (+£0.25) | £3.50 (+£0.25) | £3.25 (+£0.25) |
| Outside app / Tier 2 (>£75) | £4.75 (+£0.25) | £4.50 (+£0.25) | £4.25 (+£0.25) |
| Anywhere ECJ / Tier 1 (<£75) | £3.75 (+£0.25) | £3.50 (+£0.25) | £3.25 (+£0.25) |
| Anywhere ECJ / Tier 2 (>£75) | £4.75 (+£1) | £4.50 (+£1) | £4.25 (+£1) |
| Retailer ECJ / Tier 1 (<£75) | £0–£2.50 (no change) | £0–£2.25 (no change) | £0–£2.00 (no change) |
| Retailer ECJ / Tier 2 (>£75) | £0–£3.50 (+£1, fee-free remain free) | £0–£3.25 (+£1, fee-free remain free) | £0–£3.00 (+£1, fee-free remain free) |

No changes to the fee cap calculation logic — new pricing automatically included in fee cap.

**Engineering assessment:**
- FX fee (item 3): config change on Thredd side. Sean Hederman confirmed there is "zero reason it would be later than that [7 April]".
- Fee changes (items 1, 2, 4): initially assessed as config-only, but a significant complication emerged on 6 March (see Running Notes).
- Team ownership of the config work confirmed on 6 March: **Merchant team** will own the fee changes.

**Approvals (per Confluence brief):**
- Joe Zender (CPO) — approved
- Ozzie Yuce (SVP of Product) — approved
- John Moore (Compliance Manager) — approved

**APR assessment (Harrison Curtis):**
- No APR change needed for Classic or X.
- Up customers are close to the 31.9% limit. Over last 30 days, fee changes take Up from 28.33% to 31.27% — still within limit. Over 90 days (including high-usage December), the figure is 24.9%. Conclusion: no APR change required.
- APR impact detail (items 1+2 combined): Classic +0.82%, Up +2.94%, X +0.77%. Items 3 and 4 have no APR impact.

**RCA (Regulatory Comms Acknowledgement):**
- Filtering requirements set by Tom Wood: email verified; exclude fraud (confirmed 1st-party card fraud, confirmed 1st-party never-pay fraud), overdue churned, insolvency, DRO, bankruptcy, defaulted, not obsolete; must have signed the minimum version of the RCA. Flag (not filter) for 6-month activity.
- RCA update ticket: RTCR-19.

**Comms logistics:**
- Customer lists: 3 lists required (Up, Classic, X) — single column, User ID only. Edward Newkirk pulling; to share with Thomas Peter Breakwell.
- Comms throttled to ~7k/hour across all product lines to reduce operational burden.
- Thomas Peter Breakwell noted that new customers joining weekly will also need to be sent emails quoting the change date — an ongoing task, not just a one-off.

**Rollout order (per Confluence brief):**
Staff → Zilch X → Zilch Up → Zilch Classic V2

**Lender notice:**
Assumed both tiered pricing tiers require notice to lenders — to be confirmed with Legal.

**Consumer Duty:**
- Following required product delivery process.
- Vulnerable customer assessment: TBD
- Price and value review: TBD (to be updated in brief prior to launch)

**Engineering approach (confirmed in Confluence brief):**
FE-only changes — no BE dependency on pricing changes. Acknowledged tech debt: no single source of truth for fee calculation. Fast-follow clean-up planned after PayMonthly and pricing go-live.

**Compliance:**
- Wayne Badura confirmed that any delay beyond 7 April in activating the FX fee is to customers' benefit and is therefore acceptable.
## References

### Jira

**Epic:** [ZILCH-49226](https://payzilch.atlassian.net/browse/ZILCH-49226) — "Pricing changes April 2026" — Status: Proposed, Priority: Unknown, Assignee: Unassigned. Created 6 March 2026. Note: epic description covers only the Po6/Po3 changes (items 1–4); the FX fee (item 3) is not referenced — possibly a separate ticket or omitted because it requires no Zilch engineering effort.

### Confluence

- Product Brief (Tamara Quinn): https://payzilch.atlassian.net/wiki/spaces/ZP/pages/5188386851/April+Pricing+change+Brief

### Slack

#april-pricing-changes

### Other

- Designs (Isabela Coelho): https://www.figma.com/design/8qCUc616l1vDhMvkOp4Fmn/PO6-Fees?node-id=376-6500
- Compliance ticket: https://trello.com/c/om0MbmHP/1585-crm-crm-email-rca-fee-change-current-05-03-2026

## Personnel

- Ozlem Yuce (Ozzie) — SVP of Product (coordinating)
- Steve Rayko — SVP Engineering (engineering timelines)
- Nicklas Chapman — Engineering Manager, Merchant (added to channel 5 Mar; previously briefed by Steve Rayko)
- Tamara Quinn — Product Brief, RCA update ticket
- Tom Wood — RCA filtering requirements
- Sean Hederman — CTO (confirmed FX is Thredd config)
- Harrison Curtis — APR assessment
- Will Tran — data
- Edward Newkirk — data (customer list extraction)
- Thomas Peter Breakwell — comms/CRM
- Isabela Coelho — design
- Marcelo Dos Santos — (joined)
- Rocharne Brady — service ops
- Wayne Badura — compliance
- Ella Harding — copy
- Joe Zender — (decision on Po3 fee cap)
- Kirsty Spickett — (decision on Po3 fee cap)
- Andrzej Lorenz — VP Engineering (cross-team scope clarification)
- Grzegorz Ziemiański — Engineering Manager, Acquirer/Issuer (raised fee-service/EHI dependency)
- Michał Górny — Engineering Manager (Purchase team scope, to confirm)

## Digest

### 2026-03-05

- Channel #april-pricing-changes created. Ozzie kicked off with urgency: pricing changes effective 7 April, 30-day notice period means customer comms must go out tonight/tomorrow morning.
- Po3 fee cap decision made same day: increase from £40 to £80.
- Engineering date confirmed (Steve Rayko): 7 April.
- Harrison Curtis completed APR assessment: no change required. Up customers checked against 31.9% limit — within bounds.
- Tom Wood set RCA filtering criteria; Tamara Quinn raised RCA ticket (RTCR-19).
- Tamara Quinn published draft Product Brief to Confluence.
- Isabela Coelho published Figma designs; copy marked in red for Jen Woods-Blee.
- Rocharne Brady requested approval to throttle comms sends to ~7k/hour; Thomas Peter Breakwell approved.
- Ozzie confirmed to Nicklas and Steve: ECJ pricing for 0£ retailers will NOT increase by £1 — caveat to item 2.

### 2026-03-06

- Ella Harding: copy ready, pending compliance feedback.
- Wayne Badura (compliance): confirmed FX delay beyond 7 April is acceptable as it benefits customers.
- Sean Hederman: clarified FX fee is a Thredd config change — no engineering effort required; no reason for it to be late.
- Edward Newkirk: pulling customer lists; to share with Thomas Peter Breakwell at 11am.

**Engineering complexity — fee-service/EHI (second Slack thread, ~10am):**

Andrzej Lorenz asked Tamara Quinn to clarify what engineering work is required for Purchase, Merchant, and Issuer. Grzegorz Ziemiański raised a significant complication: Po6 is still partially routed through EHI rather than fee-service. Because item 2 (Po6 OV >£75 ECJ increase) is amount-dependent, EHI would need the fee-service integration to be fully rolled out in order to handle it.

Context: the fee-service integration with EHI was previously rolled out but was reverted due to risk and timeouts. The team had been waiting to re-enable it as part of a historical fees initiative. Andrzej expressed frustration ("why have we not rolled out fully the f-s integration?"); Grzegorz responded that they were waiting because they were told to. Andrzej did not pursue this further and redirected to the immediate question of scope per team.

Nicklas Chapman added to the thread at 10:12 AM (same moment Andrzej asked for a Purchase/Merchant/Issuer breakdown).

Tamara Quinn confirmed the Purchase team is assessing scope; Michał Górny to confirm in the next few hours. Impact on Pay Monthly and Flex also being assessed.

**Status as of mid-morning 6 March:** Scope across Purchase, Merchant, and Issuer is not yet confirmed. The fee-service/EHI dependency may materially increase engineering complexity beyond the initial "config only" assessment.

**Fee-service rollout greenlit (same thread, ~10:28 AM):**

Grzegorz Ziemiański shared current split: 23% EHI vs 77% fee-service, 80 timeouts over the past 4 weeks, 99.997% success rate. Andrzej confirmed: no reason not to move 100% to fee-service.

Tamara Quinn invited Nicklas Chapman and Grzegorz to join the Purchase refinement session immediately; Andrzej was in interview and unavailable. Nicklas joined ~10 minutes late.

**Purchase team scope confirmed (Michał Górny, ~12:23 PM):**

- Hardcoded fee values: update on FE (web + mobile)
- ECJ pricing: update (web + mobile)
- Calculator fee cap: PO3 change (max fee £40 → £80)
- Test updates

Dependencies flagged by Purchase team:
- **Storefront adaptive header:** sourced from fee-service on the Merchant side — flagged to Nicklas Chapman
- **Issuer:** fee-service rollout status — flagged to Grzegorz Ziemiański (TBC)

**April 6th feasibility:** Purchase scope achievable by end of next sprint, but will delay PayMonthly work by approximately one sprint. Items deferred: Credit Multiplier, ECJ, Purchase Comms.

Tamara asked Nicklas and Grzegorz to confirm sign-off on this update.

**Cross-team capacity question (Andrzej, ~12:39–1:17 PM):**

Andrzej asked whether Ossie (Merchant FE) could help Purchase with the ECJ work to preserve the PayMonthly timeline. Michał Górny: workable if Ossie has ECJ experience, but onboarding a new engineer adds complexity. BE scope should be fine provided the pricing change scope doesn't grow.

PO3 calculator cap clarified: a single change to the max fee value (£40 → £80).

**Tech debt alternative (Michał Górny, ~1:42 PM):**

Michał proposed an alternative: FE-only changes, removing the BE dependency on pricing changes. This would preserve the PayMonthly timeline but introduce tech debt — no single source of truth for fee calculation in a sensitive area, requiring a fast-follow clean-up after PayMonthly launch and pricing go-live.

Andrzej's response: "we already are in this situation." Directed Tamara to document it as a known system limitation — and a potential blocker for any subsequent pricing changes.

**Ossie availability (Nicklas Chapman, ~3:00 PM):**

Responded to Andrzej's question: Ossie is currently slated for Pay Monthly Admin Portal work, but Jacek is also capable of covering that — swapping them could free Ossie up for Purchase. Noted this is more feasible given the fee-service changes have been significantly simplified. Committed to giving a definitive answer by end of day.

Michał Górny to post a summary of the options to #april-pricing-changes to keep all parties informed.

**Fee change ownership resolved:** Merchant team confirmed as the owner of the fee changes for April pricing.

### 2026-03-09

- Cross-team refinement session scheduled to refine FE tickets under ZILCH-49226. Merchant team picking up this work to allow Purchase and other teams to remain focused on EWA/Extra and Pay Monthly.
