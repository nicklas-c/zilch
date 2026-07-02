---
name: review-jira-issue
description: Reviews the contents and structure of a Jira issue and provides feedback and suggested edits
---

# Review Jira Issue

## Background

Jira is used heavily to manage backlogs and sprints.  Many people in different functions raise issues in Jira, and the quality of information can vary greatly, with different conventions favoured by different people.  This skill is intended to help standardise and improve our Jira issues by assisting with reviews.  Jira issues are often also referred to informally as 'tickets' or 'Jira tickets'.

## Resources

The folder `./resources/jira/` from the project root contains a set of `*-guide.md` files with specific guidance and best practice statements for each issue type separately.

## Jira Project

This skill will primarily be used to review Jira issues in the project `ZILCH`.

### Issue Types

The issue types covered by this skill are:

- **Epics** (`Epic`) - container-type issues that aggregate the work required to complete a stakeholder-level deliverable.
- **PBIs** - (Product Backlog Items) A category of types, rather than a defined type itself.  Individual work items prioritised on the team's backlog and planned into sprints. Including:
  - **Stories** (`Story`) - Increments of product value, including features and product improvements.
  - **Tasks** (`Task`) - Engineering tasks that don't directly map to new features or product improvements.
  - **Tech Debt** (`"Tech Debt"`) - Similar to a task, but specific to a noted piece of technical debt that needs to be paid down.
  - **Defect** (`Defect`) - A defect discovered in the product that needs to be remediated, including security vulnerabilities.
  - **Bug** (`Bug`) - A bug found during active development, used as a bug report from QA to engineers.

Other issue types are defined in the `ZILCH` project, but are not of interest for the purposes of this skill.  They include `Initiative` (for issues that aggregate Epics), `Subtask` (for issues that subdivide PBIs), and others.

## Instructions

- Use the Jira MCP connection to open the Jira issue.
- Assess whether the issue is of the most appropriate type using the guidelines below.
- Assess whether the issue should be split into multiple issues using the issue type indicators below. 
- If there is a reasonable chance that the issue type is wrong or it could be split, pause and ask the user before continuing.  **DO NOT** directly update the issue.
- Once issue type is established, read the relevant guidelines from a file in the `./resources/jira/` folder.  The file name will indicate the issue type it relates to.
- Assess the Jira ticket against the guidelines.
- Summarise your review.
- Suggest changes in a numbered list with brief justification for each.

## Issue Type Guidelines

The guidelines in this section are for determining correct issue type and whether an issue should be split. The resource files contain guidance on issue content, structure, and quality for each type.

### Epics

Indicators that an issue SHOULD be an Epic:
- It represents a deliverable at a level of granularity and abstraction that a stakeholder would care about.
- It is an MVP or incremental feature complete enough for customers to use.
- Epics may deliver technical value rather than product value.  In this case the stakeholder is a senior member of engineering staff.
- Its value is easy to express without reference to implementation details.


Indicators that an issue SHOULD NOT be an Epic:
- It represents a sequence of deliverables, each of which delivers substantial value to customer independently.
- It represents a deliverable that is too granular or implementation-specific to be of interest to a stakeholder.

Good Examples:
- Introduce the ability to apply spend limits
- Reduce app load times by at least 25%
- Provide operational dashboards for retailer-service

Bad Examples:
- Apply index to table for faster query results (too granular)
- UI Refresh including new design language, new flows across whole estate, refreshed assets, (several epics in one)

### Stories

Indicators that an issue SHOULD be a Story:
- It represents a small increment of product value.
- Its deliverable can easily be expressed in terms of value to the customer or business.
- Completion can be gated using a small number of acceptance criteria

Indicators that an issue SHOULD NOT be a Story:
- Its value is to Engineers or Operators
- Its value can't be expressed without reference to implementation details
- It represents several increments of value in one
- Its acceptance criteria clearly cluster into distinct domains, indicating potential to split

Good Examples:
- Make advertising space in receipt pop-up 
- Default fee to £2 in Admin Portal

Bad Examples:
- Remove LaunchDarkly switch (no direct value to business or customer)
- Introduce the ability for customers to apply spend limits (likely multiple increments: in-app configuration, application of cap, notification of cap being hit)

### Tasks

Indicators that an issue SHOULD be a Task:
- It captures an atomic piece of engineering work that can be delivered in isolation
- Its value is primarily to Engineers or Operators, for example improved maintainability, operability, observability, performance, security, etc.
- It is not in service of a Story for the SAME team.
- It is a technical change in service of a Story for a DIFFERENT team.

Indicators that an issue SHOULD NOT be a Task:
- Its value can be expressed in terms of changes to product behaviour or features.
- It cannot be delivered in isolation - systems will break without related changes.
- It consists of multiple changes that could be performed in isolation.
- It remediates a poor design choice or corner-cut.
- It addresses a production issue, failing test, security vulnerability, or known defect.

Good Examples:
- Remove LaunchDarkly switch.
- Apply index to table for faster queries
- Add API endpoint for Issuer team feature

Bad Examples:
- Patch security vulnerability
- Add API endpoint for Semantic Search (same team)
- Make 'OK' button respect dark mode (product value)

### Tech Debt

Indicators that an issue SHOULD be Tech Debt:
- It remediates a known shortcut, poor design choice, or architectural compromise
- The motivation is improving internal quality (maintainability, testability, coupling) rather than adding capability
- The debt is documented or widely acknowledged — it's not speculative cleanup

Indicators that an issue SHOULD NOT be Tech Debt:
- It's a bug or defect (observable incorrect behaviour) — use Defect
- It's a proactive improvement with no prior compromise to point to — use Task
- It bundles multiple unrelated debt items that could be addressed independently

Good Examples:
- Replace hand-rolled retry logic with resilience4j (original was a known time-pressure shortcut)
- Decouple payment-service from legacy shared schema

Bad Examples:
- Fix intermittent 500 on checkout (that's a Defect)
- Upgrade Spring Boot to latest (proactive improvement, no specific debt — Task)

### Defects

Indicators that an issue SHOULD be a Defect:
- There is observable incorrect behaviour in a production or production-like environment
- It describes a deviation from intended or documented behaviour
- It was discovered outside the context of active sprint development (e.g. by support, monitoring, or a user)

Indicators that an issue SHOULD NOT be a Defect:
- It was found during active development of the feature that introduced it — use Bug
- It describes a missing feature rather than broken behaviour — use Story
- It bundles multiple distinct defects that could be fixed and verified independently

Good Examples:
- Customers charged twice when retrying a failed payment
- Admin portal shows stale data after merchant updates trading name

Bad Examples:
- App crashes on Android 12 during QA testing of in-progress feature (Bug — found during active development)
- Add validation to prevent negative amounts (enhancement, not a defect in current behaviour)

### Bugs

Indicators that an issue SHOULD be a Bug:
- It was found during active development or QA testing of an in-progress feature
- It serves as a report from QA to the engineer(s) working on the feature
- It describes unexpected behaviour relative to the acceptance criteria or design of the current work

Indicators that an issue SHOULD NOT be a Bug:
- It was found in production or in previously-released functionality — use Defect
- It's a suggestion for improvement rather than a report of broken behaviour
- It requires a separate piece of work unrelated to the current feature — use Task or Defect

Good Examples:
- Dark mode toggle doesn't persist after app restart (found during QA of dark mode feature)
- Spend limit validation allows negative values (found during sprint testing)

Bad Examples:
- Checkout flow intermittently fails (production issue — Defect)
- Would be better if the button was bigger (enhancement suggestion, not a bug)

## Example Output

```
## Review: ZILCH-1234 — "Add retry logic to payment webhook handler"

**Current type:** Story
**Suggested type:** Task — the value is to engineers (resilience/operability), not directly to the customer or business. Recommend changing to Task.

**Split assessment:** No split needed. The scope is atomic and deliverable in isolation.

### Structural Review

1. **Acceptance criteria missing** — Task requires at least one concrete, verifiable criterion.
2. **Component not set** — Should specify the affected service (e.g. payment-service).
3. **Owned By** — Specifes `Product Initiative` but the issue looks like an `Engineering Initiative`.

### Content Review

The issue is reasonably well-structured but has gaps against the Task guidelines:

1. **Add a clear definition of done** — Currently there are acceptance criteria phrased in story format ("As a..."). For a Task, state the technical outcome directly (e.g. "Webhook handler retries up to 3 times with exponential backoff").
2. **Remove user-story framing** — "As a developer, I want..." is unnecessary for a Task. Lead with what needs to change and why.
3. **Specify scope boundaries** — Clarify whether this covers only the payment webhook or all webhook handlers, to prevent scope creep during implementation.
4. **Add context on the current failure mode** — Briefly describe what happens today (e.g. "single attempt; silent failure on timeout") so the engineer understands the baseline.
```

