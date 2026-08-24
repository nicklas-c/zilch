# Defect Guide

## Structural Expectations

- **Summary** — describes the broken behaviour, not the fix. Should be understandable without reading the description.
- **Description** — must not be empty; see content guidance below.
- **Acceptance Criteria** — required; see acceptance criteria guidance below.
- **Parent Epic** — must belong to an epic.
- **Owned By** — must be set. Strong correlation with "KTLO (Keep the Lights On)". Other values are possible but less common — if the defect is in a system actively being worked on under a product or engineering initiative, it may belong to that initiative's ownership.
- **Priority** — must be set. This is a severity indicator and is required for defects at the TRIAGED state onward.
- **Labels** — must include at least one of `backend`, `frontend`, and `qa`.

## Content Guidance

### Expected vs Actual

Defects must clearly articulate:

1. **Expected behaviour** — what the system should do, per specification or common sense.
2. **Actual behaviour** — what the system currently does.
3. **Steps to reproduce** — how to observe the defect.

If the expected behaviour was never specified and the ticket is requesting new functionality, it is not a defect — it is a Story.

If the system works as specified but the implementation is suboptimal, it is not a defect — it is Tech Debt.

### Evidence

Where possible, include evidence: screenshots, logs, error messages, affected user counts, or links to monitoring dashboards. This helps prioritisation and aids the engineer fixing the issue.

### Impact

Note the scope of impact: how many users are affected, what functionality is degraded, whether there is a workaround.

### Acceptance Criteria

Acceptance criteria for defects should describe how the fix is verified — what the corrected behaviour looks like and how it can be demonstrated. They should be deterministic and testable.

Avoid restating the work ("fix the bug"). Instead describe the observable outcome: "Given [the reproduction steps], when [the action], then [the correct behaviour]."
