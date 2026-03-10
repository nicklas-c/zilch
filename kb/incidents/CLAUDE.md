# Incidents Folder

One file per incident, named `incident-NNN.md`.

## Standard Structure

```
# Incident-NNN
## Status
## Summary
## Reference
## Actions
## Digest
```

## Content Guidance

Where a formal Post Incident Review exists in an external system (e.g. Confluence), treat that as the primary source. The local file should be a thin record: a link to the PIR and a status tracker for mitigation actions. Do not duplicate the PIR content here.

Where no external PIR exists (e.g. the incident is owned by another team that doesn't use Confluence), record the relevant detail directly in the file.

In all cases, the file should clearly indicate the incident's current status (open or closed) and the state of any mitigation actions.

Do not write to incident files during routine logging — use `kb/log.md` with an incident tag instead. Incident files are populated during compaction.
