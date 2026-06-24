# Merchant

## Rewards
- Resolved a SQL deadlock (CannotAcquireLockException) and a broken idempotency check, redeployed and stabilised the rewards-service, aligned the rewards-pending flag across all environments up to staging, and fixed broken late-payment reward-blocking tests.
- Block Rewards on Late Payments now enabled in pre-prod. Pending Rewards support is now being turned on for initial customers.

## Intelligent Commerce
- Improved affiliate integration service logging for better dashboards

## Personalisation & Engagement
- Added a LaunchDarkly toggle for the new Personalise Header and enhanced Appsflyer deeplinking into promotional pages.

## Sponsored Retailer Search
- Held a workshop to shape upcoming search experience work.
- Actively building the backend (search mapping, serving results, admin portal config)

## KTLO
- Scheduled the TasteCard cancellation report to Ello

## Recruitment

2 L3 BE candidates accepted in London
2 L4 open roles in recruitment

## Risks
- High likelihood that rewards service migration to Aurora will not be complete by the time Nick Holt leaves.  Mitigating with strong handover to Jacek.