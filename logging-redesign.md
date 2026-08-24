# Logging Redesign — Decision Record

Date: 2026-07-30

## Problem

Logging has been inconsistent. Almost all log entries are driven by Slack sweeps; day-to-day activity (meetings, decisions, observations) is being lost.

### Root Causes

1. **Competing with real work.** Logging feels like make-work. When choosing between a task and narrating to an AI, the task wins.
2. **Explanation overhead.** Writing up meetings and 1:1s requires explaining in detail what felt simple in the moment. Doing the job then explaining it feels like a chore.
3. **Detail fades** (amplifier, not root cause). Exacerbates the above — if logging were more frequent, this wouldn't matter.

## Design

### Scratch Pad (Capture Layer)

A low-ceremony staging area in the Knowledge Base. Separates *capture* from *commit*.

- Slack sweeps write here silently (no approval prompts).
- Fragments dumped here from working conversations.
- Anything captured from calendar or ad-hoc input lands here.
- Nothing is committed to the log until reviewed.

### Background Slack Sweep

Slack sweep runs as a periodic background cron rather than a user-initiated action.

- Writes to the scratch pad, not directly to the log.
- Silent unless something warrants immediate attention.
- Alerting threshold: high-signal items (e.g. a message from my boss asking for something) interrupt with a notification. Everything else stages silently.

### Breakpoint Prompts

When the user asks "what's next?" (or similar task-seeking prompts), surface pending scratch pad items before moving to the task list.

- Short, targeted questions — not a full review.
- Opportunity to capture context while it's fresh.
- Triggered by natural workflow, not by discipline.

### End-of-Day Review

Walk through the scratch pad together. Confirm, discard, or add colour. Agreed items get committed to the log as proper entries.

- Isolates the discipline problem to a single step that can be optimised.
- User answers questions rather than generating content from memory.
- Anything not committed is discarded or carried forward.

### Working Conversation Logging

Already happens — log entries are written as a side-effect of substantive interactions (interview prep, task assistance, etc.). No change needed.

## Open Items

- **Scratch pad tooling:** Needs building into the KB and exposing through MCP tools.
- **Slack sweep skill rework:** Change from proposing log entries to writing to scratch pad.
- **Cron schedule:** Determine sweep frequency (likely 15-20 minutes).
- **Alerting threshold logic:** Define what constitutes "high enough importance" to interrupt.
- **Calendar integration:** Investigate Outlook export options and automation.
- **"What's next?" hook:** Behaviour change to surface scratch pad items at task-seeking moments.

## Constraints

- Cron only fires while Claude Code is running and idle.
- Recurring cron jobs auto-expire after 7 days.
- No write access to Confluence or Jira.
- This work is tracked outside the SitRep system to avoid circularity.
