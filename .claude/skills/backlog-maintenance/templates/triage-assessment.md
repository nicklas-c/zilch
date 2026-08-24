# Triage Assessment Report Template

## Format

```markdown
## Triage Assessment

_N tickets assessed._

### Incomplete

Tickets missing required fields — cannot progress without changes.

| Ticket | Type | Summary | Missing | Also |
|---|---|---|---|---|
| [ZILCH-XXXXX](https://payzilch.atlassian.net/browse/ZILCH-XXXXX) | Tech Debt | Summary text | Priority | |
| [ZILCH-YYYYY](https://payzilch.atlassian.net/browse/ZILCH-YYYYY) | Defect | Summary text | Priority | Ownership may be wrong |

### Flagged

Required fields present, but something looks suspect against the guides.

| Ticket | Type | Summary | Concern |
|---|---|---|---|
| [ZILCH-ZZZZZ](https://payzilch.atlassian.net/browse/ZILCH-ZZZZZ) | Tech Debt | Summary text | Type may be Defect (incident-driven resilience failure); KTLO unusual for Tech Debt |

### No Issues Noted

Appears ready to progress based on available information.

| Ticket | Type | Summary |
|---|---|---|
| [ZILCH-AAAAA](https://payzilch.atlassian.net/browse/ZILCH-AAAAA) | Task | Summary text |
```

## Rules

- **Source:** Jira lookup on tickets in the New state.
- **Scope:** Determined by user request (e.g. "triage the new arrivals", "triage the next 10 by rank", "triage ZILCH-XXXXX"). Ask if unclear.
- **Incomplete:** Objective gate failures only — fields that must be present for Triaged but are missing or empty. The required fields are:
  - Parent epic
  - Owned By
  - Competency labels (frontend, backend, qa)
  - Priority (Defects and Tech Debt only)
- **Flagged:** Judgement-based concerns. Things that look suspect when assessed against the guides:
  - Issue type doesn't match the description
  - Owned By inconsistent with parent epic's ownership
  - KTLO on a non-Defect
  - Story that can't be expressed as "As a... I want..."
  - Bug lingering in the backlog
  - Any other misclassification signals from the skill's Issue Type Rules
- **No Issues Noted:** All required fields present, no obvious concerns. This is not a certification — it means nothing stood out, not that everything is definitely correct.
- **Single-listing rule:** Each ticket appears in exactly one section — the most severe that applies. Incomplete takes precedence over Flagged, which takes precedence over No Issues Noted. If a ticket has both a missing field and a judgement concern, list it in Incomplete and include the concern in the same row.
- **Empty sections:** Show the section heading with "None." beneath.
- **Tone:** Observations and recommendations, not directives.
