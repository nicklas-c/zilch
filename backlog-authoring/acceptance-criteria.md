 # Acceptance Criteria Best Practices
## Formats
Acceptance criteria take one of two formats depending on the issue type.  See the PBI type table in ./CLAUDE.md for which format applies.
## General Principle
**Describe how you will know the work is done, not what the work is.**  An AC that restates the task is performative and adds no value.  Good ACs describe an observable, verifiable outcome.  For example: "Log messages are improved" is useless; "Transaction value is filterable in Datadog" tells you how to verify success.
### GWT (Given/When/Then)
Used for Stories and Defects.  Each acceptance criterion is a named scenario with Given, When, and Then clauses.
#### Principles
1. **One trigger per scenario.** Each scenario has exactly one "When" clause. This identifies the single action under test. Any preceding actions belong in "Given" clauses as preconditions.
2. **Declarative voice throughout.** Write what the system or user state *is*, not instructions to perform. "The user submits the form" not "Submit the form". Use active voice for Given and When clauses; use passive voice for Then clauses.
3. **Given clauses use present perfect tense.** Describes a completed state: "The user has logged in", "The basket has been emptied".
4. **When clauses use simple present tense.** Describes the triggering action: "The user clicks Submit", "The session expires".
5. **Then clauses use simple present passive tense.** Describes the expected outcome: "The confirmation page is displayed", "The error message is shown".
6. **Split compound clauses.** If a Given or Then contains "and", split it into separate clauses joined by "And". Each clause should assert one thing.
7. **When clauses are never compound.** Multiple actions in a When implies multiple triggers, which violates principle 1.
### Checklist
Used for Tasks and Tech Debt.  A bulleted list of conditions that must be met for the work to be accepted.  Each item should be a single, verifiable statement.
#### Principles
1. **One assertion per item.** Each bullet should be independently verifiable.
2. **Be specific.** "Logs are forwarded to Datadog" not "Logging is set up".
