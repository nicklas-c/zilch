# Task Guide

## Structural Expectations

- **Summary** — describes the work to be done. Can be technical; the audience is the team, not stakeholders.
- **Description** — must not be empty; see content guidance below.
- **Acceptance Criteria** — required; see acceptance criteria guidance below.
- **Parent Epic** — must belong to an epic.
- **Owned By** — must be set. No strong constraints — Tasks can be any ownership value depending on context.
- **Labels** — must include at least one of `backend`, `frontend`, and `qa`.

## Content Guidance

### What and Why

Tasks are enabling or supporting work with no independent user-facing value. They exist to make other work possible or to perform housekeeping.

The description should explain:

1. **What** needs to be done.
2. **Why** — what it enables or what depends on it. A Task without a "why" is suspicious; it may be orphaned from its original context.

### Examples of Tasks

- LaunchDarkly flag creation or removal
- Terraform changes to support a feature
- Database column additions
- Dependency upgrades
- Configuration changes

### When a Task Is Something Else

- If it delivers independent user-facing value → Story.
- If it addresses a quality delta in the codebase → Tech Debt.
- If it fixes something broken in production → Defect.

### Acceptance Criteria

Acceptance criteria for Tasks should describe the completion condition — how you know the work is done. They are typically not test cases in the GWT sense, but confirmations:

- "Feature flag `xyz` exists in LaunchDarkly with targeting rules as specified."
- "Column `foo` present in production with backfill complete."
- "Terraform plan shows no diff after apply."

The criteria must be deterministic and demonstrable — not a restatement of the work.
