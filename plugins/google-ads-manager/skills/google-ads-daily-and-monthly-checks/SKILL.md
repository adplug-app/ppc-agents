---
name: google-ads-daily-and-monthly-checks
description: "Use for the daily check routine and the monthly check routine. The daily check is alarms only. The monthly check is the operator's month-end pass. Change nothing."
---

# Daily and monthly checks

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Daily check routine, the Monthly check routine, or "is anything broken" and "what should I look at this month". The full audit is a different skill. Neither check repeats it.

## The daily check

Five minutes, every day, including weekends. Alarms only. On a normal day the whole reply is one line: "Nothing on fire."

Compare yesterday with the same weekday last week, and with the average of the same weekday over the last four weeks. Mondays are not Sundays. Read per campaign with real spend.

Raise an alarm for:

1. Spend. A campaign more than about 50% above or below its usual for that weekday, when the gap is more than a tenth of the account's usual daily spend. Smaller gaps are noise.
2. A campaign that stopped. Impressions on the same weekday last week, none yesterday. Read `campaign.primary_status` and `campaign.primary_status_reasons` for the cause: paused by someone, ended, budget, policy, or not eligible.
3. The tag. A primary conversion action whose last request is older than usual (`metrics.conversion_last_received_request_date_time`). On an account that converts every day, a day of silence is the alarm. Zero conversions yesterday on its own is not, because yesterday is still filling. Flag it only when the campaign usually has three or more on that weekday.
4. The account. `customer.status` not enabled. On invoiced accounts, `account_budget` with less than about a tenth of the spending limit left, or an end date this week. Card payment failures do not show here. Say that once, the first time.
5. Disapprovals. Ads newly `DISAPPROVED` since yesterday. Products newly not eligible, against the count you remembered yesterday.
6. Budget pace. Month to date more than about 15% ahead of or behind the budget they gave, on the day it first crosses. Not every day after.

An alarm from yesterday that is still open is one line: what, and "day 2". Do not write it out again.

Each alarm is one line: the campaign, the number, the likely cause if you can see it, and the decision. At most five lines. No table. Pausing a campaign that is on fire is still a change. It needs a yes in chat.

When a tracking break is fixed, the next step is a data exclusion for those dates. Conversions and bidding has it.

## The monthly check

The operator's month-end pass, on the second day of the month, after the monthly report. It looks at what changes over a month. It is not the full audit.

Run each section. Write up only what needs a decision, then the scorecard.

1. Quality Score. Always shown. The three lines from Search build: the spend-weighted score, the share of spend at 1 to 4, and the weak part that explains it.
2. Keywords. Spend and no conversions over 90 days, no impressions in 90 days, low search volume, duplicates across ad groups, and existing negatives that block an enabled keyword.
3. Search terms. The n-gram pass from Search terms and negatives on the last 30 days.
4. Ads. Ads and copy: ad groups with a clear winner, low-rated assets with a replacement drafted on request, and disapproved or limited ads.
5. Bidding. Smart Bidding status, and targets against what each campaign achieved, from Conversions and bidding.
6. Tracking. The measured lag, refreshed. Tag requests, auto-tagging, URL tracking, actions counted twice, windows, and offline upload health. Only what is wrong.
7. Segments. Device, day of week and hour of day against the KPI, over 90 days. Only a gap with real money behind it. Conversions and bidding says what the strategy lets you do about it.
8. Landing pages. Conversion rate by page, speed and mobile scores, pages with paid traffic and no conversions, and final URLs that did not load.
9. Audiences. Suppression lists missing, remarketing lists closed or under the serving size, Search on Targeting, Demand Gen prospecting not excluding customers. From Audiences and remarketing.
10. Brand. Brand impression share, top and absolute top share, and brand CPC over three months. Support and login terms still costing money on brand.
11. Shopping, when there is a product campaign. Feed improvements from Shopping products.
12. The next six weeks. Ask once whether a sale, a launch or a closure is coming, if the dates are not remembered. Seasonality adjustments, promotion assets and copy for the ones that are.

## What the monthly check returns

Account. One line: name, id, currency, the month.

Needs a decision. At most five items, worst first, each with its number.

Scorecard. One table, one row per section that applies: the area, OK, Fix or Check, and one short line. Quality Score always has a row.

Then ask which rows to preview, and which area they want in full.
