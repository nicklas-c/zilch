# CMP Steel Thread — ad-service (Serving Path)

**Supersedes:** ZILCH-55414 (ST1), ZILCH-55415 (ST2) — serving-side scope only
**Absorbs:** ZILCH-56959 (iteration 1)

**Epic Owner** Jacek

## Context

The CMP steel thread proves an end-to-end path from campaign configuration through ad selection, creative delivery, and reporting. This epic covers the serving path: the stateless ad-service, its public gateway, creative storage and CDN delivery, and the click redirect endpoint.

The serving path is defined across three ADRs — ST1 (Content Delivery), ST2 (Ad Selection), and ST4 (Reporting, click capture only). The original epics split this work by functional phase (random selection first, then audience-aware selection). This epic recuts it by subsystem: everything ad-service owns, delivered as one stream against agreed contracts.

ad-service reads from DynamoDB and writes to Firehose. It has no synchronous dependency on campaign-service or audience-service at request time. As long as the DynamoDB table shapes (ST2) and event schemas (ST4) are agreed, this stream can proceed in parallel with all others.

## Description

Build the ad-service and its supporting infrastructure:

- **ad-service** — Spring Boot service on Zilch's standard platform. Reads the DynamoDB execution store and audience cache in parallel, retains eligible line items by audience match, selects randomly, and returns the ST1 decision response.
- **ad-public-api gateway** — Dedicated public API Gateway reusing the existing authorisation Lambda. Authenticates requests, extracts `customerRef` from the JWT, and forwards to ad-service as `X-Customer-Ref`.
- **Decision endpoint** — `POST /v1/ad-decisions` accepting `placementRef` and `appContext`. Returns creative payload or `204 No Content` for no-fill. Logs no-fill reason codes (`no_line_items`, `no_audience_match`, `dependency_error`).
- **Creative storage and CDN** — Private S3 bucket (SSE-S3, OAC) with CloudFront distribution. Immutable content-hashed keys. Long-lived cache headers.
- **Click redirect** — `GET /v1/click?d={decisionId}` on the ad-service behind the same gateway. Records the click to Firehose, returns 302 to the destination. Signed, time-limited URLs.
- **Event emission** — Decision events and click events emitted to Firehose via `PutRecord`. Schema per ST4 decision event contract.
- **Observability** — Structured logs and metrics: request count, latency, 4xx/5xx, no-fill rate, decision/creative identifiers. Must evidence the 200ms end-to-end RTT target.

The endpoint ships first with a hardcoded response so the contract can be exercised end-to-end early. DynamoDB reads and selection logic follow once tables are seeded (manually first, then by campaign-service).

## Contracts (interfaces with other streams)

| Contract | Defined by | This stream is |
|---|---|---|
| DynamoDB execution store shape | ST2 section 2 | Consumer (reader) |
| DynamoDB audience cache shape | ST2 section 1 | Consumer (reader) |
| `POST /v1/ad-decisions` request/response | ST1 section 2 | Producer |
| Decision event schema | ST4 section 2.1 | Producer |
| Click redirect contract | ST4 section 5 | Producer |
| S3 key layout and CDN URL pattern | ST1 sections 3-4 | Producer |

## Out of Scope

- Campaign hierarchy, data model, management API (campaign-service epic)
- Audience resolution and Snowflake queries (audience-service epic)
- App placement component, impression events, feature-flagged rollout (App epic)
- Firehose-to-Looker pipeline, dbt models, dashboards (Reporting pipeline epic)
- Frequency capping, advanced selection, multi-slot responses (post-steel-thread)

## Deliverables

- ad-service with selection logic and click redirect
- ad-public-api gateway with authorisation
- S3 bucket, CloudFront distribution, OAC configuration
- DynamoDB table creation (execution store and audience cache — tables owned by this stream's Terraform, written by other streams)
- Firehose delivery stream (shared with reporting pipeline)
- Decision event emission
- Observability: dashboard or queries demonstrating RTT and error rates

## Dependencies

- DynamoDB table shapes agreed with campaign-service and audience-service streams
- Event schema agreed with reporting pipeline stream
- campaign-service Terraform workspace exists (for table provisioning coordination)

## Success Criteria

- The ad-service returns a creative for an eligible customer and `204 No Content` for an ineligible one, reading from DynamoDB.
- Creative assets are served from CloudFront with correct cache behaviour.
- Click redirect records the click and returns 302 to the destination.
- Decision events land in Firehose with the agreed schema.
- End-to-end decision RTT is within the 200ms target under realistic conditions.

## Design Documentation

- [ADR CMP ST1 - Content Delivery](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5853053070/ADR+CMP+ST1+-+Content+Delivery)
- [ADR CMP ST2 - Ad Selection](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5863505941/ADR+CMP+ST2+-+Ad+Selection)
- [ADR CMP ST4 - Reporting](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5862227995/ADR+CMP+ST4+-+Reporting+-) (click capture, section 5)
- [CMP Steel Thread Architecture Overview](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5958598716/CMP+Steel+Thread+Architecture+Overview)
