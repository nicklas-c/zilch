# Tom McKenzie

## Context for AI
Tom McKenzie is a QA Engineer Level 3 in the Merchant Team. 

## Running Notes

### 2026-02-05 — 1:1 prep

**Talking points:**
1. Status of Nikos's defect analysis project
2. Appraisals — how did he appraise himself? (Haven't seen his since he reports to Nikos)
3. Maestro project — is he comfortable running with it once Alex leaves (tomorrow)?

### 2026-02-05 — 1:1 notes

**React Native update**
- Merging today, out with next release
- Very confident — thinks should have gone live a month ago
- Recent issues have been minor cosmetic fixes; would have preferred a big push to get them all done sooner

**Maestro**
- Test pack ready to be turned on in CI/CD pipeline on PR
- All front-end engineers will benefit (shared project)
- Will then start removing Appium tests — only keep where full E2E is required
- Confident taking it forward without Alex; one test still needs fixing, but other engineers know how to use it

**Defect analysis**
- Going fine
- Raising questions about whether we need an SLA for defect resolution — some stale defects

**Team dynamics**
- Nick H still pushes back on writing E2E tests
- Nikos has guidance: integration tests sufficient if change is internal to service with no API changes
- Encouraged Tom to treat Nikos's rule as guidance, not absolute — he has authority to decide test strategy and should feel able to say "this is what I expect"
- Thinks things are improving: pipeline changes mean actual benefits to writing E2E tests (automatic promotion to production)
- Could move many Fee Service E2E tests to integration testing under Nikos's guidance, but wouldn't want to move all

**Appraisals**
- Nikos wrote his appraisal (not me). Nikos didn't ask for my input, but asks periodically through the year.
- Feedback from Nikos:
  - Needs to take leadership duties as seriously as technical/testing duties *(I agree)*
  - Emphasis on incorporating AI
  - Didn't do as well as he could have on Memberships work — Tom attributes this to being brought in late; would have preferred earlier involvement
  - Feedback about ContentStack — feels like becoming an SME is being pushed at him
    - I expressed uncertainty about why this would fall to QA — doesn't fit the function

### Stand-up — 2026-02-12
- ZILCH-40343 (retry on 401): ran complete regression test — all passed. Tried to mimic a 401 to test for a retry. Needs to work with Ossie to make sure his test is working correctly.
- ZILCH-47687 (Zilch Pro label on Rewards on Purchases): test working, evidence added to ticket. Available for QA review — should move soon.

### Stand-up — 2026-02-13
- Active on several tickets in QA: ZILCH-47687 (adding proof before moving forward), ZILCH-48084 (signing off today), ZILCH-48303 (satisfied with automated test coverage after discussion).
- Had to encourage him to consider himself an authoritative stakeholder for quality — that he can assert what he expects to see from a test perspective. Recurring theme: see also 1:1 on 2026-02-05 where I encouraged him to treat Nikos's guidance as guidance, not absolute, and to own test strategy decisions.
- Suggested he write a test policy document that the team can sign up to — a way to codify expectations and reduce the recurring stand-up debates about testing levels.

### Aurora / fee-service connectivity — 2026-02-12
- Asked a sharp question: how could regression/sanity tests have passed if the JDBC driver update broke DB connectivity? Offered to re-run regression and sanity to verify staging is now fixed.
- Good QA instinct — questioning the test coverage gap rather than accepting the fix at face value.

### 2026-02-05 — 1:1 notes (cont.)

**Other topics**
- Gated content release approval process (segued from ContentStack discussion)
- Mutation testing initiative: wasn't on his radar at all; discussed merits and issues; he hasn't done much with it in the past

