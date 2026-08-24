# Epic Guide

## Structural Expectations

- **Summary** — concise statement of the deliverable value; understandable without domain-specific jargon.
- **Description** — must not be empty; see content guidance below.
- **Productboard link** — should have a linked Productboard feature to maintain 1:1 mapping between epics and Productboard features.

## Size and Granularity

An epic is not defined by duration or effort. A tiny epic completed in less than a sprint is fine if it genuinely represents a stakeholder-visible unit of value. Conversely, "4–5 sprints of work" is not what makes something an epic.

The Jira hierarchy maps to audience, not effort:

- **Subtasks** — engineers' personal to-do lists; only engineers care about them.
- **PBIs** — the team's planning and tracking; engineers and engineering managers care about them.
- **Epics** — units stakeholders want to track. Engineers use them for context; engineering managers and stakeholders care about delivery.

## Endpoint and Scope

All epics must have a clearly defined endpoint — if you can't say "this epic is done when..." then it's not a well-scoped epic.

Bucket epics are acceptable only when their scope is explicitly bounded and locked. Once loaded with tickets, scope should not creep.

Good Examples:
- "Introduce spend limits" — clear feature, clear completion point.
- "Merchant Iteration 13 Tech Debt" — scoped bucket with a defined set of tickets; once loaded, scope is locked.

Bad Examples:
- "Tech Debt" — perpetual bucket with no endpoint and ever-growing scope.
- "Ongoing BAU maintenance" — reactive, no completion condition.
- "Improve checkout experience" — no defined endpoint; could absorb any number of UX improvements indefinitely.

## Content Guidance

A well-written epic should be easy to understand by anyone familiar with Zilch and its product. It should not assume prior knowledge of specifics, minimising ambiguity and providing a clear record of the work and its motives.

Consider including the following sections in the description where appropriate. Not all are required for every epic; the reviewer should suggest sections that would add value given the nature of the specific epic.

| Section | Purpose |
|---------|---------|
| Context or Background | Scene-setting information that helps readers understand the feature request |
| Description | Clear, concise description of the feature or work |
| Statement of Value | The value the epic will deliver, in business terms |
| Implementation Notes | Up-front thoughts on implementation — keep brief; the epic is not the place for full design documentation |
| Out of Scope | Anything that may be inferred as in-scope but isn't; useful for managing stakeholder expectations |
| Success Criteria | What success looks like — distinct from Acceptance Criteria (which belong on individual PBIs). An epic can meet all ACs but still fail its success criteria if the value isn't realised |
| Risks | Foreseen risks |
| Test Plan | Notes on testing approach if it differs from the norm |
| Roll-Out Plan | Notes on roll-out if non-standard |
| Deliverables | Explicit list — consider software releases, documentation, training, analytical metrics, operational metrics, and alerts |
