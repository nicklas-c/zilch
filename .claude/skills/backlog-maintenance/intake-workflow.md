# Intake Workflow

## Overview

The intake workflow describes how tickets progress from arrival to sprint commitment. States reflect **readiness only** — prioritisation is a separate axis and can happen at any point.

## States

| State | Jira Status | Description |
|---|---|---|
| NEW | Created | Just arrived. Untriaged. Needs first eyes. |
| TRIAGED | Ready for Refinement | Validated as belonging here, correct type, ownership set, priority set if applicable. |
| IN REFINEMENT | In Refinement | Being refined with the team: description, ACs, discussion. |
| READY FOR PLANNING | Ready for Development | Team happy, estimated. Available for sprint planning. |
| PLANNED | Ready for Development + sprint set | Picked up in planning. Assigned to a sprint and ready to go. |

## Gates

Each transition requires the ticket to meet specific criteria. These are cumulative — each state inherits all requirements from the states before it.

### NEW → TRIAGED

- Parent epic assigned
- Owned By set (and consistent with the parent epic's Owned By)
- Competency labels applied (`frontend`, `backend`, `qa`, or combination)
- Correct issue type for the work described
- If Defect or Tech Debt: Priority set

### TRIAGED → IN REFINEMENT

- Description written to standard
- Acceptance Criteria written to standard (in the dedicated AC field, not the Description)

### IN REFINEMENT → READY FOR PLANNING

- Story Points set (not zero, not empty)

### READY FOR PLANNING → PLANNED

- Sprint assigned

## Prioritisation

Prioritisation is **orthogonal to readiness**. A ticket can be high-priority but not yet ready, or fully refined but low-priority.

- **Backlog ordering** = intended work sequence, reflected by rank position. Informed by: severity (for Defects/Tech Debt), business deadlines, dependency sequencing, commitments to other teams. The head of the backlog should be strictly ordered; fuzzier further down.
- **Priority field** = severity indicator, applicable to Defects and Tech Debt only. Not the same as backlog position, though they should correlate.
