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
| MVP launch | **Q2 2026 (probably May)** |
| V1 launch | **H2 2026** |
| Target: 2.3% MAU adoption | 1 April 2026 (likely outdated) |

**Note (11 Feb):** Original timelines defunct. Resource being moved off Pro. Scope reduced for MVP: auto-snooze and physical card dropped (likely return in V1). Partnerships remain in scope but deals not yet closed.

### Tier Comparison
| Feature | Standard (Free) | Plus (£3.99) | Pro (£7.99) |
|---------|----------------|--------------|-------------|
| ~~Physical Card~~ | £4.99 | Free | ~~Free Pro card~~ (dropped from MVP; likely V1) |
| Customer Service | Standard | Priority | 24/7 Premier Support |
| Tastecard | ❌ | ✅ | ✅ |
| Partner Perks | ❌ | ❌ | ✅ |
| ~~Free Snoozes~~ | ❌ | ❌ | ~~3/month~~ (dropped from MVP; likely V1) |
| ~~Milestone Rewards~~ | ❌ | ❌ | ~~✅~~ Descoped |
| Rewards (unlock & pay now) | Min 2% | Min 3% | Min 4% |

### Key Pro Benefits
- **24/7 Premier Support** — top-tier customer service
- **Higher Rewards** — minimum 4% on debit purchases
- ~~**Free Snoozes** — 3 per month (payment deferrals)~~ Dropped from MVP; likely V1
- **Partner Perks** — exclusive perks across supermarkets, travel, food, electronics
- ~~**Milestone Rewards**~~ — descoped early due to insufficient value vs effort. May return as a separate initiative in future.
- ~~**Free Pro Card** — premium physical card~~ Dropped from MVP; likely V1

### Delivery Status (as of Iteration 11)

#### Team Ownership
| Feature | Primary Team | Notes |
|---------|-------------|-------|
| Higher Rewards | Decisioning | Rate config in DB would normally fall to Merchant — **needs verifying** |
| Free Auto Snooze | Payments | Blocked on compliance approval and product definition |
| Partnerships | Merchant | Blocked on business deals closing |
| Subscription/Tier Management | Product Service / Decisioning | |
| Mobile App UI | Retain | |
| Merchant UI Updates | Merchant | |
| Premier Support | Ops (not engineering) | |
| Physical Card | Cross-team | Engineering done; remaining work is marketing/design |
| Tastecard | — | Inherited from Plus; no Pro-specific work |
| Digital Card to Wallet | — | Inherited from Plus; no Pro-specific work |
| ~~Milestone Rewards~~ | — | Descoped — dropped early for insufficient value vs effort. May return as a separate initiative. |

**Complete:**
- Card design and ordering
- Pro card issuance journeys
- Merchant domain touchpoints identified
- Retain domain touchpoints identified
- Higher rewards implementation (pending verification of rate config)
- Premier support setup

**In Progress:**
- Design Pro UX
- Snooze (compliance approval)
- Physical card (marketing/design only — engineering done)
- Commercial value prop (partnerships)
- Marketing assets

**Not Started:**
- Free snooze feature build
- Partnerships integration
- T&Cs
- Partner offers in UX

### Jira Status (as of 2026-02-11, from [filter 20356](https://payzilch.atlassian.net/issues/?filter=20356))

**Summary:** 50 tickets tracked in the Pro filter.

| Status | Count |
|--------|-------|
| Done | 20 |
| Ready for Release | 5 |
| In QA | 1 |
| In PR | 1 |
| In Dev | 3 |
| Ready for Dev | 4 |
| Created (not started) | 13 |
| Rejected | 3 |

**By category:** To Do: 17 | In Progress: 5 | Done (incl. Ready for Release, Rejected): 28

**Key work streams:**
- **Product/subscription foundation** — largely complete (Tomasz Więckowski, Tomasz Michalski)
- **Tier migration (upgrade/downgrade)** — downgrade done; un-downgrade BE ([ZILCH-47599](https://payzilch.atlassian.net/browse/ZILCH-47599)) now In PR (Tomasz Więckowski), FE ([ZILCH-47613](https://payzilch.atlassian.net/browse/ZILCH-47613)) Ready for Dev
- **Mobile app UI** — Compare Plans in QA (Paweł), My Plans and structure still In Dev (Paweł)
- **Pro card design/issuing** — [ZILCH-46939](https://payzilch.atlassian.net/browse/ZILCH-46939) deprioritised to P3 Medium, still Created; [ZILCH-48046](https://payzilch.atlassian.net/browse/ZILCH-48046) (card designs UPDATE) also Created
- **Comms/marketing** — mostly done; cancellation email ([ZILCH-46331](https://payzilch.atlassian.net/browse/ZILCH-46331)) and subscription resumed email ([ZILCH-48086](https://payzilch.atlassian.net/browse/ZILCH-48086)) still not started
- **T&Cs** — [ZILCH-46803](https://payzilch.atlassian.net/browse/ZILCH-46803) still Created (not started)
- **Analytics/Mixpanel** — [ZILCH-47423](https://payzilch.atlassian.net/browse/ZILCH-47423) still Created
- **Subscription endpoint rework** — two new Created tickets: [ZILCH-48269](https://payzilch.atlassian.net/browse/ZILCH-48269) (split start/resume), [ZILCH-48263](https://payzilch.atlassian.net/browse/ZILCH-48263) (rework cancel endpoint)

**Merchant team involvement:**
- [ZILCH-47571](https://payzilch.atlassian.net/browse/ZILCH-47571) — Add product line taxonomy for Pro in ContentStack — **Ready for Release** (Ossie Nwokedi)
- [ZILCH-47687](https://payzilch.atlassian.net/browse/ZILCH-47687) — Add Zilch Pro to Rewards Earned on Purchases Page — **In Dev** (Ossie Nwokedi)

**Note:** [ZILCH-47117](https://payzilch.atlassian.net/browse/ZILCH-47117) (Zilch Pro Merchant UI Updates) is the Merchant team's epic — doesn't appear in the filter as it tracks PBIs, not epics.

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

### Jira Filter
[Zilch Pro — all tickets](https://payzilch.atlassian.net/issues/?filter=20356) — cross-team filter maintained by the project. More reliable than text search; includes infrastructure/plumbing tickets that don't mention "Pro" explicitly.

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

### 2026-02-11

**Pre-meeting Jira review** using [filter 20356](https://payzilch.atlassian.net/issues/?filter=20356).

**Movement since 5th Feb:**
- ZILCH-46362 (Compare Plans page): In PR → **in QA** (Paweł)
- ZILCH-47571 (ContentStack taxonomy): In Dev → **Ready for Release** (Ossie)
- ZILCH-47687 (Pro rewards label): Ready for Dev → **In Dev** (Ossie picked it up)
- ZILCH-47599 (BE un-downgrade): new, **In PR** today (Tomasz Więckowski)
- ZILCH-47871 (tier migration tech design): Ready for Testing → **Done**
- ZILCH-46622 (multiple card designs CREATE): Ready for Release → **Done**
- ZILCH-46939 (Pro card designs BE): priority dropped from P2 High to **P3 Medium**, still Created

**New tickets since last review:**
- ZILCH-48269 — Split subscription start endpoint into START and RESUME (Created)
- ZILCH-48263 — Rework subscription cancel endpoint (Created)
- ZILCH-48086 — Send email on subscription resume (Ready for Dev)
- ZILCH-48046 — Support multiple card designs UPDATE (Created)
- ZILCH-47999 — Clean up membership-specific feature availability logic (Created)

**Observations:**
- Only 5 tickets genuinely in progress; 17 still in To Do. The "in progress" work is concentrated in Retain (Paweł) and Merchant (Ossie).
- ZILCH-47117 (Merchant UI Updates) is the epic — doesn't appear as the filter tracks PBIs only.
- All 13 Created tickets and all 4 Ready for Dev tickets are unassigned.
- Pro card work has been deprioritised — aligns with potential pivot/reduced scope direction.

**Questions for Pro status meeting:**
1. What's the latest on the pivot decision?
2. Upgrade/downgrade status with Payments and Decisioning — still unclear from 5th Feb.
3. ZILCH-47524 (targeting service segment conflict) — who owns resolving this before rollout?
4. Release plan — what's the sequence for the 5 Ready for Release items?
5. ZILCH-46727 (only apply additional rewards for loans in continuous subscription) — Ready for Dev, unassigned, no Merchant backlog items. Chased Marcin and Tommy on 11 Feb.

**Pro status meeting notes:**

*Partnerships:*
- Still exploring options. Aligns well with the value prop. Customer survey going live soon.
- Luke Williams (Senior Sales & Partnerships Manager) shared current prospects: **Deliveroo**, **Tesco** (free grocery deliveries), and **Railcard** (reduced fare rail tickets). Also some retailers.

*Strategic / scope update (from Zac):*
- Original timelines now defunct. Some resource being moved off Pro onto other initiatives.
- **Scope reductions for MVP:** Free auto-snooze dropped. Physical card dropped.
- **New timeline:** MVP in Q2 (probably May), V1 in H2. Physical cards and auto-snooze would likely return in V1.
- Kieren: no huge movement on UK partnership designs yet.
- Mike Davis noted a couple of engineering dependencies — need to find out what they are.
- Tamara: her work has been descoped with the MVP scope change.

*My actions:*
- Coordinate with Zac and Ethan on rollout plan from a product perspective (A/B testing, cohorts, etc.).
- Once that's clear, coordinate with other EMs to understand the technical steps for rollout.
- Document the end-to-end release plan when the above is done.
