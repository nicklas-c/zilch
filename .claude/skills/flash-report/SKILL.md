---
name: flash-report
description: Draft weekly flash reports for Merchant and DevOps teams, gathering context from Jira, Slack, and the knowledge base
---

# Flash Report

## Background

I'm required to provide a brief report each Friday summarising progress, status, risks, etc for each of my teams.  The reports are sent by Slack to a shared managers' channel especially for the reports and, occasionally, to Sean Hederman directly.  They're typically aggregated with other teams' reports and summarised for the next reporting level up.

This skill describes how to draft friday reports for me to review, tweak and send.

## Instructions

Reports for the Merchant team and DevOps team should be treated as separate exercise.  Separate reports for each, which can be generated independently.  However, unless otherwise stated, the action is to generate both reports.  In that case you should generate one and then the other in two separate passes.


1. Phase one is to gather as much information as possible about what has happened in the previous week.  Use the following sources:
   - **Jira**: Use the JQL queries listed in the `JQL Queries` section of this document to pull back relevant Jira issues.  Read the issue titles.  Also open them and read the descriptions in them.  If helpful, open the parent items to get epic-level context.
   - **Slack**:  Use the slack channel listed in the `Slack Channels` section of this document to get relevant messages.  Read back to the previous Friday (inclusively) for possibly useful information.  Also read the previous week's report from the #eng-management-weekly-reports channel for an idea of topics currently being tracked.
   - **Knowledge Base**: Get the logs from the previous week from `srkb`.
   - **User**: Ask the user, me, of anything I'm aware of from the previous week that might be relevant.
2. Phase two is to filter, categorise, and dedupe
   - Use judgement, context, and examples of previous reports to decide which pieces of information are candidates for inclusion.
   - Some activity will be noted in Slack, in the knowledge base, and in Jira.  Merge and dedupe.
   - Attempt to group the information into discreet categories.  Use Epics, known Projects, and previous reports as guidance on what categories might be relevant.
3. Phase three is to validate and refine.  Work through the categories one at a time.  For each:
   - Request any clarifications that might be needed
   - Propose the updates to include and seek changes, additions, or corrections.
4. Phase four is to generate a draft report
   - Use the example report in ./example.md as a guide to formatting.
   - Compare with the previous week's report to ensure that status-quo updates aren't presented as new information.
   - Generate a draft report in mardown format in the /temp folder off the project root.

## JQL Queries

### Merchant Team Queries

- This query brings back all the Jira issues closed in the last seven days: `filter = '.Merchant PBIs' AND statusCategory = Done AND status != Rejected AND statusCategoryChangedDate >= -7d`
- This query brings back all the Jira issues currently in progress; `filter = '.Merchant PBIs' AND statusCategory = 'In Progress'`

### DevOps Team Queries

- This query brings back all the Jira issues closed in the last seven days: `filter = '.DevOps PBIs' AND statusCategory = Done AND status != Rejected AND statusCategoryChangedDate >= -7d`
- This query brings back all the Jira issues currently in progress; `filter = '.DevOps PBIs' AND statusCategory = 'In Progress'`

## Slack Channels

### Merchant Team Channels

- #unicorn (The main private team channel)
- #support-merchant (A channel for others to request help from the team)
- #alert-merchant (A channel for automated alerts)
- #merchant-domain (A channel for merchant team and stakeholders)

### DevOps Channels

- #team-devops (The private team channel)
- #tech-devops (A channel for others to contact the team with technical queries)
- #platypus (A channel shared between the DevOps and the Platform team)
- #tech-on-call (A channel for operational annoucements and incidents) 