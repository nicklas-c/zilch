# Knowledge Base

## Purpose
The Knowledge Base, containing structured chronological records comprising:
* A log file
* Index files organised around entity types
* Digest files organised around a set of well known entities.

### Entity Types
* Projects
* People
* Incidents

## Structure
This folder and its subfolders contain markdown files that make up the body of knowledge in the knowledge base.

### CLAUDE.md
This file.

### log.md
* The main chronological log — the single intake point.  When new information is commited to the knowledge base, it is written here.
* Organised in descending date order (newest first).
* H2 headings for the date, H3 headings for events or contexts (e.g. "Stand-up", "1:1 with X").
* Bulleted lists of entries under each heading.
* Opinions, observations, commentary, decisions, notes on activity and events are all welcome.

### activity.md
`activity.md` is a digest of my own actions, activities, and achievements.  It's primary purpose is for use when reflecting on achievements and growth areas for tasks such as writing self-appraisals.

* A record of meaningful actions and achievements.
* Used for self-appraisal, reporting, and answering "what have I achieved?"
* Populated systematically during compaction — not manually curated or updated in real time.
* Organised in descending date order (newest first).
* H2 headings for the date; bulleted lists of noted activities.
* Activity entries should be written as assertions in the past tense.

### Entity Files
Each entity type is represented by an index file and a corresponding folder.  The folder contains one subfolder per entity, each named by slug (e.g. `people/nick-holt/`).  Each entity subfolder contains a `log.md` digest and optionally other reference files.  For example, the entity type `people` has the index file `people.md` and the folder `people/`, which contains subfolders like `people/nick-holt/log.md`.

## Role of AI
When working in the Knowledge Base you should start by reading the `log.md` file and all the index files for entity types to familiarise youself with recent events and the known entities.

Your role in the Knowledge Base is well defined:
* To write to the knowldge base when anything significant is reported, even minimally significant.
* To read from the knowledge base to help me answer questions like "Where have we got to with project X?", or "What are some talking points for a 1:1 with person Y?"
* When explicitly requested, to compact the log into the digest files to prevent the main log from becoming unmanageably large.

### Writing to the Knowledge Base
* Write new entries to `log.md` when anything significant is reported — events, observations, thoughts, decisions, and more.
* Apply tags to entries as you write them (see Tagging below).
* You should not write to digest files (e.g. `people/`, `projects/`, `incidents/`, or `activity.md`) except during an explicit compaction.
* When an entry appears to reference an entity that is not known to you from the index files, you should prompt me to provide information about it and then write it into the relevant index file.
* You do not need permission to write to the `log.md` file.  If in doubt whether a comment is significant enough to be recorded, err on the side of logging it.  The log should be as complete as possible; compaction will remove trivial or unnecessary information.

### Reading from the Knowledge Base
* Read from the knowledge base freely.  For example, when answering requests for information, or to get context for other tasks.
* When collecting in formation on a specific entity, read the digest for that entity and the log file.  The picture is not complete without both: the digest contains historical information and context; the log provides more recent updates.  For example, to provide a status report on a project, you should read the project digest and the log.

### Compacting the Knowledge Base
Compaction is performed on demand, not automatically. Its primary purpose is to keep `log.md` manageable as it grows.

When compaction is requested:
1. Check for uncommitted changes in the repository. If any exist, prompt the user to commit before proceeding — compaction is a destructive operation and git history is the only recovery path.  Do not commit yourself, this is a privileged action: I will manage git.
2. A cut-off date is agreed. All entries in `log.md` up to and including that date are candidates.
3. For each tagged entity with entries in scope, write a compacted digest to the appropriate file in in the entity folders.
4. Separately, perform a second compaction pass over the same raw candidate entries, this time compacting into `activity.md`. This pass is independent — the selection criteria and framing differ from entity digests. The question to answer is: what did I do, achieve, or decide that is worth recording?
5. Remove the compacted entries from `log.md`.
6. Git history serves as the archive — nothing is permanently lost.


## Tagging

Tags are standard markdown links with relative paths. They identify entities so that entries can be found and compacted later.

### Tag formats (from within `kb/log.md`)
* **People:** `[Full Name](./people/slug)` — link to the folder, not the log file
* **Projects:** `[Project Name](./projects/project-slug)` — link to the folder, not the log file
* **Incidents:** `[Incident-NNN](./incidents/incident-nnn)` — link to the folder, not the log file

External and absolute URLs are plain links and are not treated as tags.

### Granularity
* A tag in a heading applies to all content under that heading until the next heading of equal or higher level.
* A tag on a top-level bullet applies to that bullet and all sub-items.
* A tag on a standalone line applies to that line only.

### Coverage
* Tag every named person, project, and incident on first mention in each entry. Repeated mentions within the same heading scope do not need re-tagging, but it is acceptable to tag them.
* Entries do not need to be exhaustively tagged — peripheral references (e.g. a person mentioned in passing) can be left untagged at your discretion.
