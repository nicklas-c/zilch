# Tom McKenzie

## Context for AI
Tom McKenzie is a QA Engineer Level 3 in the Merchant Team. 

## Running Notes

### 2026-02-18
* Raised concern in support-merchant that velocity limits may prevent users from fully redeeming rewards before a deadline — flagging potential customer experience issue.

### 2026-02-19 — 1:1 prep

**Talking points:**
1. Test policy document — how is he going to approach it?
2. QA sign-off process — engineers are pushing tickets through the QA stage themselves; how does he think about his role in that from a process perspective?
3. Feedback on the defect analysis presentation — the findings were interesting, but facilitation of the root cause and mitigations section was unstructured

### 2026-02-19 — 1:1 notes

**QA culture across teams**
* Tom attended a meeting of QA engineers across the company. A common theme: QAs struggling to get engineers — especially back-end engineers — to do appropriate testing, and facing push-back. Sounds worse on some other teams than on ours.
* In Merchant this manifests as Nick H sometimes arguing for less testing than Tom expects. Recurring theme — see also 1:1 2026-02-05.
* Reiterated that I assert in front of the whole team that he has authority to insist on tests. Tom said he wishes Nikos did the same more.
* Tom wants to use pre-refinement meetings to specify test requirements on tickets before they enter refinement. I have been pushing for this for some time.
* I raised the Jira stage issue: tickets being moved through the QA stage by the engineer themselves. The preferred pattern is for Tom to move them — creates an audit trail. If the engineer must move it, a comment explaining why QA signed off is the minimum requirement.
* I made the point that for straightforward tickets the policy document, once written, can be referenced in lieu of a detailed per-ticket justification.

**Test policy document approach**
* Tom is still at the ideas stage — vague on detail but confident. One firm opinion: whether a change is purely internal to the service (no API changes) should be a key criterion, consistent with Nikos's existing informal guidance.
* I suggested framing the rules deterministically enough that an AI tool could read the policy alongside a Jira ticket / commit and automatically assert what testing is required.
* Tom mentioned Nikos is working on something like this already, though from his description it sounds fairly basic at present.

**Testing terminology**
* We discussed the ambiguity of the term "Integration Test": it can mean a single service tested in an integrated mode (as distinct from unit tests), or it can mean a multi-service / subsystem test. The distinction will need to be clear in any policy document.

**Nick H tension — recurring**
* Tom raised tension with Nick H last week over testing expectations. Recurring theme — see 1:1 2026-02-05 and stand-up 2026-02-13.
* Reiterated: the policy document removes the need to relitigate arguments case by case.
* Reiterated: Tom is the gatekeeper. If he is not satisfied, the ticket does not pass. If poor quality code makes it past QA, it is his reputation at stake — not Nick's. Nick needs to understand that.

**Production incident example**
* Tom cited a recent case: instalment miscalculation when a boost was included in a loan. A Payments team issue, not Merchant.

**Defect analysis follow-up**
* Nikos has asked Tom to log follow-up actions in Jira from the defect analysis.
* Tom's view is that our biggest problem is unknown unknowns — e.g. a recent case where duplicate events from another service caused issues; the team had no expectation multiple events were possible. *[Personal note, not said in the meeting: I'm not fully persuaded — idempotent event handling should be the default and would contain this class of problem.]*
* Tom described a technique from a previous employer: new service versions deployed alongside existing in production; inputs split across both; outputs compared. Shadow mode / parallel-run testing in production.

**Feedback on defect analysis presentation**
* I gave Tom feedback:
  * Insights were good and enjoyed.
  * Wanted more grouping of defects by common cause or domain area — would have made findings more actionable.
  * Facilitation of the discussion section was poor — unstructured, didn't land. Advised planning the facilitation properly in future.
* Connects to recurring feedback from Nikos (appraisal, 2026-02-05): Tom needs to take leadership duties as seriously as technical ones. Facilitation is a leadership skill.

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

### Defect analysis read-out — 2026-02-16

Presented defect analysis findings to the team (with Nikos). The stats and insights were reasonable. However, the follow-up workshop on common root causes was unstructured and unhelpful — Tom kept picking on people randomly with oddly specific questions that weren't necessarily related to their function or domain. Little value gained from the workshop portion. Meeting overran.

This connects to recurring feedback from Nikos (appraisal, 2026-02-05): Tom needs to take leadership duties as seriously as technical/testing duties. Facilitating a productive workshop is a leadership skill — there's a gap here.

### Stand-up — 2026-02-13
- Active on several tickets in QA: ZILCH-47687 (adding proof before moving forward), ZILCH-48084 (signing off today), ZILCH-48303 (satisfied with automated test coverage after discussion).
- Had to encourage him to consider himself an authoritative stakeholder for quality — that he can assert what he expects to see from a test perspective. Recurring theme: see also 1:1 on 2026-02-05 where I encouraged him to treat Nikos's guidance as guidance, not absolute, and to own test strategy decisions.
- Suggested he write a test policy document that the team can sign up to — a way to codify expectations and reduce the recurring stand-up debates about testing levels.

### Stand-up — 2026-02-18
- ZILCH-40366: his QA concerns satisfied — agreed it can go to prod on the basis that it won't be in active use yet, just available.

### 2026-02-18 — Pending Rewards
Asked in Slack whether Tom is familiar enough with Nick Holt's pending rewards design proposal to define the tests required.

### 2026-02-18 — Test policy document chase

Chased Tom on the test policy document (originally suggested 13 Feb). Still waiting on delivery.

### Aurora / fee-service connectivity — 2026-02-12
- Asked a sharp question: how could regression/sanity tests have passed if the JDBC driver update broke DB connectivity? Offered to re-run regression and sanity to verify staging is now fixed.
- Good QA instinct — questioning the test coverage gap rather than accepting the fix at face value.

### 2026-02-05 — 1:1 notes (cont.)

**Other topics**
- Gated content release approval process (segued from ContentStack discussion)
- Mutation testing initiative: wasn't on his radar at all; discussed merits and issues; he hasn't done much with it in the past

