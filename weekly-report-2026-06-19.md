## HIGHLIGHTS
### Merchant
- **`rewards-service` Aurora migration**
  - Created rewards-service DB baseline in Aurora. Fixed spurious warnings.
  - Aligned inter-service request signing with the established pattern, with E2E coverage added.
  - Investigating rewards-related E2E failures (passing locally; longer-running failure raised with Purchase team).
- **Sponsored Retailer Search** 
  - Deployed to dev-cu and ready for testing.
  - Admin Portal fully implemented; new search endpoint on Public Retailer Gateway blends sponsored results.
  - Search quality issue identified — special-character handling needs fixing.
- **Personalisation & Engagement**
  - User behaviour tracking now sending events to Mixpanel and Personalize.
- **Customer Service Routing**
  - Implemented LaunchDarkly-toggled redirect of selected customer-service requests to retailer-gateway.
- **KTLO**
  - Fixed offer-service race condition and health check issues. Improved cross-partner observability logging.
  - Fixed failing merchant Appium tests. All failed nightly E2E re-runs now passing.

### DevOps
- **Dev Platform Rebuild**
  - Readied the eu-ew1-dev-unified cluster for migrating dev environments.
  - Completed API Gateway ingress migration. 
- **Zephyr Zero**
  - payments-service deploy-on-PR pipeline to zephyr-zero in progress.
- **Observability Cost Reduction** 
  - Refactored backend services Datadog monitors into a single project with prod and non-prod workspaces.
  - Raised logging review initiative for teams.
- **KTLO**
  - Fixed API gateway Terraform module. Added admin-ui deployment lock cleanup to nightly shutdown script.

## RECRUITMENT
- 2 L4 open roles in recruitment
- 3 candidates in pipeline in Vilnius

## RISKS
- Rewards-service Aurora migration unlikely to complete before Nick Holt leaves at end of June. Mitigating with structured hand-over to Jacek Zańko and the Loyalty team starting next week.
