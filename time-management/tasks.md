# Tasks

## Next

### Clear down Slack messages
End of day 10th Feb.

### Write up Abhishek's 1:1 notes from 11th Feb

### Write up Nick H's 1:1 notes from 11th Feb

### Set up cross-team refinement with Decisioning and Merchant
Continuity of membership for Pro.

## Soon

### Understand gateway vs customer-service proxy question (ZILCH-40366)
Jacek raised whether to use a new gateway or proxy through customer-service. Need to understand the thinking and form a view.

### Set up call with Nick H and Charlie Hurst re Aurora connectivity issue
Align on root cause and fix for fee-service. Conversation with Charlie was at cross-purposes over Slack — need to get everyone on the same page.

### Review ZILCH-40366 (gateway service authoriser Lambda)
Jacek deploying to pre-prod today — needs review today.

### Task out ZILCH-47400 (Merchant O11y Audit & Refresh)
Break the epic down into refinable tickets so the team can start picking up work.

### ZILCH-46727 — Rewards on loans during tier change
Chased Marcin and Tommy on 11 Feb — directed to a Slack thread. Need to meet with Jacek and Michal to understand what was agreed with Decisioning and capture as Jira tickets.

### Set up regular rota review meeting
Regular meeting with on-call staff to review upcoming tickets.

### Ask Mike Davis what his engineering dependencies are for Pro
He mentioned them in the status meeting — need to understand what they are.

### Coordinate Pro rollout plan with Zac and Ethan
Product perspective: A/B testing, cohorts, etc. Then coordinate with other EMs on technical steps for rollout. Document it up.

### Understand scope of Aurora connectivity issue across other services
Platform's change affects any service using the AWS JDBC failover plugin. Need to identify which services beyond fee-service and ehi-service are silently affected and will break on next restart.

### Order two Lego unicorns
Team mascot tradition — everyone who joins the Merchant team gets one. Need two: one for Stefan, one for Michal Baran's eventual backfill.

### Get up to speed on FE initiatives for Stefan's onboarding
Need to understand Maestro test pack, server-side rendering, new architecture, modular FE architecture, and ContentStack well enough to brief Stefan.  Confer with the team where needed.

### Write LinkedIn reference for Alex Murphy

### Set up Jira to support new DevOps team process

### Write up thoughts on improved data model for rewards

### Add Stefan to regular team meetings
Stand-ups, refinement, planning, retro, etc.

### Set up 1:1s with Stefan

### Draft day-one email for Stefan
Depends on getting other onboarding prep done first (FE initiatives, tooling access, first piece of work, etc.).

### Document step-by-step release plan for Pro
Depends on completing the cross-team review.

## Later

### Move Merchant team's support rota into JSM
Blocked on permissions — raised ITOPS-14282 to get access. Remove Michal Baran as part of the migration.

### Get duplicate Merchant team records removed from JSM
Three records exist; only one is in use. No permissions to remove them — need a JSM admin.

### Update retro rota on Confluence
Remove Alex Murphy and Michal Baran from future slots. Extend the rota beyond sprint 12.1.

### Create LaunchDarkly flag enablement playbook
Retro action. Step-by-step process for enabling flags safely — will live in playbooks/.

### Design quarterly peer feedback programme
Collect structured feedback from team members on their peers each quarter, to feed into appraisals. Format, scope, anonymity, and mechanism still to be decided.

## Waiting On

### PO-1589 — Lambda VPC move for Ello SFTP
Chased 9 Feb. Unassigned, blocking Tastecard SFTP integration going live. No response yet.

### ZILCH-48105 — WebSocket/IDV deadlock fix
Planned into sprint 11.3.

### Michal Baran backfill — role approval
Backfill promised but role not yet approved.

### ITOPS-14282 — JSM permissions for Merchant support rota
Raised 9 Feb. Needed to set up the Merchant team's support rota in JSM.

### ZILCH-48248 — Race condition fix blocked by failing test
Nick H's fix is in PR but a failing test puts this back on Platform. Their Lambda move for static IP caused the original issue. May need EventBridge migration.

### ZILCH-46901 — Partnerize integration awaiting platform ticket
Nearly done. Abdul looking at the platform side.

### Data file from Ethan Stockwell for Visa Flex
