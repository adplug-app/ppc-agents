---
name: linkedin-ads-account-audit
description: "Use when they ask for an audit, a health check or a second opinion, and for the Tuesday short pass. Change nothing unless they then pick a row."
---

# Account audit

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

An audit, a second opinion, a new account, or "what should I look at". The Tuesday short pass below is what the Needs you routine runs. The daily check, the monthly check and the quarterly pass are in Daily and monthly checks. The weekly and monthly reports are in Reports. Do not run the full audit inside a routine.

If they have not yet said whether they are an agency or in-house, which account, what they sell, who the buyer is, the goal, the form or the page, the budget and the target, ask and stop. Listing accounts so they can pick one is allowed. An audit is not.

## Before the checklist

Name the client, the account id, the currency and the date range before the findings. One account. Do not add figures across clients or currencies. Spend from `linkedin_ads_performance` is in the account's own currency, the same as its budgets.

Default the full audit to the last 30 days against the previous 30, and at least four weeks of data before you judge an ad set. Ad set rows come from `report_type` `campaign`. Lead rows come from `report_type` `lead_gen`. Campaign totals are the ad sets added up, or `campaign_groups` with `include_performance`. Say if a tool returns a different window.

Use the other skills for their sections. Do not invent a thinner version.

## The full audit

Work in this order. Skip a section that does not apply and say "not in this account". You run every section. You only write up what needs a decision, plus the scorecard.

1. Goal. Qualified leads, demos, pipeline or account engagement, in their words. If the number the account is buying is clicks, visits, or engagement, that is the first paragraph. A form completion is the result only when the form is the agreed goal. Cost per lead on a form is not pipeline.

2. Fit. Given what they sell and the budget, is one lead gen campaign the right start? Use How to run the account. Thought leadership mixed into that campaign is a finding. A jobs objective scored as pipeline is a finding. Accelerate ad sets are a finding: name them and judge them on the same goal. If LinkedIn is a poor fit, say it here.

3. Measurement. Use Lead forms and conversions. Which result is recording. Each rule's windows and attribution model, and whether ad set rows are being added up under "each ad set". Post-click against post-view. Whether CRM stages come back, and the gap between LinkedIn's leads and the CRM's. What you cannot see: the tag in the browser, the CRM, whether sales called them back.

4. Audiences. Use Audiences. Forecast on every live ad set. Under 300 is called out and nothing on that ad set gets enabled. Expansion on, or the Audience Network on, is a line per ad set. A list still building or failed. An ad set with location and little else. Penetration on a named list.

5. Suppression. Use Suppression and retargeting. Customers, open opportunities, employees, competitors, job seekers and past converters still reachable by a prospecting ad set. Whether the account has its exclusion block, and which live ad sets are missing it. Retargeting pools that do not exist, or that are mixed into cold ad sets.

6. Ads. Use Creatives. Rejected ads and the reason. Fatigue: ad set frequency up, one ad taking the impressions, landing-page click rate down against itself. A document, a conversation ad, or a thought leader ad sitting in the wrong job. Copy past the visible length. Ads still in review are not a finding.

7. Bidding and pace. Use Bidding and budget. Maximum delivery, a cost cap, or manual, named in words. A cold ad set on a click goal. A shared campaign budget that pools two jobs. A cost cap starving delivery. Pace against the budget they gave, when the currencies allow the comparison. Accelerated pacing, if it is on.

8. Tests and changes. Use Tests and changes. Changes with no check date, tests with no end, two changes on the same ad set in the same fortnight.

9. What not to launch. The audience that cannot clear 300 without abandoning the ICP. A second ad set that repeats the first. Auto-Targeting, Accelerate. Expansion or the Audience Network as a rescue. A format whose job is not the goal.

## The short weekly pass

This is Tuesday. It is not the full checklist, and it does not repeat Monday's report. Last 7 to 14 days. Only what needs a decision. Meeting the goal matters. Spending more is not the goal.

In this order:

1. Audience Expansion on, or the Audience Network on, on a live ad set. Name the ad set. Recommend it off. Do not turn it off.
2. An ad set optimising a cold audience to clicks, visits, or engagement, while the goal is a lead, a demo, or pipeline.
3. Cost and form completion against the target. Say whether the lead is a form fill or the conversion sales would recognise. A thin week is not a broken tag until the quiet-form test in the daily check says it is.
4. A prospecting ad set missing the exclusion block, or reaching customers or open opportunities.
5. An audience under 300, or a live ad set whose forecast you have not counted. Under 300 does not get a bid increase.
6. Pace, when a budget is known and the currency lets you compare. If no budget was given, ask once and leave pace out. Do not invent a number.
7. Fatigue: frequency up where one ad took the impressions and its landing-page click rate fell. Read `report_type` `reach` with the ad set ids, last 7 days against the 7 before, and `report_type` `creative` for the ads.
8. A cost cap ad set spending well under its budget, or a maximum delivery ad set that meets the cost cap test in Bidding and budget.
9. Thought leadership and lead gen in the same ad set or the same budget pool, judged on one cost per lead.

Each line names the ad set, the number, and the decision. At most five lines. Then ask which rows to preview. Do not move a budget or a bid in this pass.

## What the full audit returns

Use these headings and no others. Keep it to one screen before the detail.

Account. One line: name, id, currency, range.

The headline. Three sentences: how the account sits against the goal, the biggest problem with its cost, and the biggest opportunity.

Needs a decision. At most five items, worst first. Each has the number that makes it matter and the decision you need.

Scorecard. One table. One row per area that applies: Goal, Measurement, Audiences, Suppression, Ads, Bidding, Pace, Tests. OK, Fix or Check, and one short line. Areas not in the account are left out, with one line listing them.

What I would change. Numbered rows you can preview. Nothing applied. Expansion and the Audience Network named per ad set.

What I could not see. The Insight Tag in the browser, the CRM stage, whether sales called the lead, the author approval for a thought leader ad, sender approval for a conversation ad, the sites an Audience Network placement ran on, Companies Hub, and a frequency cap the connector cannot set on a feed ad set. Say so. Do not fill them in.

Close by asking which rows to preview, and which area they want in full. A yes to "fix it" is not a yes to every row. Ask them to name the rows.
