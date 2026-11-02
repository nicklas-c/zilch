# CMP Steel Thread — audience-service (Audience Resolution)

**Extracted from:** ZILCH-55419 (ST3) — audience resolution scope (ST3 section 4)

**Epic Owner** Mindaugas

## Context

The CMP steel thread proves an end-to-end path from campaign configuration through ad selection, creative delivery, and reporting. This epic covers audience resolution: a separate service that reads audience definitions from campaign-service, queries Snowflake for matching customers, and writes memberships to the DynamoDB audience cache.

Audience resolution was originally a subsection of the ST3 (Campaign Management) ADR, and the existing ST3 epic includes it. However, audience-service is a distinct Spring Boot service with its own deployment, its own external dependency (Snowflake), and a hard dependency on campaign-service's audience definition API. Extracting it into its own epic makes the dependency explicit and allows it to be tracked and staffed independently.

This is the one stream with a hard runtime dependency on another: audience-service needs campaign-service's audience definition read API to exist, not just be agreed. It can be developed against a stub, but cannot integrate without it.

## Description

Build audience-service and its refresh pipeline:

- **audience-service** — Spring Boot service on Zilch's standard platform. Separate from campaign-service.
- **Read audience definitions** — Reads active audience definitions and their structured JSON rules from campaign-service's read-only API.
- **Query Snowflake** — Translates audience rules into parameterised Snowflake queries using supported fields and operators. Maps CDP identifiers to `customerRef` where necessary.
- **Update audience cache** — Groups results by customer and writes to the DynamoDB audience cache in the ST2 shape: `PK: customerRef`, `value: audienceRefs` (string set).
- **Safe refresh** — Builds the complete result before applying changes. A failed Snowflake query preserves the previous valid memberships rather than removing them. Each successful refresh removes customers who no longer match and references to inactive audiences.
- **Scheduling** — Periodic execution. Refresh frequency is an implementation decision. The mechanism for applying a complete refresh safely (full replace vs incremental) is an implementation decision.
- **Observability** — Refresh duration, success/failure, membership counts, time of last successful refresh.

## Contracts (interfaces with other streams)

| Contract | Defined by | This stream is |
|---|---|---|
| DynamoDB audience cache shape | ST2 section 1 | Producer (writer) |
| Audience definition read API | ST3 section 4.1 | Consumer (reader) |

## Out of Scope

- Audience definition CRUD, rules schema, validation (campaign-service epic)
- ad-service, selection logic, DynamoDB execution store (ad-service epic)
- App component (App epic)
- Reporting (Reporting pipeline epic)
- Real-time audience refresh triggered by definition changes (polling is the only option; customer attributes drift independently)

## Deliverables

- audience-service with scheduled refresh job
- Snowflake query engine (parameterised queries from audience rules)
- DynamoDB audience cache writer
- Safe refresh logic (build-before-apply)
- Observability: refresh metrics and last-success timestamp

## Dependencies

- **Hard dependency:** campaign-service audience definition read API must exist for integration (can stub for development)
- DynamoDB audience cache table exists
- Snowflake access and customer data availability
- Confirmation of whether the CDP keys customers by `customerRef` — if not, a mapping step is needed

## Success Criteria

- audience-service reads active audience definitions from campaign-service and resolves them against Snowflake.
- The DynamoDB audience cache reflects current memberships after a successful refresh.
- A failed Snowflake query does not corrupt existing valid memberships.
- Refresh metrics are available for operational monitoring.

## Design Documentation

- [ADR CMP ST3 - Campaign Management](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5890670646/ADR+CMP+ST3+-+Campaign+Management) (section 4: Audience resolution and refresh)
- [ADR CMP ST2 - Ad Selection](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5863505941/ADR+CMP+ST2+-+Ad+Selection) (audience cache shape)
- [CMP Steel Thread Architecture Overview](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5958598716/CMP+Steel+Thread+Architecture+Overview)
