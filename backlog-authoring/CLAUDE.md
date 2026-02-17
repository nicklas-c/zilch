# Backlog Authoring
We will use this folder to collaborate on writing and improving backlog items including Epics, and PBIs.
## Structure
* **CLAUDE.md** — This file.  Workspace instructions.
* **epics.md** — Standards document for writing Epics.
* **acceptance-criteria.md** — Standards document for writing acceptance criteria.
* **output/** — All authored backlog item files go here, one markdown file per item, named by Jira key (e.g. `ZILCH-48444.md`).

Output is always markdown.
## Standing Instructions
* When working on an existing Jira ticket, always read the full ticket first — including any existing description, acceptance criteria, and other fields — before drafting.  Use existing content as a starting point rather than writing from scratch.
## Jira Issue Types
The following Jira issue types are worth knowing.
### Epics
Epics are containers that group PBIs into deliverables that stakeholders track.  I have no objection to small Epics with only one or two PBIs.  Epics should usually correspond directly to a deliverable in the iteration plan.  I don't like open-ended Epics used as a bucket for things like bugs and defects.  I allow one 'bucket' Epic in each iteration for BAU work, and close it at the end of the iteration.

I have a standards document for well-written Epics that you should consult when working on Epics in ./epics.md
### PBIs
Product Backlog Items are units of work from the point of view of refinement, estimation, and sprint planning.  They include the following issue types:

| Issue Type | Description | Acceptance Criteria |
|---|---|---|
| **Story** | A new feature or behaviour change. | GWT scenarios per ./acceptance-criteria.md |
| **Task** | Non-user-facing work (config, migrations, documentation, etc.). | Checklist per ./acceptance-criteria.md |
| **Defect** | Something in production behaving incorrectly. | GWT scenarios per ./acceptance-criteria.md |
| **Tech Debt** | Refactoring or improvement without user-facing change. | Checklist per ./acceptance-criteria.md |
| **Spike** | Timeboxed investigation to reduce uncertainty. | No ACs.  Specify a timebox and a defined output. |

I have a standards document for well-written acceptance criteria in ./acceptance-criteria.md
### Sub tasks
I don't work with subtasks, I consider these to be the preserve of individual engineers and allow them to use sub tasks as a kind of personal to-do list on any given PBI.