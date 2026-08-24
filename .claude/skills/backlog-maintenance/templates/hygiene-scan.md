# Hygiene Scan Report Template

## Format

Present results as a single table with one row per filter. All filters are always shown, including those with zero breaches.

| Filter | Count | Tickets |
|--------|------:|---------|
| Defects Missing Priority | {n} | {linked ticket IDs, comma-separated} |
| Tech Debt Missing Priority | {n} | {linked ticket IDs} |
| Epics Missing Owner | {n} | {linked ticket IDs} |
| Mismatched Owners | {n} | {linked ticket IDs} |
| PBIs Missing Competency | {n} | {linked ticket IDs} |
| PBIs Missing Estimate | {n} | {linked ticket IDs} |
| PBIs Missing Owner | {n} | {linked ticket IDs} |
| PBIs Missing Parent | {n} | {linked ticket IDs} |
| Bugs in Backlog | {n} | {linked ticket IDs} |
| Premature Estimates | {n} | {linked ticket IDs} |

## Rules

- Zero-count rows show `0` and `—` in the Tickets column.
- Ticket IDs are hyperlinked: `[ZILCH-XXXXX](https://payzilch.atlassian.net/browse/ZILCH-XXXXX)`
- Multiple tickets in a cell are comma-separated.
- No commentary, no additional sections. The table is the report.
