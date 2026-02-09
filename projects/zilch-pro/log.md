# Zilch Pro

## Also Known As
* Memberships Pro
* Pro Tier
* Pro Memberships
* Pro Subscriptions

## Context

### Overview
Zilch Pro is the premium-tier paid membership at **£7.99/month**, positioned above Zilch Plus (£3.99/month). Targeted at Zilch's most highly engaged customers.

### Key Dates
| Milestone | Date |
|-----------|------|
| Staff testing enabled | 16 February 2026 |
| Last FE release (with 2 weeks ramping) | 16 February 2026 |
| Customer launch | **Uncertain** (was 4 March 2026) |
| Target: 2.3% MAU adoption | 1 April 2026 |

**Note:** Launch date is uncertain due to partnership dependencies and a likely strategic pivot. See running notes for 2026-02-05.

### Tier Comparison
| Feature | Standard (Free) | Plus (£3.99) | Pro (£7.99) |
|---------|----------------|--------------|-------------|
| Physical Card | £4.99 | Free | Free Pro card |
| Customer Service | Standard | Priority | 24/7 Premier Support |
| Tastecard | ❌ | ✅ | ✅ |
| Partner Perks | ❌ | ❌ | ✅ |
| Free Snoozes | ❌ | ❌ | 3/month |
| Milestone Rewards | ❌ | ❌ | ✅ |
| Rewards (unlock & pay now) | Min 2% | Min 3% | Min 4% |

### Key Pro Benefits
- **24/7 Premier Support** — top-tier customer service
- **Higher Rewards** — minimum 4% on debit purchases
- **Free Snoozes** — 3 per month (payment deferrals)
- **Partner Perks** — exclusive perks across supermarkets, travel, food, electronics
- **Milestone Rewards** — bonus rewards for early repayment
- **Free Pro Card** — premium physical card

### Delivery Status (as of Iteration 11)
**Complete:**
- Card design and ordering
- Pro card issuance journeys
- Digital card to wallet
- Merchant domain touchpoints identified
- Retain domain touchpoints identified
- Higher rewards implementation
- Premier support setup

**In Progress:**
- Design Pro UX
- Snooze (compliance approval)
- Physical card
- Commercial value prop (partnerships)
- Marketing assets

**Not Started:**
- Free snooze feature build
- Partnerships integration
- T&Cs
- Partner offers in UX

### Jira Status (as of 2026-02-05)

**Summary:** ~50 tickets in ZILCH project related to Pro.

| Status | Count |
|--------|-------|
| Done/Completed | ~18 |
| Ready for Release | ~8 |
| In PR / Ready for Testing | ~4 |
| In Dev | ~10 |
| Ready for Dev / Created | ~15 |
| Rejected | ~5 |

**Key work streams:**
- **Product/subscription foundation** — largely complete (Tomasz Więckowski)
- **Tier migration (upgrade/downgrade)** — mostly complete; [ZILCH-38927](https://payzilch.atlassian.net/browse/ZILCH-38927) (Plus→Pro upgrade) still in PR
- **Mobile app UI** — actively in progress (Paweł Pęcikiewicz, Rory Fielding)
- **Pro card design/issuing** — pending, P2 High priority
- **Comms/marketing** — mostly done
- **T&Cs** — [ZILCH-46803](https://payzilch.atlassian.net/browse/ZILCH-46803) still Created (not started)
- **Analytics/Mixpanel** — [ZILCH-47423](https://payzilch.atlassian.net/browse/ZILCH-47423) still Created

**Merchant team involvement:**
- [ZILCH-47117](https://payzilch.atlassian.net/browse/ZILCH-47117) — Zilch Pro Merchant UI Updates — In Dev (unassigned)
- [ZILCH-47571](https://payzilch.atlassian.net/browse/ZILCH-47571) — Add product line taxonomy for Pro in Content Stack — In Dev (Ossie Nwokedi)

**Key ticket:** [ZILCH-45705](https://payzilch.atlassian.net/browse/ZILCH-45705) — Zilch Pro (P1 Highest) — owned by Zac Barclay

### Technical Notes
- Subscriptions managed by **Product Service**
- Coordinates with Payments (billing) and Customer (product alignment)
- Single active subscription at any time
- Global free trial: at most one free trial across all tiers
- Upgrades: immediate; Downgrades: scheduled for next billing date
- Targeting service controls rollout via segments (e.g. `PRO_SUBSCRIPTIONS_INITIAL_ROLLOUT`)
- Downgrade API: `POST /customer-api/products/subscriptions/change`

### Known Issues / Lessons from Plus Launch
- **Duplicate subscription bug**: Race condition (130ms delay between requests) can cause multiple active subscriptions. Requires manual cancellation via admin endpoint.
- **Bank statement text**: Shows "ZILCH * INSTALMENT" — confusing for customers expecting "Zilch Membership". Acquirer ticket needed.
- **Billing race condition**: P4 incident #incident-362 — some fees not collected due to race condition in billing mechanism.
- **Dark mode styling**: Back arrow not skinned correctly in dark mode.

### Plus Launch Billing Stats (for reference)
First major billing cycle (July 2025):
- 780 customers due to be billed
- 59 cancelled before due date (721 billing attempts)
- 68.9% success on first attempt; 83% of declines were insufficient funds
- After 3 retry attempts: **76% free-to-paid conversion** (592/780)

### Strategic Context
Part of a broader memberships roadmap:
- **Zilch Extra** (future) — £1.99 entry tier below Plus
- **Zilch Ultimate** (future) — ~£16.99 power user tier

Pro's strategic role:
- Platform to introduce richer, differentiated tiers over time
- Retain highest-value customers
- Improve GP by migrating highly engaged Plus users
- Create a "value anchor" enhancing perceived value of Plus

### Experimentation Plan
Two parallel cohorts:
1. **MAU Cohort** — lifecycle and penetration learning
2. **Plus MAU Cohort (10k)** — statistically powered measurement of financial impact

Key metrics: GP per user, penetration, GMV per user, adoption/retention rates, benefit utilisation.

### Key Confluence Pages
- [Zilch Pro Product Overview](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4566122730/Zilch+Pro+Product+Overview)
- [Zilch Pro Delivery Plan](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4661641220/Zilch+Pro+Delivery+Plan)
- [Zilch Pro Experimentation Plan](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4949016869/Zilch+Pro+Experimentation+Plan)
- [Marketing Brief](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4721672193/Marketing+Brief+-+Zilch+Pro+onwards+emails+push+notifications+in+app+customer+flow+breakdowns)
- [Memberships Strategy](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4899143704/Memberships+Strategy)
- [Technical Design: Subscriptions](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/5050040321/Technical+Design+Subscriptions+and+Migration+Between+Product+Tiers)
- [Memberships Pivot Strategy](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/5073961037/Zilch+Memberships+Pivot+Strategy)

## Personnel

- Ozzie Yuce (SVP Product — launch decision-maker)
- Zac Barclay (PM)
- **Nicklas Chapman (coordinating Pro launch)**
- Craig Main, Marek Chodak (Payments)
- Tomasz Michalski, Tommy Kwok, John Strawhorne (Decisioning/Product Service)
- Rory Fielding, Jan Michalak (Retain FE)
- George Sharpe (cohort management)
- Harrison Curtis (data/analytics)

## Running Notes

### 2026-02-04

Project log created.

### 2026-02-05

**Launch date now uncertain.** Two factors:

1. **Partnership dependency**: Ozzie Yuce (SVP Product) has said she does not want to launch without at least one, preferably two, partnerships in the offering. Business-side timelines for agreeing these are uncertain.

2. **Strategic pivot likely**: Pro may be deprioritised in favour of other projects. Two possible outcomes:
   - **(a) Pause**: Hold work for completion at a later date.
   - **(b) Reduced scope**: Finish current benefits, launch with lower price and lesser value proposition.

**Open question**: What cohorts do we release to? Rollout strategy needs clarification.

**Catch up meeting prep — talking points:**
1. Timeline for pivot decision — when will we know if it's pause vs reduced scope?
2. If reduced scope, what features get dropped?
3. Rollout strategy — what cohorts do we release to?
4. What's technically involved in a release?
5. Share Jira query — cross-team view of all Pro tickets

**Pro sync meeting notes:**

*X-functional updates:*
- **Partnerships**: Luke leading. Some opportunities moving forward in the pipeline. Luke will attend future meetings with sales updates. Dates still hard to predict. If things continue as-is, would be an iteration 12 launch.
- **Customer support**: Talking to business partners about differentiating tiers for enhanced support.
- **Marketing (Pro card)**: Assets still not complete. Was planned for next sprint but pushed back due to shifting priorities.
- **Marketing (Pro marketing)**: Assets in progress — should be done by end of next week.
- **Snooze**: Product discussing what snooze would look like. Possible option to go to market without snooze, but no decision taken.
- **T&Cs**: Still have lead time. Not started yet.
- **Upgrade/downgrade**: Dependencies on Payments and Decisioning. *[Status unclear — need to clarify asynchronously.]*

*Other:*
- Reviewed Jira query showing tickets that need to be completed.
- Raised topic of technical steps for rollout and cohort plan. Will meet next week with Zac, Ethan (Product Analyst), and EMs to figure that out.
- Noted smooth release of Memberships × Physical Cards to GA yesterday.

*(Potential pivot still confidential — not discussed.)*
