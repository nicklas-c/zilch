# Tech Debt Guide

## Structural Expectations

- **Summary** — describes the target state or improvement, not just "refactor X".
- **Description** — must not be empty; see content guidance below.
- **Acceptance Criteria** — required; see acceptance criteria guidance below.
- **Parent Epic** — must belong to an epic.
- **Owned By** — must be set. Follows who incurred the debt: product stop-gap → "Product Innovation"; retroactive engineer-raised → typically "Engineering Initiatives". Should not be blanket-assumed as Engineering-owned without justification.
- **Priority** — must be set. This is a severity indicator and is required for Tech Debt at the TRIAGED state onward.
- **Labels** — must include at least one of `backend`, `frontend`, and `qa`.

## Content Guidance

### The Delta

Tech Debt represents the gap between how the system currently works and how it would work under its ideal design. The system functions — this is not about broken behaviour — but the internals are suboptimal.

The description must explain:

1. **Current state** — how the code works today.
2. **Ideal state** — how it should work.
3. **Why it's like this** — how the debt was incurred. This is important context, especially for debt raised after the fact.

### Origin and Timing

Tech Debt is ideally raised when incurred — placed in the originating epic so it's visible alongside the work that created it. Debt raised retroactively should still reference the originating context where possible.

### Ownership

Ownership follows the initiative that incurred the debt:

- A product feature shipped with a known shortcut → "Product Innovation" (the debt belongs to that initiative).
- An engineer identifies a longstanding structural issue → "Engineering Initiatives".
- Blanket-assumed Engineering ownership without justification is a flag.

### When Tech Debt Is Something Else

- If the system is broken (doesn't match spec or common-sense expectation) → Defect.
- If the work delivers new user-facing value → Story.
- If it's a one-off enabling task (not improving design quality) → Task.

### Acceptance Criteria

Acceptance criteria for Tech Debt should describe the target state — what "improved" looks like. They should be verifiable without reference to the implementation approach:

- "Service X responds to requests without calling deprecated endpoint Y."
- "No remaining references to legacy auth middleware in the codebase."
- "Test suite runs in under 3 minutes (currently 8)."

Avoid criteria that merely restate the work ("refactor the module"). Describe the observable outcome.
