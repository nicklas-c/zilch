---
name: slack-sweep
description: Sweep Slack for new messages since last check, digest them, log noteworthy items to the journal, and flag action items
---

# Slack Sweep

## Background

Slack is a firehose. This skill performs a periodic sweep of all new messages since the last sweep, producing a digest and capturing anything substantive in the knowledge base or task list.

## State

The last sweep timestamp is stored in `./slack-sweep-timestamp.txt` at the project root. The file contains a single Unix timestamp (seconds). If the file does not exist, default to 24 hours ago.

## Instructions

### 1. Determine Time Window

- Read the timestamp from `./slack-sweep-timestamp.txt`.
- If the file doesn't exist, default to one working day ago (i.e. if today is Monday, go back to Friday morning; otherwise go back to yesterday morning).
- Record the current time — this becomes the new timestamp at the end.

### 2. Gather Messages

Use the `slack_search_public_and_private` tool to pull messages since the last sweep. Search broadly — all channel types (public, private, DMs, group DMs).

Strategy:
- Search all channel types (public, private, DMs, group DMs) filtered by time using the `after` parameter with the stored timestamp.
- Paginate if results are capped.
- Use `slack_read_channel` to pull additional context from threads where needed.

### 3. Digest

Produce a concise summary of what's happened since the last sweep. Organise by theme or channel as appropriate — use judgement. The digest should:

- Surface what's **notable** — decisions, announcements, requests, blockers, status changes.
- Skip routine noise — bot messages, automated notifications, social chatter — unless they carry signal.
- Highlight anything directed at the user specifically (mentions, DMs, requests).

Present the digest to the user before proceeding to logging.

### 4. Log

For any item that is **substantive** — meaning it represents an observation, event, decision, or piece of information worth recording — write a journal entry to the knowledge base using `add_log_entry`.

- Follow the journal entry structure defined in CLAUDE.md.
- Tag entities appropriately using markdown links.
- One entry per discrete item (not one mega-entry for the whole sweep).
- Use judgement on what crosses the threshold for logging. Not every message warrants an entry. Routine status updates, social messages, and noise do not need logging.
- Write entries without requiring further permission (per CLAUDE.md, journal entries are freely permissible).

### 5. Tasks

If any messages suggest an action item for the user — something they need to do, have been asked to do, or are waiting on — invoke the `task-management` skill to handle addition.

This requires the user's permission per the task-management skill's rules.

### 6. Update Timestamp

After the sweep completes, write the current time (captured in step 1) to `./slack-sweep-timestamp.txt`.

## Notes

- The sweep is triggered manually — the user will invoke it when they want it.
- The volume of results will vary. A quiet weekend will produce little; a busy Monday morning may produce a lot. Adapt the digest length accordingly.
- If the time window is very large (e.g. first run, or after a long gap), consider noting this and offering to narrow the scope.
- When encountering threads, read into them if the top-level message suggests something substantive. Don't read every thread.
