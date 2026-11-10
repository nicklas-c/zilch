<u>Merchant</u>

*Semantic Search*
- Positive experiment results: searches +5%, clicks and unlocks +1%, GMV +0.5%.
- 1-second timeout with lexical fallback brought into Sprint 15.2 as top priority. Unblocks 100% rollout.
- Stress test planned to inform Black Friday readiness decision.

*CMP (AdTech)*
- S3 reporting bucket and Firehose delivery stream completed.
- Campaign CRUD API and database schema in sign-off. Line-item CRUD API in dev. Front-end event contract in dev.
- Audience/targeting model agreed: attribute-based audiences, runtime computation as north star. Stefan and Mindaugas proposing solution with data team.

*Sponsored Search v2: Images*
- Campaign image override (FE) completed. Admin portal override, image cards in search results, E2E tests, and campaign migration all in PR — targeting 12 Nov code cut-off.
- Admin Portal Selenium tests for sponsored campaigns in dev.

*Sponsored Search v2: AdMarketplace*
- API investigation in PR.
- Final set of integration questions answered by AdMarketplace. Amr reviewing.

*Post Purchase Offers*
- Displaying offers on Upcoming Payments receipt in PR — targeting 12 Nov code cut-off.
- Agreed to use unit tests rather than Maestro for post-purchase testing (vendor environment limitations).

*Commercial*
- Paid Brand Defence live in production. Full-partnership-only restriction (IC v1.2) in testing.
- Hero Banner ramp held at 50% pending investigation of a visual defect.

*KTLO*
- Awin API key rotation caused affiliate import failures; resolved same day — 627 transactions reprocessed from DLQ.
- affiliate-integration-service dependency upgrade and Aurora Global Database fix completed and awaiting release.
- Retailer-image-optimiser lambda migrated to Node 24.
- Retailer Search Suggestions component and enriched UI completed — awaiting release.
- Merchant domain TypeScript error cleanup completed.
- **In Progress**: Android storefront carousel scrolling defect. Insecure local networking iOS fix in QA.
