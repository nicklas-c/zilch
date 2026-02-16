# Gateway Service

## Also Known As

*To be added*

## Context

*To be populated from reference material*

## Personnel

*To be added*

## Running Notes

### 2026-02-16

Stand-up: authoriser ready for review. Jacek has doubts about how to go to production. Will organise a meeting with stakeholders to take forward.

Next-steps meeting (with Jacek, Rory Fielding, and others): decided to take the iterative approach — deploy the new authoriser Lambda for authorisation while continuing to use customer-service for other gateway functions. Full gateway-service build will follow. This resolves the question raised on 11 Feb about whether to use a new gateway or proxy through customer-service.

Rory raised a request for the gateway to detect jailbroken device requests and fire events for the fraud detection engine. He'd been directed to request this by Saeed. Premature — gateway service is nowhere near that maturity level. Saeed should have known this. Agreed with Rory that he'll look for alternative solutions, but that we need a follow-up discussion (including Saeed) to ensure any interim solution can be migrated into the gateway service in the future if appropriate.

### 2026-02-12

- Discussed with Abhishek Chatterjee in 1:1. He clarified that gateway service isn't something he's tracking — it sits with Saeed. Informed him that Jacek will be leading the cross-team effort.

### 2026-02-11

Stand-up update: Jacek is working on deploying the authoriser Lambda (ZILCH-40366) to pre-prod today. Needs review today. Tomasz Surowiec is interested in making use of the new gateway service too. Jacek raised a question about whether to use a new gateway or proxy through customer-service — I need to understand the thinking better.

### 2025-02-04

Project log created.
