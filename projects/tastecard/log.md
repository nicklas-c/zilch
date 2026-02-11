# Tastecard

## Also Known As

Member Exclusive Offers, offer-service

## Context

Zilch has partnered with Tastecard (operated by Ello as a B2B2C provider) to offer dining and lifestyle discounts as a benefit of Zilch Plus membership. Tastecard is the first "Member Exclusive Offer" — a category of partner-provided perks designed to reinforce the value proposition of Plus beyond its core Rewards feature.

### How It Works

- Ello provides batches of unique redemption codes in plain text files.
- Codes are ingested into Zilch's system via S3 bucket upload, triggering an ingestion workflow.
- Each active Plus member (including free trialists) is allocated one code on a one-to-one basis.
- Members reveal their code in-app and redeem it in the Tastecard app.
- When a membership is cancelled (and transitions to inactive), the code is deallocated and marked as obsolete.
- Deallocated codes are reported monthly to Ello via SFTP, along with quarterly reports on free trial and paid membership counts.
- A Slack alert fires when remaining unallocated codes drop below 10,000.

### Architecture

- **offer-service**: A Java back-end service handling code ingestion, allocation, deallocation, and reporting. Categorised as a Tier 2 Domain Implementation Service. Note: the service was built before its ADR was approved by Architecture, and the name is misleading — it is an integration layer for third-party offer providers, not a domain model for "offers". A rename (e.g. offer-integration-service) is intended but not yet scheduled. A domain-level offer-service is planned, which will create a name clash.
- **Lambda**: Handles SFTP PUT of deallocated code reports to Ello. Infrastructure includes key-pairs stored in AWS Secrets Manager.
- **SFTP**: Non-prod SFTP server set up for testing; prod SFTP used for Ello communication.
- **Front-end**: Code reveal widget, offers carousel on My Plan and Compare Plan pages, Tastecard banners on Home and Account pages, deep linking support. Content managed via ContentStack. iOS, iPad, and Android in scope; web out of scope.
- **LaunchDarkly**: Feature flag `tastecard-activation-marketing-tile` controls visibility of activation tiles (removal ticket exists: ZILCH-46162).

### Key References

- **Product spec**: Component: Member Exclusive Offers (tastecard) — Confluence ZP space, page 4474044475
- **ADR**: [ADR] offer-service — Confluence ZARCH space, page 4768104453
- **Technical design**: Miro board at https://miro.com/app/board/uXjVJb2r9rU=/
- **API docs**: https://payzilch.stoplight.io/docs/offer-service
- **Tastecard FAQs**: Confluence ZP space, page 4580933635
- **Epic**: ZILCH-42678

## Personnel

- **Zac Barclay** — Product Owner (reporter on epic and multiple tickets)
- **Nick Holt** — Lead Back-End Engineer (assignee on most BE tickets, created the offer-service)
- **Alex Murphy** — Front-End Engineer (code reveal widget, offers carousel, app store linking)
- **Ossie Nwokedi** — Front-End Engineer (tastecard activation tile on Homepage/Account)
- **Kieren Messenger** — Designer
- **Nicklas Chapman** — Engineering Manager (reporter on initial BE tickets)
- **Ethan Stockwell** — Data/Analytics (tastecard reporting, billing data for Ello)
- **Chris Prowse / Charlie Hurst / Paul Batey / Alfie Cleveland** — Platform/DevOps (SFTP setup, key-pairs, S3 operations, secrets)

## Running Notes

### 2025-07-10

Initial epic ZILCH-42454 created (later rejected in favour of ZILCH-42678) documenting the full scope of the Tastecard integration: code ingestion, allocation, deallocation, Ello reporting, edge cases, and open questions.

### 2025-07-18

Epic ZILCH-42678 "Member Exclusive Offers (Tastecard)" created by Zac Barclay. Detailed product spec published on Confluence (Component: Member Exclusive Offers).

### 2025-07-22

Initial engineering tickets created: code ingestion (ZILCH-42737), code allocation (ZILCH-42738), deallocation on cancellation (ZILCH-42739), code reveal to customer (ZILCH-42742), deactivated codes file generation (ZILCH-42743). All reported by Nicklas Chapman, assigned to Nick Holt (BE) and Alex Murphy (FE).

### 2025-08-11

FE ticket ZILCH-43199 created for offers carousel on My Plan and Compare Plan pages.

### 2025-09-03

BE tickets for tastecard code endpoint (ZILCH-43800) and account/home banners (ZILCH-43831) created.

### 2025-09-19

Ticket ZILCH-44309 created by Zac Barclay for admin portal support — ability to regenerate a tastecard code for eligible customers. Status: Ready for Refinement (still open).

### 2025-10-01

FE ticket ZILCH-44651 for linking to tastecard app on appropriate app store completed.

### 2025-10-22

Core BE and FE work largely complete. Mobile release mobile-2.37.0 (EC-1304) included tastecard-related Merchant team tickets.

### 2025-10-29

ZILCH-45497 created (by Nicklas Chapman, assigned to Nick Holt) to retrospectively create the ADR and Datadog catalog for offer-service, and update Stoplight documentation. Background explicitly notes that the service was built before the ADR was approved — a deviation from standard process.

### 2025-11-17

PO-1454 raised by Nick Holt to set up a non-prod SFTP server for testing the deallocation report feature.

### 2025-11-18

BE tickets for checking whether a customer has an allocated code (ZILCH-46014) and exposing that through customer-service (ZILCH-46015) created by Nick Holt.

### 2025-11-19

FE ticket ZILCH-46075 for tastecard activation tile on Homepage and Account marketing banners. Experiment ticket EXP-476 created for tastecard activation widgets.

### 2025-11-24

ZILCH-46162 created to remove the LaunchDarkly flag `tastecard-activation-marketing-tile` once experimentation is complete. Still open.

### 2025-12-05

SFTP secrets configured across non-prod environments (PO-1495). Nick Holt working on deactivated codes file generation.

### 2025-12-16

ZILCH-46917 — fix for a flickering deallocation report test caused by async processing race condition.

### 2026-01-29

PO-1582 — RSA key-pair created for Ello SFTP and private key stored in AWS Secrets Manager for the prod deallocation code report Lambda. Assigned to Chris Prowse, completed.

### 2026-02-09

ADR for offer-service updated on Confluence: "Notes and Corrections" section added acknowledging the service was built before ADR approval, that the name is misleading (should be something like offer-integration-service), and that a domain-level offer-service is planned creating a future name clash. Exceptions section updated accordingly. ZILCH-45497 marked done.

Update from Nick Holt on Ello SFTP integration: received connection details from Ello this morning. Will raise a PO ticket to get the details added to AWS secrets. Blocked on PO-1589 — the s3-to-sftp-put Lambda needs to be moved into the VPC so that Ello can whitelist a static egress IP. PO-1589 is currently To Do and unassigned.

### 2026-02-11

Stand-up: ZILCH-46901 (Partnerize MVP integration) nearly done. Awaiting a platform ticket — Abdul Wahid is looking at it.

### Open Items

- **PO-1589**: Move s3-to-sftp-put Lambda into VPC and configure egress for Ello IP whitelisting (To Do, unassigned) — blocking SFTP integration going live
- **ZILCH-44309**: Admin portal — regenerate tastecard code (Ready for Refinement, unassigned)
- **ZILCH-46162**: Remove LD flag `tastecard-activation-marketing-tile` (Created, unassigned)
- **EXP-476**: Tastecard Activation Widgets experiment (To Do, unassigned)
- **Service rename**: offer-service needs renaming to avoid clash with planned domain-level offer-service (not yet scheduled)
