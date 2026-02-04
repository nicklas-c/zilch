# Refinement Preparation

## Goal
Reduce time spent in refinement meetings from 3×1hr to 2×1hr per week while improving output so that sprint planning becomes a simple matter of checking dependencies and matching work to capacity.

## Phases

| Phase | Purpose | Who |
|-------|---------|-----|
| Before Pre-Refinement | Prepare backlog and identify priorities | EM |
| Pre-Refinement Meeting | Align on priorities and discuss candidates | QA, EM, PM |
| Between Pre-Refinement and Refinement | Gate tickets and notify team | EM |

---

## Before Pre-Refinement

- [ ] Check backlog hygiene — paying particular attention for any tickets that may have been prematurely dropped into future sprints.
- [ ] Identify my (EM) highest priority tickets for refinement

---

## During Pre-Refinement

Attendees: QA, EM, PM

- [ ] Each attendee shares their priorities
- [ ] Calibrate to decide overall highest priorities
- [ ] Adjust priorities in backlog as necessary
- [ ] Discuss highest priority tickets, adding clarifying details where necessary

---

## Between Pre-Refinement and Refinement

- [ ] Rewrite ticket descriptions and ACs into standard format according to guidelines
- [ ] Bring tickets up to standard to meet Readiness for Refinement (see gate criteria below)
- [ ] Move passing tickets to "Ready for Refinement" status
- [ ] Notify team of candidates for upcoming refinement so they can pre-review if they wish

### Ready for Refinement Gate Criteria

For a ticket to be Ready for Refinement:

- [ ] Has label(s) indicating functions required: `frontend`, `backend`, `qa` (or combination)
- [ ] Owner field filled: `KTLO`, `Product Initiative`, or `Engineering Initiative`.
- [ ] Story points field cleared.
- [ ] Description follows story-authoring guidelines.
- [ ] Acceptance criteria follow AC guidelines.
- [ ] Has a parent epic, and the epic choice makes sense.

### If a Ticket Doesn't Pass the Gate

1. Try to fix it yourself before refinement
2. If others are needed, resolve asynchronously
3. If that fails, drop from this refinement and bring back to next pre-refinement
