# Interview Prep — Neli Hargeliya

**Role:** L4 Back-end Engineer | **Location:** Vilnius | **Pattern:** Fully remote
**Key consideration:** Must demonstrate the experience, seniority, and temperament to work autonomously alongside a team with much more in-person contact.

---

## Part 1: Pre-read

### Candidate Summary

Neli Hargeliya — Senior Backend Java Engineer, 10 years' experience, currently based in Vilnius. Her entire recent career (Aug 2019–present, ~7 years) has been at EPAM Systems, a large outsourcing/consultancy firm, where she's been placed on client projects for major brands: Zalando (payments, ML platform), Expedia (risk/security), Schneider Electric, LSEG, and most recently Travel + Leisure. Before EPAM, she led a small team at a Belarusian telco.

Tech stack is a strong fit: Java 21, Spring Boot, Kafka, AWS (SQS, ECS, EKS), PostgreSQL, Kubernetes, event-driven microservices. Payment-domain experience at Zalando is directly relevant to fintech. She emphasises production ownership, observability, and security — all useful.

Salary expectation (€83k) and notice period (~4 weeks) are both reasonable. Location matches.

### Signals

**The consultancy model is the dominant pattern here.** Seven years at EPAM across 7+ client placements, each lasting 3–23 months. This shapes everything:

- **Strengths it implies:** Fast ramp-up on unfamiliar codebases, adaptability, delivery within defined scope, comfort with new teams and contexts. She's likely good at "parachuting in" and being productive quickly.
- **Weaknesses it implies:** Consultancy work is typically well-briefed — you're placed on a team, given a remit, and expected to execute. Long-term strategic ownership, operating in ambiguity, and self-directed prioritisation are often less developed. The question is whether she's been a consultant who delivers to spec, or one who shapes direction.

**The CV language skews toward execution, not influence.** "Built", "developed", "maintained", "designed" — strong IC verbs but not L4 leadership verbs. Missing: "proposed", "advocated", "influenced the roadmap", "set the technical direction for". The one genuine leadership example (Team Lead at Velcom, team of 9) is from 2017–2019 — seven years ago and in a very different context.

**Short recent tenures.** The last four placements were 3, 7, 6, and 6 months respectively. This may simply be the nature of EPAM engagements, but it raises a question: has she had the runway to own anything long-term, see consequences of her architectural decisions, or build something she's accountable for over a sustained period?

**"Owned end-to-end" needs calibrating.** She uses ownership language (Mako: "Owned account and membership services end-to-end"; Zalando: "Owned the full software delivery lifecycle") — but what does ownership mean in a consultancy context where you're placed on the team for 6 months? Is this "I was the sole engineer responsible" or "I participated in the full lifecycle"?

**Mentoring and interviewing are positives** — 20+ technical interviews, active mentor at EPAM. This shows inclination toward seniority beyond individual output.

**No explicit evidence of remote/autonomous working patterns.** EPAM is distributed, so she's likely worked remotely, but the consultancy structure provides its own scaffolding (defined engagements, client stakeholders setting direction). The specific challenge here — working autonomously alongside a co-located team without drifting into isolation — is untested on paper.

**Belarusian background, now in Lithuania** — a common relocation pattern in the region. Not a concern, just context.

### What to Explore

- **L4 vs strong L3:** The CV presents an excellent senior IC. You need to find evidence of influence beyond her own code — shaping team practices, driving technical strategy, getting buy-in for ideas that weren't handed to her. If every answer is "I built X well," that's L3.
- **Operating without a brief:** Consultancy engagements come with scope. Probe for situations where she defined the problem, not just solved it. How does she behave when nobody's written the Jira ticket?
- **Long-term ownership and consequence:** With recent placements of 3–7 months, test whether she's had to live with her decisions. Has she maintained a system she designed? Dealt with the downstream consequences of an architectural choice?
- **Remote autonomy specifically:** How does she stay connected, visible, and aligned with a team she's not physically co-located with? How does she handle the information asymmetry that remote workers face against in-office teams? Does she over-communicate or disappear?
- **Why leave EPAM / why this role:** After 7 years in consultancy, what's drawing her to a permanent product role? Is it genuine desire for ownership, or pragmatic (stability, salary, location)?

---

## Part 2: During the interview

---

**Describe a situation where you were given a problem with no clear solution or well-defined requirements. How did you go about structuring it?**

- Push past "the requirements were unclear so I clarified them with the client" — that's normal consulting hygiene, not ambiguity
- Look for an example where *she* decided what to build, not where she clarified what someone else wanted
- Probe: in your EPAM placements, how much of the problem definition was done for you vs. by you?
- If she struggles: how would she operate in a product team where the backlog isn't fully formed and the PM expects engineering to co-own the "what"?

---

**Tell me about a time you identified a significant technical problem or opportunity that wasn't on anyone's roadmap, and drove it forward.**

- The CV claims quantified improvements (30–40% incident reduction, 80% false positive reduction) — were these self-initiated or assigned?
- Specifically: did she write a proposal, get it prioritised, and lead it? Or was she asked to fix the thing?
- How did she build the case when the client or team hadn't asked for it?
- On a 6-month placement, the incentive to drive long-term improvements is low — did she do it anyway?

---

**Tell me about a time you disagreed with a technical decision. How did you handle it, and what was the outcome?**

- As a consultant, disagreeing with the client's technical direction carries political risk — probe whether she's willing to challenge when the power dynamic isn't in her favour
- Look for: does she commit after the decision, or withdraw effort?
- Test whether she can rally others around a decision she questioned — critical for a remote L4 who won't always get their way

---

**Describe two real projects: the one you were most enthusiastic about, and the one you were least enthusiastic about.**

- With 7+ placements, she has genuine range to draw from — press for specifics about *why*
- If the "enthusiastic" project is greenfield/novel and the "tedious" one is maintenance: flag this against a role with operational responsibility
- Probe: after 7 years of rotating placements, what is she looking for in a permanent role? What does she think she'll gain — and what might she miss?
- Does her answer suggest she'll thrive with sustained ownership, or does she need novelty?

---

**What approaches or techniques do you employ to ensure the features you deliver are of high quality?**

- She lists testing tools extensively and claims incident reduction — validate depth vs. breadth
- Push into: how does she ensure quality when she's remote and can't lean over to a colleague for a quick review?
- Does she think about quality *culture* (setting standards for a team) or just personal practice?
- AI usage: where does it fit in her workflow? Does she validate AI-generated code or trust it?
