# subscriptions-tech 2026-02-05

This is a transcript copied from Slack channel #subscriptions-tech on 5th February 2026.  It covers conversation about memberships in general, some of which will be about Pro.

## Transcript
Rob Nelson  [11:02 AM]
Just over-running slightly - will be starting call very shortly
Rob Nelson  [11:30 AM]
Decisioning:
Released Product service 1.2.0 todayIncludes Ts and Cs document update to s3 and location in dbSolution is very basic right now and would need manual changes on website and in DB if Ts and Cs were to change - but this is fine for MVPNext billing date issue fixedCurrently working on the Staff user reward configuration.product service update to fix this will ensure the BE behaves as expectedIn order for the UI to be entirely correct, we also need a customer-service updateMaybe we don't need this for the launch as the reward % will be correctly resolved in the BE, just not displayed properly on the UI for staffPotentially explore a customer service patch if we have time Error message adjustments are also underway, working with Retain. Implementing Error codes.These error message changes will not be live for the MVP

Retain:
Working on Error message changes for the next release (after initial launch)Minor styling and copy fixes also underwayAdmin Portal changes are underway for the Cancellation buttonAiming for completion and deployment before launch dayOTA and latest version of app went live earlier this weekFAQ "Audience" needs updating before launch day

Payments:
All changes required for testing have been released into production - including next payment date on failed payment eventsRecurring payment schedule was initially switched off in productionFor testing, the schedule was activated last Friday and configured to run during office hours. 1pm every dayBefore we launch to customers, this will be changed to run in the early hours of the morning - 1amITAM/Platform will update this timing before the launch day - Monday 21st would be a good time to changePayment history is also ready and live

Merchant:
Spend rewards anywhere has an active defect open for the Web journeyThis is planned to be fixed next sprint (quality sprint) so will not be fixed for launch dayNumber of users is very low, so not an urgent priorityEnhanced debit reward toggle is planned to be turned on for all customers in production in advance of launch dayWill not be turned on before decisioning staff change is doneIf we hit launch day and decisioning change is not ready, we can turn on for everyone except staffRob Nelson  [12:15 PM]
@here - Just wanted to say, a week out from launch, the tech side is looking very good. Well done everyone for producing such high quality work!
 
Rob Nelson  [9:27 AM]
@Craig Main @Marek Chodak - Question from Data team:
is there a way going forward that we can tell from the ledger if a transaction_type = 'FEE' is snooze, membership or physical card fee?Craig Main  [9:29 AM]
Fee service contains the detail on the type of fee, not the ledger.
The snooze fees will have no fee code, and therefore do not require the join, the fee_calculation_code will be NULL.
For the other fee types, the fee table needs to be queried.[9:29 AM]select fc.* from customer.customer_ledger cl
inner join fee.fee_calculation fc on fc.reference_id = cl.fee_calculation_reference
where cl.fee_calculation_reference is not null 
  and cl.customer_id = XXXXXXX
  and cl.transaction_type = 'FEE'
order by customer_ledger_id desc[9:30 AM]Fee service likely does not yet contain fees/calculations for physical card fees.
Rob Nelson  [9:49 AM]
But what from this query specifically identifies that 3.99 fee as a subscription fee?
Andrzej Lorenz  [9:57 AM]
you need to join to fee_calculation (and likely other tables) to find fee type for a given fee_calculation_reference. @Jacek Zanko can you help answer?
Rob Nelson  [5:53 PM]
Subs is now live for all staff. Have a go and give your feedback here 
seanh  [9:41 AM]
Love the experience. Super slick, really looks great.
Rob Nelson  [9:58 AM]
@Rory Fielding @Jan Michalak @Alex Murphy - Is the banner on the homepage live that points you at memberships?
Ryan Walastyan  [1:18 PM]
is there a way of linking a subscription fee in the fee service tables back to the subscription id it is for? or to an ID in the payments.payment_collection or payment.recurring tables? (edited) 
Abhishek Chatterjee  [2:48 PM]
Minor thing, the left arrow is not skinned in dark mode.
1000062677.jpg Rob Nelson  [10:02 AM]
@George Sharpe @Kevin Came - Do we have the 10k cohort from @Kieran Patel to use in LD this week?
George Sharpe  [10:03 AM]
I got the 10k cohort from @Antony Evmorfopoulos this morning (containing myself)
Rob Nelson  [10:27 AM]
@George Sharpe - We need a couple of product service releases today and we are hoping for a customer-service patch deployment tomorrow as well. Decisioning are working on this
George Sharpe  [10:27 AM]
Nice
Rob Nelson  [2:30 PM]
Hi All - we have completed a first run through of a "Pre-Mortem" for the subscriptions launch.
Please add any thoughts you have to this Miro: https://miro.com/app/board/uXjVJcYnovA=/
@Marcin Żołna @Nicklas Chapman @Mike Davis @Andrzej Lorenz - Please take into account any orange notes in this board as they require actions from your teams to set up monitoring/alerting.
Rob Nelson  [10:21 AM]
@here - we are about to switch on the enhanced debit reward toggle for everyone except staff in production.
Please keep an eye on logs and monitors during this change.Ryan Walastyan  [10:24 AM]
is there a subscriptions table that gives the start and end timestamp for each instance (e.g. month) of a subscription? The payment_collection table only has a due_date and the subscription_instance table has most of the end_date as NULL? I am currently just adding one month to the payment_collection.due_date for my revenue model but this wont work if we have non monthly subscriptions
Rob Nelson  [11:52 AM]
The toggle is now on.
@Michal Baran @Marcin Żołna are we seeing what we expect from reward and product service?
Rob Nelson  [1:48 PM]
@Tom McKenzie @Nicklas Chapman is there anything Merchant can do to validate the production behaviour of the toggle now?
Rob Nelson  [2:00 PM]
I have moved myself onto a non-staff plan to see if I can see the "enhanced debit rewards" in production, but I cannot!
@Michal Baran @Nicklas Chapman I would have expected to see 3% rewards right? Since you use the plan to determine if I am staff or not and then source my reward % from the right place?
@Tomasz Michalski is our config in product-service in production correct?
Rob Nelson  [2:01 PM]
3 files [2:05 PM]@here - any thoughts on the above?
Why am I not seeing the new reward amounts?Tomasz Michalski  [2:08 PM]
Prod config:
image.png Rob Nelson  [2:08 PM]
I just looked in looker as well - looks correct!
Rob Nelson  [2:11 PM]
replied to a thread:The LD toggle is targeted on a "staff cohort" - so we need to removed from that for it to work correctly.
Plus be on a non-staff planRob Nelson  [2:11 PM]
@George Sharpe - can you remove me from the staff cohort in LD temporarily please?
Rob Nelson  [2:22 PM]
replied to a thread:We're in business
3 files [2:24 PM]@Antony Evmorfopoulos @Kieran Patel @George Sharpe - can we include someone in the 10k rollout tomorrow that we have direct communication with please?
Then we can ask them to sign up etc straight away?George Sharpe  [2:25 PM]
Yeah me
Rob Nelson  [2:25 PM]
and you're excluded from the LD cohorts etc?
George Sharpe  [2:26 PM]
I will be before we go live
Rob Nelson  [10:55 AM]
@here - Staff should now be seeing 6% rewards.....!
enhanced debit rewards is now on for everyone! fyi @Nicklas Chapman @Michal Baran
Rob Nelson  [10:55 AM]
@Alex Murphy - do we need to incorporate a CMS targeting change into our launch plan today? fyi @Kevin Came
Rob Nelson  [11:02 AM]
@here - Launch call is going ahead: https://payzilch.zoom.us/j/85704042649?pwd=x6NVmlb6yQ3dwmfdtb6PIMgYIDFG8E.1&from=addon
Ozzie  [12:06 PM]
Are we still reconvening at 12:30 team? 
Thomas Peter Breakwell  [12:07 PM]
apparently is now fixed - @Zac Barclay mentioned
Thomas Peter Breakwell  [12:07 PM]
so im free whenever
Rob Nelson  [12:26 PM]
@Kishan Muman - please prepare to push the SQS messages for the popup
Thomas Peter Breakwell  [12:31 PM]
i dont have call invite (edited) 
Rob Nelson  [12:31 PM]
sending....
[12:32 PM]https://payzilch.zoom.us/j/85704042649?pwd=x6NVmlb6yQ3dwmfdtb6PIMgYIDFG8E.1
Thomas Peter Breakwell  [12:54 PM]
can see a few more coming through now
[12:54 PM]subbing
Zac Barclay  [1:00 PM]
Copy has been updated to include "Tap Account to sign up." on the final screen
Thomas Peter Breakwell  [1:15 PM]
plz let me know when you wanna send remainder email
Thomas Peter Breakwell  [1:22 PM]
61 subs now (edited) 
Ozzie  [1:34 PM]
@Thomas Peter Breakwell let's go ahead with the rest of the send
Thomas Peter Breakwell  [1:35 PM]
sent
Thomas Peter Breakwell  [2:39 PM]
shall we look to send push at 3pm?
Zac Barclay  [2:42 PM]
For those curious, I put a dash together for the product pop-up here: https://eu.mixpanel.com/project/2367288/view/2912136/app/boards#id=10370133
Thomas Peter Breakwell  [2:53 PM]
@Ozzie @Rob Nelson any objections to push at 3pm?
Thomas Peter Breakwell  [3:28 PM]
sent
[3:32 PM]https://eu.mixpanel.com/s/2hxX94
[3:32 PM]hence the large spike by minute
[3:36 PM]500 subs now (staff and todays batch so far) (edited) 
Rob Nelson  [3:38 PM]
wow!
Rob Nelson  [3:41 PM]
8 cancellation requests so far
Harrison Curtis  [9:36 AM]
Information button isn’t opening for me in the memberships hub 
2 files Kieren Messenger  [9:46 AM]
  same, stopped working for me too
Rocharne Brady  [11:23 AM]
Only the 10,001 cohort can see the articles at the moment. I can include all staff when I get home 
Ryan Walastyan  [9:29 AM]
for subscription fees in the ledger, who is the best person to ask about the difference between fee.fee_calculationand fee.fee_calculation_item? I need to document them in the PR I have to make the subscription revenue model
Rob Nelson  [9:30 AM]
@Craig Main - If a payment schedule is started on the 30th Jan for a monthly subscription, does the schedule run like this:
30th of January -> 28th of Feb -> 28th of March

or like this:
30th of January -> 28th of Feb -> 30th of MarchTomasz Michalski  [9:12 AM]
We got notified about a customer C02783475 having multiple (2) active subscriptions. It seems that it was caused by almost immediate requests to start a subscription (130ms delay), where the 1st transaction hasn't finished yet, and the 2nd transaction started. The customer now has 2 subscriptions, 2 payments schedules and will be billed twice in a month.
1st subscription:
instance reference SI00004825payment reference RPM1RG42nd subscription:
instance reference SI00004826payment reference RPM1RH3We should cancel one of the subscription instances for this customer:
there is an admin endpoint to request subscription cancellation, which will also cancel the associated payment schedule, but the end datetime will be set for in a month, so also the end datetime should be manually modified in the Prod DB for current datetime, so that this subscription instance is picked up in the next reconciliation run (also this is an improvement area to allow admin to this within the same API call)OR we could manually cancel payment schedule and manually change the subscription instance status to CANCELLED - because this way the notifications won't be triggered to the customerWe should also investigate how this could happen that multiple requests were triggered immediately, was this triggered by UI? FYI @Jan Michalak @Rory Fielding
FYI @Rob Nelson @Tommy Kwok @Marcin Żołna @decisioning (edited) 
Parry Champaneriya  [10:07 AM]
Z****3*1 - Password for Memberships Retro (edited) 
Rob Nelson  [4:06 PM]
never share your password @Parry Champaneriya 
Parry Champaneriya  [4:14 PM]
Noted and changed now
Rob Nelson  [4:22 PM]
hahaha
Tommy Kwok  [11:32 AM]
Hey @Aditi Kedia / @Craig Main (cc @decisioning )

Question for you guys in payments

Do we have any monitoring on customers being billed too frequently (i.e. twice within the same day, or 2 payment successful event where the time difference between the 2 event is less than the subscription interval etc…) for their membership?

We were reviewing the landmines list and this came up
Ryan Walastyan  [4:48 PM]
do the fee_calculation and fee_calculation_item tables get a new row created for a subscription fee refund? Does it go into the ledger as a FEE_REFUND with the fee_calculation_reference populated?
Abhishek Chatterjee  [8:58 PM]
Why do we say upto 6% on the plan but then provide more instead of saying more?

Not complaining, happy to receive more  
just asking2 files Ryan Walastyan  [3:09 PM]
do the fee_calculation and fee_calculation_item tables get a new row created for a subscription fee refund? Does it go into the ledger as a FEE_REFUND with the fee_calculation_reference populated?
Rob Nelson  [9:00 AM]
Hi all - We are rapidly approaching the first major billing cycle for memberships. The first day we launched was the 23rd July, meaning we will first bill many of our Plus members on the 23rd Aug (Or the morning of the 24th? please correct me!).

Several staff members are due to be billed either this week or last week (I was billed last week successfully!).

In advance of the larger billing run on the 23rd/24th, can we look at the logs and metrics for the staff billing runs happening now? @Craig Main @Marek Chodak please can you give us feedback on this and confirm things are running as you expect?

Has any staff member not been billed as they would have expected?
Craig Main  [9:05 AM]
I extracted these numbers a few days ago to alert the team, and make sure that we are ready.
We are increasing the threading on payments service in the current sprint, just to ensure that the run scales as it should.
This scaling is not required for the numbers now, but we are doing it ahead of the volume increase anyway.

2025-08-13	1
2025-08-15	3
2025-08-16	2
2025-08-17	11
2025-08-18	11
2025-08-19	3
2025-08-21	4
2025-08-22	4
2025-08-23	787
2025-08-24	272Craig Main  [9:07 AM]
Our dashboard for the last two days shows successful billing of 16 recurring payments, and no declines.
We have had declines before, but understandably few, most from aggressive testing by @Nikos Sofianos and team.
Ozzie  [9:17 AM]
I was billed successfully on Friday   
Abhishek Chatterjee  [1:25 PM]
I got billed just now, 2 questions on it

Why are we calling it Zilch Instalment instead of something like Zilch Membership on the transaction?       Got initially confused on what it was as I did not have any open loans, and no way to see it in the app why 3.99 was deducted.
Did not get a push notification telling me membership was deducted. Is that expected? as I received normal notification on txn just before that.Rob Nelson  [1:54 PM]
@Andrzej Lorenz @Abhishek Chatterjee - We flagged the bank statement text some time ago, but it looks like we didn't create an acquirer ticket for it - is this a big change? Can we do it quickly/easily?
https://payzilch.slack.com/archives/C08S3BB9WNA/p1752494645219759?thread_ts=1752485781.009379&cid=C08S3BB9WNA
my banking app won't let me screenshot it, but yes! 3.99 charge is now pending.
"ZILCH * INSTALMENT"From a thread in subscriptions-staff-testing | 14 Jul 2025 | View replyWojciech Mielczarek  [5:00 PM]
Hey @decisioning team, we need to coordinate across our teams on the rollout of the physical card and membership features.

On the physical card side, the rollout will target hand-picked customer cohorts, where we want to measure card performance independently of memberships.
To achieve this, these customers must not be eligible for membership, so we’ll need your support in excluding them on your end.

Do you already have anything planned around this, or would it make sense to set up a discussion on how we might approach it?
This message was deleted.Kevin Came  [10:49 AM]
replied to a thread:This is great @Craig Main. Are these the number of customer we are expecting to be billed for their Membership fee on those dates? c.c. @Rocharne Brady
Craig Main  [10:50 AM]
The statistics might be a little out now - probably the same - but yes. (edited) 
Harrison Curtis  [11:28 AM]
Yeah these numbers will change as we get cancelations, we also have a view of this in the Memberships Dashboard in the billing section - right now we have 735 customers due to be billed on Saturday (Have had 45 cancelations which would have been billed)
Rocharne Brady  [1:55 PM]
Thank you @Kevin Came @Craig Main @Harrison Curtis (edited) 
Ozzie  [7:55 PM]
Can you link me to the datadog dashboard that I can look at on Saturday to see the status of the members billing? Looker will be 1 day behind...
Aditi Kedia  [8:04 PM]
@Ozzie DD Dashboard: scroll right to the end (recurring payment metrics) (edited) 
Craig Main  [4:56 AM]
The billing run was a little longer than usual last night for the first large tranche of customers on subscriptions.
All the billing attempts were made. (edited) 
image.png Harrison Curtis  [6:41 PM]
Some stats from Saturdays cohort of billed customers (Excluding staff) 

TLDR - 76% of customers were eventually successfully billed and converted from free to paying membership 

Billing Attempt 1 - Saturday780 were due to be billed, with 59 cancelling before due date, leaving us with 721 billing attempts497 were successful (68.9%), 224 were declined - 83% for insufficient fundsBilling Attempt 2 - Sunday211 of the 224 declines were reattempted, with 13 cancelling after their 1st decline69 were successful (32,7%), 142 were declined - 80% for insufficient fundsBilling Attempt 3 - Monday138 of the 142 declines were reattempted, with 4 cancelling after their 2nd decline26 were successful (18,8%), 112 were declined - 78% for insufficient funds

So out of the initial 780, 592 customers have successfully been billed and converted to paid membership - giving us a free to paid conversion of ~76%
Tommy Kwok  [10:11 AM]
Hey all (cc @Josh Darling @Ozzie @Marcin Żołna @Rob Nelson @Steve Rayko)

Quick message to flag that the Ability to Extend a Customer’s Free Trial (assuming they are still on the free trial) has been made available in Production since 22nd August
(Ticket here for details: https://payzilch.atlassian.net/browse/ZILCH-42773)

To use this endpoint, we will need ITAM’s help - we’ve also not used this in production before so a small trial run would be recommended

AFAIK the first non-staff membership was started on 23rd July - so if we want to be extending free trial for existing customers then we might want to look into this
(Source: https://zilch.cloud.looker.com/sql/b5xxcywbfpwjfw)
Andrzej Lorenz  [9:27 AM]
I've declared a P4 incident (#incident-362) - some membership fees were not collected tonight due to a race condition in the billing mechanism. we're now assessing the size of the problem and looking for ways to retry. cc @Marcin Żołna
Iain Miller  [1:21 PM]
I'm on Zilch Plus, and I can see that we're promising 6-9% when I enable my card.

But, when I enable for online, it's only showing 5%?
2 files Iain Miller  [7:04 PM]
replied to a thread:Aha!

I see that the wording has been updated, it's crystal clear now!

Thanks all!
Screenshot_20250904-185946.png Oleksandr Tertyshnyi  [11:14 AM]
hi team, @merchant-fe, @retain, as I am currently working on targeting-service and moving the feature variants configurations into it, I am wondering if we are still using the outdated feature debit-ecj-rewards somewhere in a code (the one that was substituted with debit-rewards ), and if not then probably we can get rid of it.
CC: @Tommy Kwok
Marcin Żołna  [3:57 PM]
Plan for supporting subscriptions rollout beyond 15k customers - (Decisioning + Retain) meeting summary:
Decisioning is finalizing targeting service in 9.3Decisioning to create a membership featureDecisioning to create 2 segments matching LD segments for initial 10k customers + 1% randomly selected (help from ITAM will be needed)Once 1,2 and 3 are done. Retain may switch to GET /customer-api/products/features/membership  CS endpoint to get membership eligibility for a customerIf everything is fine LD check may be removed and decisioning is going to create a 3rd segment for the next cohortWe may ask ITAM to populate customers from 3rd cohort to the segment

In the meantime decisioning will share how to configure a test user to get all of segments, variants and features needed to be eligible for memberships

Open questions:
@Tommy Kwok who is going to prepare the list of customers for the next memberships cohort? (edited) 
Rob Nelson  [4:52 PM]
replied to a thread:@Mike Davis @Rory Fielding - Im concerned if we need mobile changes ready to use on the 6th Oct, we need to actually deploy them in advance of that.
When do you think the mobile changes for this targeting will be ready to release?Rory Fielding  [11:22 AM]
Just regarding the call yesterday @Tomasz Więckowski I know you mentioned you'd like us to cache the value returned from /customer-api/products/features/membership on the frontend. I have at the moment set it to not call the feature endpoint again for 8 hours after having fetched it once, however I think this may be too long.

Does anyone have thoughts on how long this should be? 30 secs? 5 mins? 10 mins?
Tomasz Więckowski  [11:24 AM]
1h maybe
Tomasz Więckowski  [11:26 AM]
The value can change only if the customer is added/removed from the segment. Which will be done by ITAM
John Strawhorne  [12:34 PM]
In this customer service release the new GET /customer-api/products/features/{feature} endpoint will only look at targeting service if the product-features-lookup-by-customer-id LD flag returns true.

I was think that for this customer service and mobile regression we will run with product-features-lookup-by-customer-id disabled in staging and then enable it afterwards. Does that sound like a good plan?
John Strawhorne  [12:48 PM]
To assign a customer to a segment we have the targeting-api/customers/{customerRef}/segments/{segment} targeting service API. In e2e-test we are using  the targetingServiceInternalApi.assignCustomerToSegment method but I have also created the customers.subscription().assignCustomerToSegment()  method to assign customers to the subscription/membership segment.
Tom McKenzie  [12:18 PM]
@here afternoon all. Today we’ll be deleting all segments for the LD flag spend-rewards-availability and defaulting it to ALL for pre-prod envs. This has been running in staging for the past few months, so we don’t anticipate any issues. I've amended the e2e tests, please see
Any initial concerns, or you can see some oddities whilst configuring . . . . please reach out. (edited) 
#2922 feat: remove additional parameters### Merge / deployment checklist

• Confirm this change is backwards compatible with existing workflows.zilchdev/e2e-test | 1 Dec 2025 | Added by GitHubJohn Strawhorne  [1:10 PM]
@here for those of you that don't know, we can now start a pro subscription for a user who is not on a subscription via the start subscription API.  The user will first need to be added to the targeting service PRO_SUBSCRIPTIONS_INITIAL_ROLLOUT segment in order to get access to the pro subscription and then they can use the start subscription API with the zilch-pro-tier-subscription code.

In the e2e-test repo this can be done with the customers.subscription().startProSubscription();  method. I will look to add this to the mobile-test repo shortly.
Rob Nelson  [2:57 PM]
@Zac Barclay @Rory Fielding - Is there a plan for a UI change to go along with the new functionality from Decisioning and Payments to allow the "un-cancelling" of a subscription?
Zac Barclay  [3:01 PM]
Yes - that's in @Crinan's list for i11. I'm not sure if we have mock-up for it yet or where it is on their sprint plan
Tomasz Więckowski  [3:11 PM]
un-cancelling also known as subscription resume will be triggered with the existing start subscription endpoint, so the work on the Retain side could be started anytime (edited) 
Steve Rayko  [10:22 AM]
Can someone do multiple cancelling and un-cancelling?
John Strawhorne  [9:48 AM]
FYI in test environments, subscriptions can now be downgraded via API from pro to plus. There is a new customer-api/products/subscriptions/change API with body
{
    "currentSubscriptionCode": "zilch-pro-tier-subscription",
    "targetSubscriptionCode": "zilch-plus-tier-subscription"
}When the user requests to downgrade they will only get downgraded at their next billing date. See https://payzilch.atlassian.net/browse/ZILCH-45024 for more detailsZILCH-45024 Ability to Downgrade from Zilch Pro to Zilch Plus (or Zilch Stan…Status: DoneType: StoryAssignee: Tomasz WięckowskiPriority: UnknownAdded by Jira Cloud
Message subscriptions-tech