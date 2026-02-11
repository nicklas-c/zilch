# Jacek

## Context for AI
Jacek is a back-end engineer in the Merchant team, graded at level 4, equivalent to a senior or tech lead.  He acts as de facto tech lead for the team and is the foremost subject matter expert on the systems the team owns.  He is based in Krakow.

## 2025 year-end appraisal

### His self-appraisal

#### Achievements
Over the past year, I delivered technically complex and business-critical changes across Zilch’s backend services and admin tooling, while taking on increased ownership and operational responsibility.

* Do it 💥 / Do it the right way ✅ 
    * Delivered features and fixes across rewards-service, fee-service, retailer-service, admin-service, and admin-ui, with strong focus on correctness, backward compatibility, and safe production rollouts.
* Do it brilliantly 🥇
    * Implemented Credit Rewards, including new reward calculation logic and cross-service integrations.
    * Fixed complex financial edge cases such as partial rewards clawback, ensuring calculations were based only on the cash portion of purchases.
    * Led a major AWS SDK v2 upgrade, involving large-scale refactoring and careful handling of behavioural changes.
* Do it for our customers 💚
    * Successfully removed in-memory caching from fee-service and improved its performance, enabling better scalability under load.
    * Improved fee-service latency by implementing targeted optimisations and introducing asynchronous processing where appropriate.
    * Took an active role in several complex fee schedule migrations, ensuring data consistency and minimal risk during transitions.
* Fees & admin experience improvements
    * Enhanced fee schedule configurators in the Admin Portal to include product and loan product names, improving transparency and ease of use for admin users.
    * Worked on multiple Admin Portal projects, including UI changes
* Extended platform capabilities:
    * Together with the other team members I worked on adding semantic search support, including vector-based querying.
    * Added retailer-level rewards blocking, affiliate externalId support, and card-tracking transaction type support.
* Took ownership of production deployments, being trusted to deploy services on behalf of the team.
* Remained consistently available during incidents, supporting investigation and resolution.
* Supported team growth by helping onboard a new engineer, sharing product knowledge and enabling them to become an independent contributor.

#### Growth Areas
* Increase impact by aligning earlier on complex fee and platform changes, especially when multiple services or teams are involved.
* Share technical context and design decisions earlier to reduce review cycles and support team understanding.
* Continue developing system-level design and performance optimisation skills, particularly for high-throughput services.
* Further improve communication of technical trade-offs to non-engineering stakeholders.

### Final Summary
Over the last year, I consistently delivered complex backend and admin-portal work, improved the scalability and performance of critical services (particularly fee-service), and took responsibility for production stability through deployments and incident support. I also worked across the full stack when needed, including UI changes in the Admin Portal, despite my primary role being backend Java development.

Beyond individual delivery, I increasingly contributed at a broader team and cross-team level. I took part in reviews and recruitment interviews for more senior engineers, temporarily covered managerial responsibilities during manager’s absence, and acted as a key point of contact between engineering and the data team, especially around affiliate partner integrations. I also supported team growth by mentoring a new engineer and helping them become an independent contributor.

Overall, I believe this year reflects strong ownership, technical depth, and growing impact beyond my immediate scope. Going forward, I want to continue expanding this impact through deeper involvement in technical design and planning, continued cross-team collaboration, and further development of my leadership and system-level skills.

### My appraisal of Jacek
#### Impact
Jacek continues to show up as a very dependable engineer in the Merchant team; combining consistency with great subject matter expertise in the Merchant domain and a willingness to take ownership.

He is alert to risks and potential pitfalls and raises them helpfully and calmly. On call, he monitors actively and responds quickly when issues arise. He's responsive to other teams and leans in well when help is needed from the Merchant team. An increased availability to help has been noted and appreciated.

Jacek has demonstrated good flexibility during the year: showing a willingness to change personal plans in order to assist during incidents and critical releases. He's shown similar flexibility in a technical sense and recently got started on a new project that required him to switch to an unfamiliar programming language (Go).

Jacek carries a lot of weight for the team and almost every one of our backend projects would have gone less well without his involvement.

He is liked and respected by colleagues and is easy to manage.

#### Growth Areas
I'd like Jacek to think about how he provides visibility on the things he's doing. He proactively communicates - especially in 1:1s, but coverage can be a little patchy. Jacek's ability to act autonomously and get stuff done is an advantage, but it sometimes results in things happening a little under the radar. Providing better visibilty will help keep me in the loop and also ensure his efforts don't go unappreciated.

Jacek could be a little more ambitious if he chooses. He sometimes seems happy to stay in his lane and go with the flow. I'm happy with that if he is, but the opportunity is there for him to lead more and work towards an L5 promotion. To do that, I'd like to see him think about his cross-team impact in terms of leadership rather than contribution.

## Running Notes

2026-02-02 In a conversation with Michal, he mentioned that he thought Jacek may be feeling jaded about the projects he's working on - having been tied to the same codebases for a long time.  He thought Jacek might enjoy changing team.

### Stand-up — 2026-02-11
- ZILCH-40366 (gateway service authoriser Lambda): attempting pre-prod deploy today. Needs review. Raised question about whether to use new gateway vs proxying through customer-service.
- ZILCH-46901 (Partnerize integration): nearly done, awaiting platform ticket.
- Agreed to review Nick H's PR for ZILCH-43742 (remove fetchRecentlyPurchasedRetailers query).

### 1:1 — 2026-02-10

Opened with social chat — just back from skiing holiday, enjoyed it, good for the whole family.

**Michal's departure:**
- Hadn't been aware — missed the news while on leave.
- Sought confirmation Michal is joining a new team, not leaving the company. Confirmed.
- Discussed the strategic rationale for the new Spend Platform team and that it will be almost entirely colocated in Poland.
- Timelines: Michal moves at end of sprint.

**"Jaded" signal (from Michal's feedback):**
- Jacek recognises the conversation being referenced.
- Reassures it wasn't a strong preference — would consider a move if offered, but not a flight risk.
- Actually quite interested in current work: intelligent commerce and gateway service are providing fresh direction.
- I made the point that he's valued: I'd prefer not to lose him from the team, but I'd prefer that to losing him from the company.
- Asked if I should actively look for move opportunities. Not actively — agreed I should keep my eyes open rather than hunt one down.

**Stefan's role:**
- Hadn't been aware Stefan would be joining as Zilch's first L5 FE.
- Knew the role had previously been considered for someone.
- I clarified some history of the vacancy and selection process without going into sensitive areas.
- Asked if Stefan will have roles beyond the Merchant team. Confirmed — scope to operate beyond the team; hired partly to provide FE engineering leadership. May have strong opinions on SSR project or modular FE architecture.
- Confirmed Stefan is London-based, working normal hybrid pattern.

**New team (follow-up):**
- Cycled back for more detail. I described the new team as purely back-end, owning platform services for the spend domain. Shared the team composition and that fee-service will move to the new team.

**Appraisal:**
- Discussed what I can and can't share before the process has run its course.
- Discussed how I approached writing my parts.
- Shared what I had written about him.
- My feedback that he could be more ambitious and look for chances to take a leadership role in cross-team initiatives landed very well.
- He responded with the idea that he could lead the gateway service as it transitions from a Merchant team initiative into something other teams adopt.

**My observations:**
- Delighted he spotted the gateway service opportunity — ideal for demonstrating the cross-team leadership I'm encouraging.
- On the "jaded" topic: I also raised this in a recent engineering leadership meeting, posing the question of whether we should look to regularly rotate engineers to keep them engaged and give them maximum exposure to Zilch systems.