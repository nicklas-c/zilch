<u>Merchant</u>

*Storefront Hero Placement*
* Done.

*Sponsored Retailer Search*
* Brand Defence suppression logic done pending review.

*Intelligent Commerce / Affiliate Integration*
* CJ recommending implementing a delay between refunds and orders to avoid potential race condition — pulled into Sprint 14.3.

*Post-Purchase Offers*
* *In Progress*: RewardsBag mobile integration.
* *In Progress*: Display Post Purchase Offers in Purchase Receipt.

*Rewards-Service Aurora Migration*
* DWH and Looker dependency investigations completed.
* Data sync between MSSQL and Aurora using AWS's Data Migration Service is up and running.
* *In Progress*: Switch-over planning, with a view to completion early next sprint.

*Visa Flex Tech Debt Pay Down*
* *In Progress*: Sync Affiliated Retailer Status with Issuer Service - earlier blocker resoved: design approach agreed with Issuer.

*AdTech / CMP*
* Architecture discussions continuing.

*KTLO*
* Dynamic-group endpoint latency fix — identified ForkJoinPool contention causing 5–30s outliers, switched to virtual-thread executor. Ready for sign-off.
* Pact mock server RAM increased for more stable maestro test execution.

*Vilnius Recruitment*
* Reviewed 2 additional CVs - Passed both.
* 1 interview scheduled for today.

*Issues*
* Difficulties getting accurate information on SDK usage (ROKT and RewardsBag) has added friction to the Post-Purchase Offers feature.