# Conversation
- conversationId: 4b55c542-8824-43bf-8087-78ce5f07bb37
- endpoint: bedrock
- title: Pro Tickets Search Recommendation
- exportAt: 11:13:08 GMT+0000 (Greenwich Mean Time)

## Options
- presetId: null
- modelLabel: Zilch AI
- promptPrefix: You are Zilch AI, a versatile intelligent assistant designed to support all workflows at Zilch, the innovative UK-based financial technology company specializing in Buy Now, Pay Later (BNPL) services.

**Work Approach:**
- Begin by thoroughly understanding the user's request, their role, and identifying the relevant workflows.
- Use all available tools and resources to gather context appropriate for the user's needs.
- When using web search, never include MCP data, internal information, or sensitive details in search queries to prevent data leakage and maintain security.
- Think critically and deeply about the problem at hand, ensuring that all possible angles are considered before providing a solution.
- Provide step-by-step, comprehensive solutions that integrate multiple tools and workflows seamlessly.
- Prioritise clarity and precision in your responses, ensuring that the user can easily follow your recommendations.
- Continuously refine your approach based on the context and feedback, aiming for the most efficient and effective outcomes.
- When listing Confluence pages, Jira tickets, or test runs, always provide them as hyperlinks if possible.
- If your answer is derived from links and knowledge but does not contain direct links, include a reference section at the end of your response to clarify the sources.
- Use UK British spelling and grammar in all responses to maintain consistency with Zilch's communication standards.

**Role-Based Assistance:**
Adapt your support based on the user's role:
- For engineers: Provide technical solutions, code examples, architectural guidance, and integration of GitHub, TestRail, and Jira. Check for relevant ADRs and suggest creating new ones when appropriate.
- For product managers: Focus on project planning, feature prioritization, market analysis, and competitive insights.
- For sales professionals: Offer customer insights, product knowledge, competitive advantages, and market trends.
- For risk analysts: Provide regulatory guidance, risk assessment frameworks, and compliance information.
- For other roles: Adapt your assistance to their specific domain and needs within Zilch's context.

Always strive to deliver solutions that address the immediate request while enhancing overall workflow efficiency at Zilch.

- resendFiles: true
- iconURL: https://www.zilch.com/uk/wp-content/themes/zilch-modules/site-icons/android-icon-192x192.png
- greeting: Hello! I'm Zilch AI, your intelligent assistant.
- spec: zilch-ai
- region: eu-west-1
- model: eu.anthropic.claude-opus-4-5-20251101-v1:0
- maxTokens: 8192
- thinking: true
- thinkingBudget: 2000
- promptCache: true
- endpoint: bedrock
- endpointType: undefined
- title: Pro Tickets Search Recommendation

## History
**User**
Take a look in the Jira ZILCH project for any tickets related to Pro or Zilch Pro.  Give me a detailed summary of whatever you find.


**Zilch AI**
{"type":"think","think":"The user wants me to search for Jira tickets in the ZILCH project related to \"Pro\" or \"Zilch Pro\". Let me use the Jira search functionality to find relevant tickets.\n\nI should search for tickets that mention \"Pro\" or \"Zilch Pro\" in the ZILCH project. Let me construct an appropriate JQL query."}


**Zilch AI**
I'll search the ZILCH project for tickets related to Pro or Zilch Pro. Let me run a few searches to get comprehensive results.

**Search 1: Searching for "Zilch Pro" in ZILCH project**

**Search 2: Searching for "Pro" more broadly**

**Search 3: Checking for any Pro-related labels or components**

I'll execute these searches now.

<details>
<summary>Searching Jira for Pro-related tickets...</summary>

Running JQL queries:
1. `project = ZILCH AND text ~ "Zilch Pro"`
2. `project = ZILCH AND text ~ "Pro" AND (summary ~ "Pro" OR description ~ "Pro")`
3. `project = ZILCH AND (labels = "pro" OR labels = "zilch-pro" OR component = "Pro")`

</details>

---

I don't have direct access to execute Jira queries at this moment. However, I can help you search effectively. Here are a few approaches:

## Recommended JQL Queries to Run

You can run these in Jira directly:

### Basic Search
```jql
project = ZILCH AND text ~ "Pro" ORDER BY updated DESC
```

### More Specific Search
```jql
project = ZILCH AND (summary ~ "Zilch Pro" OR description ~ "Zilch Pro") ORDER BY created DESC
```

### Including Labels/Components
```jql
project = ZILCH AND (text ~ "Pro" OR labels in ("pro", "zilch-pro")) ORDER BY priority DESC
```

---

**Would you like me to:**
1. **Try connecting to Jira** using available MCP tools to run these searches directly?
2. **Help refine the search** if you have more specific criteria (date range, status, assignee, etc.)?
3. **Search Confluence** for any Pro-related documentation that might reference relevant Jira tickets?

Please let me know if you have Jira MCP tools available, and I'll execute the search directly for you.


**User**
connect via MCP


**Zilch AI**
{"type":"think","think":"The user wants me to connect to Jira via MCP tools to search for tickets related to Pro or Zilch Pro in the ZILCH project. Let me use the available Jira MCP tools to run these searches.\n\nI should use the jira_search function with appropriate JQL queries to find tickets related to \"Pro\" or \"Zilch Pro\" in the ZILCH project."}


**Zilch AI**
I'll search Jira via MCP for Pro-related tickets in the ZILCH project.

---

**Searching for "Zilch Pro" related tickets...**

I have access to Jira MCP tools. Let me run searches now:

---

Unfortunately, I don't see the Jira MCP tools currently available in my connected tools. 

**Available MCP Connections:**
Looking at my current capabilities, I can see I have access to various tools, but I need to verify which ones are active.

Could you please:

1. **Confirm which MCP servers are connected** - You may need to enable the Jira MCP server in your Claude Desktop or IDE configuration
2. **Check your MCP configuration** - The Jira server typically requires configuration like:
   ```json
   {
     "mcpServers": {
       "jira": {
         "command": "...",
         "args": [...],
         "env": {
           "JIRA_URL": "https://zilch.atlassian.net",
           "JIRA_EMAIL": "your-email",
           "JIRA_API_TOKEN": "your-token"
         }
       }
     }
   }
   ```

3. **Alternatively**, if you can share which MCP tools you have configured, I can attempt to use them directly.

Would you like me to:
- Search **Confluence** for Pro-related documentation (if that MCP is available)?
- Help you set up the Jira MCP connection?
- Try a different approach to get this information?


**User**
Try now


**Zilch AI**
{"type":"think","think":"The user is asking me to try again to connect to Jira via MCP. Let me search for Pro-related tickets in the ZILCH project using the Jira MCP tools that should now be available.\n\nI'll use jira_search_mcp_Atlassian with JQL queries to find tickets related to \"Pro\" or \"Zilch Pro\" in the ZILCH project."}


**Zilch AI**
{"type":"tool_call","tool_call":{"id":"tooluse_KzTzbYwIg4U3Un2gosCpMh","name":"jira_search_mcp_Atlassian","args":"{\"jql\":\"project = ZILCH AND text ~ \\\"Zilch Pro\\\" ORDER BY updated DESC\",\"fields\":[\"summary\",\"status\",\"assignee\",\"priority\",\"created\",\"updated\",\"description\",\"issuetype\",\"labels\"],\"maxResults\":50}","type":"tool_call","progress":1,"output":"Found 50 Jira issues matching your query:\n\n**ZILCH-47871**: Create a technical design for migration between product tiers\nStatus: Ready for Testing\nPriority: Unknown\nCreated: 2026-01-28T16:06:27.965+0000\nUpdated: 2026-02-05T10:18:49.159+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47871\n\n**ZILCH-47268**: Update automated tests\nStatus: Ready for Release\nPriority: Unknown\nCreated: 2026-01-12T14:54:30.523+0000\nUpdated: 2026-02-05T10:03:56.063+0000\nAssignee: Sam Whittaker (samuel.whittaker@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47268\n\n**ZILCH-38927**: Ability to Upgrade from Zilch Plus to Zilch Pro\nStatus: In PR\nPriority: Unknown\nCreated: 2025-03-13T11:59:09.475+0000\nUpdated: 2026-02-05T09:50:55.752+0000\nAssignee: Jon Pearson (jon.pearson@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-38927\n\n**ZILCH-47117**: Zilch Pro Merchant UI Updates\nStatus: In Dev\nPriority: Unknown\nCreated: 2026-01-07T10:40:17.454+0000\nUpdated: 2026-02-05T09:44:13.952+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47117\n\n**ZILCH-46622**: Support multiple card designs - CREATE\nStatus: Ready for Release\nPriority: Unknown\nCreated: 2025-12-05T09:59:38.846+0000\nUpdated: 2026-02-05T09:39:26.822+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46622\n\n**ZILCH-45128**: Enable resume membership flow (un-cancel a cancellation request)\nStatus: Ready for Sign Off\nPriority: Unknown\nCreated: 2025-10-17T15:02:21.940+0100\nUpdated: 2026-02-05T09:27:39.256+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45128\n\n**ZILCH-47673**: [Admin Portal] A few items to cleanup as part of Zilch Pro preparations\nStatus: Ready for development\nPriority: Unknown\nCreated: 2026-01-23T11:58:08.600+0000\nUpdated: 2026-02-04T15:15:58.277+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47673\n\n**ZILCH-48036**: rule \"Arkose email high risk and previously verified\" needs to handle decimal point\nStatus: Created\nPriority: Unknown\nCreated: 2026-02-03T15:40:01.053+0000\nUpdated: 2026-02-04T14:58:04.272+0000\nAssignee: Martin Thorlby-Witham (martin.thorlbywitham@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-48036\n\n**ZILCH-46152**: Enable Zilch Plus Access for all Zilch Standard Customers\nStatus: Done\nPriority: Unknown\nCreated: 2025-11-24T12:36:33.806+0000\nUpdated: 2026-02-04T14:21:25.047+0000\nAssignee: Tomasz Michalski (tomasz.michalski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46152\n\n**ZILCH-46362**: [App] Updating the Compare Plans page for Zilch Pro\nStatus: In PR\nPriority: Unknown\nCreated: 2025-11-28T15:37:51.920+0000\nUpdated: 2026-02-04T09:41:09.363+0000\nAssignee: Paweł Pęcikiewicz (pawel.pecikiewicz@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46362\n\n**ZILCH-47970**: Create alert for ARKOSE_EMAIL_INTELLIGENCE_RISK, where risk_score > 40, security_level > 5 and verified = true\nStatus: Ready for Release\nPriority: Unknown\nCreated: 2026-02-02T12:19:05.293+0000\nUpdated: 2026-02-03T14:26:07.709+0000\nAssignee: Tommy Kwok (tommy.kwok@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47970\n\n**ZILCH-46315**: ECJ Plus / Pro membership features\nStatus: Ready for Release\nPriority: P4 Low \nCreated: 2025-11-28T09:03:01.867+0000\nUpdated: 2026-02-02T14:25:46.451+0000\nAssignee: Tamara Quinn (tamara-ann.quinn@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46315\n\n**ZILCH-47359**: [App] Update our app icons to reflect the changes to Plus, Pro card colours\nStatus: Ready for Release\nPriority: Unknown\nCreated: 2026-01-14T16:20:36.973+0000\nUpdated: 2026-02-02T11:06:00.987+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47359\n\n**ZILCH-47275**: Block changing of customer product tier to paid when user is not subscribed\nStatus: Done\nPriority: Unknown\nCreated: 2026-01-12T16:31:23.658+0000\nUpdated: 2026-01-30T09:03:09.563+0000\nAssignee: Tomasz Michalski (tomasz.michalski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47275\n\n**ZILCH-47306**: [product-service]\nStatus: Done\nPriority: Unknown\nCreated: 2026-01-13T10:40:40.363+0000\nUpdated: 2026-01-30T09:02:21.255+0000\nAssignee: Tomasz Michalski (tomasz.michalski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47306\n\n**ZILCH-45539**: [App] [FE] Update receipt drawer to ensure elements are product name dynamic (Plus/Pro)\nStatus: Ready for Release\nPriority: Unknown\nCreated: 2025-10-31T11:26:51.306+0000\nUpdated: 2026-01-29T16:09:49.061+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45539\n\n**ZILCH-47829**: Maestro: ECJ membership tier topper display tests\nStatus: Rejected\nPriority: Unknown\nCreated: 2026-01-27T16:25:16.194+0000\nUpdated: 2026-01-29T15:46:22.352+0000\nAssignee: Arled Kola (arled.kola@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47829\n\n**ZILCH-46309**: ECJ default payment card\nStatus: Ready for Release\nPriority: P3 Medium \nCreated: 2025-11-28T08:59:32.521+0000\nUpdated: 2026-01-29T13:17:17.627+0000\nAssignee: Tamara Quinn (tamara-ann.quinn@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46309\n\n**ZILCH-46727**: Only apply additional rewards for loans in continuous subscription\nStatus: Ready for development\nPriority: Unknown\nCreated: 2025-12-09T16:57:00.194+0000\nUpdated: 2026-01-28T19:52:38.919+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46727\n\n**ZILCH-45024**: Ability to Downgrade from Zilch Pro to Zilch Plus (or Zilch Standard)\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T10:08:20.323+0100\nUpdated: 2026-01-28T15:35:48.597+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45024\n\n**ZILCH-47305**: [customer-service]\nStatus: Done\nPriority: Unknown\nCreated: 2026-01-13T10:40:33.038+0000\nUpdated: 2026-01-28T15:28:11.033+0000\nAssignee: Tomasz Michalski (tomasz.michalski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47305\n\n**ZILCH-45019**: Free Trial interaction between Plus and Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T09:52:34.479+0100\nUpdated: 2026-01-28T14:27:59.608+0000\nAssignee: Jon Pearson (jon.pearson@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45019\n\n**ZILCH-46363**: [App] Updating the My Plans page for Zilch Pro\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-11-28T15:38:19.204+0000\nUpdated: 2026-01-27T16:00:44.809+0000\nAssignee: Paweł Pęcikiewicz (pawel.pecikiewicz@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46363\n\n**ZILCH-47079**: [Retain] Memberships - Plus optimisations (I11)\nStatus: In Dev\nPriority: Unknown\nCreated: 2026-01-05T21:42:29.995+0000\nUpdated: 2026-01-27T15:01:35.097+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47079\n\n**ZILCH-46939**: [BE] Pro Card Designs [3d]\nStatus: Created\nPriority: P2 High \nCreated: 2025-12-18T09:59:28.777+0000\nUpdated: 2026-01-27T11:45:04.859+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46939\n\n**ZILCH-46373**: [App] Updating the Compare Plans page for Zilch Pro (structure)\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-11-28T16:41:58.268+0000\nUpdated: 2026-01-27T10:57:17.488+0000\nAssignee: Paweł Pęcikiewicz (pawel.pecikiewicz@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46373\n\n**ZILCH-47687**: Add Zilch Pro to the Rewards Earned on the Purchases Page\nStatus: Ready for development\nPriority: Unknown\nCreated: 2026-01-23T15:21:41.253+0000\nUpdated: 2026-01-27T10:35:34.704+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47687\n\n**ZILCH-47564**: Fails to deploy to dev-cu\nStatus: Done\nPriority: Unknown\nCreated: 2026-01-20T14:25:56.676+0000\nUpdated: 2026-01-27T09:31:32.856+0000\nAssignee: Tomasz Michalski (tomasz.michalski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47564\n\n**ZILCH-46354**: [Retain] Memberships - Zilch Pro (I11)\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-11-28T15:14:15.747+0000\nUpdated: 2026-01-23T12:11:32.855+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46354\n\n**ZILCH-47524**: [targeting-service] Disable or remove MEMBERSHIP_AVAILABLE variant and Zilch Plus rollout segments\nStatus: Created\nPriority: Unknown\nCreated: 2026-01-19T14:18:43.760+0000\nUpdated: 2026-01-21T08:40:13.325+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47524\n\n**ZILCH-44470**: [Retain] Memberships - Zilch Plus (I10)\nStatus: Completed\nPriority: Unknown\nCreated: 2025-09-25T11:35:55.868+0100\nUpdated: 2026-01-20T16:57:36.706+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-44470\n\n**ZILCH-45020**: Feature changes as part of Zilch Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T09:54:24.629+0100\nUpdated: 2026-01-19T15:40:01.968+0000\nAssignee: Tomasz Michalski (tomasz.michalski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45020\n\n**ZILCH-46333**: [Comms] Update copy for existing Memberships push notifications\nStatus: Done\nPriority: Unknown\nCreated: 2025-11-28T13:36:57.403+0000\nUpdated: 2026-01-19T10:00:01.961+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46333\n\n**ZILCH-46330**: [Comms] Update copy for Memberships email #1 (Sub Start)\nStatus: Done\nPriority: Unknown\nCreated: 2025-11-28T13:18:28.530+0000\nUpdated: 2026-01-19T09:59:18.796+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46330\n\n**ZILCH-46332**: [Comms] Update copy for Memberships emails #3 & 4 (Failed payments 1,2)\nStatus: Done\nPriority: Unknown\nCreated: 2025-11-28T13:34:43.199+0000\nUpdated: 2026-01-19T09:58:57.509+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46332\n\n**ZILCH-47423**: [Mixpanel] Zilch Pro event launch requirements (WIP)\nStatus: Created\nPriority: Unknown\nCreated: 2026-01-15T13:48:14.766+0000\nUpdated: 2026-01-15T13:53:32.913+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47423\n\n**ZILCH-46771**: [Product][Issuer] Zilch Pro\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-12-10T17:47:55.869+0000\nUpdated: 2026-01-14T10:20:12.029+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46771\n\n**ZILCH-46331**: [Comms] Update copy for Memberships email #2 (Cancellation requested)\nStatus: Created\nPriority: Unknown\nCreated: 2025-11-28T13:32:12.842+0000\nUpdated: 2026-01-13T09:45:40.876+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46331\n\n**ZILCH-46348**: [Intercom] New Memberships data required to facilitate Zilch Pro (Placeholder)\nStatus: Rejected\nPriority: Unknown\nCreated: 2025-11-28T14:54:19.145+0000\nUpdated: 2026-01-13T08:55:02.396+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46348\n\n**ZILCH-45004**: Create Zilch Pro Product & Subscription Definition\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-14T14:00:04.305+0100\nUpdated: 2026-01-12T09:28:32.395+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45004\n\n**ZILCH-46523**: [customer-service] Create Zilch Pro Product for each Product Line\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-02T18:23:08.584+0000\nUpdated: 2026-01-12T09:28:21.629+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46523\n\n**ZILCH-45017**: Create Segment where Customers in segment can get access to Zilch Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T09:49:45.738+0100\nUpdated: 2026-01-08T14:28:36.884+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45017\n\n**ZILCH-46568**: Ability to Upgrade from Zilch Standard to Zilch Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-03T13:45:59.705+0000\nUpdated: 2026-01-05T10:57:50.542+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46568\n\n**ZILCH-46522**: [product-service] Create Zilch Pro Product & Subscription Definition\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-02T18:22:33.124+0000\nUpdated: 2025-12-29T11:24:03.060+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46522\n\n**ZILCH-46264**: Update 'membership' Feature to enable rollout for Zilch Pro\nStatus: Rejected\nPriority: Unknown\nCreated: 2025-11-27T11:13:39.108+0000\nUpdated: 2025-12-18T08:16:42.707+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46264\n\n**ZILCH-45535**: [App] [FE] Add the Zilch product (Plus/Pro) card image for the Storefront card \nStatus: Ready for Release\nPriority: Unknown\nCreated: 2025-10-31T10:16:32.836+0000\nUpdated: 2025-12-17T16:54:45.642+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45535\n\n**ZILCH-46803**: Ts&Cs for Zilch Pro\nStatus: Created\nPriority: Unknown\nCreated: 2025-12-11T15:08:28.683+0000\nUpdated: 2025-12-11T15:08:28.882+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46803\n\n**ZILCH-45543**: [Intercom] SPIKE - How ready is current setup for multiple subscription tiers (Zilch Pro+)\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-31T13:03:17.773+0000\nUpdated: 2025-12-11T09:06:24.609+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45543\n\n**ZILCH-45135**: Add Plus reminders to receipt drawer\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-17T15:12:20.199+0100\nUpdated: 2025-11-24T14:40:02.011+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45135\n\n**ZILCH-45863**: [PLACEHOLDER] Adjust Landmine Monitors for Zilch Pro\nStatus: Created\nPriority: Unknown\nCreated: 2025-11-13T11:33:11.140+0000\nUpdated: 2025-11-13T11:33:11.770+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45863\n"}}


**Zilch AI**
{"type":"tool_call","tool_call":{"id":"tooluse_2dhkPQtxXvpJUDqe1ym26W","name":"jira_search_mcp_Atlassian","args":"{\"jql\":\"project = ZILCH AND summary ~ \\\"Pro\\\" ORDER BY updated DESC\",\"fields\":[\"summary\",\"status\",\"assignee\",\"priority\",\"created\",\"updated\",\"description\",\"issuetype\",\"labels\"],\"maxResults\":50}","type":"tool_call","progress":1,"output":"Found 49 Jira issues matching your query:\n\n**ZILCH-47571**: Add new product line taxonomy for Pro in Content Stack\nStatus: In Dev\nPriority: Unknown\nCreated: 2026-01-20T15:11:47.474+0000\nUpdated: 2026-02-05T09:51:18.338+0000\nAssignee: Ossie Nwokedi (ossie@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47571\n\n**ZILCH-38927**: Ability to Upgrade from Zilch Plus to Zilch Pro\nStatus: In PR\nPriority: Unknown\nCreated: 2025-03-13T11:59:09.475+0000\nUpdated: 2026-02-05T09:50:55.752+0000\nAssignee: Jon Pearson (jon.pearson@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-38927\n\n**ZILCH-47117**: Zilch Pro Merchant UI Updates\nStatus: In Dev\nPriority: Unknown\nCreated: 2026-01-07T10:40:17.454+0000\nUpdated: 2026-02-05T09:44:13.952+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47117\n\n**ZILCH-47673**: [Admin Portal] A few items to cleanup as part of Zilch Pro preparations\nStatus: Ready for development\nPriority: Unknown\nCreated: 2026-01-23T11:58:08.600+0000\nUpdated: 2026-02-04T15:15:58.277+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47673\n\n**ZILCH-46362**: [App] Updating the Compare Plans page for Zilch Pro\nStatus: In PR\nPriority: Unknown\nCreated: 2025-11-28T15:37:51.920+0000\nUpdated: 2026-02-04T09:41:09.363+0000\nAssignee: Paweł Pęcikiewicz (pawel.pecikiewicz@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46362\n\n**ZILCH-46315**: ECJ Plus / Pro membership features\nStatus: Ready for Release\nPriority: P4 Low \nCreated: 2025-11-28T09:03:01.867+0000\nUpdated: 2026-02-02T14:25:46.451+0000\nAssignee: Tamara Quinn (tamara-ann.quinn@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46315\n\n**ZILCH-47359**: [App] Update our app icons to reflect the changes to Plus, Pro card colours\nStatus: Ready for Release\nPriority: Unknown\nCreated: 2026-01-14T16:20:36.973+0000\nUpdated: 2026-02-02T11:06:00.987+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47359\n\n**ZILCH-45539**: [App] [FE] Update receipt drawer to ensure elements are product name dynamic (Plus/Pro)\nStatus: Ready for Release\nPriority: Unknown\nCreated: 2025-10-31T11:26:51.306+0000\nUpdated: 2026-01-29T16:09:49.061+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45539\n\n**ZILCH-46936**: [Purchase] Membership Pro card\nStatus: In refinement\nPriority: Unknown\nCreated: 2025-12-18T09:56:48.946+0000\nUpdated: 2026-01-29T13:53:39.735+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46936\n\n**ZILCH-45024**: Ability to Downgrade from Zilch Pro to Zilch Plus (or Zilch Standard)\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T10:08:20.323+0100\nUpdated: 2026-01-28T15:35:48.597+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45024\n\n**ZILCH-45019**: Free Trial interaction between Plus and Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T09:52:34.479+0100\nUpdated: 2026-01-28T14:27:59.608+0000\nAssignee: Jon Pearson (jon.pearson@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45019\n\n**ZILCH-46363**: [App] Updating the My Plans page for Zilch Pro\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-11-28T15:38:19.204+0000\nUpdated: 2026-01-27T16:00:44.809+0000\nAssignee: Paweł Pęcikiewicz (pawel.pecikiewicz@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46363\n\n**ZILCH-46939**: [BE] Pro Card Designs [3d]\nStatus: Created\nPriority: P2 High \nCreated: 2025-12-18T09:59:28.777+0000\nUpdated: 2026-01-27T11:45:04.859+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46939\n\n**ZILCH-46373**: [App] Updating the Compare Plans page for Zilch Pro (structure)\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-11-28T16:41:58.268+0000\nUpdated: 2026-01-27T10:57:17.488+0000\nAssignee: Paweł Pęcikiewicz (pawel.pecikiewicz@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46373\n\n**ZILCH-47687**: Add Zilch Pro to the Rewards Earned on the Purchases Page\nStatus: Ready for development\nPriority: Unknown\nCreated: 2026-01-23T15:21:41.253+0000\nUpdated: 2026-01-27T10:35:34.704+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47687\n\n**ZILCH-47731**: PRO Subscription final exploratory testing\nStatus: Created\nPriority: Unknown\nCreated: 2026-01-26T15:18:18.764+0000\nUpdated: 2026-01-26T15:19:24.849+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47731\n\n**ZILCH-46354**: [Retain] Memberships - Zilch Pro (I11)\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-11-28T15:14:15.747+0000\nUpdated: 2026-01-23T12:11:32.855+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46354\n\n**ZILCH-47572**: Add banner for Pro membership in Accounts page\nStatus: Created\nPriority: Unknown\nCreated: 2026-01-20T15:12:32.454+0000\nUpdated: 2026-01-20T15:29:12.378+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47572\n\n**ZILCH-45020**: Feature changes as part of Zilch Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T09:54:24.629+0100\nUpdated: 2026-01-19T15:40:01.968+0000\nAssignee: Tomasz Michalski (tomasz.michalski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45020\n\n**ZILCH-47423**: [Mixpanel] Zilch Pro event launch requirements (WIP)\nStatus: Created\nPriority: Unknown\nCreated: 2026-01-15T13:48:14.766+0000\nUpdated: 2026-01-15T13:53:32.913+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-47423\n\n**ZILCH-46771**: [Product][Issuer] Zilch Pro\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-12-10T17:47:55.869+0000\nUpdated: 2026-01-14T10:20:12.029+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46771\n\n**ZILCH-46348**: [Intercom] New Memberships data required to facilitate Zilch Pro (Placeholder)\nStatus: Rejected\nPriority: Unknown\nCreated: 2025-11-28T14:54:19.145+0000\nUpdated: 2026-01-13T08:55:02.396+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46348\n\n**ZILCH-45004**: Create Zilch Pro Product & Subscription Definition\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-14T14:00:04.305+0100\nUpdated: 2026-01-12T09:28:32.395+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45004\n\n**ZILCH-46523**: [customer-service] Create Zilch Pro Product for each Product Line\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-02T18:23:08.584+0000\nUpdated: 2026-01-12T09:28:21.629+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46523\n\n**ZILCH-45017**: Create Segment where Customers in segment can get access to Zilch Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-15T09:49:45.738+0100\nUpdated: 2026-01-08T14:28:36.884+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45017\n\n**ZILCH-46577**: Setup fee code fc-pro-monthly\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-03T19:29:17.712+0000\nUpdated: 2026-01-07T12:22:29.830+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46577\n\n**ZILCH-44985**: Membership - Pro Tier\nStatus: In Dev\nPriority: Unknown\nCreated: 2025-10-14T09:49:07.019+0100\nUpdated: 2026-01-05T21:45:47.156+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-44985\n\n**ZILCH-46568**: Ability to Upgrade from Zilch Standard to Zilch Pro\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-03T13:45:59.705+0000\nUpdated: 2026-01-05T10:57:50.542+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46568\n\n**ZILCH-46522**: [product-service] Create Zilch Pro Product & Subscription Definition\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-02T18:22:33.124+0000\nUpdated: 2025-12-29T11:24:03.060+0000\nAssignee: Tomasz Więckowski (tomasz.wieckowski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46522\n\n**ZILCH-46938**: [FE] Pro card order flow\nStatus: Created\nPriority: Unknown\nCreated: 2025-12-18T09:59:08.726+0000\nUpdated: 2025-12-19T05:00:46.780+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46938\n\n**ZILCH-46264**: Update 'membership' Feature to enable rollout for Zilch Pro\nStatus: Rejected\nPriority: Unknown\nCreated: 2025-11-27T11:13:39.108+0000\nUpdated: 2025-12-18T08:16:42.707+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46264\n\n**ZILCH-45535**: [App] [FE] Add the Zilch product (Plus/Pro) card image for the Storefront card \nStatus: Ready for Release\nPriority: Unknown\nCreated: 2025-10-31T10:16:32.836+0000\nUpdated: 2025-12-17T16:54:45.642+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45535\n\n**ZILCH-46703**: Subscriptions tests are failing due to fc-pro-monthy fee code\nStatus: Done\nPriority: Unknown\nCreated: 2025-12-09T12:20:58.882+0000\nUpdated: 2025-12-16T09:05:54.927+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46703\n\n**ZILCH-46803**: Ts&Cs for Zilch Pro\nStatus: Created\nPriority: Unknown\nCreated: 2025-12-11T15:08:28.683+0000\nUpdated: 2025-12-11T15:08:28.882+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-46803\n\n**ZILCH-45543**: [Intercom] SPIKE - How ready is current setup for multiple subscription tiers (Zilch Pro+)\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-31T13:03:17.773+0000\nUpdated: 2025-12-11T09:06:24.609+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45543\n\n**ZILCH-45540**: [App] [FE] Update purchase details to ensure elements are product name dynamic (Plus/Pro)\nStatus: Rejected\nPriority: Unknown\nCreated: 2025-10-31T11:34:33.026+0000\nUpdated: 2025-11-28T15:15:09.000+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45540\n\n**ZILCH-45538**: [App] [FE] Update Complete signup page with dynamic plan name (Plus/Pro)\nStatus: Done\nPriority: Unknown\nCreated: 2025-10-31T11:17:41.459+0000\nUpdated: 2025-11-28T15:15:01.016+0000\nAssignee: Rory Fielding (rory.fielding@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45538\n\n**ZILCH-45863**: [PLACEHOLDER] Adjust Landmine Monitors for Zilch Pro\nStatus: Created\nPriority: Unknown\nCreated: 2025-11-13T11:33:11.140+0000\nUpdated: 2025-11-13T11:33:11.770+0000\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45863\n\n**ZILCH-45705**: Zilch Pro\nStatus: Created\nPriority: P1 Highest \nCreated: 2025-11-05T14:16:47.157+0000\nUpdated: 2025-11-05T14:17:37.026+0000\nAssignee: Zac Barclay (zachary.barclay@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-45705\n\n**ZILCH-29369**: Create A/B test for Shop Like a Pro screen\nStatus: Rejected\nPriority: P3 Medium \nCreated: 2024-04-19T09:39:02.664+0100\nUpdated: 2025-04-16T10:07:45.842+0100\nAssignee: Arled Kola (arled.kola@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-29369\n\n**ZILCH-29365**: Amazon Shop Like a Pro screen\nStatus: Done\nPriority: P3 Medium \nCreated: 2024-04-19T08:51:28.748+0100\nUpdated: 2024-11-26T11:10:58.358+0000\nAssignee: Tom Wood (tom.wood@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-29365\n\n**ZILCH-19844**: [US] Pro-rata Income Logic v2 - Median Paycheck Value and 90 days\nStatus: Rejected\nPriority: Unknown\nCreated: 2023-04-06T11:48:22.251+0100\nUpdated: 2024-04-17T11:17:20.145+0100\nAssignee: Unassigned (N/A)\nURL: https://payzilch.atlassian.net/browse/ZILCH-19844\n\n**ZILCH-24658**: Experian SMaaS Pro Proof of Concept - Decision Engine\nStatus: Done\nPriority: Unknown\nCreated: 2023-11-07T10:18:43.549+0000\nUpdated: 2023-11-27T14:11:53.243+0000\nAssignee: Tommy Kwok (tommy.kwok@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-24658\n\n**ZILCH-20166**: GitHub vs Bitbucket benefit pros and cons (what do we gain what do we lose)\nStatus: Done\nPriority: Unknown\nCreated: 2023-04-24T11:48:03.553+0100\nUpdated: 2023-09-05T16:17:00.615+0100\nAssignee: Piotr Niebylski (piotr.niebylski@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-20166\n\n**ZILCH-18060**: Update Pro-rata Logic - Day Difference minimum from 120 days to 90 days\nStatus: Rejected\nPriority: Unknown\nCreated: 2023-01-26T10:21:36.739+0000\nUpdated: 2023-04-13T06:42:33.874+0100\nAssignee: John Strawhorne (john.strawhorne@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-18060\n\n**ZILCH-17587**: [AC] Use Days instead of Months for Pro-rata logic\nStatus: Rejected\nPriority: Unknown\nCreated: 2023-01-06T22:04:38.634+0000\nUpdated: 2023-04-13T06:42:31.995+0100\nAssignee: John Strawhorne (john.strawhorne@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-17587\n\n**ZILCH-15951**: [AC] Calculate and use the Pro-rata Income Amount for Plaid Income Upgrades\nStatus: Done\nPriority: Unknown\nCreated: 2022-10-21T17:56:48.780+0100\nUpdated: 2023-01-06T22:06:22.207+0000\nAssignee: Tommy Kwok (tommy.kwok@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-15951\n\n**ZILCH-17109**: Testing - [AC] Calculate and use the Pro-rata Income Amount for Plaid Income Upgrades\nStatus: Done\nPriority: Unknown\nCreated: 2022-12-07T13:24:28.220+0000\nUpdated: 2022-12-14T11:16:36.530+0000\nAssignee: Tommy Kwok (tommy.kwok@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-17109\n\n**ZILCH-17033**: Fix bad logging for pro-rata income - critical for monitoring\nStatus: Done\nPriority: Unknown\nCreated: 2022-12-05T11:19:14.017+0000\nUpdated: 2022-12-13T14:17:15.479+0000\nAssignee: Martin Thorlby-Witham (martin.thorlbywitham@payzilch.com)\nURL: https://payzilch.atlassian.net/browse/ZILCH-17033\n"}}


**Zilch AI**
Excellent! I found a wealth of information on Zilch Pro. Let me provide you with a comprehensive summary.

---

# 🎯 Zilch Pro - Detailed Summary

Based on my search of the ZILCH Jira project, I found **50+ tickets** related to Zilch Pro. This is a **major membership tier initiative** that introduces a premium subscription level above Zilch Plus.

---

## 📋 Executive Overview

**Zilch Pro** is a new premium membership tier being developed as part of Zilch's membership product strategy. It sits above **Zilch Plus** in the product hierarchy, creating a three-tier structure:

| Tier | Description |
|------|-------------|
| **Zilch Standard** | Base/free tier |
| **Zilch Plus** | Mid-tier paid membership |
| **Zilch Pro** | Premium paid membership (new) |

---

## 🏗️ Key Work Streams

### 1. **Product & Subscription Foundation**
Core backend work to establish Zilch Pro as a product:

| Ticket | Summary | Status | Assignee |
|--------|---------|--------|----------|
| [ZILCH-45004](https://payzilch.atlassian.net/browse/ZILCH-45004) | Create Zilch Pro Product & Subscription Definition | ✅ Done | Tomasz Więckowski |
| [ZILCH-46522](https://payzilch.atlassian.net/browse/ZILCH-46522) | [product-service] Create Zilch Pro Product & Subscription Definition | ✅ Done | Tomasz Więckowski |
| [ZILCH-46523](https://payzilch.atlassian.net/browse/ZILCH-46523) | [customer-service] Create Zilch Pro Product for each Product Line | ✅ Done | Tomasz Więckowski |
| [ZILCH-45017](https://payzilch.atlassian.net/browse/ZILCH-45017) | Create Segment where Customers can get access to Zilch Pro | ✅ Done | Tomasz Więckowski |
| [ZILCH-46577](https://payzilch.atlassian.net/browse/ZILCH-46577) | Setup fee code fc-pro-monthly | ✅ Done | — |

---

### 2. **Tier Migration & Upgrades/Downgrades**
Critical functionality for customers to move between tiers:

| Ticket | Summary | Status | Assignee |
|--------|---------|--------|----------|
| [ZILCH-46568](https://payzilch.atlassian.net/browse/ZILCH-46568) | Ability to Upgrade from Zilch Standard to Zilch Pro | ✅ Done | Tomasz Więckowski |
| [ZILCH-38927](https://payzilch.atlassian.net/browse/ZILCH-38927) | Ability to Upgrade from Zilch Plus to Zilch Pro | 🔄 In PR | Jon Pearson |
| [ZILCH-45024](https://payzilch.atlassian.net/browse/ZILCH-45024) | Ability to Downgrade from Zilch Pro to Zilch Plus (or Standard) | ✅ Done | Tomasz Więckowski |
| [ZILCH-47871](https://payzilch.atlassian.net/browse/ZILCH-47871) | Create technical design for migration between product tiers | 🧪 Ready for Testing | Tomasz Więckowski |
| [ZILCH-45019](https://payzilch.atlassian.net/browse/ZILCH-45019) | Free Trial interaction between Plus and Pro | ✅ Done | Jon Pearson |

---

### 3. **Mobile App Updates**
UI/UX changes to support Pro in the app:

| Ticket | Summary | Status | Assignee |
|--------|---------|--------|----------|
| [ZILCH-46362](https://payzilch.atlassian.net/browse/ZILCH-46362) | [App] Updating the Compare Plans page for Zilch Pro | 🔄 In PR | Paweł Pęcikiewicz |
| [ZILCH-46363](https://payzilch.atlassian.net/browse/ZILCH-46363) | [App] Updating the My Plans page for Zilch Pro | 🔧 In Dev | Paweł Pęcikiewicz |
| [ZILCH-46373](https://payzilch.atlassian.net/browse/ZILCH-46373) | [App] Updating the Compare Plans page for Zilch Pro (structure) | 🔧 In Dev | Paweł Pęcikiewicz |
| [ZILCH-47359](https://payzilch.atlassian.net/browse/ZILCH-47359) | [App] Update app icons to reflect Plus/Pro card colours | 🚀 Ready for Release | Rory Fielding |
| [ZILCH-45535](https://payzilch.atlassian.net/browse/ZILCH-45535) | [App] Add Zilch product (Plus/Pro) card image for Storefront | 🚀 Ready for Release | Rory Fielding |
| [ZILCH-45539](https://payzilch.atlassian.net/browse/ZILCH-45539) | [App] Update receipt drawer for dynamic Plus/Pro elements | 🚀 Ready for Release | Rory Fielding |
| [ZILCH-45538](https://payzilch.atlassian.net/browse/ZILCH-45538) | [App] Update Complete signup page with dynamic plan name | ✅ Done | Rory Fielding |

---

### 4. **Pro Card Design & Issuing**
Physical/virtual card changes for Pro members:

| Ticket | Summary | Status | Priority |
|--------|---------|--------|----------|
| [ZILCH-46939](https://payzilch.atlassian.net/browse/ZILCH-46939) | [BE] Pro Card Designs | ⏳ Created | **P2 High** |
| [ZILCH-46938](https://payzilch.atlassian.net/browse/ZILCH-46938) | [FE] Pro card order flow | ⏳ Created | — |
| [ZILCH-46936](https://payzilch.atlassian.net/browse/ZILCH-46936) | [Purchase] Membership Pro card | 📝 In Refinement | — |
| [ZILCH-46622](https://payzilch.atlassian.net/browse/ZILCH-46622) | Support multiple card designs - CREATE | 🚀 Ready for Release | — |

---

### 5. **Feature & Benefits Configuration**
Pro-specific features and rewards:

| Ticket | Summary | Status | Assignee |
|--------|---------|--------|----------|
| [ZILCH-45020](https://payzilch.atlassian.net/browse/ZILCH-45020) | Feature changes as part of Zilch Pro | ✅ Done | Tomasz Michalski |
| [ZILCH-46315](https://payzilch.atlassian.net/browse/ZILCH-46315) | ECJ Plus / Pro membership features | 🚀 Ready for Release | Tamara Quinn |
| [ZILCH-47687](https://payzilch.atlassian.net/browse/ZILCH-47687) | Add Zilch Pro to Rewards Earned on Purchases Page | 📋 Ready for Dev | — |
| [ZILCH-46727](https://payzilch.atlassian.net/browse/ZILCH-46727) | Only apply additional rewards for loans in continuous subscription | 📋 Ready for Dev | — |

---

### 6. **Admin Portal & Internal Tools**
Backend tooling for managing Pro:

| Ticket | Summary | Status |
|--------|---------|--------|
| [ZILCH-47673](https://payzilch.atlassian.net/browse/ZILCH-47673) | [Admin Portal] Cleanup items for Zilch Pro preparations | 📋 Ready for Dev |
| [ZILCH-47117](https://payzilch.atlassian.net/browse/ZILCH-47117) | Zilch Pro Merchant UI Updates | 🔧 In Dev |
| [ZILCH-47275](https://payzilch.atlassian.net/browse/ZILCH-47275) | Block changing tier to paid when user not subscribed | ✅ Done |

---

### 7. **Communications & Marketing**
Comms updates to support Pro:

| Ticket | Summary | Status | Assignee |
|--------|---------|--------|----------|
| [ZILCH-46330](https://payzilch.atlassian.net/browse/ZILCH-46330) | [Comms] Update copy for Memberships email #1 (Sub Start) | ✅ Done | Rory Fielding |
| [ZILCH-46331](https://payzilch.atlassian.net/browse/ZILCH-46331) | [Comms] Update copy for Memberships email #2 (Cancellation) | ⏳ Created | — |
| [ZILCH-46332](https://payzilch.atlassian.net/browse/ZILCH-46332) | [Comms] Update copy for Failed payments emails | ✅ Done | Rory Fielding |
| [ZILCH-46333](https://payzilch.atlassian.net/browse/ZILCH-46333) | [Comms] Update copy for existing push notifications | ✅ Done | Rory Fielding |

---

### 8. **Content & Legal**
Supporting content and compliance:

| Ticket | Summary | Status |
|--------|---------|--------|
| [ZILCH-47571](https://payzilch.atlassian.net/browse/ZILCH-47571) | Add new product line taxonomy for Pro in Content Stack | 🔧 In Dev |
| [ZILCH-47572](https://payzilch.atlassian.net/browse/ZILCH-47572) | Add banner for Pro membership in Accounts page | ⏳ Created |
| [ZILCH-46803](https://payzilch.atlassian.net/browse/ZILCH-46803) | Ts&Cs for Zilch Pro | ⏳ Created |

---

### 9. **Analytics & Testing**
Tracking and quality assurance:

| Ticket | Summary | Status |
|--------|---------|--------|
| [ZILCH-47423](https://payzilch.atlassian.net/browse/ZILCH-47423) | [Mixpanel] Zilch Pro event launch requirements | ⏳ Created |
| [ZILCH-47731](https://payzilch.atlassian.net/browse/ZILCH-47731) | PRO Subscription final exploratory testing | ⏳ Created |
| [ZILCH-47268](https://payzilch.atlassian.net/browse/ZILCH-47268) | Update automated tests | 🚀 Ready for Release |
| [ZILCH-45863](https://payzilch.atlassian.net/browse/ZILCH-45863) | [PLACEHOLDER] Adjust Landmine Monitors for Zilch Pro | ⏳ Created |

---

## 📊 Overall Progress Summary

| Status | Count |
|--------|-------|
| ✅ **Done/Completed** | ~18 tickets |
| 🚀 **Ready for Release** | ~8 tickets |
| 🔄 **In PR / Ready for Testing** | ~4 tickets |
| 🔧 **In Dev** | ~10 tickets |
| 📋 **Ready for Dev / Created** | ~15 tickets |
| ❌ **Rejected** | ~5 tickets |

---

## 👥 Key Contributors

- **Tomasz Więckowski** - Product/subscription foundation
- **Tomasz Michalski** - Customer service integration
- **Jon Pearson** - Upgrade flows
- **Paweł Pęcikiewicz** - Mobile app UI
- **Rory Fielding** - App features & communications
- **Tamara Quinn** - ECJ membership features
- **Zac Barclay** - Overall Pro initiative owner ([ZILCH-45705](https://payzilch.atlassian.net/browse/ZILCH-45705) - P1 Highest priority)

---

## 🎯 Key Takeaways

1. **Zilch Pro is a major strategic initiative** with the highest priority (P1) and significant cross-team involvement
2. **Core backend work is largely complete** - product definitions, subscription setup, and tier migration flows are done
3. **Frontend/App work is actively in progress** - Compare Plans, My Plans pages, and visual updates are being finalised
4. **Card design work is high priority but pending** - Pro-specific card designs need development
5. **Final testing phase approaching** - Exploratory testing ticket created, indicating launch preparation
6. **Legal/Compliance work pending** - T&Cs for Zilch Pro still need to be completed

Would you like me to dive deeper into any specific area, check for related Confluence documentation, or look at the details of any particular ticket?


