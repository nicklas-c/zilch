---
name: task-management
description: Manage the to-do list, waiting-on items, reminders, and recurring tasks in tasks.md
---

# Task Management

## Background

I maintain a task list in `./tasks.md` at the project root. It tracks to-do items (prioritised), waiting-on items, and recurring tasks. This skill describes how to interact with that file.

## Structure

The file has the following sections:

- **Next** — high-priority tasks to action imminently
- **Soon** — tasks to address in the near term
- **Later** — lower-priority items
- **Waiting On** — things I'm waiting on from others (with optional chase dates)
- **Reminders** — items to surface at a specific occasion (e.g. sprint planning, refinement, a particular 1:1) rather than to action unprompted
- **Recurring** — tasks that repeat on a schedule

Each section uses a markdown table. Do not alter the table structure or column headings.

## Instructions

### Adding Tasks

- If a comment notes something I need to do, have been asked to do, or am waiting on:
    - Propose adding it to the task list
    - Make a sensible choice of priority if I don't specify one
    - Wait for permission
    - Add the item if permission is given
    - Confirm which priority you've added it at so I can correct if necessary
- If I explicitly ask you to add an item:
    - Make a sensible choice of priority if I don't specify one
    - Add it — no further permission needed
    - Confirm which priority you've used

### Removing Tasks

- If a comment notes something I've done that was on the list:
    - Propose removing it
    - Wait for permission
    - Remove it if permission is given
    - Write a journal entry to the knowledge base recording what was done
- If a comment makes a task redundant:
    - Propose removing it
    - Wait for permission
    - Remove it if permission is given
- If I explicitly ask you to remove an item:
    - Remove it — no further permission needed
    - If the task was completed, write a journal entry recording what was done
    - If being removed for another reason and the context is unclear, clarify first

### Reading Out and Grooming

I will often ask to see my tasks — either to pick a next action or to groom and reprioritise.

- List tasks verbatim. Do not summarise or presume which are most important.
- Number the list so I can refer to items easily.
- When grooming:
    - I may ask you to move tasks to change priority. You may do this without further permission, so long as no information is lost.
    - I may ask you to add or remove tasks — follow the standard rules above.

### Reminders

Reminders are items that should be surfaced at a specific occasion rather than actioned unprompted. They differ from tasks: a task is something to do now or soon; a reminder is something to remember *when the moment comes*.

- The "Trigger" column identifies the occasion (e.g. "Sprint planning", "Refinement", "1:1 with Steve").
- When the user is prepping for an occasion, scan the Reminders section and surface any items matching that trigger.
- Once a reminder has been actioned, remove it from the list.
- If something initially looks like a task but is really "remember to do X at occasion Y", propose adding it as a reminder rather than a task.

### Recurring and Waiting On

When a check is triggered (e.g. by the ambient patterns in CLAUDE.md):

- Check the chase date on any waiting-on items. If lapsed, ask if I want to add a chase-up task.
- Check the recurrence pattern on any recurring tasks. If a match is due, ask if I want to add a to-do item for it.

## Limits of Autonomy

The integrity of the task list is important. The risk of unintended changes through misunderstanding is real.

**Never make changes to `tasks.md` without my permission.**

You may freely propose changes. If you think a change is appropriate:
1. Summarise the change and propose it.
2. Make the change only if I give permission.
