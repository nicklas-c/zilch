<u>**Merchant**</u>

**Sponsored Retailer Search**
* Engineering complete. Remaining dependency is retailer category data cleanup, coordinated by Kieran Patel with the data team.

**Rewards / Aurora Migration**
* Fixed URL length breach in prod by batching calls to purchase-service for ledgers.
* Fixed broken request signing on rewards admin endpoint.
* Data source switchable (LD flag for MSSQL/Aurora) in PR.

**Intelligent Commerce**
* CJ network card tracking integration complete and Ready for Release.

**Quality & Testing**
* Re-enabled Maestro runs on frontend PRs (non-blocking).
* Fixed failing merchant Appium tests.
* Fixed offer-service deallocation race condition affecting E2E tests.

**Loyalty Services Handover**
* Documented TasteCard code upload process.
* TasteCard (`offer-service`) handover complete.
* Fresh TasteCard voucher codes ingested in collaboration with Loyalty team.
* `rewards-service` handover to Loyalty team completed successfully (Merchant will complete Aurora migration work).

**KTLO**
* Increased customer lock timeout from 5s to 30s to resolve intermittent loan completion failures.
* Schedule-aware maintenance banner display in development (platform request).

**Recruitment**
* 2 L4 open roles in Vilnius remain active.
   * Pipeline now empty — 3 rejects (inc. 1 no-show). Feedback given to talent team; sourcing new candidates.
* Amr Aljundi starting in London 27th July
* Reeya Patel starting in London 3rd August

**Risks**
* Will be running with just one back-end engineer for the next month.