# Knowledge Base

## Purpose
Maintain a chronological record of events and a curated record of achievements. `log.md` is the single intake point — all events, observations, notes, and decisions are logged here first, tagged, and remain here until explicitly compacted. After compaction, the full picture of any entity spans both the relevant digest file and the main log.

## Role of AI

Your role is to:
* Write new entries to `log.md` when anything significant is reported — events, observations, thoughts, decisions, and more.
* Apply tags to entries as you write them (see Tagging below).
* When requested, perform compaction (see Compaction below).

You should not:
* Write to digest files (`people/`, `projects/`, `incidents/`) or `activity.md` except during an explicit compaction.

You should also:
* When a task is removed from `tasks.md` because it has been completed, log the completion in `log.md` under today's date.

## Tagging

Tags are standard markdown links with relative paths. They identify entities so that entries can be found and compacted later.

### Tag formats (from within `kb/log.md`)
* **People:** `[Full Name](./people/slug.md)`
* **Projects:** `[Project Name](./projects/project-slug)` — link to the folder, not the log file
* **Incidents:** `[Incident-NNN](./incidents/incident-nnn.md)`

External and absolute URLs are plain links and are not treated as tags.

### Granularity
* A tag in a heading applies to all content under that heading until the next heading of equal or higher level.
* A tag on a top-level bullet applies to that bullet and all sub-items.
* A tag on a standalone line applies to that line only.

### Coverage
* Tag every named person, project, and incident on first mention in each entry. Repeated mentions within the same heading scope do not need re-tagging, but it is acceptable to tag them.
* Entries do not need to be exhaustively tagged — peripheral references (e.g. a person mentioned in passing) can be left untagged at your discretion.

## Compaction

Compaction is performed on demand, not automatically. Its primary purpose is to keep `log.md` manageable as it grows.

When compaction is requested:
1. Check for uncommitted changes in the repository. If any exist, prompt to commit before proceeding — compaction is a destructive operation and git history is the only recovery path.
2. A cut-off date is agreed. All entries in `log.md` up to and including that date are candidates.
3. For each tagged entity (person, project, incident) with entries in scope, write a compacted digest to the appropriate file in `people/`, `projects/`, or `incidents/`.
4. Separately, perform a second compaction pass over the same raw candidate entries, this time compacting into `activity.md`. This pass is independent — the selection criteria and framing differ from entity digests. The question to answer is: what did I do, achieve, or decide that is worth recording for self-appraisal?
5. Remove the compacted entries from `log.md`.
6. Git history serves as the archive — nothing is permanently lost.

The format for compacted digests is still being calibrated. The first compaction pass will establish the standard.

## Structure

### log.md
* The main chronological log — the single intake point for all events.
* Organised in descending date order (newest first).
* H2 headings for the date, H3 headings for events or contexts (e.g. "Stand-up", "1:1 with X").
* Bulleted lists of entries under each heading.
* Everything goes here first. Opinions, observations, and commentary are all welcome.

### activity.md
* A record of meaningful actions and achievements.
* Used for self-appraisal, reporting, and answering "what have I achieved?"
* Populated systematically during compaction — not manually curated or updated in real time.
* Organised in descending date order (newest first).
* H2 headings for the date; bulleted lists of noted activities.

### people/
* One file per person, named by slug (e.g. `firstname-lastname.md`).
* Digest files only — populated during compaction, not during routine logging.

### projects/
* One folder per project, named by slug (e.g. `project-name/`).
* Each folder contains a `log.md` and optionally reference files.
* Digest files only — populated during compaction, not during routine logging.

### incidents/
* One file per incident (e.g. `incident-001.md`).
* Digest files only — populated during compaction, not during routine logging.

## Reading Back

When answering questions about a person, project, or incident — e.g. "where do we stand with project X?" or "what's the latest on person Y?" — build the complete picture from two sources:
1. The relevant digest file in `people/`, `projects/`, or `incidents/` (compacted history up to the last compaction).
2. The main `log.md`, scanning for tagged entries relating to the entity (recent history not yet compacted).

Neither source alone is sufficient. The digest may be stale; the log holds the latest entries.

## Formatting Conventions
* Log entries should be factual and concise — who, what, which ticket.
* Activity entries should be written as assertions in the past tense.
