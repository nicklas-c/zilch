# Incident-166

## Status

Closed. Date: 2024-07-19 (Friday). Incident Commander: Sean Hederman.

## Summary

A payment processing component lacked idempotency. A DevOps misconfiguration deployed it with a replica count of 6 instead of the intended 1. When the next billing run executed, approximately 35,575 customers with due payments were charged six times over.

The incident occurred on a Friday, meaning many customers had their bank accounts effectively emptied before the weekend. Zilch responded by issuing refunds and cancelling affected debt.

This is the worst incident in Zilch's history and is frequently referenced in engineering conversations. It shaped engineering practice and culture for months afterwards — in particular, the concept of "landmines": latent issues in the system that must be actively sought out and mitigated before they are inadvertently triggered.

## Reference

* [Incident 166 PIR (WIP)](https://payzilch.atlassian.net/wiki/spaces/PAYZ/pages/3842637825)
* [Operational Clean-Up Plan](https://payzilch.atlassian.net/wiki/spaces/ZO/pages/3843719818)

## Actions

* **Enhanced production sign-off process** introduced for all production changes. This has since been largely rolled back as confidence in systems has grown.
* **Personnel consequences**: a number of people lost their jobs as a result.
* **Engineering-wide audit**: all teams downed tools to conduct a root-and-branch audit of potential footguns, alerts, and monitors across their domains.
* The audit exercise is one that benefits from repeating as team ownership evolves. ZILCH-47400 captures the intent to revisit it for the Merchant team now that there is clearer understanding of what the team actually owns and what that means.

## Digest

**Known Financial Impact** (from Service Operations EOD updates, as of 22 July 2024):
* Compensation (goodwill gestures): £2,180
* Loan write-offs: £5,740.80
* Additional costs (refund processing, etc.) not fully captured here — see PIR

**Notes:**
* The "incident-166-j" label used in some Confluence pages refers to a subset identifier used during the operational clean-up.
* The PIR is marked [WIP] in Confluence — it may never have been completed.
