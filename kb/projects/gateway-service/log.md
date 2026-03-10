# Gateway Service

## Also Known As

*To be added*

## Context

*To be populated from reference material*

## Personnel

*To be added*

## Digest

### 2025-02-04

Project log created.

### 2026-02-11

Stand-up: Jacek deploying authoriser Lambda (ZILCH-40366) to pre-prod. Needs review. Tomasz Surowiec interested in using the gateway service. Open question: new gateway or proxy through customer-service? (Resolved 2026-02-16 — iterative approach.)

### 2026-02-12

1:1 with Abhishek Chatterjee: gateway service sits with Saeed, not something Abhishek is tracking. Informed him Jacek will lead the cross-team effort.

### 2026-02-16

Next-steps meeting: decided on the iterative approach — deploy the authoriser Lambda for authorisation while continuing to use customer-service for other gateway functions. Full gateway-service build to follow.

Rory Fielding requested gateway support for detecting jailbroken devices (directed by Saeed). Premature — gateway is nowhere near that maturity. Agreed Rory will look for alternatives; follow-up discussion needed (including Saeed) to ensure any interim solution can migrate into the gateway later.

### 2026-02-18

Stand-up: ZILCH-40366 (authoriser) ready to go to prod. Tom McKenzie's concerns satisfied — it won't be in active use yet, just available in production.

### 2026-02-20

Flash report: authoriser lambda done, pending DevOps review. Next step: build retailer service gateway.

Iteration 12 planning prep: gateway service listed as a work stream. Jacek to propose next steps at the planning meeting; may result in ticket refinement.
