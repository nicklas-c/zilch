# CMP Steel Thread — campaign-service (Management Path)

**Supersedes:** ZILCH-55419 (ST3), ZILCH-55426 (ST5) — management-side scope only
**Absorbs:** ZILCH-57299 (iteration 2)

**Epic Owner** Stefan

## Context

The CMP steel thread proves an end-to-end path from campaign configuration through ad selection, creative delivery, and reporting. This epic covers the management path: the campaign-service, its relational data model, CRUD API, creative metadata, the placement registry, and write-through refresh to the DynamoDB execution store.

The management path is primarily defined by ST3 (Campaign Management) and ST5 (Inventory Management). ST5's placement registry is a table in campaign-service's database, seeded by migration and exposed read-only — it is a deliverable within this stream, not a separate workstream. This epic consolidates both.

campaign-service writes to the DynamoDB execution store on every management API call (write-through). It exposes audience definitions for audience-service to read. It has no runtime dependency on ad-service or the app. As long as the DynamoDB execution store shape (ST2) and the audience definition API (ST3 section 4.1) are agreed, this stream can proceed in parallel.

## Description

Build campaign-service and its supporting infrastructure:

- **campaign-service** — Spring Boot service on Zilch's standard platform, backed by its own Aurora PostgreSQL database (`campaign`).
- **Data model** — Campaigns, line items, creatives, creative assets, audiences, and placements. Singular table naming. Entity references (campaignRef, lineItemRef, creativeRef) per the Entity Reference ID ADR. Soft deletion throughout.
- **Placement registry** — `placement` table seeded by migration, not API-writable. Human-authored `placementRef` slugs. Accepted formats, nominal dimensions, slot count. `line_item.placement_id` as a foreign key enforcing that bookings reference issued placements.
- **Management CRUD API** — REST endpoints versioned `/v1/`:
  - Campaigns: POST/GET collection, GET/PATCH/DELETE by ref
  - Line items: POST/GET collection, GET/PATCH/DELETE by ref (placement resolved at POST)
  - Creatives: POST/GET collection, GET/PATCH/DELETE by ref
  - Creative assets: POST/GET/PATCH/DELETE under creative
  - Audiences: POST/GET collection, GET/PATCH/DELETE by ref
  - Attach/detach: creatives and audiences to line items
  - Validation: supported creative types, HTTPS destinations, required asset metadata, foreign key integrity
- **Audience definitions** — `audience` table with structured JSON rules. Read-only API for audience-service to consume.
- **Write-through to DynamoDB** — Every management write refreshes affected execution store entries in the ST2 shape. Creative metadata (CDN URL, dimensions, MIME type, destination) included in the execution store payload.
- **Operational tooling** — Postman collection against the management API.

## Contracts (interfaces with other streams)

| Contract | Defined by | This stream is |
|---|---|---|
| DynamoDB execution store shape | ST2 section 2 | Producer (writer) |
| Audience definition read API | ST3 section 4.1 | Producer |
| S3 key layout and CDN URL pattern | ST1 sections 3-4 | References (stores metadata, not bytes) |

## Out of Scope

- ad-service, gateway, selection logic (ad-service epic)
- Audience resolution, Snowflake queries, audience cache writes (audience-service epic)
- S3 bucket and CloudFront setup (ad-service epic owns the bytes)
- App component (App epic)
- Reporting pipeline (Reporting pipeline epic)
- Upload API, transcoding, creative review (post-steel-thread)
- Booking tool UI (prototype gap, not steel thread)
- Campaign validity rules, status lifecycle (prototype gap)

## Deliverables

- campaign-service with Aurora database
- Database schema (Liquibase migrations) including placement seed
- Entity reference generation
- Management API endpoints (all CRUD plus attach/detach)
- Audience definition table and read API
- Write-through refresh to DynamoDB execution store
- Postman collection

## Dependencies

- DynamoDB execution store table exists (provisioned by ad-service stream's Terraform, or coordinated)
- ST2 execution store shape agreed with ad-service stream
- ST5 placement content agreed (first placement: storefront placement)

## Open Points

- How placement attributes reach the execution store after a seeding migration, given write-through is triggered by API writes and placements have no write API. Needs resolving with the ad-service stream.
- Whether a line item should be bookable across several placements (currently exactly one).

## Success Criteria

- An authorised user can create, update, and soft-delete campaigns, line items, creatives, audiences, and attachments via the API.
- Management writes are reflected in the DynamoDB execution store without manual intervention.
- The placement registry rejects line items booked against unknown or inactive placements.
- The Postman collection exercises all endpoints.

## Design Documentation

- [ADR CMP ST3 - Campaign Management](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5890670646/ADR+CMP+ST3+-+Campaign+Management)
- [ADR CMP ST5 - Inventory Management](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5879660545/ADR+CMP+ST5+-+Inventory+Management)
- [ADR CMP ST2 - Ad Selection](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5863505941/ADR+CMP+ST2+-+Ad+Selection) (execution store shape)
- [CMP Steel Thread Architecture Overview](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5958598716/CMP+Steel+Thread+Architecture+Overview)
