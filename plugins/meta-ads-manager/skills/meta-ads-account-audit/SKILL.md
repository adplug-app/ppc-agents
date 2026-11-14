---
name: meta-ads-account-audit
description: "Use when they ask for an audit, a health check or a second opinion on a Meta ad account. The full pass. Change nothing unless they then pick a row."
---

# Account audit

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

An audit, a second opinion, a new account, or "what should I look at". The routines cover the daily alarms, fatigue and placements, pace and the goal, lists and structure, the ads, and the month. This skill is the full pass. Do not run it inside a routine. The daily, Tuesday and monthly passes are in Daily and monthly checks.

## Before the checklist

You need the business, the goal, the button or the form, the budget, the target, and the margin or what a lead is worth. If you do not have them, ask, and still pull the structural facts so the questions are specific. Do not audit a new account until Get started has those answers.

Name the client, the ad account, the currency and the date range before the findings. One account. Do not add figures across clients or currencies. Default the comparison to the last 30 days against the previous 30 days, with two performance calls. Say if a tool returns a different window.

New account, new pixel or no conversion history: say so first. Judge the tracking and the setup, not the results. A new pixel is not bad creative, and a week of data is not a verdict.

Use the other skills for their sections. Do not invent a thinner version of them. Pull lists with `fields` so the calls stay small: ad sets with their budget, event, learning status, attribution setting and targeting in one call.

## The full pass

Work in this order. Skip a section that does not apply and say it is not in this account. You only write up what needs a decision, plus the scorecard line.

1. Money. Spend against the budget. The result against the target, and against the break-even return or the most they can pay per result. A campaign that loses money on the margin they gave is the first line, whatever its Meta score.

2. Fit. Given what they sell and the budget, is one sales or one leads campaign the right shape? Use How to run the account, after the ICP. If Meta is a poor fit, that is the first paragraph.

3. Tracking and the event. Use Tracking, conversions and bidding. The live event against the button. One purchase row, not three added together. Whether the pixel fired. The attribution setting on the ad sets that spend, and the click-only read next to the default. Lead quality, if leads. Conversions API coverage and match-key flags from Meta's recommendations, and what you still cannot see.

4. Learning and structure. The learning status of each ad set that spends, and the share of spend in learning limited. Too many ad sets splitting too few events. Prospecting and remarketing separate. Advantage+ audience on or off, read from the ad set, and any campaign that lost its Advantage+ state by accident. Too many objectives for the budget. Catalogue only if Catalogue and shopping finds one.

5. Lists. Use Remarketing and suppression. Customers excluded from prospecting when a list exists. The lists that are missing, too small, or still empty.

6. Creative. Use Creatives and fatigue. Tired ads, ad sets with no variety, disapprovals, enhancements on that nobody chose, and whether the live ads say something the page does not say.

7. Placements and audiences. Use Audiences and placements. Waste first. Overlap second.

8. Bidding. The strategy against the target, from Tracking, conversions and bidding. A step larger than about 20% that someone already took.

9. Recent edits. The activity log for the last 14 days. Name the edit and the date when results moved. Do not claim a cause you cannot see.

10. Meta's recommendations. `meta_ads_list` with `entity_type` `recommendations`. Diagnostic flags, such as creative fatigue, learning limited, Conversions API coverage or match keys, go beside your own numbers in the section they belong to. Recommendations that conflict with this method, such as Advantage+ audience, automatic placements, creative enhancements or a big budget jump, are judged on money against the target. Never apply one to raise the opportunity score.

11. Automated rules. `meta_ads_list` with `entity_type` `rules`. An enabled rule that pauses ads or raises budgets explains learning resets and moves you did not make. Name each enabled rule and what it does. Rules come from Tests and changes.

12. Tests and the log. Use Tests and changes. Tests running, changes due for a check, and anything that was never checked.

13. Competitor creative, optional. Only when competitors are on file or they ask. Use Competitor ads, short form: new launches, long runners and the angles nobody uses.

## What you return from a full audit

Use these headings and no others. Keep it to one screen before the detail.

Account. One line: name, id, currency, range.

The headline. Three sentences: how the account sits against the goal and the margin, the biggest problem with its cost, and the biggest opportunity.

Needs a decision. At most five items, worst first. Each has the number that makes it matter and the decision you need. Anything else is one line saying how many smaller items there are.

Scorecard. One table, one row per area that applies: Money, Fit, Tracking, Learning and structure, Lists, Creative, Placements, Bidding. OK, Fix or Check, and one short line. Areas not in the account are left out, with one line listing them.

What I would change. Numbered rows you can preview. Nothing applied. New work marked paused.

What I could not see. The event match quality score, the deduplication report, the incremental attribution setting, account-level placement controls and value rules, quality rankings, and any page you could not open. Say so. Do not fill them in.

Close by asking which rows to preview, and which area they want in full. A yes to "fix it" is not a yes to every row. Ask them to name the rows.
