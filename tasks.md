# Tasks

## Next

| Task | Project | Notes |
|---|---|---|
| Confirm/correct DevOps epic mappings in Parry's LinearB H1 cost cap spreadsheet (Merchant done) | | [Post](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1792752688690859) |
| Inform SalesOps that Sponsored Images campaign migration is ready to start | Sponsored Retailer Search | [DM](https://zilch.enterprise.slack.com/archives/D0C7K1QECFJ/p1794392907665839) · [KP Handover](https://payzilch.atlassian.net/wiki/spaces/ZP/pages/6021251090/KP+Handover+7th-22nd+Nov) |
| Review and agree CMP glossary (attribute, audience, targeting rules) | Commerce Media Platform | Abhishek requested a root doc. [Thread](https://payzilch.slack.com/archives/C0A9H4JPWP8/p1794588582649729) |
| Map out or review the CMP domain ERD in a single diagram | Commerce Media Platform | Consider how deferred MVP questions change the ERD: can a line item book multiple placements, and is creative-to-line-item assignment optional? |
| Ensure a Jira ticket exists for documenting the CMP OpenSearch decision record (alternatives and tradeoffs) | Commerce Media Platform | Abhishek's condition for approval. [Thread](https://payzilch.slack.com/archives/C0A9H4JPWP8/p1794588332261499) |
| Provide feedback on Mindaugas's v2 audience targeting solution design | Commerce Media Platform | Points to raise: attribute/audience distinction is artificial (finding 1 in workbench), audience registration mechanism (how Data team tells campaign-service which audiences exist). [Doc](https://payzilch.slack.com/archives/C0A9H4JPWP8/p1794565118642619) |


## Soon

| Task | Project | Notes |
|---|---|---|
| Discuss Christmas cover plan with Merchant team | | |
| Discuss Christmas cover plan with DevOps team | | |
| Chase product decisions on stale LD flags found during backlog grooming | | `rotating-search-tiles`: fully on since Mar 2025 — confirm safe to remove (may be kept as incident kill-switch). `curated-shop-again-retailers`: stuck at 50% since Apr — forgotten experiment, need a conclusion. `categories-rotating-banner`: off, unchanged 8 months, but being evaluated — investigate why. `personalize-sdk-enabled`: off, unchanged 6 months, being evaluated — investigate why. `search-home-auto-keyboard-disabled`: experiment turned off due to UJ impact — need keep/kill decision. |
| Review and respond to Grzegorz Ziemiański's market expansion plan — explicit acknowledgement requested | Global Market Readiness | [Thread](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1790154268384269) |
| Review competency matrix and consider next career move | | Steve wants a walk-through conversation discussing where I think I stand on each point vs where he thinks I stand. Andrzej is making the matrix more EM-specific — can wait for that or use as-is. Ball is in my court. |
| Chat with Mike Davis about splitting internal / CS agent apps | | [GDM](https://zilch.enterprise.slack.com/archives/C0CDR1VFR60/p1793379212257819) |
| Remove #temp-tech-blackfriday-prep from Slack watch list | Black Friday 2026 | Once past BFCM |
| Gather FY27 gap ideas from Merchant and DevOps teams (Steve Rayko request) | | [Post](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1793983498585229) |
| Check in with David Ramsay — confirm he's getting what he needs from Grafana on the SQL Server private preview (launches ~16 Nov) | Observability Platform Migration | He asked to be included during the 9 Nov DB observability call |
| Check whether Grafana PII follow-ups have landed — Steven (Grafana) committed 9 Nov to sharing secrets filter docs, sensitive data control plane preview details, and mockups | Observability Platform Migration | Nandini is the primary stakeholder |
| Chase IaC vs click-ops follow-up with Grafana — Piotr asked about Terraform coexistence with Instrumentation Hub/Fleet Management on 6 Nov, Ted couldn't answer, follow-up call with Grafana's platform team was mentioned | Observability Platform Migration | Key architectural question for a Terraform-heavy org |
| Get a definitive answer on SNS/SQS trace propagation in OTel — Sam asked on 6 Nov, Ted was unsure about AWS-specific support | Observability Platform Migration | Datadog injects trace IDs into SNS→SQS; if OTel can't, it's a distributed tracing gap. Post in the Grafana Slack channel if not already raised |
| Discuss ZILCH-56520 (Investigate FE tooling) with Stefan Amarie before triaging — needs parent and competency labels | Frontend Module Federation | Skipped during backlog grooming 2026-11-11 pending this conversation |
| Check where ZILCH-53737 (Storefront: Search Bar Configurability) stands with Kieran Patel when he's back from leave | | Passed over for i14 and i15 planning. 3 open PBIs, epic in unusual "Ready for development" status. May be a quiet abandon candidate. |
| Chase Tom McKenzie for a ticket on the RewardsBag impression inflation issue | | RewardsBag counting ~20% more impressions than ROKT on purchase receipts due to duplicate counting. Needs quantifying before drawing comparison conclusions. [Source](https://zilch.enterprise.slack.com/archives/C07JKP2E080/p1794485140649299) |
| Create a Confluence page for DevOps to list things they want handed over from Phil before he leaves | DevOps L4 Replacement 2026 | |
| Fix 1:1 meeting link with Jacek Zanko — he reported it's not working | | [DM](https://zilch.enterprise.slack.com/archives/D07DVKYK1T3/p1793356274194999) |
| Capture Grafana functional gaps against PoC Success Criteria document — vuln management, SQL Server blocking chain view, SQL Server trace-to-query linkage, post-mortem Google Docs dependency, per-query IO metrics and disk throughput visibility | Observability Platform Migration | Gaps surfaced across IRM demo (2 Oct), DB observability (9 Nov), and PII discussion (9 Nov) |
| Find out what's needed to get access to the Fable model (Claude Fable 5.1) | | Zilch-hosted — access controlled internally, not by Anthropic |

## Later

| Task | Project | Notes |
|---|---|---|

## Waiting On

| Task | Project | Chase date | Notes |
|---|---|---|---|
| Tom McKenzie to provide write-up on affiliate-integration-service test strategy and coverage | | 7 Aug | Promised to George Sharpe. Chased again 7 Aug — he said he'd raise a Jira ticket but hasn't. Pattern of deferring until things get forgotten. [DM](https://zilch.enterprise.slack.com/archives/D0825CH1AK0/p1786101755786929) |
| Tom McKenzie to introduce gate on PR-merge builds so no merge can turn a Maestro test red | | 23 Jul | Tests now stable and passing. Gate expected within a couple of weeks. |
| BE engineers to estimate Spring Boot security password logging fix in retailer-service | | | Jira ticket raised. [Source](https://zilch.enterprise.slack.com/archives/C028GA4CW80/p1794922344896349) |
| Mark Swarbrick to respond on Thredd reference call time | Observability Platform Migration | | Emailed with suggested time. [DM](https://zilch.enterprise.slack.com/archives/D0CBKQANUF8/p1794918601872109) · [Steve confirmation](https://zilch.enterprise.slack.com/archives/D097D2RU0UQ/p1795009060214049) |
| David Taylor (Talent Team) to respond with guidance on Director of TPM interview | | | Interviewing with Zac Barclay on Friday. [Source](https://zilch.enterprise.slack.com/archives/D07J7BBQ4D8/p1794996866278549) |
| Grafana to respond on PoC kick-off meeting time | Observability Platform Migration | | Proposed a time |


## Reminders

| Reminder | Trigger | Project | Notes |
|---|---|---|---|
| Ask Nick Gilbert for referrals for L4 replacement — Łukasz and Piotr done | 1:1 with Nick Gilbert | DevOps L4 Replacement 2026 | Steve Rayko requested. [Source](https://zilch.enterprise.slack.com/archives/C0CHABFQJPN/p1794498088418779) |
| Confirm who's presenting Post Purchase Offers at today's sprint demo | Stand-up | | Parry suggested it for Merchant. |
| Raise CMP prioritisation with Kieran — OpenSearch pivot tickets (ZILCH-58385, 58386, 58381) are unassigned and blocking all targeting work | 1:1 with KP | Commerce Media Platform | |
| Check in with Stefan on booking tool auth — what's the status with Julien and Okta/Cloudflare? | 1:1 with Stefan Amarie | Commerce Media Platform | |

## Recurring

| Task | Recurrence | Playbook | Notes |
|---|---|---|---|
| Create flash report for Merchant team | Every Friday | | |
| Create flash report for DevOps team | Every Friday | | |
