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
All log-related folders to be consolidated under `./kb/`, not `./logs/` as originally proposed. Rationale: the KB is a distinct functional area — information flows in, gets logged, gets compacted, and stays within its boundary. Other areas (content authoring, task management, etc.) consume the KB but never write to it. This clean partition earns a folder boundary. The root-level log file (`log.md`) lives at `./kb/log.md`.

```
./kb/
    log.md              (main log; currently ./logging/log.md)
    people/             (currently ./people/)
    projects/           (currently ./projects/)
    incidents/          (currently ./incidents/)
```

All other top-level folders remain as working areas (intake, playbooks, backlog-authoring, content-authoring). Root-level reference files (CLAUDE.md, people.md, jira.md, confluence.md) stay in place.

## Under Consideration

### Project file structure
Considered splitting project folders into discrete files (reference / context / digest). Rejected — keep it simple: one `log.md` per project. Can revisit if the single-file approach proves insufficient.

## Pending / To Calibrate

- **Compaction format**: Need to review sample compacted digests before committing to a standard. Risk of digests being either too sparse (losing useful context) or too verbose (effectively replicating the main log). Expect to iterate.
- **Switchover approach**: Proceed incrementally with the ability to back out. Not a big-bang migration.

## Log

### 2026-02-23 — Design session

Designed the new model during an evening session. All key decisions above agreed. Implementation deferred — estimated to be several hours of collaborative work including calibration of compaction output.

### 2026-03-09 — Further design; implementation started

Resumed the project with a view to beginning implementation this evening. Two further decisions made:

- **Project file splitting rejected.** One `log.md` per project. Keep it simple; revisit only if necessary.
- **`./kb/` folder adopted** in place of the previously proposed `./logs/`. The KB is functionally self-contained — information enters, is logged, and is compacted entirely within this boundary. Other system functions (content authoring, task management) consume it but never write to it. This makes it a clean partition deserving its own folder. `log.md` lives at `./kb/log.md`.

**Migration approach agreed:** full migration in a single session, done incrementally so that any failing step can be backed out without losing prior progress. The system will not be used for real during the transition.
