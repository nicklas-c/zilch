<u>Merchant</u>

*CMP (AdTech)*
* campaign-service skeleton created and ready for release. CMP reporting API gateway done.
* CMP prototype epic created — focus on getting ad-service functional with caches in place; campaign-service to follow.
* Campaign Management and Inventory Management ADRs in review — completing the Steel Thread ADR set.
* ad-reporting gateway deployed to prod.

*Brand Defence*
* Brand Defence admin UI deployed to prod. Verification via LaunchDarkly flag in progress.

*Sponsored Retailer Search*
* Retailer search suggestions component and enriched UI both in PR (Ossie, handed over before holiday).
* Semantic Search A/B test prep: profanity filter QA in prod, assessing whether IC retailer vectors need updating.

*Storefront / Search*
* Hero Banner test continuing — extending to more discretionary and discovery-inclined merchants.
* Keyboard test result: search GMV shifted from Search Results to Recent Searches. Recommendation: keep keyboard raised until Recent Searches supports monetisation.
* Existing carousel removed from Search Home (Ready for Release).

*Non-UK Market Expansion*
* Vendor integrations, backend services, and search capabilities all verified for non-UK readiness.

*KTLO*
* Lambda AWS SDK v3 upgrades completed (mixpanel integration, retailer image optimiser).
* gRPC-Go vulnerability fixed. jwt-authorizer lambda Datadog monitoring added.
* *In Progress*: Rokt SDK bump (bug fix requested by Rokt). Remove feeAmount from retailer SNS event. E2E test hardening and review.
