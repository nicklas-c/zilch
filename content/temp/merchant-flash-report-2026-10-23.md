<u>Merchant</u>

*CMP (AdTech)*
* Complete Steel Thread ADR consolidated and shared with Abhishek for review. Campaign Management ADR completed; Inventory Management ADR at Ready for Testing — completing the full set.
* **In Progress**: CMP prototype build — ad-decisions endpoint, serving ads from DynamoDB campaign-cache in dev, creative storage (S3 + CloudFront).

*Sponsored Search*
* Semantic Search A/B test launched to 50% of users. Latency increased from ~150ms to ~700ms (Bedrock vectorisation). Keeping at 50% — p95 under 1s currently acceptable to Product for the experiment. Optimisations identified: caching Bedrock embedding responses and building a hybrid OpenSearch index.
* Profanity filter extended to suppress GABD results.
* **In Progress**: Retailer search suggestions component and enriched UI in PR — UI feedback being addressed.

*Sponsored Search v2: Images*
* **In Progress**: Sponsored image and headline in retailer-service. Admin-service and campaign image override both in dev.

*KTLO*
* E2E test review completed. Remove feeAmount from retailer SNS event at Ready for Release. Rokt SDK update.
* **In Progress**: E2E test hardening continues.
* **In Progress**: Android storefront carousel scrolling defect.
