# Nick Holt

## Context for AI
Back end engineer on the Merchant team (Level 3), based in London.

## 2025 year-end appraisal

### His self-appraisal

#### Achievements
* Collaborated on the extraction of rewards logic from a legacy monolith into a dedicated service. This work reduced coupling with core systems and improved the team’s ability to evolve the rewards domain independently.
* Worked as part of the team to design and implement semantic retailer search using OpenSearch, including ingestion and indexing of retailer vector embeddings. This enabled more relevant, intent-based retailer searching.
* Individually designed and delivered core APIs for the Rewards Hub, owning the API contracts and implementation to provide a stable, well-documented interface unblocking downstream development.
* Individually built and integrated the Taste Card membership offering delivering a customer benefit through a clean, extensible integration while ensuring alignment with existing architecture and operational requirements.
* Contributed to the introduction of shared infrastructure libraries for Aurora database connectivity and security, helping to standardise best practices across services, reduce duplication, and improve the platform’s overall security and reliability.
* Worked with external auditors to review reward and fee history to ensure Zilch was meeting our contractural obligations.

#### Growth Areas
* Refine how I influence decisions, focusing on when, where, and how ideas are introduced rather than on technical correctness alone.
* Continue to improve communication by leading with outcomes, adjusting depth and framing to suit different audiences and decision-making contexts.
* Develop my ability to guide discussions through questions and constraints, enabling others to arrive at sound conclusions collaboratively rather than relying on direct advocacy.
* Focus on growth from “strong individual contributor” to “multiplier for the team,” improving my ability to bring others with me and increase overall team effectiveness.

### My appraisal of Nick H
#### Impact
Nick is an excellent technologist who brings rigour in thinking about design to the team, most especially with regard to his affinity for cloud-native computing. His abilities as a programmer are admired by others in the team and his opinions always worth hearing.

He defends his opinions when when necessary, but has demonastrated that he his willing to commit to decisions he disagrees with when overruled.

He has contributed well on many of the Merchant team's projects - his contribution to Semantic Search and Tastecard integration spring to mind.

He focuses well and works hard to move productively through tasks.

#### Growth Areas
As a technologist, Nick is operating well above his current grading. In order to capitalise on that fully, he could consider two important growth areas.

See beyond the engineering task. Nick can tend to approach his work with the view that it's a solo programming problem. By developing a keener awareness of the needs of stakeholders and peers in the team, he will emmerge as a much stronger team player. His focus on the coding part of a task also often leads to him underestimating the task at hand.

Communication style. Nick could demonstrate better situational awareness in some conversations so that the information he provides is apporopriate to the meeting or conversation. Setting some context before diving into details will help others to understand his point. He can tend to talk at length and in detail unaware that others have not managed to follow his train of thought. Considering how to ensure he's bringing others with him will transform his communication.

I'm delighted by Nick's self-appraisal which shows great self-awareness and aligns very well with my review.

## Running Notes

### PRD Review (Pending Rewards) — 2026-02-11
- Observed Nick steering the conversation away from requirements clarification and into solution design, which derailed the meeting's purpose for a while. Other engineers got pulled in too — not solely on Nick — but he initiated the tangent.

### Stand-up — 2026-02-11
- ZILCH-43742 (remove fetchRecentlyPurchasedRetailers query): has done query optimisation, PR up, Jacek picking up review.
- ZILCH-48084 (fix fee-service deployment): in PR. Staging deploy was broken — root cause still unclear to me; need to dig into what happened.
- ZILCH-48248 (race condition between offer-service and product-service): fix is in PR, but it appears to have caused another issue with a failing test. Puts onus back on Platform — their move of a lambda for a static IP caused the original issue. May need to switch everything over to EventBridge.

### Aurora / fee-service connectivity — 2026-02-12
- Identified that a Dependabot update to the AWS JDBC driver was the cause of the staging connectivity breakage (confirming Michal's hunch). Downgraded the driver and staging came back up.
- Excluded the AWS JDBC driver from Dependabot ([PR #336](https://github.com/zilchdev/fee-service/pull/336)).
- Plans to raise a separate ticket to investigate upgrading the driver safely.
- Good debugging instinct and follow-through here — identified the issue, fixed it, and took preventive action promptly.

### Stand-up — 2026-02-12
- ZILCH-43742 (remove fetchRecentlyPurchasedRetailers query): Jacek has reviewed it. Found a place where the removed code might be called from the front end. Back with Nick H to check with Ossie.
- ZILCH-48084 (Aurora connectivity / fee-service): has a way forward by downgrading the JDBC driver for now. Has created a new ticket to implement a proper fix for the updated driver.
- ZILCH-48222 (design task): in progress. Talking about tests despite this being a design task — appears to be validating his ideas work. Characteristic of his tendency to jump into implementation.
- ZILCH-48248 (race condition fix): can be moved to QA sign-off.
- **WIP observation:** Four tickets in flight at stand-up. Pattern of high WIP — consistent with the tendency to pick up the next thing before the current one is fully closed out.

### 1:1 — 2026-02-11

#### Planned Talking Points
1. **Appraisal** — Share and discuss year-end appraisal feedback.
2. **Michal's departure** — Michal leaves the team on 24th Feb. Impact on team capacity and the dynamic between remaining BE engineers (Nick and Jacek will be the only two until a backfill arrives).
3. **Fee-service staging breakage** (time permitting) — ZILCH-48084 broke staging; root cause unclear. Want to understand what happened, but prefer to do this as a session with all BE engineers to spread the knowledge.

#### Notes
Only the appraisal was discussed from the planned items. Michal's departure and fee-service breakage were not covered. Another indicator that Nick tends to pull conversations down rabbit holes of his own making.

**Pending rewards design discussion** (Nick-led)
- His design is predicated on writing 'pending' records into the ledger. Only read the pendings up to an actual 'earn' — the ledger records don't need to be converted to earns.
- *My private reflection:* I like this approach because it takes a write-only approach to a ledger, which is good design. But I'm not yet convinced it works logically.

**Appraisal discussion**
- Discussed what I can and can't share with him.
- Explained my approach: I bullet-pointed talking points before reading his self-appraisal, then read the self-appraisal before writing my appraisal of him.
- Reviewed his self-appraisal and reminded him what he wrote.
- Reviewed my appraisal of him. On the positive side, I placed emphasis on his cloud-native competency and the fact that others in the team admire his technical competence. On the critical side, I emphasised that the 'growth areas' weren't just nice-to-haves but genuine blockers for him.
- He recognises some of his communication challenges and feels genuinely frustrated that he struggles in that area.
- I used a recent meeting as an example where he used a refinement meeting to dive deep into technical solutions.
- His perspective: he gets *drawn into* those conversations. *My private observation:* from the outside, it always feels like he leads them, not that he's drawn in.
- His response to the appraisal conversation was "That was painless." I get the sense he was expecting a difficult conversation — some conspicuous criticisms over the last few months have obviously taken their toll.
- Bizarrely, he then started discussing solutions in detail again as an example of *why* he goes into detail on things — "you need to know X, Y, and Z so that you can make a decision on A." Somewhat ironic given the conversation we'd just had.

**Knowledge base frustration**
- He's frustrated at the lack of a knowledge base at Zilch.

**AI scepticism**
- Conversation segued into AI. He is sceptical.

### Next 1:1 — Talking Points

1. **Michal's departure** — Carried over from 11th Feb. Michal left on 24th Feb. Discuss Nick's view of the impact — on capacity, on the dynamic with Jacek as the only other BE engineer, and on any work that's landed back on him.
