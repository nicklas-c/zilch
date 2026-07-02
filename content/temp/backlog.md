# Merchant Backlog — Tickets by Service

Tickets from the Merchant PBIs backlog (statusCategory = "To Do") that relate to fee-service, rewards-service, or offer-service. These are the tickets that may need to move with the services.

## fee-service

| Ticket | Summary |
|---|---|
| [ZILCH-52920](https://payzilch.atlassian.net/browse/ZILCH-52920) | fee-service snooze schedules missing in dev environments — determine ownership and automate bootstrap |
| [ZILCH-52678](https://payzilch.atlassian.net/browse/ZILCH-52678) | Support unequal fee splits across multiple repayments |
| [ZILCH-52407](https://payzilch.atlassian.net/browse/ZILCH-52407) | fee-service - Reduce log volume & optimise retention |
| [ZILCH-51033](https://payzilch.atlassian.net/browse/ZILCH-51033) | Display Fees and Unlocks on a Transaction Level in Customer 360 (to be refined) |
| [ZILCH-50127](https://payzilch.atlassian.net/browse/ZILCH-50127) | Centralize Fee Configuration in E2E Tests to Eliminate Hardcoded Values |
| [ZILCH-50073](https://payzilch.atlassian.net/browse/ZILCH-50073) | Investigate 0.00 fee timeouts appearing in pre-prod environments |
| [ZILCH-50042](https://payzilch.atlassian.net/browse/ZILCH-50042) | Remove unused fee fields from ProductLoanFees and related logic |
| [ZILCH-49802](https://payzilch.atlassian.net/browse/ZILCH-49802) | Improve saving functionality when calculating fees |
| [ZILCH-49634](https://payzilch.atlassian.net/browse/ZILCH-49634) | Upgrade fee-service to Java 25 |
| [ZILCH-49122](https://payzilch.atlassian.net/browse/ZILCH-49122) | Review fee-service monitors |
| [ZILCH-49117](https://payzilch.atlassian.net/browse/ZILCH-49117) | Rebuild fee-service dashboard |
| [ZILCH-49105](https://payzilch.atlassian.net/browse/ZILCH-49105) | Move fee-service monitors to new team |
| [ZILCH-48343](https://payzilch.atlassian.net/browse/ZILCH-48343) | Upgrade AWS JDBC Driver in fee-service |
| [ZILCH-47814](https://payzilch.atlassian.net/browse/ZILCH-47814) | Migrate to RR - Select ... fee_schedule |
| [ZILCH-47643](https://payzilch.atlassian.net/browse/ZILCH-47643) | Remove LD Flag: sort-better-deals-by-lower-fees |
| [ZILCH-45927](https://payzilch.atlassian.net/browse/ZILCH-45927) | Introduce pre-warm capability to fee-service |
| [ZILCH-45531](https://payzilch.atlassian.net/browse/ZILCH-45531) | Fix Fee configurator Selenium tests |
| [ZILCH-43645](https://payzilch.atlassian.net/browse/ZILCH-43645) | Remove LD flag: fee-calc-result-save-async |
| [ZILCH-43640](https://payzilch.atlassian.net/browse/ZILCH-43640) | Remove LD flag: disable-schedule-cache |
| [ZILCH-42256](https://payzilch.atlassian.net/browse/ZILCH-42256) | [QA] Write an automated test for the External Network fees AP |
| [ZILCH-41947](https://payzilch.atlassian.net/browse/ZILCH-41947) | Handle fee calculation requests without input field |
| [ZILCH-41036](https://payzilch.atlassian.net/browse/ZILCH-41036) | Investigate fee-service slowness |
| [ZILCH-41034](https://payzilch.atlassian.net/browse/ZILCH-41034) | Add warmup-code to schedules so we don't see errors |
| [ZILCH-40734](https://payzilch.atlassian.net/browse/ZILCH-40734) | Fix e2e tests after the po3 fee updates |
| [ZILCH-40557](https://payzilch.atlassian.net/browse/ZILCH-40557) | [QA] Complete failover testing for the fee-service |
| [ZILCH-40371](https://payzilch.atlassian.net/browse/ZILCH-40371) | Create Pay over 3 months low fee retailer filter |
| [ZILCH-39878](https://payzilch.atlassian.net/browse/ZILCH-39878) | Clean-up legacy schedule amount lookups |
| [ZILCH-38436](https://payzilch.atlassian.net/browse/ZILCH-38436) | [BE] Add support for PO3 fees to enricher |
| [ZILCH-38016](https://payzilch.atlassian.net/browse/ZILCH-38016) | [BE] Incorrect fees appear in search when users change plans |
| [ZILCH-31511](https://payzilch.atlassian.net/browse/ZILCH-31511) | Avoid exception to be thrown on schedule_amount_lookup table (schedule_amount_id, code) |

## rewards-service

| Ticket | Summary |
|---|---|
| [ZILCH-52505](https://payzilch.atlassian.net/browse/ZILCH-52505) | Expose bulk rewards GET endpoint in rewards service |
| [ZILCH-52414](https://payzilch.atlassian.net/browse/ZILCH-52414) | rewards-service - Reduce log volume & optimise retention |
| [ZILCH-51799](https://payzilch.atlassian.net/browse/ZILCH-51799) | Add new reward reason - Employee Rewards Programme |
| [ZILCH-51459](https://payzilch.atlassian.net/browse/ZILCH-51459) | Investigate DWH dependency on rewards schema in MSSQL |
| [ZILCH-51458](https://payzilch.atlassian.net/browse/ZILCH-51458) | Investigate Looker dependency on rewards schema in MSSQL |
| [ZILCH-51457](https://payzilch.atlassian.net/browse/ZILCH-51457) | Decommission the rewards-service MSSQL database |
| [ZILCH-51456](https://payzilch.atlassian.net/browse/ZILCH-51456) | Switch rewards-service onto Aurora |
| [ZILCH-51455](https://payzilch.atlassian.net/browse/ZILCH-51455) | Migrate rewards-service data from MSSQL to Aurora |
| [ZILCH-51136](https://payzilch.atlassian.net/browse/ZILCH-51136) | Idempotency support for rewards load endpoint |
| [ZILCH-50809](https://payzilch.atlassian.net/browse/ZILCH-50809) | Relax email validation in Mixpanel lambda for EVENT_REWARD_APPLIED events |
| [ZILCH-49609](https://payzilch.atlassian.net/browse/ZILCH-49609) | Rationalize the way reward rates are stored |
| [ZILCH-49103](https://payzilch.atlassian.net/browse/ZILCH-49103) | Review rewards-service throughput monitor |
| [ZILCH-48938](https://payzilch.atlassian.net/browse/ZILCH-48938) | Clean-up legacy loan completion credit reward logic |
| [ZILCH-48444](https://payzilch.atlassian.net/browse/ZILCH-48444) | Exclude boost from rewards calculation |
| [ZILCH-48304](https://payzilch.atlassian.net/browse/ZILCH-48304) | Remove LD Flag: block-rewards-on-late-payment |
| [ZILCH-48128](https://payzilch.atlassian.net/browse/ZILCH-48128) | Handle validation errors in Rewards Service with proper ControllerAdvice (return 400 instead of 500) |
| [ZILCH-47220](https://payzilch.atlassian.net/browse/ZILCH-47220) | Deprecate/Remove Rewards APIs that use email to identify customers |
| [ZILCH-46885](https://payzilch.atlassian.net/browse/ZILCH-46885) | [BE] Document the full lifecycle of credit rewards |
| [ZILCH-46861](https://payzilch.atlassian.net/browse/ZILCH-46861) | [Admin Portal] Understand how a refund has been processed (rewards or cash) |
| [ZILCH-46853](https://payzilch.atlassian.net/browse/ZILCH-46853) | Remove LD flag: rewards-refund |
| [ZILCH-46798](https://payzilch.atlassian.net/browse/ZILCH-46798) | Remove LD flag: loan-rewards-subscription-date-validation |
| [ZILCH-46774](https://payzilch.atlassian.net/browse/ZILCH-46774) | Follow-up Ticket: Revisit Reward Eligibility Logic for Subscription/Product Edge Cases |
| [ZILCH-46683](https://payzilch.atlassian.net/browse/ZILCH-46683) | Review reward-history tests |
| [ZILCH-46378](https://payzilch.atlassian.net/browse/ZILCH-46378) | Remove LD flag: zilch-loan-rewards |
| [ZILCH-46377](https://payzilch.atlassian.net/browse/ZILCH-46377) | Remove LD flag: rewards-service |
| [ZILCH-46376](https://payzilch.atlassian.net/browse/ZILCH-46376) | Remove LD flag: zilch-now-rewards-in-store-enabled |
| [ZILCH-46375](https://payzilch.atlassian.net/browse/ZILCH-46375) | Remove LD flag: zilch-now-rewards-enabled |
| [ZILCH-46106](https://payzilch.atlassian.net/browse/ZILCH-46106) | Duplicate rewards on delayed ZILCH_NOW payments due to `loan_completed` event |
| [ZILCH-45876](https://payzilch.atlassian.net/browse/ZILCH-45876) | Remove unlockedRetailerId field from rewards-service |
| [ZILCH-45522](https://payzilch.atlassian.net/browse/ZILCH-45522) | Rewards should be calculated from net purchase amount (after refunds), not full loan amount |
| [ZILCH-45306](https://payzilch.atlassian.net/browse/ZILCH-45306) | Extend OpenSearch queries to respect reward and voucher start/end dates |
| [ZILCH-44865](https://payzilch.atlassian.net/browse/ZILCH-44865) | Remove LD flag: ecj-debit-rewards-from-products-api |
| [ZILCH-44824](https://payzilch.atlassian.net/browse/ZILCH-44824) | Route Rewards-service to Product-service feature lookup |
| [ZILCH-44284](https://payzilch.atlassian.net/browse/ZILCH-44284) | Remove LD flag: rewards-refund |
| [ZILCH-43879](https://payzilch.atlassian.net/browse/ZILCH-43879) | Investigate Customers with Negative Rewards Balance (spent more than earned) |
| [ZILCH-43697](https://payzilch.atlassian.net/browse/ZILCH-43697) | Stabilise Rewards History tests |
| [ZILCH-43664](https://payzilch.atlassian.net/browse/ZILCH-43664) | Remove LD flag: home-rewards-widget-update |
| [ZILCH-43065](https://payzilch.atlassian.net/browse/ZILCH-43065) | Remove rewards-related SNS and SQS subscriptions from customer-service |
| [ZILCH-42522](https://payzilch.atlassian.net/browse/ZILCH-42522) | Enable Reference ID Generator Post-Aurora Migration |
| [ZILCH-40929](https://payzilch.atlassian.net/browse/ZILCH-40929) | Rewards Balance Not Refreshing |
| [ZILCH-40182](https://payzilch.atlassian.net/browse/ZILCH-40182) | Create missing Rewards service tests |
| [ZILCH-39314](https://payzilch.atlassian.net/browse/ZILCH-39314) | Hide call to fetch rewards summary behind a LD toggle |
| [ZILCH-38717](https://payzilch.atlassian.net/browse/ZILCH-38717) | Rewards missing due to rounding when earning both static and dynamic % rewards |

## offer-service (tastecard)

| Ticket | Summary |
|---|---|
| [ZILCH-52807](https://payzilch.atlassian.net/browse/ZILCH-52807) | Complete handover of offer-service and rewards-service to Loyalty team |
| [ZILCH-52423](https://payzilch.atlassian.net/browse/ZILCH-52423) | offer-service - Reduce log volume & optimise retention |
| [ZILCH-49457](https://payzilch.atlassian.net/browse/ZILCH-49457) | Switch offer-service to use subscription event queue |
| [ZILCH-49170](https://payzilch.atlassian.net/browse/ZILCH-49170) | Replace product change event handling with feature change handling |
| [ZILCH-49099](https://payzilch.atlassian.net/browse/ZILCH-49099) | Remove offer-service failure messages for all non-prod environments |
| [ZILCH-47018](https://payzilch.atlassian.net/browse/ZILCH-47018) | Alert for offer-service (new issues only) |
| [ZILCH-46162](https://payzilch.atlassian.net/browse/ZILCH-46162) | Remove LD flag: tastecard-activation-marketing-tile |
| [ZILCH-51025](https://payzilch.atlassian.net/browse/ZILCH-51025) | [FE] Remove LD flag: tastecard-member-signup-experiment |
| [ZILCH-44581](https://payzilch.atlassian.net/browse/ZILCH-44581) | Increase timeout on New Codes queue |
| [ZILCH-44309](https://payzilch.atlassian.net/browse/ZILCH-44309) | Regenerate tastecard Code on Admin Portal |
| [ZILCH-42979](https://payzilch.atlassian.net/browse/ZILCH-42979) | Offer Codes Info in Admin Portal |
| [ZILCH-42799](https://payzilch.atlassian.net/browse/ZILCH-42799) | Feature Roll-Out |
| [ZILCH-42797](https://payzilch.atlassian.net/browse/ZILCH-42797) | Educate Customer Service Agents in Code Reallocation |
| [ZILCH-42745](https://payzilch.atlassian.net/browse/ZILCH-42745) | Alert on Code Exhaustion |
| [ZILCH-42744](https://payzilch.atlassian.net/browse/ZILCH-42744) | Report Memberships for Billing |
| [ZILCH-42740](https://payzilch.atlassian.net/browse/ZILCH-42740) | Reallocate a Code In Case of Failure |
| [ZILCH-35830](https://payzilch.atlassian.net/browse/ZILCH-35830) | GABD evaluates vouchers in in-store search |
| [ZILCH-34210](https://payzilch.atlassian.net/browse/ZILCH-34210) | Monitoring for Single User Vouchers |

## Other / Unrelated

The remaining ~210 tickets do not clearly relate to fee-service, rewards-service, or offer-service. They cover areas such as:

- Retailer service / storefront
- Frontend (mobile app, web, admin portal)
- Data consistency service
- CMS / content
- Search (semantic search, sponsored search)
- Testing infrastructure (Maestro, Pact, e2e)
- Vulnerabilities / dependency upgrades
- LaunchDarkly flag removals (non-service-specific)
- Affiliate integrations (Awin, Partnerize, CJ, Quidco)
- Lambdas (Mixpanel, image optimiser, content cache)

These tickets remain with the Merchant team.
