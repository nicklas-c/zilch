# Interview Crib Sheet — Engineering (L3 / L4)

**Purpose:** Standard question set and evaluation criteria for culture-fit / hiring-manager interviews. Role-specific probes (tech stack, domain concerns) should be tailored per candidate during interview prep.

**Format:** ~35–40 minutes of questioning. Pick 4–5 questions per session.

---

## 1. Motivation & Resilience

**Question:** Describe two real projects from your past career: the one you were most enthusiastic about — where you couldn't wait to get to work on a Monday morning — and the one you were least enthusiastic about, where getting out of bed was a real drag.

**Follow-up threads:**
- What specifically made the difference? Was it the people, the tech, the problem domain, the autonomy?
- What did you do to keep yourself productive through the tedious one?
- Did you try to change the situation, or adapt to it?

**What to look for:**

| | L3 | L4 |
|---|---|---|
| **Strong** | Clear self-awareness about what drives them. Found ways to stay productive through the tedious project — took learning opportunities from it, found by-product benefits (e.g. tidying tech debt along the way), or used tooling (including AI) to handle the monotonous parts. Motivation aligns with the kind of work we'd give them. | All of L3, plus: shows consideration for team morale, not just their own motivation. Aware of how their energy affects others and took steps to keep the team engaged, not just themselves. |
| **Adequate** | Can articulate the contrast but may stay surface-level (e.g. "the tech was boring"). Some evidence of agency. Motivations are not misaligned with Zilch engineering environment and culture. | Same as L3. |
| **Weak** | Blames external factors entirely. No evidence of taking ownership or adapting. Motivation factors suggest they'd disengage from routine operational work. | Same as L3. |

**Watch for:** Candidates whose "enthusiastic" project is purely greenfield/shiny-tech and whose "tedious" project is maintenance/operations — red flag for a role with significant operational responsibility.

---

## 2. Quality Mindset

**Question:** What approaches or techniques do you employ to ensure the features you deliver are of high quality?

**Follow-up threads:**
- How do you decide what level of testing is appropriate for a given change?
- How do you think about quality before code is written?
- How do you validate that something works correctly in production?
- Where does AI fit into your quality process?

**What to look for:**

| | L3 | L4 |
|---|---|---|
| **Strong** | Demonstrates quality thinking across the full SDLC — refinement, design, implementation, observability, production validation. Mentions specific practices beyond testing (e.g. feature flags for safe rollout, observability, design reviews, static analysis). Can articulate trade-offs between coverage and velocity. | All of L3, plus: thinks systemically — how quality practices scale across a team or function. May have introduced or championed quality frameworks. Talks about setting standards, not just following them. |
| **Adequate** | Covers testing well, mentions one or two non-testing practices (code review, readable code). May need nudging to think beyond the implementation phase. | Gives a solid individual-contributor answer but may not demonstrate shaping quality culture for others. |
| **Weak** | Only mentions testing, or gives a textbook list without depth. Can't articulate why they'd choose one approach over another. | Same as L3 weak. |

**Specific signals to probe:**
- Observability: Do they think about how they'll know something is broken in production?
- AI usage: Do they use AI for test generation, code review, or identifying edge cases? How do they validate AI-generated code?
- Beyond their own code: Do they consider quality practices for the broader delivery (infrastructure, design handoff, documentation, dependencies)?

---

## 3. Technical Leadership

**Question:** Tell me about a time you identified a significant technical problem or opportunity that wasn't on anyone's roadmap, and drove it forward. How did you build the case, get buy-in, and see it through?

**Follow-up threads:**
- How did you convince stakeholders it was worth the investment?
- What resistance did you encounter?
- How did you balance this with your existing commitments?
- What would you do differently if you had to do it again?

**What to look for:**

| | L3 | L4 |
|---|---|---|
| **Strong** | Identified a real problem (not invented one), articulated its impact, proposed a solution, and delivered it. May have needed some support from a senior to get buy-in, but did the legwork. Scope: within their team or a single system. | Identified a problem with cross-team or strategic impact. Built a compelling case independently. Navigated competing priorities and stakeholder politics. Brought others along — delegated, mentored, or influenced peers to contribute. Scope: across teams or the function. |
| **Adequate** | Was handed a problem and solved it well, showing initiative in the solution. Or: identified something but needed significant help driving it forward. | Shows genuine initiative and delivered something meaningful, but scope may have been limited to their immediate team or system rather than cross-team. |
| **Weak** | Can't point to an example, or describes something that was clearly assigned to them. Confuses "I had an idea" with "I drove it through." | Same. Also: takes credit for collective work without acknowledging others' contributions. |

**Watch for:** The difference between "I noticed this and told my manager" (fine for L3) and "I noticed this, wrote a proposal, got it prioritised, and led delivery" (expected for L4).

---

## 4. Navigating Ambiguity

**Question:** Describe a situation where you were given a problem with no clear solution or well-defined requirements. How did you go about structuring it?

**Follow-up threads:**
- How did you decide what to tackle first?
- How did you manage stakeholder expectations while the shape was still unclear?
- At what point did you feel confident enough to commit to an approach?
- Were there false starts? How did you course-correct?

**What to look for:**

| | L3 | L4 |
|---|---|---|
| **Strong** | Describes a structured approach: breaking the problem down, identifying unknowns, time-boxing spikes or experiments, communicating progress. Shows comfort with not knowing the answer upfront. Presented options with trade-offs and recommended a path. | All of L3, plus: guided a team through the ambiguity, not just themselves. Set direction, created frameworks or decision criteria that others could follow. Managed up — kept stakeholders informed and aligned without needing hand-holding. |
| **Adequate** | Made progress through a vague problem, possibly in a somewhat ad-hoc way. Got there eventually but may not clearly articulate their approach. | Structured it for themselves but may not have brought others along. Or: may have waited for clarity rather than creating it. |
| **Weak** | Froze, escalated immediately, or just started coding without thinking. Treats ambiguity as someone else's problem to solve. | Same as L3 weak. Also: claims to have "just figured it out" without evidence of method. |

**Watch for:** Candidates who've spent their career in well-structured environments (detailed Jira tickets, strong product management) may struggle here. Not disqualifying but worth probing — will they cope when requirements aren't handed to them fully formed?

---

## 5. Interpersonal / Challenge & Commitment

**Question:** Tell me about a time you disagreed with a technical decision. How did you handle it, and what was the outcome?

**Follow-up threads:**
- What was at stake?
- Did you escalate? At what point?
- Once the decision was made, how did you move forward?
- *(If they "won")* How did you bring the other person along?
- *(If they "lost")* Did you receive or seek feedback on how you handled it?

**What to look for:**

| | L3 | L4 |
|---|---|---|
| **Strong** | Raised the disagreement constructively. Articulated their position with evidence, not just opinion. Either influenced the outcome or committed to the decision and executed faithfully. Shows respect for the other party. Evidence of learning from the situation. | All of L3, plus: navigated a more politically complex situation (cross-team, senior stakeholders, higher stakes). May have mediated between others. Demonstrates "disagree and commit" at scale — rallying a team behind a decision they personally questioned. |
| **Adequate** | Has a relevant example but may not have pushed hard — raised a concern but deferred to seniority, or stayed fairly passive. | Raised the disagreement clearly and with evidence. May not have navigated significant political complexity or brought others along after the decision was made. |
| **Weak** | Can't give an example (suggests either conflict-avoidance or lack of technical opinion). Or: describes steamrolling someone without awareness. Or: clearly still bitter — hasn't committed. | Same. Also: frames every disagreement as "I was right, they were wrong" — lacks nuance. |

**Watch for:** The best answers show both willingness to challenge *and* ability to commit. If you only get one, probe for the other explicitly.

---

## 6. AI Adoption

**Question:** What advice would you give to an engineer who is not yet using AI to support their coding?

**Follow-up threads:**
- What would you tell them to try first?
- What would you warn them about?
- How has your own usage evolved since you started?

**What to look for:**

| | L3 | L4 |
|---|---|---|
| **Strong** | Gives specific, practical advice drawn from clear personal experience. Identifies concrete use cases (co-authoring code, code review, unfamiliar domains/languages, rubber-ducking design decisions). Articulates where AI needs to be held in check — hallucination, over-trust, context limits. Has clearly evolved their practice and can map the learning curve for someone else. | All of L3, plus: frames advice in terms of team effectiveness or engineering practice, not just personal productivity. May reference helping others adopt, establishing team guidelines, or how AI changes the way work is structured. |
| **Adequate** | Identifies several concrete use cases and can speak to limitations, but advice may stay at the practical/personal level. Knows where it helps and where to be cautious, but may not have thought much about it beyond their own workflow. | Solid personal adoption and awareness of pitfalls, but may not yet have a broader perspective on team adoption or changing practices. |
| **Weak** | Can't give meaningful advice because they haven't seriously used AI themselves. Or: gives only vague generalities ("try Copilot, it's useful") without specific use cases or caveats. Or: reveals uncritical adoption ("just accept what it gives you"). Or: dismissive ("I'd tell them not to bother"). | Same as L3 weak. |

**Watch for:** The best answers will naturally reveal the candidate's own workflow without being asked directly — they'll draw on specific experiences to form their advice. A candidate who gives abstract advice ("AI is the future, everyone should use it") without grounding it in their own practice likely hasn't gone deep. The key differentiator between strong and adequate is being able to talk about how their own usage has evolved — that shows learning, adaptation, and self-reflection.

---

## Cross-cutting: AI Usage

AI can also be woven into follow-ups across the other themes rather than (or as well as) using the standalone question above.

**Good entry points:**
- In Quality Mindset: "Where does AI fit into your quality process?"
- In Technical Leadership: "How are you using AI tools day-to-day? How has that changed your workflow?"
- In Navigating Ambiguity: "When you were exploring the problem space, did you use AI to help structure your thinking or prototype approaches?"
