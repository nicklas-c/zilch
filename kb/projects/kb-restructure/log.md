# Knowledge Base Restructure

A project to improve the knowledge base by moving from distributed, replicated logs to a single main log with tagging and periodic compaction.

## Decisions

### Model
- The main log (`./kb/log.md`) is the single source of truth. All entries go here.
- Secondary logs (people, projects, incidents) become **digests** — compacted summaries, not replicated logs.
- On-demand compaction: when requested, tagged entries in the main log are compacted into the relevant digest and removed from the main log. Git history serves as the archive.
- Compaction cadence: on-demand, with a quarterly recurring task as a reminder.

### Tagging
- Tags are standard markdown links with **relative paths**.
- Tags are identified by their path resolving into the `./kb/` subfolder structure. From within `./kb/log.md`, tags take the form `[Friendly Name](./people/slug.md)`, `[Project Name](./projects/project-slug)`, `[Incident Name](./incidents/incident-nnn.md)`.
- Projects are tagged by **folder**, not file — e.g. `[Merchant Operations](./projects/merchant-operations)`. This is consistent regardless of whether a project has one file or several. Folder links are supported in VS Code's markdown previewer.
- People and incidents are tagged by **file** as they are single-file entities.
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

### 2026-03-10 — Migration completed; tagging pass done

Migration completed across two sessions (2026-03-09 and 2026-03-10).

**Steps completed:**
- `./logging/` renamed to `./kb/`; all CLAUDE.md references updated.
- `./people/`, `./projects/`, and `./incidents/` moved inside `./kb/`.
- All cross-references in CLAUDE.md files, `people.md`, and project logs updated.
- Project folder structure retained (one `log.md` per project folder); project tags point to the folder rather than the log file.
- Tagging pass completed on `./kb/log.md`: all people, projects, and incidents referenced in the log have been replaced with markdown link tags. Several hundred replacements made across ~1,000 lines.

**Issues encountered during tagging:**
- One link-inside-backtick corruption (`audit-fee-service.md` filename) — caught and fixed.
- One nested link corruption (KB Restructure reference already linked; script double-linked it) — caught and fixed.
- `Phil Stevenson` had been consistently misspelled as `Phil Stephenson` across the log and project files — corrected throughout; people file renamed from `phil-stephenson.md` to `phil-stevenson.md`.
- A previous AI session had fabricated the surname "Slezak" for Stefan Amarie — corrected to `Stefan Amarie` throughout.
- Several people referenced in the log were not yet in `people.md` — added: Alastair Gullan, Nandini Muraleedharan, Paweł Wasielewski, Jakub Pałka, Jakub Zrebiec, Matt Garfitt.

**Pending / still to calibrate:**
- Compaction format: not yet validated. First compaction pass will establish the standard.
- A small number of references may remain untagged (names used in very peripheral contexts, or not yet identified). Acceptable — tagging is best-effort.
