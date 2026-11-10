---
name: slack-sweep
description: Sweep Slack for new messages since last check, digest them, log noteworthy items to the journal, and flag action items
---

# Slack Sweep

## Background

Slack is a firehose. This skill performs a periodic sweep of all new messages since the last sweep, producing a digest and capturing anything substantive in the knowledge base or task list.

## State

- The last sweep timestamp is stored in `./slack-sweep-timestamp.txt` at the project root. The file contains a single Unix timestamp (seconds).
- The channel watch list is stored in `./resources/slack/watch-list.md` at the project root.

## Instructions

### 1. Determine Time Window

- Read the timestamp from `./slack-sweep-timestamp.txt`.
- If the file doesn't exist, ask the user what time to use instead.
- Get the current time using the shell command `date +%s` — this becomes the new timestamp at the end.

### 2. Gather Messages

Messages are gathered in two passes to ensure completeness.

#### Pass 1: DMs and Group DMs

Use `slack_search_public_and_private` with:
- `query: "*"`
- `after` set to the stored timestamp
- `channel_types: "im,mpim"`
- `sort: "timestamp"`, `sort_dir: "asc"`
- `include_context: true`

**Paginate to exhaustion** — continue requesting pages until no cursor is returned.

#### Pass 2: Watch List Channels

Read the watch list from `./resources/slack/watch-list.md`. For each channel on the list, use `slack_read_channel` with:
- `channel_id` set to the channel's ID
- `oldest` set to the stored timestamp
- `response_format: "detailed"`

Paginate each channel to exhaustion if results exceed a single page.

#### Pass 3: Mentions

Use `slack_search_public_and_private` with:
- `query: "to:me"`
- `after` set to the stored timestamp
- `sort: "timestamp"`, `sort_dir: "asc"`
- `include_context: true`

Paginate to exhaustion. Deduplicate against messages already gathered in Pass 1 and Pass 2 — this pass exists to catch mentions in channels not on the watch list.

#### Pagination Rule

All passes MUST be paginated to exhaustion. "To exhaustion" means: continue requesting pages until the API returns no cursor (for Pass 1 and Pass 3) or no further messages (for Pass 2). Do not stop early based on a judgement that enough signal has been found. The sweep is not complete until all passes are fully exhausted.

#### Thread Expansion

Read every thread. Any message with a reply count > 0 must be expanded using `slack_read_thread`. Do not make judgement calls about which threads are worth reading.

### 3. Digest and Proposals

Produce output following the format provided in `example.md` in this skill's folder. The output consists of three parts. Before producing any output, resolve all entity references against the knowledge base (`list_entities`) so that proposed tags are verified, not assumed.

#### Part 1: Digest

A tight summary acting as a **safety net** — the purpose is to ensure nothing important is missed, not to retell every message. The user will have read most of these already; the digest should let them quickly spot anything they haven't.

**Format:**
- Show the time window in the heading. Use `date -r <timestamp>` to convert timestamps to readable datetimes. **DO NOT** try to infer the date and time — you are not reliable at that.
- Group items by **project, team, or topic** — not by source channel. Use a **Miscellaneous** section as a catch-all for items that don't fit a group.
- Compress aggressively. The goal is recognition, not reconstruction — just enough detail to know what a conversation was about. If the user doesn't recognise it, they can ask or go to Slack. Strip technical detail, numbers, ticket IDs, and lists of names unless they are essential for recognition.
- Collapse related items. Multiple items on the same topic become one line. Multiple routine items (support requests, WFH notices, bot pings, Jira transitions, alerts that self-recovered) become a single collapsed line. E.g. "Various DevOps support requests: staging rollback, ECR tag fix, deployment question" — not three separate entries.
- **Bold** items you judge to be most important or most likely to need attention.
- Include everything — the digest is a completeness check, not a curated selection. Even routine items belong here, but they should be compressed and collapsed rather than given individual entries. The filtering happens in Part 2, not here.
- **Target length: aim for roughly 20 lines for a typical weekday sweep, fewer for a quiet period, up to ~30 for a multi-day catch-up.** This is a guideline, not a hard limit — but if the digest is significantly longer, you are not compressing enough.
- Stick to the facts of what was said. Do not infer actions, draw conclusions, or editoralise. If the user needs to do something, that belongs in Part 3 (task proposals), not the digest.

#### Part 2: Proposed Log Entries

A numbered list of entries proposed for writing to the knowledge base. Each entry is presented **verbatim as it would be logged** — ready to write without reformatting.

**Format for each entry:**
```
N. `YYYY-MM-DD`
> Headline text with [Entity Tag](srkb://type/slug) inline
> - Sub-entry with detail and [tags](srkb://type/slug) as appropriate. [Source](link)
> - Further sub-entry if needed.
```

**Rules:**
- Headlines should be **headlines only** — the event or decision in one sentence. Push detail, context, and reasoning into sub-entries.
- Tags must be **verified against the entity list**. Do not tag entities that don't exist. If an untagged reference seems like it warrants a new entity, note that separately — do not embed a speculative tag.
- Apply tags at the correct scope: headline-level tags cascade to all sub-entries; sub-entry tags scope to that bullet only. Tag at headline level when the entity is central to the whole entry; tag at sub-entry level when the entity is relevant only to that detail.
- Include Slack links in sub-entries to refer back to the source conversation.
- One entry per discrete event (not one mega-entry for the whole sweep).

**What to log — and what not to:**

Only propose logging something that would be useful in a future briefing, status report, or 1:1 prep. The following are **not worth logging**:
- Someone working from home, arriving late, or taking a routine single day off
- Alerts that fired and self-recovered without intervention
- Routine sprint ceremonies happening as scheduled
- PR reviews, merges, and deployments proceeding normally
- Bot notifications and automated reminders
- Social or off-topic conversation

**Do** log: decisions, blockers, staffing changes (extended absence, new starters, departures), project milestones, escalations, cross-team requests, incidents requiring action, and anything surprising or non-obvious.

#### Part 3: Proposed Task Updates

Read the tasks list in `./tasks.md` to familiarise yourself with tasks currently on the list.
- If any messages suggest an action item for the user — something they need to do, have been asked to do, or are waiting on — suggest adding a task.
- If any messages suggest a task on the list has been completed, or a waiting-on has been satisfied, suggest removing the task.
- Include Slack links where appropriate to refer back to the source conversation.
- Present as a **numbered list** grouped by action type (Add, Remove, Resolve).


### 5. Update Timestamp

Write the timestamp captured in step one to `./slack-sweep-timestamp.txt`. This happens NOW, not after confirmation — it marks the end of the gathering window, ensuring no gap between sweeps regardless of whether logs are written.

### 6. Request Confirmation

**STOP** Do not proceed before the user has reviewed the proposals and confirmed.
- Ask the user for confirmation or amendments to the proposed log and task changes.
- Log entries and task updates are **separate approvals**. Confirmation of one does not imply confirmation of the other. If the user confirms logs only, do not touch tasks — and vice versa.
- If the response is ambiguous, seek clarification from the user.
- If any doubt remains, make no change.  The user can request log and task writes in a follow-up prompt.

### 7. Execute

Once the user confirms (with any amendments):

- Write journal entries to the knowledge base using `add_log_entry`.
    - Follow the journal entry structure defined in CLAUDE.md.
    - Tag entities appropriately using markdown links.
    - Include the Slack links, where they exist in the proposals.
- Update the tasks list by invoking the `task-management` skill.
    - Include the Slack links, where they exist in the proposals.

## Watch List Maintenance

The watch list (`./resources/slack/watch-list.md`) contains the channels worth monitoring. It should be groomed periodically:

- **Adding channels:** When the user mentions a new channel of interest, or when discovery surfaces relevant activity in an unlisted channel, propose adding it.
- **Removing channels:** If a channel is consistently empty or irrelevant, propose removing it.
- **Discovery:** Periodically (weekly, or on user request), run a broad `slack_search_public_and_private` wildcard search across `public_channel,private_channel` and flag any channels that appeared in results but aren't on the watch list. Present these to the user as candidates for addition.

## Notes

- The sweep is triggered manually — the user will invoke it when they want it.
- The volume of results will vary. A quiet weekend will produce little; a busy Monday morning may produce a lot. Adapt the digest length accordingly.
- DMs are always swept in full via Pass 1. The watch list only applies to channels.
