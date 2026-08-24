---
name: backlog-maintenance
description: Maintain the Merchant team's Jira backlog — intake triage, hygiene checks, and funnel visibility
---

# Backlog Maintenance

## Purpose

Maintain the Merchant team's Jira backlog in a healthy, well-structured state. The skill identifies hygiene issues, assists with intake triage, and provides visibility of the intake funnel.

## Scope

- **Project:** ZILCH
- **Filter:** Team = "Merchant Team" (`customfield_10113`, option ID 10189)
- **Issue types:** Story, Task, Defect, Bug, Tech Debt, Spike
- **Applies to:** Non-complete tickets (`statusCategory != Done`)

## Key Custom Fields

| Field | ID | Type | Notes |
|---|---|---|---|
| Team | `customfield_10113` | Select | "Merchant Team" (10189) |
| Owned By | `customfield_10117` | Select | See Owned By section below |
| Acceptance Criteria | `customfield_10114` | Textarea | Separate from Description — always check here for ACs |
| Story Points | `customfield_10020` | Number | 0 = not estimated (prefer EMPTY). Genuine zero-point estimates exist but are rare. |

## JQL Queries

| Purpose | JQL |
|---|---|
| All Merchant PBIs | `filter = ".Merchant PBIs"` |
| Non-complete PBIs | `filter = ".Merchant PBIs" and statusCategory != Done` |
| The backlog (priority order) | `filter = ".Merchant PBIs" and statusCategory != Done and (sprint not in openSprints() or sprint is EMPTY) order by rank asc` |
| New | `filter = ".Merchant Workflow: New"` |
| Triaged | `filter = ".Merchant Workflow: Triaged"` |
| In Refinement | `filter = ".Merchant Workflow: In Refinement"` |
| Ready for Planning | `filter = ".Merchant Workflow: Ready for Planning"` |
| Planned | `filter = ".Merchant Workflow: Planned"` |
| Hygiene: Defects missing priority | `filter = ".Merchant Hygiene: Defects Missing Priority"` |
| Hygiene: Tech Debt missing priority | `filter = ".Merchant Hygiene: Tech Debt Missing Priority"` |
| Hygiene: Epics missing owner | `filter = ".Merchant Hygiene: Epics Missing Owner"` |
| Hygiene: Mismatched owners | `filter = ".Merchant Hygiene: Mismatched Owners"` |
| Hygiene: PBIs missing competency | `filter = ".Merchant Hygiene: PBIs Missing Competency"` |
| Hygiene: PBIs missing estimate | `filter = ".Merchant Hygiene: PBIs Missing Estimate"` |
| Hygiene: PBIs missing owner | `filter = ".Merchant Hygiene: PBIs Missing Owner"` |
| Hygiene: PBIs missing parent | `filter = ".Merchant Hygiene: PBIs Missing Parent"` |
| Hygiene: Bugs in backlog | `filter = ".Merchant Hygiene: Bugs in Backlog"` |
| Hygiene: Premature estimates | `filter = ".Merchant Hygiene: PBIs with Premature Estimate"` |

## Intake Detection

New tickets are announced in **#unicorn-agile** (channel ID `C084S7DA3V3`) by **Automation for Jira** (bot ID `B04T5V6M00K`).

Relevant message patterns:
- "A {type} ticket has been raised for the Merchant team." — new ticket created
- "A {type} ticket has been updated to be owned by the Merchant team." — ticket transferred in
- "{type} ZILCH-XXXXX has been moved from `Created` to `{status}` by {user}." — ticket transitioned out of Created

Other messages in the channel (sprint additions, epic creations, LinearB alerts) are not intake signals.

The skill uses a timestamp file at `./.claude/skills/backlog-maintenance/last-triage-timestamp.txt` to track what's been seen since last run. The file contains a single Unix timestamp (seconds). At the start of a triage run, capture the current time using `date +%s`. At the end of the run, write that captured value to the file. This ensures no gap between runs regardless of how long the triage takes.

### Bypass Detection

The #unicorn-agile channel also carries messages when tickets move from Created (format: "Issue \<link\> has been moved from \`Created\` to \`{status}\` by {user}."). When processing these:

1. **Validate gates:** Check the ticket meets the field requirements for its new status.
2. **Flag third-party transitions:** If the transition was made by someone other than the user, highlight it — not necessarily wrong, but the user wants visibility of everything entering the top of the funnel.

---

## The Intake Funnel

States reflect **readiness only**, not priority. Prioritisation is a separate axis.

| State | Jira Status | Description |
|---|---|---|
| NEW | Created | Just arrived. Untriaged. Needs first eyes. |
| TRIAGED | Ready for Refinement | Triaged: validated as belonging here, correct type, ownership set, priority set if applicable. |
| IN REFINEMENT | In Refinement | Being refined with the team: description, ACs, discussion. |
| READY FOR PLANNING | Ready for Development | Team happy, estimated. Available for sprint planning. |
| PLANNED | Ready for Development + sprint set | Picked up in planning. Assigned to a sprint and ready to go. |

### Field Requirements by State

**NEW — no field requirements.** This is the entry state. The criteria below are the gates for moving *out* of Created, not requirements for being in it.

**TRIAGED — gates from Created:**
- Parent epic
- Owned By set and satisfying constraints (see Owned By Constraints)
- Competency labels (`frontend`, `backend`, `qa`, or combination)
- Correct issueType (see Issue Type Rules)
- If Defect or Tech Debt: Priority set

**IN REFINEMENT — all of the above, plus:**
- Description written to standard (see guides in this folder)
- Acceptance Criteria written to standard (field `customfield_10114`, not Description)

**READY FOR PLANNING — all of the above, plus:**
- Story Points set (HARD REQUIREMENT — not 0, not empty)

---

## Prioritisation

Prioritisation is **separate from the funnel**. A ticket can be high-priority but not yet ready, or fully refined but low-priority.

- **Backlog ordering** = intended work sequence, reflected by rank position
- Informed by: severity (for Defects/Tech Debt), business deadlines, dependency sequencing, commitments to other teams
- Head of backlog should be strictly ordered; fuzzier further down
- **Priority field** = severity indicator, applies to Defects and Tech Debt only. Not the same as backlog position, though they should correlate.

---

## Issue Type Rules

| Type | Definition | Key signals |
|---|---|---|
| **Story** | Increment of value. Delivers a feature or new value that didn't exist before. | "As a... I want... so that..." framing works naturally. |
| **Task** | Enabling/supporting work with no independent value. Housekeeping, dependencies, infra changes. | LD flag creation, terraform update, DB column addition. Usually better inside a Story but split for sequencing. |
| **Defect** | Production not working as specified, or patently contrary to common sense. | Reported production behaviour contradicts spec or obvious expectation. |
| **Bug** | Issue found during development, pre-production. Logged by QA to communicate to engineer. | Should be resolved immediately during dev. Rarely lingers in backlog. |
| **Tech Debt** | Delta between current implementation and ideal design. System works but internals are suboptimal. | Refactoring, modernising, removing dead code, architectural improvement. |
| **Spike** | Work with no clear done state or stopping criterion. Timeboxed, not estimated. | "Learn as much as you can about X." The output is understanding, not a deliverable. If you can define "done", it's not a Spike. |

### Misclassification Flags

- **Bug in the backlog** — almost always miscategorised. Bugs are resolved during dev; if one lingers, it's likely a Defect or Tech Debt.
- **Defect describing unspecified behaviour** ("app doesn't support X" where X was never specified) — should be a Story. Support for foldable devices, for example, is a new feature if never specified.
- **Defect describing poor code quality** — should be Tech Debt. Works as expected but factored poorly.
- **Story that can't be expressed as "As a... I want... so that..."** — may be a Task or Tech Debt.
- **Task that delivers independent value** — should be a Story.
- **Task that addresses a quality delta** — should be Tech Debt.
- **Task that fixes something broken** — should be a Defect.

---

## Owned By

The `Owned By` field (`customfield_10117`) attributes capacity budget. It answers: which organisational unit's capacity is being spent?

| Value | Option ID | Meaning |
|---|---|---|
| Product Innovation | 10137 | Product-sponsored work. Anything done in service of a product-driven initiative — including enabling tasks, flag removal, legacy cleanup, etc. that form part of a product initiative's lifecycle. |
| Engineering Initiatives | 10164 | Engineering-sponsored work. Engineering-driven improvements not tied to a product initiative. |
| KTLO (Keep the Lights On) | 12099 | Neither org actively pursuing, but universally necessary. |

**Key principle:** a ticket's Owned By should match its parent epic's Owned By. A task to remove a feature flag after a product experiment is "Product Innovation" because it's part of that product initiative — even though the task itself doesn't deliver new value. Ownership follows the initiative, not the individual ticket's nature.

### Owned By Constraints

| IssueType | Expected Owned By | Flags |
|---|---|---|
| Story | Almost always "Product Innovation" | "Engineering Initiatives" → challenge. "KTLO" → **always wrong**. |
| Defect | Strong correlation with "KTLO" | Other values possible but less common. |
| Tech Debt | Follows who incurred the debt | Product stop-gap → "Product Innovation". Retroactive engineer-raised → typically "Engineering Initiatives". |
| Task | Any | No strong constraints. |
| Spike | Any | No strong constraints. |
| Bug | N/A (shouldn't linger in backlog) | If present, likely miscategorised entirely. |

Additional Tech Debt rules:
- Should include an explanation of why the code is the way it is (especially if raised after the fact)
- Ideally raised when incurred, placed in the originating epic
- Blanket-assumed as Engineering-owned without justification → flag

### Cross-Check: KTLO That Isn't a Defect

KTLO should be almost exclusively Defects. A non-Defect ticket owned by KTLO is suspicious — either the type or the ownership is wrong.

---

## Acceptance Criteria Standards

AC standards vary by issue type. The field is `customfield_10114` (separate from Description).

- **Stories** — GWT format for test cases; plain natural language for non-test confirmations. See `./resources/jira/gwt-format.md` and `./resources/jira/story-guide.md`.
- **Other types** — guides not yet written (`./resources/jira/` has placeholder files). Apply general principle: ACs must be deterministic and demonstrable, describing how completion is verified rather than restating the work.

---

## Invocation Modes

### 1. Intake Monitor

Triggered by: user request, or as part of a periodic check.

1. Read #unicorn-agile since the stored timestamp.
2. Produce report per `./templates/intake-monitor.md`.
3. Update the timestamp.

No Jira lookups — built entirely from Slack messages.

### 2. Triage Assessment

Triggered by: user request. Scope determined by the request (e.g. "triage the new arrivals", "triage the next 10 by rank", specific ticket keys).

1. Fetch tickets from Jira (using the appropriate filter or JQL for the requested scope).
2. Assess each ticket against the gates for Triaged (see Field Requirements by State).
3. Produce report per `./templates/triage-assessment.md`.
4. Ask for decisions.

### 3. Hygiene Scan

Triggered by: user request (periodic or ad hoc).

Run each hygiene filter and report any tickets returned:
- `.Merchant Hygiene: Defects Missing Priority`
- `.Merchant Hygiene: Tech Debt Missing Priority`
- `.Merchant Hygiene: Epics Missing Owner`
- `.Merchant Hygiene: Mismatched Owners`
- `.Merchant Hygiene: PBIs Missing Competency`
- `.Merchant Hygiene: PBIs Missing Estimate`
- `.Merchant Hygiene: PBIs Missing Owner`
- `.Merchant Hygiene: PBIs Missing Parent`
- `.Merchant Hygiene: Bugs in Backlog`
- `.Merchant Hygiene: PBIs with Premature Estimate`

Present results per `./templates/hygiene-scan.md`.

### 4. Targeted Check

Triggered by: user provides specific ticket key(s), epic, or JQL.

Run the same checks as the hygiene scan but against the specified subset. Useful for checking a specific epic's tickets or newly-refined work.

### 5. Funnel Visibility

Triggered by: user request.

Report the distribution of non-complete tickets across funnel states:
- Count per state
- New arrivals since last check (from #unicorn-agile)
- Tickets that may be stuck (in a state for an unusually long time — threshold TBD)

---

## Output

Each invocation mode has a template in `./templates/`. Follow the template for the mode being invoked.

After presenting findings, ask for instructions. Do not make changes to Jira — all output is advisory. The user will action changes manually or instruct further.

---

## Reference Material

- `./story-guide.md` — Story structure and content standards
- `./gwt-format.md` — GWT acceptance criteria format
- `./epic-guide.md` — Epic structure and scope standards
- `./defect-guide.md` — Defect structure and content standards
- `./task-guide.md` — Task structure and content standards
- `./tech-debt-guide.md` — Tech Debt structure and content standards
- `./bug-guide.md` — Bug structure and content standards
- `./intake-workflow.md` — Intake funnel definition
