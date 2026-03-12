# Incident-467

## Status

Stable — fix deployed (comms for Zilch Plus rewards turned off). Root cause fix and re-enablement outstanding. Incident Commander: Mark Reddington.

## Summary

Customers received push notifications telling them they had earned rewards on loan completion, when in fact no rewards were awarded. Root cause: customers were not members for the full duration of the loan (`LOAN_INITIATED_BEFORE_SUBSCRIPTION_START`). `rewards-service` correctly skipped the reward, but the `onesignal-integration` lambda incorrectly triggered notifications for loan completion events where rewards were not applied.

First flagged by Boris Karaulov (ITAM team). Mike Davis requested Nick Holt and Jacek Zanko to create the incident. Fix deployed by Rory Fielding (Retain) on 27 Feb — messaging for Zilch Plus rewards turned off. Re-enablement in more accurate form still required.

**Process note:** Mark Reddington advised that future incidents should be raised directly in Datadog at the point of customer impact, not via the engineering-application-support Slack channel.

## Reference

No PIR link yet. Retrospective to be led by Merchant and Retain teams.

### Jira

[ZILCH-48940](https://payzilch.atlassian.net/browse/ZILCH-48940) — Rewards notification sent for loans created before membership start. Defect. Raised by Boris Karaulov. Unassigned; ownership sitting with Retain per Mark Reddington / Mike Davis.

## Actions

| Owner | Action | Status |
|---|---|---|
| Boris Karaulov (ITAM) | Confirm number of impacted customers; provide final list | Open |
| Murray Johnstone (Ops) | Coordinate explanatory comms to impacted customers | Open |
| Merchant / Retain | Conduct retrospective | Open |
| Retain (ZILCH-48940) | Root cause fix and re-enablement of rewards comms | Open |

## Digest

- Tom McKenzie tagged @Nicklas Chapman in the channel (09:57, 2 Mar) to add me to the incident channel.
- Andrzej Lorenz joined the incident channel.
