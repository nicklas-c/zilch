<u>Merchant</u>

*CMP (AdTech)*
- CMP steel thread well under way — ad-decisions endpoint, DynamoDB campaign-cache, and creative CDN (S3 + CloudFront) all built and working in dev.
- Audience-service work paused pending data team meeting to clarify whether a dedicated service is needed.
- **In Progress**: S3 reporting bucket and Firehose delivery stream.

*Sponsored Search*
- Retailer Search Suggestions component and enriched UI both done pending release.
- **In Progress**: AdMarketplace Search Auction API investigation (Sponsored Search v2).

*Sponsored Search v2: Images*
- Sponsored image and headline support released to production.
- Admin-service image/headline integration completed.
- Images A/B test planned for 19 Nov to 3 Dec. Migration starting w/c 2 Nov; brand images being prepared for 9 retailers.
- **In Progress**: Campaign image override (FE + admin portal), image cards in search results FE, E2E tests.

*Post Purchase Offers*
- Swapped in ahead of Embedded Web View investigation following priority refresh.
- **In Progress**: Displaying offers on the Upcoming payments receipt.

*Commercial*
- Hero Banner test showing +40% GMV for promoted retailers — first sign of ROAS. Test being extended for halo effects.
- Paid Brand Defence shipped, ready to sell from early Nov.

*KTLO*
- Rokt SDK bug-fix update completed.
- Quidco integration tests switched to WireMock — resolving recurring sandbox timeout issues in non-prod environments.
- E2E stability hardening for retailer API test suite completed - now passing at 100% reliably
- **In Progress**: Android storefront carousel scrolling defect.
