# CMP Steel Thread — App (Mobile Placement)

**Extracted from:** ZILCH-55414 (ST1, app rendering), ZILCH-55422 (ST4, front-end events)

**Epic Owner** Ossie

## Context

The CMP steel thread proves an end-to-end path from campaign configuration through ad selection, creative delivery, and reporting. This epic covers the mobile app work: the placement component, the ad-decision request, creative rendering, impression event emission, tap-through with click-redirect fallback, and feature-flagged rollout.

App work was previously split across ST1 (Content Delivery, section 5: app rendering) and ST4 (Reporting, section 2.2: front-end events). In practice this is one stream of work for a mobile engineer: build the placement component, wire it to the ad-service API, render creatives from CDN, emit events to the reporting gateway, and handle interaction. This epic consolidates it.

The app depends on the `POST /v1/ad-decisions` response contract (ST1) and the front-end event schema (ST4). As long as those contracts are agreed, development can proceed against mocked or stubbed responses in parallel with the backend streams.

## Description

Build the CMP placement component in the Zilch app:

- **Placement component** — Renders a single ad placement. Calls `POST /v1/ad-decisions` with `placementRef` and `appContext` when the placement becomes visible. One request per placement load; not repeated for ordinary view re-renders.
- **Request** — Sends `placementRef` and `appContext` (screen, theme, pixelDensity, deviceType) in the body. `customerRef` is in the JWT, not the body. Standard `User-Agent` header carries app version, locale, OS, and device model.
- **Rendering** — On `200 OK`, downloads the creative asset from the CDN URL in the response. Preserves aspect ratio. Supports `rendering.type = image` for the steel thread.
- **States** — Loading, error, empty (`204 No Content`), and rendered states.
- **Tap-through** — Opens the click redirect URL from the ad response. Falls back to the destination URL directly if the redirect fails (losing the click record rather than the user journey).
- **Impression event** — Emits an impression event to the reporting gateway (`POST /v1/events`) when the creative begins rendering. Includes `decisionId` from the ad response as the correlation key. Includes `clientEventId` for deduplication, viewability fields where measurable.
- **Feature-flagged rollout** — Controlled by LaunchDarkly flag(s). Staff users first.
- **No inference** — The component must not infer campaign or eligibility rules from the creative URL or response structure.

## Contracts (interfaces with other streams)

| Contract | Defined by | This stream is |
|---|---|---|
| `POST /v1/ad-decisions` request/response | ST1 section 2 | Consumer |
| Front-end event schema | ST4 section 2.2 | Producer |
| Click redirect contract | ST4 section 5 | Consumer (opens redirect URL) |
| S3 key layout and CDN URL pattern | ST1 sections 3-4 | Consumer (downloads assets) |

## Out of Scope

- ad-service, gateway, selection logic (ad-service epic)
- campaign-service, management API (campaign-service epic)
- audience-service (audience-service epic)
- Firehose, S3, Fivetran, Snowflake, dbt, Looker (Reporting pipeline epic)
- Multi-slot placements, video, native rendering (post-steel-thread)
- Viewability measurement to IAB threshold (open point — if the app cannot measure to 50%-for-one-second, `viewabilityMeasured` is `false`)

## Deliverables

- Placement component with loading, error, empty, and rendered states
- Ad-decision request integration
- Creative rendering from CDN
- Impression event emission to reporting gateway
- Tap-through with click-redirect fallback
- LaunchDarkly feature flag integration

## Dependencies

- `POST /v1/ad-decisions` response contract agreed with ad-service stream
- Front-end event schema agreed with reporting pipeline stream
- Reporting gateway exists and is reachable (noted as already deployed in ZILCH-57295)
- CDN URL pattern agreed

## Open Points

- Whether the app can measure viewability to the IAB 50%-for-one-second threshold, and how accurately.
- Whether events are batched or sent individually — if batched, the reporting gateway mapping template becomes more complex.
- The permitted value set for `deviceType` in `appContext`, to be agreed with the reporting stream so reporting dimensions are consistent.

## Success Criteria

- The placement component renders an ad served by the CMP ad-service, with assets loaded from CloudFront.
- No-fill (`204`) displays the empty state without error.
- Tap-through navigates to the destination via the click redirect, falling back to the destination directly on failure.
- Impression events land at the reporting gateway with a valid `decisionId` correlation key.
- The component is gated behind a LaunchDarkly flag and visible to staff users only.

## Design Documentation

- [ADR CMP ST1 - Content Delivery](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5853053070/ADR+CMP+ST1+-+Content+Delivery) (section 5: App rendering)
- [ADR CMP ST4 - Reporting](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5862227995/ADR+CMP+ST4+-+Reporting+-) (section 2.2: Front-end events)
- [CMP Steel Thread Architecture Overview](https://payzilch.atlassian.net/wiki/spaces/ZARCH/pages/5958598716/CMP+Steel+Thread+Architecture+Overview)
