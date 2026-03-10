# Phil Stevenson

## Context for AI
DevOps Engineer in the DevOps team, graded at Level 4, equivalent to senior-to-lead level.  He is based in London.  Acts as de facto tech lead in the DevOps team.

## Year-End Appraisal

### His self-appraisal

#### Achievements
A big win this year was my role in helping services get their code tested and released automatically and independently, moving us closer to true continuous deployment. This shift has enabled smaller, safer releases and significantly reduced the time spent on risky, manual deployments.

I also did the groundwork for our new ephemeral development environments. The system is now built and almost ready for developers to start using, which will let them spin up a clean environment whenever they need one. A nice side effect is that this work has already forced us to clean up a lot of our service configurations. In the meantime, I am also helping prepare a 'static' ephemeral environment to give development teams a place to start testing against the latest services sooner.

I spent more time working directly with the backend teams, getting hands-on with their Java projects and tools. Even though Java isn't my preferred language, being closer to their work helped me get up to speed and meant we could solve problems faster together.

Finally, I contributed to a roadmap for our team to give us a clearer sense of direction and help us decide what to work on next. I led by example, pushing for good quality work and building tools that make other engineers' lives easier.

#### Growth Areas
The biggest opportunity I see is how we work together as a team. The change in management this year has affected our team's rhythm. Since our manager has limited availability, they can't be involved in all the day-to-day details, but we're also not self-managing in the same way we were before. To me, it feels like this has created a gap that slows down decisions and sometimes lets things fall through the cracks. The challenge now is to find a good middle ground, a way for the team to feel empowered to run with the day-to-day work, while knowing exactly when and how to pull in our manager for guidance or to get unblocked.

On a personal level, I am making it a priority to define my role with more clarity. I will take the initiative to figure out if my time is better spent on architecture and setting standards, or on building things. Establishing a clearer focus for myself is a key action I will own to improve my effectiveness.

Building on the successful collaboration I had with the backend teams, I see an opportunity to improve how I engage with other parts of engineering. At times, it can be challenging to get the help or responsiveness needed on cross-team issues, which can slow down progress. I will get better at building these partnerships across the company. This means being more proactive in communicating what our team is working on, taking the time to understand the priorities of other teams, and finding common goals so we can tackle shared problems more effectively together.

My focus will also be on rebuilding trust in our release and test process. When things are flaky, it's frustrating and slows everyone down. I will improve our testing strategy by pushing for more unit and integration tests, especially for parts of the system that are difficult to test end-to-end. A top priority will be improving our test coverage at build time, which means actively fixing or removing flaky tests and, where it makes sense, replacing them with more reliable integration tests. Looking further ahead, I plan to contribute to creating a workflow orchestrator to bring a greater level of automation to the entire development lifecycle.

Finally, I will continue focusing on improving the overall developer experience and tooling. The goal is to reduce friction in the development lifecycle and make it easier for engineers to build, test, and ship code with confidence.

#### Final Summary
I am proud of the tangible progress made this year, particularly in automating releases, advancing ephemeral environments, and deepening collaboration with backend teams. These foundations have already made our delivery safer and more predictable.

Looking ahead, my primary focus is to help optimise our team's operating model. I want to establish a rhythm that empowers the team to self-manage day-to-day execution while effectively utilising our manager's guidance when needed. This will help us regain speed and ensure clear ownership.

I will also work to define my role with greater clarity, allowing me to focus on high-impact areas like improving the developer experience and extending cross-team partnerships. To support this, I would value having a clear progression framework in place. As the company expands, having a plan ready for how our team structure and individual roles will evolve will ensure we are prepared to scale effectively.

By prioritising the full automation of our release and testing processes, enforcing clear infrastructure standards, and driving quicker decisions, I am confident we can turn our current operational challenges into a strength. This focus will allow us to scale our platform effectively and deliver a seamless experience for the engineering team.

### My appraisal of Phil

#### Impact
Phil is a strong performer who has had a great year in terms of impact.

His commitment to doing things the right way continues to be a significant strength: Phil knows what good looks like and cares to advocate for it, while being willing to compromise where that's pragmatic.  

Phil works hard, with an admirable ability to balance competing threads of work.  His self appraisal identifies several projects he has contributed on, but undersells the bredth of his contribution.  For example, he makes no mention of his contribution to the FinCrime team, which was considerable and handled while staying involved in other DevOps work.

He has provided good high-level thought leadership during conversations on a roadmap for the team, identifying some key deliverables.

#### Growth Areas
Phil has shown a good instinct for thinking about process and how the team operates. I'd encourage him to develop that further by identifying and proposing practical solutions - he's well placed to help shape how we work.

Phil is already seen as the de facto tech lead for the team. As a development opportunity, I'd encourage him to consider ways he can raise his visibility as a direction-setter more broadly across the organisation.

## Digest

### 1:1 — 2026-02-18

**How is he?**
- OK overall.
- Still frustrated by the pace and pivots at Zilch — everything gets done in a rush.
- Concerned that quality inevitably suffers, even without knowingly cutting corners. The combination of context switching and time pressure erodes quality.
- Aware of the latest EWA pivot (new ask to deliver EWA tied to a new membership tier by end of March, discussed at Engineering Leadership Sync on 17 Feb).
- Doesn't like it — feels it moves Zilch into payday lending territory, which he sees as morally questionable and at odds with the company's 'looking out for the little guy' positioning.

**What's keeping him busy?**
- Fraud work — reacting to an uptick in fraud cases that the FinCrime team are rushing to deal with. Consistent with pattern noted in his appraisal: FinCrime support is a significant draw on his time.

**New operating model**
- Optimistic about the operational changes. Thinks the structure will help.
- In retrospect, it would have helped to keep Piotr on piste with his recent ZOE work. (Aligns with Nick G's feedback on Piotr submitting large code without iterative review.)
- Will be good to protect people not on the support rota from getting pulled into reactive work.
- Will give good visibility of what's coming through.
- Suspects a lot of reactive work the team does never gets ticketed. More rigour should mean more ticketed work and therefore better visibility.

**Actions from the meeting** (not assigned — I'll take them and either action or delegate):
1. Look at automation so that Slack requests for help can easily be turned into reactive tickets.
2. Get the rotation tag set up and stop using OpsGenie for the rotation. (Firefighter tag already on my to-do; OpsGenie cessation is new.)
3. Lean in on where we stand with debugging Zephyr Zero.

### 2026-03-03

Flagged via Slack that engineers working on the EWA project (including Radek Kachel) are handling work that would normally go through DevOps, and are showing reluctance to engage via the tech-devops channel or take suggestions on PRs. Phil is supportive of them doing the work — his concern is that it's not being done properly through the right process. He suspects the cause is external pressure. Consistent with his self-appraisal observation that cross-team engagement can be difficult. Agreed to discuss further at tomorrow's 1:1 (4 Mar).

Also asked for sign-off on ZILCH-45505 (mass update of pr-validate workflow across all GitHub repos via script). Piotr approved; Nicklas deferred pending more context — to discuss at 1:1 before proceeding.

### 2026-03-09 — DevOps Retro

During discussion of more managed work intake, Phil pushed back on formalising the process. His concern was not analytical but emotional: he described informal, responsive working as 'nice', and felt that a more constrained process would put up barriers and undermine his ability to be helpful. He did not offer a structural counter-argument.

This is a recognisable pattern — closely parallels Alex Murphy's attitude early in my tenure managing the Merchant team. Alex had been at the company for years by that point but held the same view (felt it was nicer to respond to requests directly and have autonomy to do what felt right), and eventually adapted to working within a more structured process and visibly matured as a result. In his exit interview, Alex reflected positively on the change, drawing explicit contrast with Rory Fielding who continues to work in an uncontrolled fashion.

The Alex parallel may be worth drawing on in a future 1:1 with Phil — not as a lecture, but as a concrete example of growth that Phil would recognise.

*AI observation:* The question of whether Phil is a people-pleaser is worth holding as an open hypothesis. His attachment to informal responsiveness appears values-level — he describes it as 'nice', suggesting it's tied to his sense of identity and what makes work meaningful, rather than anxiety about standing. This is distinct from Lukasz's people-pleasing, which appears confidence-driven (linked to his awareness of being the most junior team member). However, Phil also finds conflict with cross-team engineers stressful and needed a venting session in his 1:1 on 4 Mar — the combination of "I want to be seen as helpful" with "I find friction hard" does carry a people-pleasing quality worth monitoring. An open question: is Lukasz modelling on Phil? If Lukasz sees Phil being warmly received for informal responsiveness, he may emulate the surface behaviour for his own reasons, even if the underlying drivers differ. Watch for whether Lukasz defers to Phil explicitly or mirrors his attitudes in team discussions — if Phil is functioning as Lukasz's template for "what good looks like", then shaping Phil's process discipline matters more than it otherwise would.

### 1:1 — 2026-03-04

Largely a venting session. Phil needed to express concerns rather than seek specific actions.

**Quality:** Less acute than flagged. Phil successfully pushed back on Radek Kachel's changes as a codeowner and got the outcome he wanted. Quality in hand.

**Radek pattern:** The substantive concern is a recurring pattern of poor communication and cooperation from Radek — bypassing proper channels, reluctance to act on PR feedback. Nicklas will raise with Grzegorz Ziemiański and Nikos Sofianos as a light-touch inquiry about observed friction rather than a formal escalation.

**Unrealistic expectations on DevOps:** Phil perceives a persistent assumption that DevOps delivers on demand. Some historical basis to this. Advised: lean into the formalised process — use sprint records and Jira to evidence reactive pull-in when work slips; use the Kanban board and WIP limits to show requesters they're in a queue; escalate genuine reprioritisation decisions to me.

**ZILCH-45505 — mass pr-validate workflow update:** Discussed and placed on hold. Phil's concern is that a batch update across repos could be perceived as circumventing PR review processes, and he doesn't want to be criticised for it. Confirmed that I will approve it when the time comes and he can use that as cover if the approach is questioned.

**Observation:** Phil finds friction with cross-team engineers stressful, particularly when quality feels at risk. Noted that some friction is natural and productive — engineers are under delivery pressure; DevOps want things done properly. Phil understands this intellectually but still finds it hard in practice. Worth keeping an eye on his stress levels in this area.

**1:1 agenda items for 4 Mar:**
- EWA project / DevOps engagement process
- ZILCH-45505 — mass pr-validate workflow update: get more context before sign-off
- EWA capacity pressure on DevOps — same-day tickets surfacing (ZILCH-49094, 49091), Phil's concern about quality impact; George Sharpe chasing directly

**Prep notes for EWA capacity discussion:**

The four DevOps-assigned EWA tickets from George's Slack message:
- ZILCH-48967 (Lukasz, Ready for Testing) — WireMock deployment to SDE dev/staging; supports service mocking for integration testing
- ZILCH-48966 (Lukasz, In Dev) — RBAC update to grant QA access to SDE dev/staging environments
- ZILCH-49091 (Phil, Ready for Dev, created today) — Crossplane config for SQS/SNS on SDE; reactive ticket
- ZILCH-49094 (Unassigned, Ready for Dev, created today) — RDS Proxy deployment to non-prod sensitive environments; reactive ticket

The two Lukasz tickets are progressing fine. The two new ones were created today by Phil, labelled reactive, and were already being chased by George on the same day — which validates Phil's point entirely.

EWA only came into existence around 17 Feb with a 31 Mar deadline. There was no runway for infrastructure planning. The DevOps team is absorbing the cost of that.

**Questions to draw out from Phil:**
- Why is EWA using the SDE environment? It doesn't appear to be fully stood up yet (WireMock, RBAC all being added now). Other dev environments exist — what drove the choice?
- Is EWA effectively finishing off the SDE environment setup as a side effect, and if so, is that understood by the EWA team?

**Approach for the meeting:**
Lead with quality concerns — let Phil vent and get it on the table before forming a view on whether action is needed or reassurance is sufficient. Do not pre-plan the bridge to the communication conversation; that depends on what comes out of the quality discussion.

### 2026-02-18
* Worked with Nick Gilbert to resolve deployment issues — IP exhaustion and RBAC permission problems blocking releases. Also helped with DLQ replay (250k messages) and various PR approvals/deployments across teams.

### 2025-02-04 — 1:1

**Appraisal feedback discussion**
- Discussed the feedback I had written for him — he agreed it aligned well with his own take.

**On the tone of his self-appraisal**
- I made the point that I'm open to constructive feedback, but using the appraisal as a channel to escalate wasn't appropriate — it looks undiplomatic.
- He asserted he was trying to be constructive, not damaging, but acknowledged my view that the channel wasn't the right one.
- He didn't say whether he agreed, but acknowledged and respected my perspective.

**Discussing the perceived gaps**
- We discussed at length where he thinks the gaps are and what has changed since I took line management.
- He struggled to put his finger on anything specific.
- Couldn't identify much that has changed since I took over, except that the team also lost Kevin Came's involvement as scrum master.

**Path forward**
- I shared my view that if I'm going to lean in to the gaps, I'll need the team to work in a more structured fashion.
- Proposed adopting a hybrid kanban/scrum model: scrum for planned work, kanban for reactive work.
- Also: more discipline around scrum, and aligning sprints with other engineering teams.
- Phil seemed very open to trying this.
- Agreed we would discuss with the rest of the team, but I already have a strong view on what needs to happen.
