---
name: meta-ads-daily-and-monthly-checks
description: "Use for the daily check, the Tuesday pass and the monthly check routines. The daily check is alarms only. The Tuesday pass is pace and the goal. The monthly check is the operator's month-end pass. Change nothing."
---

# Daily and monthly checks

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Daily check routine, the Needs you routine on Tuesday, the Monthly check routine, or "is anything broken" and "what should I look at this month". The full audit is a different skill. None of these repeats it.

## The daily check

Every day, including weekends. Alarms only. On a normal day the whole reply is one line: "Nothing on fire."

Keep it to about five calls: the account list, the diagnose sweep, one daily report for the last 29 days, the pixels, and the ad sets with their learning status. Dates follow the ad account's timezone.

Compare yesterday with the same weekday last week, and with the average of the same weekday over the last four weeks. Mondays are not Sundays. Read per campaign with real spend.

Raise an alarm for:

1. The account. Disabled, an unpaid balance, a risk review, or the spend cap reached, from the diagnose sweep. Say that first and do not bury it under ad-level notes. Also the spend cap close: from the account list, spend so far within about a tenth of the cap, or on course to reach it within a week at the last seven days' pace. When the cap is reached, everything stops.
2. Spend. A campaign more than about 50% above or below its usual for that weekday, when the gap is more than a tenth of the account's usual daily spend. Smaller gaps are noise.
3. A campaign that stopped. It spent on the same weekday last week and nothing yesterday while it is meant to be on. Use the diagnose sweep for the cause. A paused campaign they already know about is not an alarm.
4. Disapprovals. Ads newly disapproved since yesterday, with Meta's reason. The diagnose sweep checks about 75 ads, so on a larger account also list ads with the disapproved status. Pending review is not an alarm.
5. The pixel or the goal event gone quiet. Last fired more than about a day ago while ads spend, or the goal event present on most days last week and absent for the last two days of spend. One quiet morning is not this alarm.
6. Month-to-date pace. Spend so far against the monthly budget they gave, scaled to the days gone. More than about 15% ahead or behind, on the day it first crosses. Not every day after. No budget given, no pace line.
7. Learning knocked back. An ad set that carries real spend and was out of learning is back in learning or learning limited, from its learning status against the one you remembered yesterday. Name the edit from the activity log if one explains it. Do not add another edit.
8. Frequency on a live ad. Its rolling seven-day frequency clearly above its previous seven days, with link click-through already down. Link click-through is the link clicks divided by impressions, not the all-clicks rate. One line. You do not pause it.

An alarm from yesterday that is still open is one line: what, and "day 2". Do not write it out again. Remember today's counts and learning statuses for tomorrow.

Each alarm is one line: the campaign, the number, the likely cause if you can see it, and the decision. At most five lines. No table. Pausing a campaign that is on fire is still a change. It needs a yes in chat.

## The Tuesday pass

Last 7 to 14 days. Only what needs a decision. This is pace and the goal, not Monday's fatigue table and not Friday's ad list.

In this order, and only the lines that fail:

1. The live event against the button or the form. A cheap event on a purchase or qualified-lead goal is first.
2. Results against the target and the break-even number, using one event row. A campaign that loses money on the margin they gave. A campaign that has never produced the goal event.
3. Learning. Ad sets in learning limited that carry real spend, with the sum: the weekly budget divided by the cost per result. The share of the account's spend in learning limited.
4. Highest volume still on after they named a cost or a return.
5. Pace against the monthly budget. If none was given, ask once and leave pace out.
6. Advantage+ audience on when the confirmed persona was meant to be a limit, or a campaign that lost its Advantage+ state when they wanted it.
7. A significant edit in the activity log, if results moved. No pile of new edits on top.
8. A customer list missing from prospecting, when one exists.

At most five lines. Each names the campaign, the number and the decision. Do not move a budget or switch an event. Ask which rows to preview.

## The monthly check

The operator's month-end pass, on the second day of the month, after the monthly report. It looks at what changes over a month. It is not the full audit.

Run each section. Write up only what needs a decision, then the scorecard.

1. Money. The month's result against the target and the break-even number, with the spend. Revenue divided by all ad spend, if they gave you total revenue.
2. Learning and structure. Ad sets that spent the month in learning limited, and what merging would give them. Too many ad sets or campaign types for the budget. Prospecting versus remarketing. A traffic or awareness campaign still spending against a sales or leads goal.
3. Creative. Ads to retire, from Creatives and fatigue, one line each, at most five. Ad sets with no variety. How many new ideas next month needs, from the spend and the fatigue rate. Enhancements on that nobody chose.
4. Tracking. The pixel's last fire, the event against the button they confirmed, the attribution setting on the ad sets that spend, and the gap between the default and the click-only read. For leads, the share that became qualified, if they told you. If the page has changed and you cannot read it, ask.
5. Lists. Customer list age, list sizes, and lists still missing, from Remarketing and suppression.
6. Placements. The month's placement breakdown, and what Meta still lets them do about the waste.
7. Bidding. Targets against what each campaign achieved, from Tracking, conversions and bidding.
8. The log and tests. Changes due for a check, and tests running or finished, from Tests and changes.
9. Recommendations and rules. Meta's recommendations, as flags beside your own numbers, never applied to lift the score. The account's automated rules, and any enabled one that pauses ads or raises budgets.
10. Competitors. Only when competitors are on file for this account. Run Competitor ads: new launches, which ads survived since last month, and angles nobody uses. One short table.
11. The next six weeks. From Seasonality and promotions. If no dates are remembered, ask once whether a sale, a launch or a closure is coming.

## What the monthly check returns

Account. One line: name, id, currency, the month.

Needs a decision. At most five items, worst first, each with its number.

Scorecard. One table, one row per section that applies: the area, OK, Fix or Check, and one short line.

Then ask which rows to preview, and which area they want in full.
