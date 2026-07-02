# Story Guide

## Structural Expectations

- **Summary** — describes the value increment, not the implementation. Should be understandable to non-engineers.
- **Description** — must not be empty; see content guidance below.
- **Acceptance Criteria** — required; see acceptance criteria guidance below.
- **Parent Epic** — must belong to an epic.
- **Owned By** — must be set. For stories, the correct value is almost always "Product Initiative". Other permitted values are "Engineering Initiative" and "KTLO (Keeping the Lights On)", but these should be rare and warrant scrutiny — if the value isn't product-driven, consider whether the issue should be a Task instead.
- **Labels** — must include at least one of `backend`, `frontend`, and `qa`. The label should reflect the discipline(s) expected to work on the ticket. Multiple labels are permitted where more than one discipline is involved.

## Content Guidance

### User Story Framing

Stories must include an "As a... I want... so that..." statement:

> As a **[stakeholder]**, I want **[deliverable]** so that **[reason]**.

If the story cannot be naturally expressed in this form — or if the format feels forced — that is a strong indicator the issue is not really a story and may be better suited as a Task or Tech Debt item.

The "so that" clause must articulate genuine value, not restate the "I want".

### Background / Context

Stories should include a Background or Context section that explains the landscape in which the story delivers value. This helps readers understand *why* this increment matters without having to chase context elsewhere.

### Test Strategy

Stories must include a Test Strategy or Test Approach section. This may be "TBC" initially, but the section must be present as a prompt to fill out during refinement. The intent is to ensure test requirements are considered as part of refinement, not deferred until development is complete.

### Other Sections

Other sections may be included where they add value. Examples:

- **Implementation Notes** — the story should not be predicated on implementation, but notes that help engineers understand the landscape are welcome.
- **Out of Scope** — anything explicitly excluded to prevent scope creep or misunderstanding.

### Acceptance Criteria

All acceptance criteria must be deterministic and demonstrable.

Acceptance criteria must never merely restate the work to be done. They should describe how completion is demonstrated or verified — what "done" looks like, not what work to do.

There are two styles, used according to context:

1. **Given-When-Then (GWT)** — use for criteria that represent genuine test cases; those that should be considered for test automation or manual testing at the QA stage. See `gwt-format.md` for formatting requirements.

2. **Plain natural language** — use for criteria that confirm completion but are not meaningful test cases. These should still describe how completion is demonstrated, e.g. "Documentation reviewed and approved by comment on this ticket", "Design signed off by Product Designer".

Avoid bundling unrelated acceptance criteria. If they cluster into distinct domains, the story may want splitting.
