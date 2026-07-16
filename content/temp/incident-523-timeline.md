## Incident-523 — Timeline

| Date | Event |
|---|---|
| 6 Mar 2026 | April Pricing Change Brief published by Tamara Quinn. Specifies PayOver3 fee cap increase from £40 to £80. Approved by Joe Zender, Ozzie Yuce, John Moore. |
| 6 Mar 2026 | Epic ZILCH-49226 created. No child ticket raised for the PayOver3 fee cap change. |
| 7 Apr 2026 | Pricing changes go live. PayOver6 fees updated via SD-216970. **PayOver3 fee cap not updated.** |
| 8 Jul 2026 | Tom Wood identifies a transaction capped at £40 that should have been £80. Posts in #merchant-revenue. |
| 9 Jul 2026 | Jacek Zanko confirms via prod DB: fee cap still £40. No evidence it was ever changed. |
| 9 Jul 2026 | Incident-523 raised. Mark Reddington validates as SEV3. |
| 9 Jul 2026 | SD-218509 raised for the fix. Production execution planned for 13 Jul. |
| 10 Jul 2026 | Fix applied to staging. Boris Karaulov confirms results match expected. |
| 13 Jul 2026 | Tom McKenzie confirms Fee Service and Purchase test suites pass in staging. Awaiting validation sign-off before prod execution. |

## Root Cause

Human error. The PayOver3 fee cap increase (£40 → £80) was specified in the approved pricing brief but was overlooked when the fee schedule changes were applied on 7th April. Only PayOver6 fees were updated.

## Contributing Factors

1. **No discrete trackable task.** The requirement existed only as a sentence in the brief's prose. It was not in Jira and was not an explicit item in the brief's own task checklist. It was easy to miss alongside the more detailed PayOver6 content.

2. **Fees Rate Table omits caps.** The reference document listing all fee calculation parameters does not include cap values. Anyone checking the rate table for correctness would not have noticed the cap was wrong.

## Missed Opportunities to Detect

1. **Product did not verify the outcome.** Engineers checked the fee changes post-deployment, but product did not independently verify that the outcome matched their requirements. Monitoring existed but was not being reviewed by the people who would know what "correct" looked like.

2. **Staff testing was not completed.** A staff testing plan was documented with test cases requiring execution after fees were applied to production (Part 2 and Fee Change Test Cases). None of these were executed.

3. **The one PayOver3 test case tested display, not behaviour.** Test case A5 checks that the UI displays "Maximum fee £80". It does not verify that the fee schedule actually enforces the cap.

4. **Display cap is hard-coded.** The fee cap shown in the UI is a front-end constant, not derived from the fee schedule. The UI was updated to say "Maximum fee £80" without any dependency on the actual configured cap — allowing the two to diverge silently.
