---
name: linkedin-ads-daily-and-monthly-checks
description: "Use for the daily check, the monthly check and the quarterly pass routines. The daily check is alarms only. The monthly check is the operator's month-end pass. The quarterly pass resets lists, the ICP, the CRM loop and the test plan. Change nothing."
---

# Daily and monthly checks

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Daily check, Monthly check and Quarterly pass routines, or "is anything broken", "what should I look at this month", "plan next quarter". The full audit is in Account audit. None of these repeats it.

## The daily check

Five minutes, every day, including weekends. Alarms only. On a normal day the whole reply is one line: "Nothing on fire."

If a tool says LinkedIn needs reconnecting, that is the only line: reconnect at https://adplug.app/dashboard/connections. Stop there.

Read per ad set with real spend. `report_type` `daily` drops the ad set id, so do not use it here. Read `report_type` `campaign` once per day, with the start and end date on the same day: yesterday, the same weekday last week, and the same weekday in each of the three weeks before that. That gives each ad set's yesterday, its same weekday last week, and its four-week same-weekday average. On Saturday and Sunday, compare with the previous weekends. A quiet weekend on a B2B account is normal. The alarm is spend well above that weekend, not spend going quiet.

Raise an alarm for:

1. The account. `linkedin_ads_list_accounts` shows the account as anything but active, or a live ad set's serving status names a billing or an account hold. A failed card may only show as ad sets that stopped. Say that once, the first time.
2. Spend. An ad set more than about 50% above or below its four-week same-weekday average, when the gap is more than about a tenth of the account's usual daily spend. Smaller gaps are noise. A day near twice the daily budget is allowed by LinkedIn and is not on its own an alarm. The tool's figures are in the account's currency, so they compare with each other and with the budget.
3. An ad set that stopped. Impressions on the same weekday last week, none yesterday, and it is not a draft, an end date or a pause you know about. Read the serving status on the ad set and on the ads. Name the hold reason when it is there. A thought leader ad that stopped may have lost the author's permission.
4. A newly rejected ad. The review status and the rejection reasons. An ad still in review is not an alarm. A sibling still serving does not hide a new rejection.
5. A form or the Insight Tag gone quiet. Read `lead_gen` and `conversion` for yesterday against the same weekday. One day with no lead, on an account that gets a few a week, is not a broken form. Spend with no form opens, on an ad set that usually gets opens, is the alarm. Opens holding and submits collapsing is the form. Website conversions that stop while clicks continue, past this account's usual gap, are the tag or the rule. Conversions keep arriving for days, so a light yesterday alone is not an alarm. Do not send events to fill the hole.
6. Pace. Month to date more than about 15% ahead of or behind the budget they gave, on the day it first crosses. Not every day after. Only when the currencies allow the comparison.

An alarm from yesterday that is still open is one line: what, and "day 2". Do not write it out again.

Each alarm is one line: the ad set or the ad, the number, the likely cause if you can see it, and the decision. At most five lines. No table. Pausing an ad set that is on fire is still a change. It needs a yes in chat.

## The monthly check

The operator's month-end pass, on the second day of the month, after the monthly report. It looks at what changes over a month. Run each section. Write up only what needs a decision, then the scorecard.

1. Tracking. From Lead forms and conversions: every rule enabled or not, its windows and attribution model, which ad sets it is attached to, the share of conversions that are post-view, and whether any rule recorded nothing all month. Whether CRM stages came back, and LinkedIn's leads against the CRM's count, when they can give it.
2. Suppression and lists. From Suppression and retargeting: live prospecting ad sets missing part of the exclusion block, customer and open-opportunity lists due a refresh, lists building or failed, retargeting pools under 300.
3. Forms. Each live form: number of fields, what the custom questions are doing, completion rate against last month, work-email validation, and forms still attached to paused ad sets.
4. Audiences. Forecast on every live ad set, both switches, ad sets with location and little else, and penetration on named lists from `reach`.
5. Ads. Ads past six to eight weeks on the same audience, the fatigue test from Creatives, rejected ads, copy past the visible length.
6. Bidding and budget. The strategy per ad set in words, cost cap ad sets underspending, maximum delivery ad sets that meet the cost cap test, shared budgets pooling two jobs, the month's spend against the budget.
7. Who was reached. `demographics` for seniority, job function and company size on the month, with every code resolved by name. Only a gap with real spend behind it. On a named list, `MEMBER_COMPANY`: how many target companies saw the ads, and the ones with spend and no clicks. Small rows are hidden or noisy. A handful of conversions is a hint, not a reason to cut a seniority.
8. Tests. Running tests with their day count, and tests due to be read.
9. The next six weeks. Ask once whether an event, a launch, a price change or a quiet period is coming, if the dates are not remembered. Holiday weeks are slow on most B2B accounts. Compare them with the same weeks last year, not with the week before.

## The quarterly pass

The third day of January, April, July and October. It looks back over the quarter and sets the next one.

1. Lists. Refresh the customer, open-opportunity and target account lists from the CRM. New competitors added to the exclusion block. Old retargeting pools no longer used.
2. The ICP. Ask which companies and titles turned into opportunities and customers this quarter, from the CRM, or read them from AdPlug's HubSpot tools if they are connected. Compare with who the ads reached. If the wins came from a seniority or a company size the ads barely reach, that is the one ICP change to propose.
3. The CRM loop. Cost per qualified lead and per opportunity by campaign for the quarter, when the numbers exist. If they still do not exist, the first recommendation is a route from Lead forms and conversions.
4. Jobs and money. The quarter's spend split between lead gen, thought leadership and retargeting, against what each produced. Propose next quarter's split in one line.
5. The test plan. At most three tests for next quarter, from Tests and changes, each with its hypothesis and its length.
6. What to stop. Formats, audiences or ad sets that spent for a quarter without moving the goal.

## What each check returns

Daily: the alarm lines, or "Nothing on fire."

Monthly and quarterly: Account, one line: name, id, currency, the period. Needs a decision, at most five items, worst first, each with its number. Scorecard, one table, one row per section that applies: the area, OK, Fix or Check, and one short line. Then ask which rows to preview, and which area they want in full.
