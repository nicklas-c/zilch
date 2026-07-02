# Given-When-Then Format Guide

This document defines the formatting requirements for acceptance criteria written in Given-When-Then (GWT) style. It is shared across all PBI types.

## When to Use GWT

Use GWT format only for acceptance criteria that represent genuine test cases — criteria that should be considered for test automation or manual testing at the QA stage.

For acceptance criteria that confirm completion but are not meaningful test cases (e.g. "Documentation reviewed and approved by comment on this ticket", "Design signed off by Product Designer"), use a plain natural-language statement instead.

## Structure

- **Given** — preconditions; the state of the world before the action under test.
- **When** — the single trigger or action under test. There must be one and only one `When` per criterion.
- **Then** — expected outcomes. Multiple `Then` clauses are allowed.

## Formatting Rules

- Strictly one clause per line.
- Use `And` for additional clauses within the same section (additional Givens or additional Thens).
- Never combine multiple clauses on a single line.

### One When Only

There must be exactly one `When`. It represents the single action under test. Any prior action is set-up and belongs in a `Given`.

The `When` must always be an active action performed by the actor — never a passive event or system response. The actor does something; the `Then` describes what happens as a result.

Bad:
```
When the search results are returned
Then semantic results are included
```

Good:
```
When I enter a search term with no blocked terms
Then the search results field is populated
```

Bad:
```
When I log in
And I press the submit button
Then the form is submitted
```

Good:
```
Given I am logged in
When I press the submit button
Then the form is submitted
```

### Tense and Voice

All clauses must be assertions, never imperatives.

- **Given** — past or continuous tense: "I am a...", "I pressed the button", "I have configured the spend limit".
- **When** — present tense: "I press the button", "I submit the form".
- **Then** — present or present perfect tense: "The receipt page is visible", "The click tracking event has been received".

Bad:
```
Given press the checkout button
When submit the payment
Then show the confirmation
```

Good:
```
Given I am on the checkout page
When I submit the payment
Then the confirmation screen is displayed
```

### Grounded Givens

`Given` clauses should be grounded in a specific actor and concrete context — they set the preconditions as test state. Avoid abstract or system-level conditions that don't map to observable, settable state.

Bad:
```
Given a user enters a query containing no blocked terms
And semantic search is eligible for that query
```

Good:
```
Given I am logged in as a fully-onboarded Zilch user
And I navigate to the search page
```

### Avoid Multiple Assertions in One Clause

Each clause should assert one thing. Don't sneak multiple assertions into a single line.

Bad:
```
Then the transaction is declined and a notification is displayed
```

Good:
```
Then the transaction is declined
And a notification is displayed
```

### Consistent Phrasing

Where possible, reuse the same phrase to express the same constraint across different acceptance criteria. Consistency aids readability and reduces ambiguity.

## Full Example

```
Given I am logged in as a merchant
And I have configured a spend limit of £100
When I attempt a purchase of £150
Then the transaction is declined
And a notification is displayed informing me that my spend limit has been reached
```
