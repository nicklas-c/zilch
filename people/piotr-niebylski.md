# Piotr Niebylski

## Context for AI
Piotr Niebylski is a DevOps Engineer (Level 4) in the DevOps team.  There are sometimes clashes between Piotr and Phil.  I have wondered whether Piotr sees Phil acting as de facto tech lead and feels he needs to challenge because they are graded at the same level.

## 2025 year-end appraisal
### His self-appraisal
#### Achievements
I worked on crossplane deployments for ephemerals, created all helm charts and configurations needed for all resources used in AWS by Zilch services, lambdas and frontends. Adapted lambdas to be deployed by crossplane using container approach. Configured helm charts for frontend UI's like admin-ui and customer-ui (legacy) and successfully deployed them to ephemerals with proper authentication in customer-ui.

I also worked on creating and stabilising first Zephyr environment which was deploying in under 7 min. This was used as an example at the Zilch DevOps presentation for outside non-Zilch engineers.

I created a dedicated ArgoCD deployment just for ephemeral environments. This allows for easier testing and resource management and limits the blast zone if something would go worng in ArgoCD when working on zephyrs.

I also created a mock ZOE (zephyr-orchestraton-engine) api and frontend as a PoC of a fully developed Zephyr management system.

I worked on a solution to scale up and down dev, qa and staging environments which was part of a cost saving initiative.

I integrated various external tools like e.g. LinearB to work within Zilch and help better track engineers work.

#### Growth Areas
I need to be more active when it comes to support on which I already started to work on and improve, especially during support rota, to focus as much as possible on non-project work.

I need to be more visible with my work and take new opportunities when they present themselves and take upon myself more tasks which allow engineers to work better (eg. devex).

#### Final Summary
This year I think was a good year given a huge task for DevOps team to create ephemeral environments.

I worked on some big tasks related to that project and completed them in short time with good quality which enabled my team members to take over and improve on those pretty quickly and without any big problems.

I had good cooperation with my team (devops) and had no friction or any issues with engineering teams.

There is still room for improvement for me when it comes to being more visible with my work and take non-project related tasks / opportunities. 

### My appraisal of Piotr
#### Impact
Piotr continues to show up as a competent DevOps engineer who knows his stuff.  I have enjoyed seeing the enthusiasm he has brought to the Ephemeral Environments project and his engagement on that has helped to drive the project in terms of both progress and quality.

He brings strong opinions, which he is willing to defend.

Although his contribution on Ephemeral Environments stands out, he has also contributed across a number of projects.

Piotr continues to show a preference for project work over reactive work - clearly prefering to build than to diagnose and fix.

#### Growth Areas
Piotr has acknowledged that he could lean in better to the support rota, and I'd echo that. Reactive work matters as much as project work, and being seen as responsive on rota is important for the team.

On the Ephemerals project, there have been times when Piotr's enthusiasm has led him to take ownership in a way that cut others out. I'd encourage him to think about working to the plan, and keeping the whole team involved through usual sprint processes.

## Running Notes

### 2026-02-06 1:1

* Started with social chat
  * His wife is ill and anticipating a biopsy operation — trying to stay healthy so it doesn't get postponed again
  * Looking forward to the weekend
  * Hans Zimmer playing in Poland soon; looking forward to seeing him
* Feedback on ZOE work:
  * Very nice work — clean, well-structured codebase
  * NFRs (auth, logging, self-documenting API, health endpoints) all well covered
  * Ran out of time in presentation just as we were getting to the core: K8s operator and ArgoCD generator
* Process changes discussion:
  * He wanted me to be aware they tried something similar when Andrzej was managing the team
  * Some work items don't fit well with Scrum because they're hard to estimate
  * Thinks hybrid Scrum/Kanban might help — could make the difference this time
  * Says I have the prerogative to set process to make team more efficient
  * I explained the changes aren't just about efficiency:
    * I need structure to do my job better (comms, direction, protecting from unreasonable expectations)
    * Need better visibility on work and velocity — will give me collateral to advocate for additional headcount
* Appraisal discussion:
  * Explained how I approached writing it
  * Explained limits on what I could share before process completes
  * Shared my write-up
  * He acknowledged comments were appropriate and reasonable

### 2026-02-20

* Declined 1:1 — something personal to attend to. Asked to reschedule.

#### Prepared talking points for rescheduled 1:1

* **Personal check-in** — ask how his wife is doing (awaiting biopsy as of early Feb).
* **New operating model** — still early days, but interested in his initial impressions. Use as a hook for the expectation around rota/project discipline: the hybrid model will give visibility to the split, and we'll expect that to be respected going forward.

### Peer feedback from Nick Gilbert — 2026-02-12

Via Nick G's 1:1. Re: ZOE presentation and codebase:
- Implementation looks good and clearly laid out — big piece of work.
- Needs more comments; Nick isn't a Go expert and would benefit from better documentation. Discussed Go's idiomatic godoc approach as potential leverage.
- Concern about submitting a large volume of code in one go without iterative peer review. I confirmed similar feedback has already been given to Piotr directly.
- Nick sees this as a pattern — cites the Crossplane work for Ephemeral Environments, where Piotr similarly went off piste and stability was adversely affected.

This reinforces the growth area from the appraisal: working to the plan and keeping the team involved through usual sprint processes.
