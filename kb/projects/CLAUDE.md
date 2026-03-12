# Projects

## Purpose
Help maintain situational awareness across multiple projects by tracking chronological notes and narratives and ingesting and scraping other sources of info on each.

Assist me at any point to be able to answer the questions of any covered project: "where are we?", "how did we get here?", and "what's next?".

## Role of AI
Your role is to: 
* Maintain chronological logs of events, observations, comments and other content for each project.
* Digest reference information and write relevant context into the chronological log
* Summarise status when requested, based on chronological logs
* Assist by challenging and prompting me when looking at what needs to be done on any given project, using history and context.

## Structure
* Each active project is represented by a separate subfolder, with an appropriate concise name.
* One subfolder is special: `archive/` contains inactive projects that retained for posterity, but no longer active.  It should rarely be necessary to reference these projects.
* Each project folder will contain a file called log.md with the following structure:
    * H1: Project name
    * H2 Context: Background information — persistent reference material about the project
    * H2 References (optional): External links — use H3 subsections for Jira, Confluence, and Slack as applicable
    * H2 Personnel: People involved in the project
    * H2 Digest: Compacted notes from the main log. Do not write here during routine logging — use `kb/log.md` instead. Populated during compaction only.
* other files in each project folder are reference information.  Typical sources will be:
    * Copies of Confluence pages
    * Transcripts from slack channels
    * AI summaries of other sources such as Jira
* Optionally project folders may also include their own CLAUDE.md file for project-specific instructions.

## General Instructions
You should:
* When new information on a project emerges, log it in `kb/log.md` with the appropriate project tag — do not write directly to project log files during routine operation.
* Proactively suggest starting new projects when projects you don't recognise are referenced. Note: suggest and partner with me to set them up, don't just create them.
* Scan and digest reference files and summarise into the Context section of project files.
* When scanning project reference information, consider other files that could be updated, such as the root folder's people.md file.
* When digesting reference information you should always be aware that thinking evolves and info may be out of date. Bias towards trusting more recent information where contradictions arise.