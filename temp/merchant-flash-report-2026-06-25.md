HIGHLIGHTS
Merchant
• *Sponsored Retailer Search*
    ◦ Admin Portal and search endpoint ready for testing; sponsored results blending into search.
    ◦ Go-to-market planning underway — LD flag sequencing and category backfill plan being defined.
• *Semantic Search*
    ◦ Semantic search results display work in dev (ZILCH-52327) — presenting results component-wise amongst lexical, sponsored, and GABD.
    ◦ Tracking and testing requirements being scoped with PM and FE.
• *Intelligent Commerce*
    ◦ CJ network integration code complete; test transactions can be sent.
    ◦ Blocked on advertiser setup parameters — need to identify who owns the CJ relationship on the sales/partnership side.
• *Rewards-Service Aurora Migration*
    ◦ Aurora baseline ready for prod (EC-3042 raised).
    ◦ Request signing aligned with established pattern; covered by E2E.
    ◦ Customer lock timeout increased from 5s to 30s in prod.
    ◦ Data source switchability in PR — enables cutover once validated.
• *Nick Holt Handover*
    ◦ Leaving end of June; handover meetings scheduled, dedicated Slack channel created.
    ◦ Structured handover to Jacek and the Loyalty team.
• *KTLO*
    ◦ TasteCard codes uploaded (file needed reformatting); documentation added.
    ◦ Maestro test runs enabled on frontend PRs (non-blocking).
    ◦ Offer-service deallocation race condition fixed.
    ◦ Cross-partner observability logging unified.
    ◦ Failing merchant Appium tests fixed.
    ◦ Customer-service routing via LD toggle ready for release.
    ◦ Critical vulnerability in s3-to-sftp-put ready for sign-off.
    ◦ PR approvals being reduced to 1 for Merchant BE repos (in PR).
• *Team*
    ◦ Stefan Amarie on paternity leave (2 weeks off, then WFH).
    ◦ Amr Aljundi visited the office ahead of his July start.
RISKS
• Rewards-service Aurora migration unlikely to complete before Nick Holt leaves at end of June. Mitigating with structured handover to Jacek and the Loyalty team.
