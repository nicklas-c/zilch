# DevOps Process

## Also Known As

*To be added*

## Context

*To be populated*

## Personnel

*To be added*

## Running Notes

### 2026-03-09

- First DevOps retro held under new hybrid Scrum/Kanban model. Meeting was largely taken over by the build pipeline failures topic, which had been escalated to Andrzej.
- Leave handover gap (ZILCH-48446 / Nick Gilbert) identified as a retro topic but deliberately deferred to the next retro. To be raised then.
- **Pipeline failures**: increased absolute failure count is a consequence of CD adoption driving higher deploy frequency — failure rate not necessarily higher. Team frequently asked to diagnose failures as first step. Some structural problems (e.g. IP exhaustion) are solvable but time is rarely available to fix them. Team feel expected to work at Platform level; DevOps/Platform boundary remains unclear.
- **Delivery pressure and work intake**: multiple high-pressure projects all treating DevOps as top priority. Requests arrive via desk walk-ups and DMs. Team reluctant to over-formalise but recognise informal intake doesn't scale as the organisation grows.
- Mitigations for pipeline pressure: use open questions to push diagnosis responsibility back to engineers ("What error were you seeing?", "What have you tried?").
- Mitigations for work intake: require Jira tickets for walk-up requests (immediate action at engineer's discretion for very small tasks, but still appropriate to ask); move DM conversations to #tech-devops for visibility and handover; large/project-scale requests to come via EM; over-communicate during high-pressure periods to manage expectations.
- Phil Stephenson pushed back on work intake formalisation. His concern was emotional rather than analytical: he values informal responsiveness and perceives formalisation as creating barriers. Notable parallel with Alex Murphy's early attitude — same framing, same hero-developer instinct. Alex eventually adapted and reflected positively on the change. This may be useful framing for a future 1:1 with Phil.
- Retro notes written up and shared with the team.
- EM personal actions: monitor #tech-devops more closely for trends and tone; respond to Andrzej's pipeline concerns with framing context.

### 2026-03-05

At stand-up, ambiguity surfaced about the purpose of the **Sign Off** stage on the DevOps reactive Kanban board. Also noted that ZILCH-49094 was sitting in To-Do despite the deployment already having been done — moved to the correct column. Both are signals that the board's column definitions and workflow need to be clarified with the team.

### 2026-02-20

* Jira config and hygiene work under way in preparation for adoption of the hybrid Scrum/Kanban model.

### 2026-02-18

Planning meeting that was supposed to happen on the 17th was cancelled (forgotten when the announcement was sent). All three remaining devops-process tasks promoted to Next — aiming to close off the initiative today: review backlog track assignments with the team, set up refinement and backlog prioritisation meetings, and extend Merchant stand-up from 15 to 20 minutes.

Set up new series of sprint planning meetings for the DevOps team. Rescheduled Merchant and DevOps stand-ups to give more time for the Merchant stand-up and improve the chance of making the DevOps one on time. Scheduled regular refinement meetings for the DevOps team. All ceremony meetings now in place. Only remaining devops-process task: review backlog track assignments with the team.

### 2026-02-16

Published operating model announcement to engineering-wide Slack channel: hybrid Scrum/Kanban from Sprint 11.4, with fixed capacity reserved for reactive work. Key message: foreseeable work should be raised early for sprint planning; urgent items still handled reactively.

Completed Jira setup and communicated to the team. Two boards: "DevOps Reactive" (Kanban, continuation of existing board) and a new Planned board (Scrum). Items appear on one or the other based on a `reactive` label. Sprints created through to the end of the next iteration. A stub sprint for 11.3 holds in-flight work. Columns kept deliberately simple (To Do, In Progress, Done) to start — will refine with the team. Tomorrow's planning meeting repurposed to sort tickets into the correct boards and talk through backlog management approach.

Refined and tasked out ZILCH-47773 (prepare environments for customer-web-app deployments) with the team. Agreed with Rob Nelson to prioritise for Sprint 11.4 (starting next week). Outcome: work planned into the first sprint under the new Scrum model rather than taken on reactively — process preserved while still meeting stakeholder needs.

### 2026-02-13

Project created.
