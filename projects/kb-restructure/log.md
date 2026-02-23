# Knowledge Base Restructure

A project to improve the knowledge base by moving from distributed, replicated logs to a single main log with tagging and periodic compaction.

## Decisions

### Model
- The main log (`./logs/log.md`) is the single source of truth. All entries go here.
- Secondary logs (people, projects, incidents) become **digests** — compacted summaries, not replicated logs.
- On-demand compaction: when requested, tagged entries in the main log are compacted into the relevant digest and removed from the main log. Git history serves as the archive.
- Compaction cadence: on-demand, with a quarterly recurring task as a reminder.

### Tagging
- Tags are standard markdown links with **relative paths** and `.md` file extensions.
- Tags are identified by their path resolving into the `./logs/` subfolder structure. From within `./logs/log.md`, tags take the form `[Friendly Name](./people/slug.md)`, `[Project Name](./projects/slug.md)`, `[Incident Name](./incidents/incident-nnn.md)`.
- External and absolute URLs are plain links and are not treated as tags.
- Entity types (for now): **people**, **projects**, **incidents**.

### Granularity (implied scope)
- A tag placed in a heading applies to everything under that heading until the next heading of equal or higher level.
- A tag placed on a top-level bullet applies to that bullet and all sub-items beneath it.
- A tag on a standalone line applies to that line only.

### File Restructure
All log-related folders to be consolidated under `./logs/`:

```
./logs/
    log.md              (main log; currently ./logging/log.md)
    people/             (currently ./people/)
    projects/           (currently ./projects/)
    incidents/          (currently ./incidents/)
```

All other top-level folders remain as working areas (intake, playbooks, backlog-authoring, content-authoring).

## Under Consideration

### Project file structure
Currently each project has a single `log.md` containing all information (aliases, context, personnel, running notes). An alternative under consideration is splitting each project folder into discrete files by purpose:

- **reference** — personnel, aliases, key links. Small and stable.
- **context** — background, objectives, decisions. Changes occasionally.
- **digest** — compacted activity log. Replaced periodically by compaction.

This would allow targeted file reads — e.g. answering "who is involved?" without loading months of running notes. Aligns naturally with the compaction model, where the digest is the compacted output and reference/context are maintained separately. Trade-off: more files per project.

## Pending / To Calibrate

- **Compaction format**: Need to review sample compacted digests before committing to a standard. Risk of digests being either too sparse (losing useful context) or too verbose (effectively replicating the main log). Expect to iterate.
- **Switchover approach**: Proceed incrementally with the ability to back out. Not a big-bang migration.

## Log

### 2026-02-23 — Design session

Designed the new model during an evening session. All key decisions above agreed. Implementation deferred — estimated to be several hours of collaborative work including calibration of compaction output.
