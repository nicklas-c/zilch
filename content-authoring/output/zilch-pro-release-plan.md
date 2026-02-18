# Zilch Pro — Release Plan

**Audience:** Technical; cross-team contributors and stakeholders involved in Pro delivery.

## Purpose

This page is a collaborative space for gathering knowledge about what needs to happen to release Zilch Pro. It is **not** a runbook — it will be used as source material to create run books in the form of EC tickets.

**How to contribute:** Add what you know under the relevant sections. If something is missing or wrong, update it. If you're unsure where something belongs, add it to Open Questions.

## Context

Zilch Pro is the next tier of Zilch's paid membership proposition, sitting above Plus at £7.99/month. It offers higher rewards rates, free snoozes, partnership perks, and premier support.

**Key constraint:** Customer availability of Pro is gated on the delivery of one or more partnership deals. Partnerships are the bottleneck — all other features are expected to be ready before then. The strategy is therefore to **release features independently as they become ready**, but to make them unavailable either through feature configuration in `product-service` or LaunchDarkly feature switches.  When partnerships land, turn-on should be trivial and safe.

**Key links:**
* Initiative: [ZILCH-45705](https://payzilch.atlassian.net/browse/ZILCH-45705)
* Product overview: [Zilch Pro Product Overview](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4566122730/Zilch+Pro+Product+Overview)
* Experimentation Plan: [Zilch Pro Experimentation Plan](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/4949016869/Zilch+Pro+Experimentation+Plan)

## Roll-out Plan Summary

The following has been agreed in principle:

* **Internal testing:** Two weeks of internal/staff testing before any customer exposure.
    * Requires clarification/confirmation - this may be overkill given ability to release and test features independently.  @Nikos Sofianos
* **Initial cohort:** 1% of eligible customers for one week.
    * Ditto @Nikos Sofianos
* **Experimentation:** 4–6 week experimentation window post-initial-cohort. @Zac Barclay @Ethan Stockwell
* **BAU:** General availability, with a hold-out group maintained for 6 months.  @Zac Barclay @Ethan Stockwell

## Release by Feature

Each feature should be independently releasable. Release features as they become ready; customer-facing availability is gated on partnerships.

### Core Functionality

| Feature | Notes | Release Steps | EC Ticket |
|---|---|---|---|
| Plan selection | Customers can view and select Pro as a subscription product | | |
| Checkout | Customers can set up recurring payment for the Pro fee | | |
| Billing | Monthly payment collection from Pro subscribers | | |
| Subscription management | Customers can upgrade or downgrade between plans | | |
| Subscription configuration | Internal tooling to add/remove products, set prices, configure feature levels | | |
| Customer service tooling | CS can view a customer's plan and related details | | |

### Rewards

| Feature | Notes | Release Steps | EC Ticket |
|---|---|---|---|
| Higher rewards rate (pay now) | Min. 4% rewards when unlocking and paying now | | |
| Rewards rate (pay over time, unlocked) | 1% rewards when unlocking and paying over time | | |
| Rewards rate (pay over time, not unlocked) | 0.25% rewards when paying over time without unlocking | | |

### Smart Repayment

| Feature | Notes | Release Steps | EC Ticket |
|---|---|---|---|
| ~~Free snoozes~~ | ~~3 free payment snoozes per month for Pro subscribers~~ Currently descoped | | |

### Partnership Perks

| Feature | Notes | Release Steps | EC Ticket |
|---|---|---|---|
| Tastecard membership | Tastecard included with Pro subscription. Dependent on partnership deal. | | |
| Category perks | Perks across key spend categories (supermarkets, travel, food delivery, electronics). Dependent on partnership deals; specifics TBC. | | |

### Everyday Benefits

| Feature | Notes | Release Steps | EC Ticket |
|---|---|---|---|
| ~~Physical Pro card~~ | ~~Free physical card for Pro subscribers~~ Currently descoped | | |
| 24/7 premier support | Upgraded customer service tier | | |


## Post-Release

*(Contributors: add monitoring, experimentation ramp-up steps, known follow-ups, etc.)*

## Open Questions & Dependencies

*(Contributors: add any concerns, unknowns, or dependencies here.)*
