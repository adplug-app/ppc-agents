---
name: google-ads-account-audit
description: "Use when the person asks for an audit, a health check, or what is wrong with the account. Also use the short audit section for the Tuesday routine. Change nothing unless they then pick a row."
---

# Account audit

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

An audit, a second opinion, a new account, or "what should I look at". The weekly routines cover search terms, placements and products. The daily and monthly checks have their own skill. This skill is the full pass. Do not run the full pass inside a routine.

## Before the checklist

You need the business type, the conversion that counts, the budget and the target. If you do not have them, ask, and still pull the structural facts so the questions are specific.

Name the client, the customer id, the currency and the date range before the findings. One account per audit. Do not add figures across clients or currencies. Default the comparison to the last 30 days against the previous 30 days, using `google_ads_account_performance` and `google_ads_campaign_performance`. Say if a tool returns a different window.

Use the other skills for their sections: ICP for Google Ads, Search build, Search terms and negatives, Ads and copy, Audiences and remarketing, Conversions and bidding, Placements, Shopping products. Do not invent a thinner version. The three Search locks are first if any of them is open.

## What to take into consideration

Work in this order. Skip a section that does not apply and say "not in this account", so a missing Performance Max campaign is a finding of absence, not a hole in the audit. You run every section. You only write up what needs a decision, plus the scorecard line.

1. Business fit. Given what they sell and the budget, is Search the right start, and is Performance Max or Demand Gen early? Use How to run the account, after the ICP. If the channel is a poor fit, that is the first paragraph, not a footnote.

2. Measurement. Use Conversions and bidding, including the measured lag. Primary versus secondary, count, campaign goals, a week of spend with zero conversions, when each primary tag last sent a request, enhanced conversions for leads, offline stages and upload health, and the consent question for the EEA or the UK. Then tracking hygiene: auto-tagging, URL tracking, actions counted twice, conversion windows and attribution.

3. Search locks and structure. Use Search build. Partners, Display Network, AI Max, cross-negatives, the brand campaign (support and login terms, existing customers excluded), the shared list, duplicate keywords, keyword ceiling, two RSAs, at least 6 sitelinks in the branch and at least one sitelink that belongs to the ad group, landing page against the theme. Presence or interest gets its own line. Spend by location uses the short audit method below: a place with real spend and no conversions. Say so if physical location and location of interest are mixed. Do not invent a city from a country total.

4. Keywords and Quality Score. Always shown in an audit. Use the Quality Score section of Search build: the spend-weighted score, the share of spend on keywords at 1 to 4, and the weak part that explains them. Then keywords with spend and no conversions over 90 days, keywords with no impressions in 90 days, low search volume, and below first page bid on Manual CPC.

5. Negatives. The shared list, whether it is applied, conflicts between existing negatives and enabled keywords, then the search term skill on the last 30 days, with n-grams. The opportunities section of that skill is part of a full audit. It is not a second waste list.

6. Ads and assets. Use Ads and copy. Disapproved ads first, with the policy topic. Ads that are approved but limited are a lower line. Ads still under review are not a finding. Then the two RSAs compared, low-rated assets, pinning, and the asset gaps from Search build. Ad strength is a hint.

7. Landing pages. `landing_page_view` for the last 30 days: conversion rate by page, `speed_score` and `mobile_friendly_clicks_percentage`. Pages with real paid traffic and no conversions. Final URLs on enabled ads, keywords and sitelinks that you could open and that did not load. Say when you could not open a URL.

8. Audiences. Use Audiences and remarketing. Suppression lists missing, remarketing lists open and big enough for the network, Search left on observation, Demand Gen prospecting excluding customers. A separate remarketing campaign only if that skill says it is worth it.

9. Money and bidding. Shared budgets and portfolio strategies, then impression share lost to budget and to rank, as context only. Do not recommend a higher bid to buy rank. Then Smart Bidding status, targets against actual, and the bid adjustment sections of Conversions and bidding. Name the strategy before any percentage advice. Do not change a strategy in the audit itself.

10. Segments. Device, day of week, hour of day, and age and gender where they return, over the last 90 days against the KPI. Only a segment with real money and a clear gap is a finding. What you can do about it depends on the strategy. Conversions and bidding has the rules.

11. Recommendations and recent changes. Read `recommendation_subscription` and `google_ads_recommendations`. Use the auto-apply section of Conversions and bidding. Do not apply any recommendation to lift optimisation score. `change_event` for the last 14 days: auto-applied recommendations, budget edits, bidding edits, and anything else that lines up with a performance swing. Name the change and the date. Do not claim a cause you cannot see. Experiments running, and the reminder that their auto-apply switch is only visible in Google Ads.

12. Performance Max, if enabled. Brand exclusions. Final URL expansion, which stays limited unless they asked to test it. Campaign negatives. Channel mix. Search categories, labelled as categories. Asset groups by theme. Audience signals named as signals. Product issues via the Shopping products skill when a feed is attached.

13. Demand Gen, if enabled. The Placements skill and the audience skill. View-through conversions kept separate from clicked results when you talk about them. Optimized Targeting called out if it is on.

14. Shopping, if enabled. The Shopping products skill, in full, including feed improvements. Audiences do not replace the feed check.

15. Budget pace, when a budget is known. Use the Budget pace section of Conversions and bidding, including shared budgets. If none was given, ask once.

16. Account housekeeping. Ad groups with no enabled ad or no enabled keyword, campaigns past their end date that still look live, and who has access: `customer_user_access`, when the query returns it, with the access level and the date access was given. An admin nobody recognises is worth one line on an agency account.

## The short audit

This is the Tuesday routine. It is a short performance pass, not the full checklist above, and it does not repeat Monday's search terms or Thursday's structure. Look at the last 7 to 14 days, and only at what needs a decision. Drop anything that is fine. Meeting the KPI matters. Spending more is not the goal.

In this order:

1. Search Partners or the Display Network on. AI Max on a campaign that is not a named test.
2. Auto-apply subscriptions that are on, using Conversions and bidding. Name the types. Recommend the ones that change keywords, match types, negatives, networks, bidding, or budgets switched off. Do not switch them off.
3. Conversions against the goal and the KPI. The primary conversion against the call to action on the page. A tCPA or tROAS on a thin month. Google attributes conversions to the click date. A recent CPA can look worse until conversions land. Use the measured lag. Do not call a quiet recent week a broken tag until it has passed, unless the tag itself stopped sending requests. A campaign that has never converted is still a tracking or an offer problem.
4. Smart Bidding status. A campaign learning, limited or misconfigured, with the reason and the date it started.
5. Budget pace, when a budget is known. A shared budget is one pool. Name the pool and the campaigns when brand and generic, or a strong campaign and a weak one, share it. Do not split or create one.
6. A place with real spend and no conversions. Call the view doc for `geographic_view` before you invent fields. `location_type` separates physical location (`LOCATION_OF_PRESENCE`) from location of interest (`AREA_OF_INTEREST`). If the rows mix the two, say so. A country total is not a city. Do not invent one. Presence stays the rule. Leave the exclusion until they say yes to that place.
7. Impression share lost to budget and lost to rank, as context only, when you are already talking about pace or the KPI. Do not recommend raising a bid to buy rank. Do not recommend raising the budget because share was lost.
8. A change from `change_event` in the last 14 days, if performance moved against the previous period. Name the change and the date. Do not claim a cause you cannot see.
9. Brand leaking into generic. Disapproved ads or sitelinks. Disapproved or limited products. A remarketing list that used to serve and is now closed or empty. A placement or a product spending with no return.

Each line names the campaign, the place, or the pool, the number, and the decision. At most five lines. Then ask which rows to preview. Do not move a budget, exclude a location, or turn a subscription off in this audit. If no budget was given, ask once and leave pace out.

## What you return

Use these headings and no others. Keep it to one screen before the detail. They can ask for any area in full.

Account. One line: name, id, currency, range.

The headline. Three sentences: how healthy the account is against the goal, the biggest problem with its cost, and the biggest opportunity.

Needs a decision. At most seven items, worst first. Each has the number that makes it matter and the decision you need.

Scorecard. One table, one row per area from the checklist that applies to this account: the area, OK, Fix or Check, and one short line. Quality Score always has a row. Areas not in the account are left out, with one line listing them.

What I would change. Numbered rows you can preview. Nothing applied. Match type, level and campaign named for every negative.

What I could not see. The consent banner, the tag firing in a browser, card payments, the Merchant Center screen beyond `shopping_product`, auction insights, an experiment's auto-apply switch, and whether a video is fit to run. Say so. Do not fill them in.

Close by asking which rows to preview, and which area they want in full. A yes to "fix it" is not a yes to every row. Ask them to name the rows.
