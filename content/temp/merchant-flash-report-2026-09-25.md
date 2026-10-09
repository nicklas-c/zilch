<u>Merchant</u>

*Sponsored Retailer Search / Brand Defence*
* A/B/C test final results published: +25% clicks, +11% more unlocks for sponsored retailers, no significant overall conversion impact. Treatment B (position 1) confirmed as winner.
* GABD title removal A/B test completed — no significant conversion impact, slight increase in sponsored CTR. Rolling out removal to all users.
* Category text on retailer search suggestions backend done.
* **In Progress**: Configure Brand Defence in Admin Portal — in PR.

*Storefront Placements*
* Hero Banner A/B test launched at 5%, then rolled out to 50:50.
* Experiment contamination identified: LD SDK not initialised at first evaluation fires a fallback value, then the real value moments later. Root cause confirmed; no rollback needed — analysis will use "if ever in treatment → treatment" rule.
* Storefront Takeover Placement done.

*Post-Purchase Offers*
* RewardsBag mobile integration done.
* **In Progress**: Display Post Purchase Offers in purchase and repayment receipts.
* **In Progress**: Suppress offers for repayments >14 days overdue.

*Intelligent Commerce*
* CJ Cancellations delayed sending done — delay infrastructure complete, race condition resolved.

*Rewards-Service Aurora Migration*
* Per-customer targeting toggle complete, enabling phased rollout via LaunchDarkly.
* AWS JDBC wrapper 4.x upgrade had to be redone due to Aurora/Liquibase startup failure in staging — fixed and ready for release.
* **Coming Soon**: Production migration execution.

*CMP (Commerce Media Platform)*
* **In Progress**: All five Steel Thread ADRs now raised or in progress: Content Delivery, Reporting, Inventory Management, Ad Selection, and Campaign Management.  
* Mike Ilin shared OpenRTB and IAB AdTech standards for the team to review ahead of implementation.

*Visa Flex Tech Debt*
* Sync Affiliated Retailer Status with Issuer Service done.
* **In Progress**: Full retailer sync endpoint.

*Market Expansion*
* CMS content readiness verification for non-UK markets complete.

*Affiliate Link Validation*
* Investigation into validation strategies completed.

*Ephemeral Environments*
* Mobile App Config Deeplink done.
