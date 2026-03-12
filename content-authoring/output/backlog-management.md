# Backlog Management

The source of truth for backlog management is the Confluence page: [Backlog Management](https://payzilch.atlassian.net/wiki/spaces/UN/pages/5095227469/Backlog+Management).

## Jira Cleanup Notes

Issues spotted while mapping the state machine to what's actually in Jira.

- **"Proposed" status**: Likely belongs to the Epic workflow, but some PBI-type tickets (e.g. ZILCH-47989, ZILCH-47936) are in this status. These should be moved to "Created" or the workflow should prevent PBIs from entering "Proposed".
- **EC tickets use a different workflow**: Statuses like "Planning", "Awaiting implementation", "Completed" don't appear on ZILCH tickets. May be a separate workflow for deployment tickets — worth confirming and excluding from the state machine if so.
- **Initiatives in PBI views**: ZILCH-36936, ZILCH-36939, and ZILCH-45705 are issue type "Initiative" but appear in "Created" status alongside PBIs. Consider using Jira filters or board configs to separate Initiatives from PBI backlog views so they don't muddy triage.
