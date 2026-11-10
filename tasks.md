# Tasks

## Next

| Task | Project | Notes |
|---|---|---|
| Read BFCM Technology Support confluence page (Mark Reddington mentioned you) | Black Friday 2026 | [DM](https://zilch.enterprise.slack.com/archives/D08C735G9FA/p1790553445932099) |
| Review and respond to Grzegorz Ziemiański's market expansion plan — explicit acknowledgement requested | Global Market Readiness | [Thread](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1790154268384269) |
| Test the LD SDK sequencing hypothesis for storefront-hero-carousel flag (Kieran's request to you and Ossie) | | [Post](https://zilch.enterprise.slack.com/archives/C07JKP2E080/p1790151766754479) |
| Check why DevOps approval is now required for scheduler releases (Chris Kucybala's question) | | [Post](https://zilch.enterprise.slack.com/archives/C01J1KBUS1E/p1790155978076999) |
| Confirm/correct Merchant and DevOps epic mappings in Parry's LinearB H1 cost cap spreadsheet | | [Post](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1792752688690859) |
| Discuss Visa Flex retailer list re-sync ownership with Amr (back 5 Nov) | Visa Flex | Clarify who is responsible for re-synching the retailer list — avoid ambiguity that could leave Payments tapping Merchant to run it. Should be self-serve or via ITAM. Close the Visa Flex project once resolved. |
| Run Black Friday readiness checklist with Merchant and DevOps teams | Black Friday 2026 | BFCM is 27 Nov |
| Update Merchant and DevOps team tasks on the BFCM Confluence page | Black Friday 2026 | Due each Monday until BFCM. [Confluence](https://payzilch.atlassian.net/wiki/spaces/ISD/pages/5876842865/2026+BFCM+Technology+Support#Team-Tasks%3A) |
| Confirm required changes target 13 Nov delivery — add any missing Merchant/DevOps JIRAs tagged Black-Friday-2026 | Black Friday 2026 | Mark noted most tagged JIRAs are Retain/Decisioning — verify nothing missing from our teams |
| Fill in BFCM Technology Support PoC contacts for Merchant and DevOps teams | Black Friday 2026 | [Post](https://zilch.enterprise.slack.com/archives/CCW04B38D/p1793809847696109) |
| Review BFCM Technology Support tagged JIRAs and prepare refined list for next Tuesday's call | Black Friday 2026 | [#eng-management](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1793966759956649) |
| Create BJF in Ashby for Phil Stevenson's replacement (DevOps Engineer L4) | | [GDM](https://zilch.enterprise.slack.com/archives/C0CG3GZ6XUJ/p1794237128254559) |


## Soon

| Task | Project | Notes |
|---|---|---|
| Review competency matrix and consider next career move | | Steve wants a walk-through conversation discussing where I think I stand on each point vs where he thinks I stand. Andrzej is making the matrix more EM-specific — can wait for that or use as-is. Ball is in my court. |
| Investigate feasibility of integrating Claude with LinearB — add to DevOps backlog | | Documentation link shared in synch meeting chat. |
| Review Sponsored Search AdMarketplace brief on Confluence (Kieran's request) | AdMarketplace Search Auction | [DM](https://zilch.enterprise.slack.com/archives/D0B1VUFEM2Q/p1791472421800509) |
| Respond to Stefan's end-of-year team achievements presentation proposal | | [GDM](https://zilch.enterprise.slack.com/archives/C0CACLFKC48/p1792074648693509) |
| Fix 1:1 meeting link with Jacek Zanko — he reported it's not working | | [DM](https://zilch.enterprise.slack.com/archives/D07DVKYK1T3/p1793356274194999) |
| Review Christmas leave / on-call rota planning spreadsheet (Grzegorz) | | [Post](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1792659067288859) |
| Chat with Mike Davis about splitting internal / CS agent apps | | [GDM](https://zilch.enterprise.slack.com/archives/C0CDR1VFR60/p1793379212257819) |
| Review ZILCH-47400 (Merchant O11y Audit) epic — close if no longer relevant given portfolio changes | | fee-service and rewards-service both handed over since this was scoped |
| Remove #temp-tech-blackfriday-prep from Slack watch list | Black Friday 2026 | Once past BFCM |
| Respond to Alex Pink (Coralogix) re: scheduling follow-up POC call | Observability Platform Migration | [DM](https://zilch.enterprise.slack.com/archives/D0CF4BK3RB9/p1793980116801029) |
| Gather FY27 gap ideas from Merchant and DevOps teams (Steve Rayko request) | | [Post](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1793983498585229) |
| Check in with David Ramsay — confirm he's getting what he needs from Grafana on the SQL Server private preview (launches ~16 Nov) | Observability Platform Migration | He asked to be included during the 9 Nov DB observability call |
| Check whether Grafana PII follow-ups have landed — Steven (Grafana) committed 9 Nov to sharing secrets filter docs, sensitive data control plane preview details, and mockups | Observability Platform Migration | Nandini is the primary stakeholder |
| Capture Grafana functional gaps against PoC Success Criteria document — vuln management, SQL Server blocking chain view, SQL Server trace-to-query linkage, post-mortem Google Docs dependency, per-query IO metrics and disk throughput visibility | Observability Platform Migration | Gaps surfaced across IRM demo (2 Oct), DB observability (9 Nov), and PII discussion (9 Nov) |
| Chase IaC vs click-ops follow-up with Grafana — Piotr asked about Terraform coexistence with Instrumentation Hub/Fleet Management on 6 Nov, Ted couldn't answer, follow-up call with Grafana's platform team was mentioned | Observability Platform Migration | Key architectural question for a Terraform-heavy org |
| Get a definitive answer on SNS/SQS trace propagation in OTel — Sam asked on 6 Nov, Ted was unsure about AWS-specific support | Observability Platform Migration | Datadog injects trace IDs into SNS→SQS; if OTel can't, it's a distributed tracing gap. Post in the Grafana Slack channel if not already raised |

## Later

| Task | Project | Notes |
|---|---|---|
| Check internally on JSM schedule migration tooling follow-up — Ward Bekker (Grafana) said he'd check on JSM-specific automated migration on 2 Oct, no follow-up logged | Observability Platform Migration | Low priority — worth a nudge with Mark Reddington or David Ramsay |

## Waiting On

| Task | Project | Chase date | Notes |
|---|---|---|---|
| Tom McKenzie to provide write-up on affiliate-integration-service test strategy and coverage | | 7 Aug | Promised to George Sharpe. Chased again 7 Aug — he said he'd raise a Jira ticket but hasn't. Pattern of deferring until things get forgotten. [DM](https://zilch.enterprise.slack.com/archives/D0825CH1AK0/p1786101755786929) |
| Tom McKenzie to introduce gate on PR-merge builds so no merge can turn a Maestro test red | | 23 Jul | Tests now stable and passing. Gate expected within a couple of weeks. |
| Sean Hederman to attempt to retain Phil Stevenson | DevOps L4 Replacement 2026 | | If successful, changes the shape of the replacement project significantly. |


## Reminders

| Reminder | Trigger | Project | Notes |
|---|---|---|---|
| Prioritise geo expansion KR items ZILCH-51748 and ZILCH-51747 for Merchant team | Sprint planning | Global Market Readiness | [#eng-management](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1784191731419739) |
| Take ZILCH-53474 into next sprint | Sprint planning | | Rob Nelson request. Stefan helping in #mobile-error-log-review. [#eng-management](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1784634554945229) |
| Review ZILCH-49514 (Insecure local networking in iOS) — Rob Nelson mentioned you in a Jira comment | Planning meeting | | |

## Recurring

| Task | Recurrence | Playbook | Notes |
|---|---|---|---|
| Create flash report for Merchant team | Every Friday | | |
| Create flash report for DevOps team | Every Friday | | |
