# Incidents

This folder contains the Knowledge Base digests for incidents.

Each incident is represented by a subfolder named `incident-NNN/`, where NNN is the incident number.

Within the folder are markdown files relating to that incident, one of which MUST be the digest file named `log.md`.

## Digest File Structure

Each incident's `log.md` file is structured in a consistent way:

* REQUIRED H2 Heading **Status** — open or closed.
* REQUIRED H2 Heading **Summary** — brief description of what happened.
* OPTIONAL H2 Heading **Reference** — links to external PIR, Jira tickets, etc.
* OPTIONAL H2 Heading **Actions** — mitigation actions and their status.
* REQUIRED H2 Heading **Digest** — compacted from the main log.  Digest entries are grouped under H3 headings named for the date in **YYYY-MM-DD** format, and written in ascending chronological order.

## Content Guidance

Where a formal Post Incident Review exists in an external system (e.g. Confluence), treat that as the primary source.  The local file should be a thin record: a link to the PIR and a status tracker for mitigation actions.  Do not duplicate the PIR content here.

Where no external PIR exists (e.g. the incident is owned by another team that doesn't use Confluence), record the relevant detail directly in the file.
