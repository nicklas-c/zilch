# Backlog Management

## Ticket Lifecycle

Tickets move through a defined set of states. Each state has assertions about what fields must, must not, or may be present. Jira statuses should reflect these states.

**Scope:** ZILCH project, product backlog items only (Stories, Tasks, Defects, Tech Debt). Epics and EC deployment tickets have separate workflows.

---

### CREATED

The entry state for all new tickets. No refinement has taken place.

**Jira status:** Created

| Field | Rule |
|-------|------|
| Team | MUST be "Merchant Team" |
| Story points | MUST NOT be set (not even zero) |
| Assignee | MUST NOT be set |
| Parent epic | MAY be set |
| Acceptance criteria | MAY be set |

### PRIORITISED

The ticket has been discussed in a pre-refinement meeting and its priority has been agreed. Tickets in this state should sit at the top of the backlog when ordered by Rank — when the backlog is hygienic, you can look down from the top and trust that all "Ready for Refinement" tickets are in strict priority order and have been selected as candidates for refinement.

**Jira status:** Ready for Refinement

| Field | Rule |
|-------|------|
| Team | MUST be "Merchant Team" |
| Story points | MUST NOT be set |
| Assignee | MUST NOT be set |
| Parent epic | MUST be set (and the choice must make sense) |
| Labels | MUST include function labels (`frontend`, `backend`, `qa`, or combination) |
| Owned By | MUST be set (`KTLO`, `Product Initiative`, or `Engineering Initiative`) |

### PREPARED

The ticket has been written up to standard and passes the readiness gate. Description and acceptance criteria are complete, and the ticket is queued for the next refinement session.

**Jira status:** In Refinement

| Field | Rule |
|-------|------|
| Team | MUST be "Merchant Team" |
| Story points | MUST NOT be set |
| Assignee | MUST NOT be set |
| Parent epic | MUST be set (and the choice must make sense) |
| Labels | MUST include function labels (`frontend`, `backend`, `qa`, or combination) |
| Owned By | MUST be set (`KTLO`, `Product Initiative`, or `Engineering Initiative`) |
| Description | MUST follow story-authoring guidelines |
| Acceptance criteria | MUST follow AC guidelines |

### REFINED

The ticket has been through refinement and estimated by the team. It is ready to be pulled into a sprint at planning.

**Jira status:** Ready for Development

| Field | Rule |
|-------|------|
| Team | MUST be "Merchant Team" |
| Story points | MUST be set |
| Assignee | MUST NOT be set |
| Parent epic | MUST be set (and the choice must make sense) |
| Labels | MUST include function labels (`frontend`, `backend`, `qa`, or combination) |
| Owned By | MUST be set (`KTLO`, `Product Initiative`, or `Engineering Initiative`) |
| Description | MUST follow story-authoring guidelines |
| Acceptance criteria | MUST follow AC guidelines |

### PLANNED

The ticket has been pulled into a sprint at planning. It shares the same Jira status as REFINED — the distinguishing factor is that the Sprint field is set.

**Jira status:** Ready for Development

| Field | Rule |
|-------|------|
| Team | MUST be "Merchant Team" |
| Story points | MUST be set |
| Sprint | MUST be set |
| Assignee | MUST NOT be set |
| Parent epic | MUST be set (and the choice must make sense) |
| Labels | MUST include function labels (`frontend`, `backend`, `qa`, or combination) |
| Owned By | MUST be set (`KTLO`, `Product Initiative`, or `Engineering Initiative`) |
| Description | MUST follow story-authoring guidelines |
| Acceptance criteria | MUST follow AC guidelines |

---

## Activities

The activities that move tickets between states.

### CREATED → PRIORITISED: Pre-Refinement Meeting

**Type:** Ceremony
**Attendees:** EM, Product Manager, QA Engineer

The Pre-Refinement meeting reviews the backlog, confirms that prioritisation is correct, and moves tickets to PRIORITISED. The EM should come prepared with a clear view of their own priorities, ready to trade off against product and quality priorities.

### PRIORITISED → PREPARED: Refinement Prep

**Type:** Async (EM)

The EM reviews prioritised tickets and ensures they are written up to standard — description and acceptance criteria complete and meeting the readiness gate. This is done in preparation for refinement meetings.

### PREPARED → REFINED: Refinement Meeting

**Type:** Ceremony
**Attendees:** Whole team

The team discusses and estimates prepared tickets.

### REFINED → PLANNED: Sprint Assembly

**Type:** Async (EM), with overlap in refinement and planning meetings

The EM continuously assembles a tentative sprint plan over the course of the sprint, pulling refined tickets into the upcoming sprint. Some of this may happen during refinement meetings. Sprint planning is the final opportunity to pull tickets in and ratify the plan, but the bulk of the work should already be done.

---

## Backlog Hygiene

**Backlog definition:** The backlog is everything not yet planned into a sprint.

**Ownership:** The Engineering Manager owns the backlog.

**Ordering:** The backlog should be kept in priority order, with strictness highest at the top and relaxing further down. Tickets near the top — those most likely to be refined and pulled into a sprint next — must be in strict priority order. Lower down, approximate ordering is acceptable.

**Size:** The backlog should be kept to a reasonable size. The ambition is to close more tickets than we open each sprint, so that the backlog trends downward over time.

**Ticket condition:** Tickets should be in an appropriate condition for their current state. The field rules in each state's table set the standard — a hygienic backlog is one where tickets consistently meet these standards.

**Planning readiness:** By the time sprint planning arrives, a plausible tentative plan should already exist — a candidate set of tickets selected and ordered — so that the planning session is about ratifying and adjusting, not building the plan from scratch.

---

## Field Usage

**Story points:** Where the rules state that story points MUST NOT be set, this includes zero. Jira defaults new tickets to zero points, which must be cleared. A zero value is ambiguous between "not yet estimated" and a genuine zero-point estimate — and the latter does occasionally arise.

**Assignee:** The Merchant team does not pre-allocate work. Engineers self-organise during the sprint, picking up work that is ready in real time. For this reason, the Assignee field should not be set at any point in the backlog lifecycle.

**Parent epic:** Every ticket beyond the CREATED state must belong to an epic. This is needed to understand which initiative a ticket contributes to, and it informs prioritisation and reporting.

**Labels:** Function labels (`frontend`, `backend`, `qa`, or a combination) indicate which disciplines are needed to deliver the ticket. The team has specialist engineers, not full-stack, so sprint planning must account for capacity per function.

**Owned By:** Indicates the source of demand: `KTLO`, `Product Initiative`, or `Engineering Initiative`. This is used for reporting, so we can see where our efforts are going across different demand streams.

---

## Jira Cleanup Notes

Issues spotted while mapping the state machine to what's actually in Jira.

- **"Proposed" status**: Likely belongs to the Epic workflow, but some PBI-type tickets (e.g. ZILCH-47989, ZILCH-47936) are in this status. These should be moved to "Created" or the workflow should prevent PBIs from entering "Proposed".
- **EC tickets use a different workflow**: Statuses like "Planning", "Awaiting implementation", "Completed" don't appear on ZILCH tickets. May be a separate workflow for deployment tickets — worth confirming and excluding from the state machine if so.
- **Initiatives in PBI views**: ZILCH-36936, ZILCH-36939, and ZILCH-45705 are issue type "Initiative" but appear in "Created" status alongside PBIs. Consider using Jira filters or board configs to separate Initiatives from PBI backlog views so they don't muddy triage.
