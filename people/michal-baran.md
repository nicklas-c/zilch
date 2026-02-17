# Michal Baran

## Context for AI
Michal Baran is a back-end engineer in the Merchant team, based in Krakow. He is departing the Merchant team on 24th February 2026 to join a newly created team.

## 2025 year-end appraisal

### His self-appraisal

#### Achievements
* Contributed to the implementation of **Semantic Search** using Amazon OpenSearch with kNN indexing and embeddings generated via Amazon Bedrock. I focused on integrating OpenSearch with Bedrock, including secure IAM configuration, index setup, and implementing a neural query enrichment approach to improve search relevance and result precision.
* Implemented stricter **credit rewards eligibility rules**, ensuring rewards are only granted when customers have a continuous active subscription throughout the entire loan lifecycle. Although this was a relatively small and time-boxed task, I took ownership of the implementation and delivered it to production within a few days. This change significantly reduced incorrect reward payouts and is estimated to save around £70k per month.
* Supported the rollout of **subscriptions and enhanced rewards**, contributing to backend logic for configurable reward rates, feature toggles, and validation of reward eligibility for subscribed customers.
* Played a key role in the **migration of fee-service from MSSQL to Aurora**, including data migration planning, coordination with Platform and Data teams, and enabling a controlled production cutover using feature toggles to minimise risk and downtime.
* Led the **extraction of the Rewards Service** from the monolith into a standalone service. I was responsible not only for implementation, but also for planning and coordinating the switch, setting up monitoring and alerting, and ensuring data consistency through idempotent operations and safe handling of distributed transactions.

#### Growth Areas
While I am happy with my technical impact this year, I see several areas where I can improve further:
* I would like to share architectural changes earlier, especially when they affect multiple teams, so that feedback and risks can be discussed sooner.
* I can improve my written documentation by making it more structured and by simplifying complex technical topics, so they are easier to understand for non-engineering stakeholders.
* At times, I focus deeply on solving complex technical problems. I would like to involve others earlier, especially when solutions could benefit from shared ownership or create learning opportunities for the team.

#### Final Summary
Overall, I believe I had a strong year with a clear impact on some of Zilch’s most important areas, particularly rewards, subscriptions, and fees. I delivered several complex changes safely in production, helped reduce operational and financial risk, and supported key business launches.
Going forward, I would like to focus on increasing my impact beyond delivery by improving cross-team communication, sharing knowledge more proactively, and contributing more to technical direction and design discussions. I am keen to continue working on high-impact, business-critical problems while developing stronger leadership and collaboration skills.

### My appraisal of Michal
#### Impact
Michal shows up as a very well-rounded engineer who couples solid engineering skills with many other competencies including good soft skills. He has shown himself to be conscientious and trustworthy. He actively looks for potential pitfalls and calls them out appropriately. He shows good judgement at complex decision points. He has been willing to muck in on less galmorous or more tedious tasks.

Michal regularly contributes suggestions for tweaks to the team's processes to help improve performance and contributes well in team meetings.

Where he lacks domain knowledge on an issue at hand he's proactive in bringing himself up to speed.

Michal has contrbuted significantly on many of the team's major projects through the year, notably providing a solid approach for fee service migration with good follow-through.

I would not have identified his chosen growth areas as concerns, and I read that as him proactively identifying learning opportunities before they surface as problems.

#### Growth Areas
Michal occasionally exhibits signs of imposter syndrome. I'd encourage him to recognise his strengths so that he can represent himself with greater confidence. This will matter as he grows his technical skills and experience: as he develops towards more senior roles he will need to be able to back his own judgement.

## Running Notes

### 1:1 — 2026-02-17

Final 1:1 before departing the Merchant team (moving 24 Feb).

- Discussed his year-end appraisal.
- Shared Andrzej's feedback on why he was selected for the new team: he thinks broadly with an entrepreneurial mindset, in contrast to others on the team who tend to be more narrowly focussed.
- How he's feeling about the move:
  - Excited for the new challenge, but anxious about the change.
  - Thinks Andrzej will be a demanding manager.
  - Has really enjoyed working on the Merchant team.

### 1:1 with Andrzej — 2026-02-16

Andrzej keen to have Michal on the new team for his breadth of vision and entrepreneurial nature. Thinks it will be a good counterpoint to others on the team who are more detail-oriented.

### Aurora / fee-service connectivity — 2026-02-12
- His hunch that the Dependabot AWS JDBC driver update caused the staging breakage proved correct.
- Raised two good process questions in the thread: (1) why didn't the regression/sanity tests catch this — suspects DB config differs between lower envs and staging/prod; (2) why didn't the Dependabot PR trigger a release-please minor version bump.

### Stand-up — 2026-02-12
- ZILCH-42041: still awaiting Platform to pick up a blocking task. Michal chased with them — situation unclear.
- ZILCH-46368: in progress, should be moving forward today.
- ZILCH-48303: in progress, would like to release today. High-priority ticket raised yesterday in response to a deployment that lacked a LaunchDarkly switch — rightly paused other work to address it.

### Stand-up — 2026-02-11
- ZILCH-39822 (add source IP to MDC in fee-service): in progress, status is In PR. Adding additional fields in log messages for distributed tracing.
