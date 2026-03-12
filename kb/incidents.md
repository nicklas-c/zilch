# Incidents

## Guidelines for AI
This is an index of incidents tracked in the knowledge base.  It contains brief reference information only — detailed records live in individual files under `./incidents/`.

### Fields

| Column | Optionality | Guidance |
|---|---|---|
| ID | Required | Incident identifier, matching the filename in `./incidents/` |
| Status | Required | Open, Stable, Resolved, Closed |
| Summary | Required | One-line description of the incident |

## Entries

| ID | Status | Summary |
|---|---|---|
| Incident-166 | Closed | Billing component lacked idempotency; misconfiguration caused ~35,575 customers to be charged six times |
| Incident-417 | Closed | Production incident; all actions complete |
| Incident-452 | Closed | Production incident; root cause fixed |
| Incident-467 | Stable | Customers received erroneous push notifications claiming they earned rewards; fix deployed but root cause fix and re-enablement outstanding |
