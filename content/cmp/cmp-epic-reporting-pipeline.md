# CMP Steel Thread — Reporting Pipeline (Ingestion and Modelling)

**Supersedes:** ZILCH-55422 (ST4) — ingestion and pipeline scope only
**Absorbs:** ZILCH-57295 (Steel thread - Reporting)

**Epic Owner** Reeya

## Context

The CMP steel thread proves an end-to-end path from campaign configuration through ad selection, creative delivery, and reporting. This epic covers the reporting pipeline: Firehose delivery streams, S3 landing zone, Fivetran connector, Snowflake loading, dbt models, and the end-to-end verification that events from both producers are joinable.

ST4 (Reporting) defines both the event schemas and the ingestion pipeline. Event *emission* — ad-service writing decision events to Firehose, the app posting impression events to the reporting gateway — is the responsibility of the ad-service and App streams respectively. This epic owns everything from Firehose onwards, plus the event schema contracts that the producers implement.

This stream has a cross-team dependency: the Fivetran connection is set up by Core Data, and the dbt models are maintained by a Product Analyst. CMP owns the event contract; it does not own the numbers derived from it.

## Description

Stand up the reporting pipeline:

- **Event schema contracts** — Finalise the decision event schema (ST4 section 2.1) and front-end event schema (ST4 section 2.2). Resolve open points: `reasonCode` vocabulary, identifier data types, `position` field semantics.
- **Firehose delivery streams** — One stream per event type. Gzipped NDJSON to S3 with one prefix per event type. Both producers must append a newline to every record.
- **S3 landing zone** — Raw, append-only event storage. Retained as the reprocessable source of truth.
- **Reporting gateway event contract** — `POST /v1/events` request model on the existing reporting gateway. Validates payload shape. Stamps `receivedAt` at the ingestion boundary. Writes to Firehose via native service integration (no compute).
- **Fivetran to Snowflake** — S3 connector loading gzipped JSON into Snowflake. New fields added as columns automatically. Coordinate setup with Core Data.
- **dbt models** — Join decision and front-end events on `decisionId`. Deduplicate on `clientEventId` (earliest record per logical event). Data-quality tests. Maintained by a Product Analyst; CMP provides the schema contract and test data.
- **End-to-end verification** — One render (decision + impression + click) joinable and queryable in Snowflake through the dbt models.

## Contracts (interfaces with other streams)

| Contract | Defined by | This stream is |
|---|---|---|
| Decision event schema | ST4 section 2.1 | Owner (defines the contract) |
| Front-end event schema | ST4 section 2.2 | Owner (defines the contract) |
| Click event (subset of decision events) | ST4 section 5 | Owner (defines the contract) |

## Out of Scope

- Decision event emission from ad-service (ad-service epic)
- Front-end event emission from the app (App epic)
- Reporting gateway deployment and authoriser (already exists)
- dbt model ownership long-term (Core Data / analytics)
- Looker dashboards (MVP depth, owned by analytics)
- Real-time reporting (deliberately deferred)
- GIVT/SIVT filtration (open commercial question)
- IAB certification (open commercial question)
- Athena as a reporting path (debugging tool, not the reporting path)

## Deliverables

- Finalised event schemas (decision, front-end, click)
- Firehose delivery streams with S3 destination
- S3 bucket configuration (prefixes, lifecycle)
- Reporting gateway event contract (`POST /v1/events` request model)
- Fivetran S3 connector to Snowflake (coordinated with Core Data)
- dbt models: join, deduplication, quality tests (coordinated with Product Analyst)
- End-to-end verification: one correlated render queryable in Snowflake

## Dependencies

- **Cross-team:** Core Data for Fivetran connector setup and Snowflake landing
- **Cross-team:** Product Analyst for dbt model authoring
- Reporting gateway and authoriser already deployed
- ad-service and App streams implementing their respective event emission
- ST3 opaque refs and ST5 `placementRef` for event schema fields

## Open Points

- `reasonCode` vocabulary: the closed list of values permitted per outcome.
- Identifier data types for `decisionId`, `requestId`, `viewId` — to be agreed with the ad-service stream.
- Whether `customerRef` on the decision event is required for reporting or whether audience-level granularity is sufficient (PII scope implication).
- Fivetran MAR accounting: confirm the S3 connector counts rows append-only rather than per sync.
- Expected end-to-end lag (Firehose buffer + Fivetran sync + dbt run).
- Click deduplication window and URL signing/expiry parameters.
- Whether the app batches events or sends them individually.

## Success Criteria

- Decision, impression, and click events from both producers land in S3 via Firehose as gzipped NDJSON.
- Events are loaded into Snowflake via Fivetran.
- dbt models join decision and front-end events on `decisionId` and deduplicate on `clientEventId`.
- At least one end-to-end render (decision + impression + click) is queryable and correlated in Snowflake.

## Design Documentation

- [ADR CMP ST4 - Reporting](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5862227995/ADR+CMP+ST4+-+Reporting+-)
- [ADR CMP ST1 - Content Delivery](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5853053070/ADR+CMP+ST1+-+Content+Delivery) (response contract, `appContext`)
- [CMP Steel Thread Architecture Overview](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5958598716/CMP+Steel+Thread+Architecture+Overview)
