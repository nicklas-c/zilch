# Intake Monitor Report Template

## Format

```markdown
## Intake Monitor

_Since: {last_sweep_datetime} · Until: {current_datetime}_

### New Arrivals

| Ticket | Type | Summary |
|---|---|---|
| [ZILCH-XXXXX](https://payzilch.atlassian.net/browse/ZILCH-XXXXX) | Story | Summary text here |

_N tickets since last sweep._

### Bypasses

| Ticket | Type | Summary | Transition |
|---|---|---|---|
| [ZILCH-ZZZZZ](https://payzilch.atlassian.net/browse/ZILCH-ZZZZZ) | Defect | Summary text here | → Ready for Refinement by John Smith |

_N transitions by others since last sweep._
```

## Rules

- **Source:** Built entirely from #unicorn-agile Slack messages. No Jira lookups.
- **New Arrivals:** Messages matching "A {type} ticket has been {raised for / updated to be owned by} the Merchant team."
- **Bypasses:** Messages matching "{type} ZILCH-XXXXX has been moved from `Created` to `{status}` by {user}." — only include transitions by someone other than the user. The user's own transitions are excluded.
- **Empty sections:** Show the table header with "None." beneath.
- **Time window:** Converted from Unix timestamps using `date -r`.
- **Deduplication:** If a ticket appears multiple times (e.g. raised then transferred), show only the most recent message.
