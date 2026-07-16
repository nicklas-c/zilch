# Suppress sponsored search result when the top result is an Intelligent Commerce retailer

**Parent Epic:** ZILCH-53063

**Owned By:** Product Initiative

**Labels:** `backend`

---

## User Story

As a **retailer enrolled in Intelligent Commerce**, I want **my brand to be protected from sponsored competitor results when a customer searches for me by name**, so that **competitors cannot hijack my brand's traffic through paid sponsorship**.

---

## Background

### Intelligent Commerce

"Intelligent Commerce" (also referred to as "Card Tracking") is Zilch's capability for telling retailers or retailer networks when a sale originated from a Zilch customer. When a customer uses the Zilch app — searching for a retailer, responding to an ad, and following the unlock journey to arrive at the retailer — we can track that journey. For retailers or networks who have subscribed to this capability, we send that attribution data to them via APIs they expose, and they use it as the basis for referral fees.

A retailer is considered an "Intelligent Commerce retailer" if they have a live card tracking contract in Admin Portal (regardless of transaction type — including in-store only).

### Sponsored Retailer Search

Sponsored Retailer Search v1 (ZILCH-51721) allows merchants to pay for a sponsored position in retailer search results, at a category level.

How it works:

- Retailers have a many-to-many relationship with categories, but each retailer has a **primary category** — this is the category used to resolve which sponsored result to show.
- Categories have a many-to-many relationship with sponsors. When a search result's primary category has multiple sponsors, one is selected at random to achieve even distribution.
- The customer sees a sponsored retailer result alongside (or above) the organic search results.

### Brand Defence

Brand Defence is the defensive counterpart to sponsored search. It protects IC retailers from competitors appearing as sponsored results when a customer is clearly searching for them by name.

The logic: if the result at **rank 1** in the OpenSearch response (the closest lexical match, before any sponsored result is injected) is an IC retailer, the sponsored result is suppressed entirely. The customer searched for that brand; showing a competitor above it undermines the IC value proposition.

Enrolment is automatic — any live IC retailer is protected. No campaign configuration is required. The feature sits behind a LaunchDarkly flag (`sponsored-search-brand-defence`) until the agreed go-live date. No A/B test is required.

---

## Acceptance Criteria

### AC1 — Sponsored result suppressed for IC retailer

```
Given I am logged in as a fully-onboarded user
And retailer [Retailer A] is an Intelligent Commerce retailer
And [Retailer A] has primary category [Category A]
And [Retailer B] has sponsored category [Category A]
And the feature flag "sponsored-search-brand-defence" is serving TRUE
And I have navigated to the Search screen
When I enter the search term "[Retailer A]"
Then search results do not include a sponsored retailer
```

### AC2 — Non-IC retailers unaffected

```
Given I am logged in as a fully-onboarded user
And retailer [Retailer A] is not an Intelligent Commerce retailer
And [Retailer A] has primary category [Category A]
And [Retailer B] has sponsored category [Category A]
And the feature flag "sponsored-search-brand-defence" is serving TRUE
And I have navigated to the Search screen
When I enter the search term "[Retailer A]"
Then search results include [Retailer B] as a sponsored retailer
```

### AC3 — Analytics: suppressed sponsored retailer captured

```
Given I am logged in as a fully-onboarded user
And retailer [Retailer A] is an Intelligent Commerce retailer
And [Retailer A] has primary category [Category A]
And [Retailer B] has sponsored category [Category A]
And the feature flag "sponsored-search-brand-defence" is serving TRUE
And I have navigated to the Search screen
When I enter the search term "[Retailer A]"
Then the search_analytics event field "sponsored_retailer" contains [Retailer B]
And the search_analytics event field "sponsored_suppressed_by_brand_defence" is TRUE
```

### AC4 — Analytics: no suppression fields when no sponsored candidate exists

```
Given I am logged in as a fully-onboarded user
And retailer [Retailer A] is an Intelligent Commerce retailer
And [Retailer A] has primary category [Category A]
And no retailer has sponsored category [Category A]
And the feature flag "sponsored-search-brand-defence" is serving TRUE
And I have navigated to the Search screen
When I enter the search term "[Retailer A]"
Then the search_analytics event field "sponsored_retailer" is not populated
And the search_analytics event field "sponsored_suppressed_by_brand_defence" is not populated
```

### AC5 — Feature flag off: no behaviour change

```
Given I am logged in as a fully-onboarded user
And retailer [Retailer A] is an Intelligent Commerce retailer
And [Retailer A] has primary category [Category A]
And [Retailer B] has sponsored category [Category A]
And the feature flag "sponsored-search-brand-defence" is serving FALSE
And I have navigated to the Search screen
When I enter the search term "[Retailer A]"
Then search results include [Retailer B] as a sponsored retailer
And the search_analytics event field "sponsored_suppressed_by_brand_defence" is not populated
```

---

## Test Strategy

TBC

---

## Implementation Notes

### OpenSearch indexing

IC status is a first-class field on the retailer data entity but is not currently in the OpenSearch retailer document. It needs adding to the index mapping as a boolean field `is_intelligent_commerce`, so it's available at query time without an additional service/DB call.

- **Indexing mechanism:** `[placeholder — how does retailer data sync to OpenSearch?]`
- **Index mapping definition:** `[placeholder — repo/path]`
- **IC status field name on source entity:** `[placeholder]`
- A reindex of existing retailers will be needed to backfill.

### Suppression logic

- **Search service repo:** `[placeholder]`
- **Where sponsored result is currently injected:** `[placeholder — class/module]`
- Logic: after retrieving lexical results, check the `is_intelligent_commerce` field on the rank-1 result (the top hit before sponsored injection). If `true` and the flag `sponsored-search-brand-defence` is enabled, omit the sponsored result from the response. Retain the sponsored candidate in memory for analytics.
- If no sponsored candidate exists for the top result's primary category, the suppression logic is not exercised and no brand-defence analytics fields are populated.

### Analytics

- **Event emitter:** `[placeholder — where is search_analytics published from?]`
- **Existing schema:** `[placeholder — link or location]`

New/modified fields on the `search_analytics` event:

| Field | Type | Populated when |
|---|---|---|
| `sponsored_retailer` | string (retailer ID) | A sponsored candidate exists — whether shown or suppressed |
| `sponsored_suppressed_by_brand_defence` | boolean | A sponsored candidate was suppressed due to brand defence (`true`). Not populated when no suppression occurred. |

Open question: does `sponsored_retailer` already exist in the event for the non-suppressed case? If so, the only new field is `sponsored_suppressed_by_brand_defence`.

### Feature flag

- **Flag name:** `sponsored-search-brand-defence`
- **Type:** Boolean
- **Evaluation point:** `[placeholder — where in the code path should the flag be checked?]`
- **Default (off):** Sponsored results behave as today. No suppression, no `sponsored_suppressed_by_brand_defence` field in analytics.

---

## Getting Started

_For engineers new to this area of the codebase:_

- `[placeholder — how to run the search service locally]`
- `[placeholder — how to query OpenSearch in dev and observe the retailer document]`
- `[placeholder — how to trigger a search with a sponsored result in dev]`
- `[placeholder — how to observe search_analytics events (tooling, topic, consumer)]`

---

## Out of Scope

- Bidding mechanics between brand defence and competitor conquesting (future iteration)
- Allowing non-IC brands to pay for brand defence (future iteration)
- Any Admin Portal changes — IC merchants are automatically enrolled
- Frontend changes — suppression is entirely backend; the client simply receives no sponsored result

---

## Open Questions (for refinement)

1. How does retailer data sync into OpenSearch — safe to add a field and reindex, or does it need coordinating?
2. Where is the sponsored result injected — same service, or call to a separate sponsorship service?
3. Does `sponsored_retailer` already exist in the `search_analytics` event for the non-suppressed case?
4. Edge cases around IC status transitions (merchant goes live/stops mid-day) — is eventual consistency via the OpenSearch sync acceptable?
