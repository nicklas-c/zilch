# Nick H

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

### 1:1 — 2026-02-11 (planned)

#### Talking Points

1. **Appraisal** — Share and discuss year-end appraisal feedback.
2. **Michal's departure** — Michal leaves the team on 24th Feb. Impact on team capacity and the dynamic between remaining BE engineers (Nick and Jacek will be the only two until a backfill arrives).
3. **Fee-service staging breakage** (time permitting) — ZILCH-48084 broke staging; root cause unclear. Want to understand what happened, but prefer to do this as a session with all BE engineers to spread the knowledge.

