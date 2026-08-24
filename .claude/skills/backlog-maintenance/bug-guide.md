# Bug Guide

## Structural Expectations

- **Summary** — describes what's broken, briefly.
- **Description** — see content guidance below.
- **Parent Epic** — should belong to the epic of the feature being developed.
- **Sprint** — normally raised directly into the active sprint, not the backlog.
- **Labels** — should include at least one of `backend`, `frontend`, and `qa`.

## Content Guidance

### Purpose

A Bug is a lightweight communication mechanism. It is raised by QA during active development of a feature to log an issue found before release to production. The engineer working on the feature is expected to resolve it as part of the normal dev cycle.

Bugs should not normally appear in the backlog. They are raised into the active sprint and resolved within it. A Bug lingering in the backlog is almost always miscategorised — it is likely a Defect (if the behaviour is in production) or Tech Debt (if it's a quality concern rather than broken functionality).

### What to Include

- Steps to reproduce
- Expected vs actual behaviour
- Screenshots or evidence where helpful

### Acceptance Criteria

Formal acceptance criteria are not required for Bugs. The fix is self-evident from the description: the reported behaviour no longer occurs.

### When a Bug Is Something Else

- If the issue is in production → Defect.
- If it describes poor code quality rather than broken behaviour → Tech Debt.
- If it's requesting new functionality that was never specified → Story.
