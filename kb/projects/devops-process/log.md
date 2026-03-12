# DevOps Process

## Context

*To be populated*

## Personnel

*To be added*

## Digest

### 2026-02-13

Project created.

### 2026-02-16

- Published DevOps operating model announcement to engineering-wide Slack: hybrid Scrum/Kanban from Sprint 11.4, with fixed capacity reserved for reactive work.
- Completed Jira setup: "DevOps Reactive" (Kanban) and a new Planned board (Scrum), routed by `reactive` label. Sprints created through end of next iteration; stub sprint for 11.3 holds in-flight work. Columns kept simple to start (To Do, In Progress, Done).
- Refined and tasked out ZILCH-47773 (prepare environments for customer-web-app deployments). Agreed with Rob Nelson to prioritise for Sprint 11.4. Work planned into the first sprint under the new Scrum model rather than taken on reactively.

### 2026-02-18

- Planning meeting from 17th cancelled (forgotten when announcement was sent). Three remaining tasks promoted to Next: review backlog track assignments, set up refinement/backlog prioritisation meetings, extend Merchant stand-up from 15 to 20 mins.
- Set up sprint planning, refinement, and retro meetings for the DevOps team. Rescheduled Merchant and DevOps stand-ups for better timing. All ceremony meetings now in place.
- Reviewed backlog track assignments with the team. Almost everything in the planned track — suggests the team isn't creating tickets for reactive work rather than there being less of it. Reinforces need for Slack-to-ticket automation.
- Initiative effectively closed out: all tasks complete.

### 2026-02-19

- Backlog hygiene work, including a session with the team.

### 2026-02-20

- Jira config and hygiene work under way in preparation for hybrid Scrum/Kanban adoption.

### 2026-03-05

- Ambiguity surfaced at stand-up about the purpose of the **Sign Off** stage on the reactive Kanban board. ZILCH-49094 sitting in To-Do despite the deployment being done — moved to correct column. Board column definitions and workflow need clarifying with the team.

### 2026-03-09

- First DevOps retro held under the hybrid model. Largely taken over by the build pipeline failures topic (escalated to Andrzej).
- Leave handover gap (ZILCH-48446 / Nick Gilbert) deferred to next retro.
- **Pipeline failures**: increased absolute count is a consequence of CD adoption driving higher deploy frequency — rate not necessarily higher. Team frequently asked to diagnose as first step. Some structural problems (e.g. IP exhaustion) are solvable but time rarely available. Team feel expected to work at Platform level; DevOps/Platform boundary unclear.
- **Work intake**: multiple high-pressure projects all treating DevOps as top priority. Requests via walk-ups and DMs. Team reluctant to over-formalise but recognise informal intake doesn't scale.
- Pipeline mitigations: push diagnosis responsibility back to engineers via open questions.
- Work intake mitigations: require Jira tickets for walk-ups; move DMs to #tech-devops; large requests via EM; over-communicate during pressure periods.
- Phil Stevenson pushed back on intake formalisation — values informal responsiveness, perceives formalisation as barriers. Parallel with Alex Murphy's early attitude; Alex eventually adapted positively. Useful framing for a future 1:1.
- Retro notes written up and shared.
- EM actions: monitor #tech-devops more closely; respond to Andrzej's pipeline concerns with framing context.
