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
- `include_context: false`

**Paginate to exhaustion** — continue requesting pages until no cursor is returned.

#### Pass 2: Watch List Channels

Read the watch list from `./resources/slack/watch-list.md`. For each channel on the list, use `slack_read_channel` with:
- `channel_id` set to the channel's ID
- `oldest` set to the stored timestamp
- `response_format: "detailed"`

Paginate each channel to exhaustion if results exceed a single page.

#### Pagination Rule

Both passes MUST be paginated to exhaustion. "To exhaustion" means: continue requesting pages until the API returns no cursor (for Pass 1) or no further messages (for Pass 2). Do not stop early based on a judgement that enough signal has been found. The sweep is not complete until both passes are fully exhausted.

#### Thread Expansion

Read every thread. Any message with a reply count > 0 must be expanded using `slack_read_thread`. Do not make judgement calls about which threads are worth reading.

### 3. Digest and Proposals

Produce output following the format provided in `example.md` in this skill's folder.  The output consist of three parts:

#### Part 1: Summary
A concise and structured summary of messages since the last sweep.
- Show the time window in the Digest heading, as per `example.md`.  Use `date -r <timestamp>` to convert timestamps to readable date times.  **DO NOT** try to infer the date and time - you are not reliable at that.
- Surface what's **notable** — decisions, announcements, requests, blockers, status changes.
- Skip routine noise — bot messages, automated notifications, social chatter — unless they carry signal.
- Highlight anything directed at the user specifically (mentions, DMs, requests).

#### Part 2: Proposed Logs Entries
A list of logs entries proposed for writing to the knowledge base
- Include anything that is **substantive** — meaning it represents an observation, event, decision, or piece of information worth recording.
- One entry per discrete item (not one mega-entry for the whole sweep).
- Include Slack links where appropriate to refer back to the source conversation.
- Format as nested bullets mirroring the journal structure: headline as the top-level bullet, sub-entries indented beneath.

Example:
```
- Lukasz Kowalczyk took emergency partial day off on 1 Jul
  - Needed time off 11:00–14:30 Poland time. Approved.
  - Still attending 3pm Chris Walker call re New Web. [DM](link)
- Abhishek reviewed Snowflake staging proposal, favours Option 2
  - Concerns about data mixing risk in Option 1
  - Suggested involving InfoSec. [Thread](link)
```

#### Part 3: Proposed Task Updates

Read the tasks list in `./tasks.md` to familiarise yourself with tasks currently on the list.
- If any messages suggest an action item for the user — something they need to do, have been asked to do, or are waiting on — suggest adding a task.
- If any messages suggest a task on the list has been completed, or a waiting-on has been satisfied, suggest removing the task.
- Include Slack links where appropriate to refer back to the source conversation.


### 5. Update Timestamp

Write the timestamp captured in step one to `./slack-sweep-timestamp.txt`.

### 6. Request Confirmation

**STOP** Do not proceed before the user has reviewed the proposals and confirmed.
- Ask the user for confirmation or amendments to the proposed log and task changes.
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
