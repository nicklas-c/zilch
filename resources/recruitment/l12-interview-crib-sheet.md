# Interview Crib Sheet — Engineering (L1 / L2)

**Purpose:** Standard question set and evaluation criteria for culture-fit / hiring-manager interviews. Role-specific probes (tech stack, domain concerns) should be tailored per candidate during interview prep.

**Format:** ~35–40 minutes of questioning. Pick 4–5 questions per session.

---

## 1. Motivation

**Question:** What drew you to software engineering, and what keeps you interested in it?

**Follow-up threads:**
- What's something you've built or worked on outside of work (or at university) that you're proud of?
- What kind of problems do you enjoy solving most?
- What does a good day at work look like to you?

**What to look for:**

| | L1 | L2 |
|---|---|---|
| **Strong** | Genuine enthusiasm grounded in something specific — not just "I like tech." Can describe what they enjoy about the craft. Evidence of self-directed learning or side projects. | Clear articulation of what energises them, informed by professional experience. Motivation aligns with the kind of work we'd give them. Shows agency — chose this path deliberately, not passively. |
| **Adequate** | Interested but can't go much deeper than "I like building things." Enthusiasm is present but undifferentiated. | Can describe what they enjoy but stays generic. Hasn't reflected much on what specific conditions help them thrive. |
| **Weak** | Can't articulate why engineering beyond "it pays well" or "it seemed like a good career." No evidence of curiosity. | Same as L1 weak. Or: motivation factors suggest they'd disengage from routine work (wants only novelty/greenfield). |

---

## 2. Learning

**Question:** Tell me about a time you needed to learn something new quickly to get a piece of work done. How did you go about it?

**Follow-up threads:**
- What resources did you reach for first?
- How did you know when you'd learned enough to start?
- What's something you've recently taught yourself outside of what was required?

**What to look for:**

| | L1 | L2 |
|---|---|---|
| **Strong** | Describes a structured approach — broke it down, identified sources, experimented, validated understanding. Didn't just follow a tutorial passively. Shows initiative in seeking out knowledge. Comfortable saying "I didn't know this." | All of L1, plus: can describe how their learning approach has matured. Distinguishes between learning enough to unblock themselves vs. building deeper expertise. May have helped someone else learn the same thing afterward. |
| **Adequate** | Has an example but the approach was fairly ad-hoc. Got there eventually but can't clearly articulate their method. | Has a good example but doesn't show evolution in how they learn. Relies on a single approach (e.g. always reads docs, never experiments). |
| **Weak** | Waited to be taught. Or: can't describe a specific example. Or: "I just Googled it" with no depth beyond that. | Same as L1 weak. Or: hasn't had to learn anything new recently — suggests a comfort zone. |

---

## 3. Curiosity

**Question:** How have you continued to learn since you finished your formal education?

*For candidates still at university or recently graduated, adjust to: "How do you learn outside of your formal curriculum?"*

**Follow-up threads:**
- What's the most recent thing you've learned? How did you go about it?
- How do you decide what to invest time in?
- Have you ever started learning something and abandoned it? Why?

**What to look for:**

| | L1 | L2 |
|---|---|---|
| **Strong** | Evidence of deliberate, self-directed learning beyond what's required by the job. Can name specific things they've pursued and articulate why. Shows genuine curiosity — learning isn't just career maintenance, it's something they enjoy. | All of L1, plus: shows judgement about where to invest — not just chasing every new framework but building depth in areas that matter. May have shared what they've learned with others. |
| **Adequate** | Has done some learning but it's reactive (e.g. only when a project required it) or unfocused. Can name something but can't articulate much about why or what they took from it. | Has continued learning but can't describe a strategy or pattern. Reads blogs or watches talks occasionally but can't recall specifics convincingly. |
| **Weak** | Has done nothing since finishing education. Or: claims to learn but can't name a single specific recent example. Or: learning is entirely passive (subscribed to a newsletter, never reads it). | Same as L1 weak. Also: relies entirely on the employer to provide training — no initiative to learn independently. |

---

## 4. Getting Stuck

**Question:** Describe a time you were stuck on a problem and couldn't make progress. What did you do?

**Follow-up threads:**
- How long did you wrestle with it before changing approach?
- Who did you go to, and how did you frame the question?
- What did you learn from it about how you work?

**What to look for:**

| | L1 | L2 |
|---|---|---|
| **Strong** | Tried specific things before asking for help. When they did ask, they framed the problem clearly — showed what they'd tried and where they were stuck. Took away something that changed their approach next time. | All of L1, plus: shows judgement about when to ask vs. when to persist. Frames help-seeking as efficient, not as failure. May have since helped others who were stuck on similar problems. |
| **Adequate** | Had a go before asking — even if the attempt was thin or not well articulated. Shows the instinct to try rather than immediately escalate. | Tried things and framed the question reasonably when asking for help, but doesn't show much evolution in how they handle being stuck. Still relies heavily on the same approach each time. |
| **Weak** | Sat stuck for days without asking anyone. Or: immediately escalated without attempting anything. Or: can't recall being stuck (suggests lack of self-awareness or never pushing beyond comfort zone). | Same as L1 weak. Also: frames being stuck as someone else's fault (unclear requirements, bad documentation) without taking ownership of unblocking themselves. |

**Watch for:** The quality of the question they asked matters more than whether they asked at all. "I'm stuck" is weak. "I've tried X and Y, I expected Z but got Q, I think the issue might be..." is strong.

---

## 5. Quality Mindset

**Question:** How do you make sure the code you write is correct before it reaches anyone else?

**Follow-up threads:**
- What's your process between "I think this works" and "I'm confident this works"?
- How do you decide what to test?
- *(L2)* Have you ever shipped something that turned out to be broken? What happened?

**What to look for:**

| | L1 | L2 |
|---|---|---|
| **Strong** | Has a personal workflow — doesn't just rely on CI catching things. Thinks about edge cases. Tests their own work before raising a PR. Can describe learning from a mistake. | All of L1, plus: thinks about quality beyond their own code — readability for reviewers, meaningful commit messages, documentation where needed. Starting to develop opinions about what "good" looks like for a team, not just themselves. |
| **Adequate** | Writes tests because they're expected to, but hasn't internalised why. Relies on code review to catch issues rather than self-checking. | Has good personal habits and can articulate the reasoning behind them, even if the reasoning is shallow or lacks subtlety. |
| **Weak** | No quality process beyond "I run it and see if it works." Or: treats testing as someone else's job. Or: has never shipped a bug (suggests either no production experience or lack of honesty). | Same as L1 weak. Also: dismissive of quality practices ("slows me down"). |

---

## 6. Collaboration & Communication

**Question:** How do you contribute to your team beyond your own tickets?

*For candidates straight out of university with no professional team experience, adjust the language to include any team-based context: group projects, hackathons, open source, etc.*

**Follow-up threads:**
- Can you give me a specific example?
- How do you know what your teammates are working on?
- *(L2)* Have you ever noticed a teammate struggling and done something about it?

**What to look for:**

| | L1 | L2 |
|---|---|---|
| **Strong** | Shows awareness of the team beyond their own work. Can give specific examples — helping someone, raising something in a retro, offering to pick up work, sharing something they learned. Engaged in the team dynamic, not just executing in parallel. | All of L1, plus: actively contributes to team effectiveness — notices patterns, offers help unprompted, builds on others' ideas. May have helped onboard someone or mentored a less experienced colleague. |
| **Adequate** | Participates in ceremonies and doesn't actively disengage, but contribution beyond their own work is limited or reactive (helps when asked, but doesn't initiate). | Contributes beyond their own work but in a narrow or inconsistent way. Aware of what others are doing but doesn't act on it much. |
| **Weak** | Can't give any example beyond their own work. Or: describes teamwork purely in terms of not blocking others. Treats the team as a collection of individuals working in parallel. | Same as L1 weak. Also: shows no awareness of or interest in what teammates are working on. |

---

## 7. AI Adoption

**Question:** Tell me about a time you rejected or significantly changed something an AI suggested. What was wrong with it and how did you know?

**Follow-up threads:**
- What advice would you give to an engineer who is not yet using AI to support their coding?
- What would you warn them about?
- If your AI tools went down for a week, what would change about how you work?

**What to look for:**

| | L1 | L2 |
|---|---|---|
| **Strong** | Gives a specific, credible example demonstrating they understood the code well enough to spot the problem. Can explain what was wrong and why — not just "it didn't work" but the reasoning. Shows that AI is a tool they use critically, not a crutch. | All of L1, plus: more nuanced view of where AI helps vs. hinders. Can describe patterns of failure they've learned to watch for. May have helped a peer develop critical habits around AI output. |
| **Adequate** | Has an example but the reasoning is shallow ("it gave me an error so I changed it"). Uses AI regularly but validation is mostly trial-and-error rather than understanding. | Can give an example with some reasoning, but doesn't show a developed sense of when to trust vs. question AI output. |
| **Weak** | Can't give an example — either doesn't use AI or has never questioned its output. Both are concerning: the first suggests disengagement from current tooling, the second suggests lack of critical thinking about code they're submitting. | Same as L1 weak. |

**Watch for:** Candidates who cannot describe writing code without AI, or who cannot explain the logic of code they claim to have authored. At L1/L2, you need to establish that AI is augmenting genuine understanding, not substituting for it. If they can't reason about what the AI produced — explain why it works, identify where it might fail — that's a fundamental concern regardless of how productive they appear.
