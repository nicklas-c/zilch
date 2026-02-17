# Abhishek Chatterjee

## Context for AI
Architect at Zilch. Not a direct report — peer/stakeholder relationship. Regular check-ins to stay aligned on architectural decisions affecting Merchant and DevOps teams.

## Running Notes

### 2026-02-11 — 1:1 notes

- Social chat to open — covered arbitrary topics including cricket and tea. He likes neither, despite stereotypes.
- **Offer-service naming clash** — He's planning a new service called offer-service, which clashes with an existing service we built and poorly named. He was curious why we picked up work on the 'other' offer service. I said Merchant team sometimes gets used to pick up services that don't have a natural home elsewhere. He thinks there should be a cross-functional team for that kind of work. I suggested that's what the new Spend Platform team is meant to be. Broader observation: we've tended to divide the Zilch stack vertically rather than recognising the need for horizontal platform components alongside vertical feature domains.
- **Pending Rewards** — Gave him an overview of the project. He asked what the purpose was; I explained the incentive for customers to repay on time by seeing pending rewards. Discussed edge cases that make it complex. He was relieved it's not a feature that holds rewards in a pending state for months until funds clear on debit purchases. Asked who's working on it — I explained Nick and Michal are partnering, and why, given Michal's imminent move to the new team. I committed to creating an ADR. He pushed back that we don't need detailed ADRs for every small change. I pressed that it's not small — it introduces a lifecycle concept to rewards — and that I want to use the project to demonstrate willingness to engage with the ADR process and reinforce discipline on it with the team.
- **Gateway Service (ZILCH-40366)** — I raised the ambiguity over whether to move straight to a gateway service or stick with the plan of using customer-service as the gateway now that the authentication Lambda is done. He clarified this isn't something he's tracking — it sits with Saeed. I let him know Jacek will be leading the cross-team effort.
- **Fee-service move** — Conversation segued to fee-service moving to the new team with Michal. He hadn't been aware. We discussed other parts of the new team's remit.
- **Visa Flex** — He shared his designs for the project. Sounds like we'll need to implement a new system event that triggers whenever a retailer is updated. I expressed the view that that's a reasonable domain-level event we should have anyway.
