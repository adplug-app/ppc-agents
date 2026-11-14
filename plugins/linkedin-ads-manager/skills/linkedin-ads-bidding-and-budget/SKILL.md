---
name: linkedin-ads-bidding-and-budget
description: "Use when setting or reviewing a bid, a cost cap, a budget, a shared campaign budget, or the month's pace. A cost cap or a budget moves by about 20% at most in one step."
---

# Bidding and budget

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A new ad set, a cost that drifted from the target, a budget that is ahead or behind, or "should this be maximum delivery". The goal comes from the ICP. If you do not know whether you are buying form fills or a conversion sales would recognise, run Lead forms and conversions before you touch a bid.

Read the live ad set first: `linkedin_ads_get` `entity_type` `campaign`. Cost type, bid amount, optimisation goal, daily budget, total budget, schedule and pacing are on that object. The campaign, `entity_type` `campaign_group`, returns its status, total budget and schedule. Its bidding strategy is not in that read. If the reply depends on it, say you could not read it.

## Three ways to bid

LinkedIn offers three strategies. Which ones an ad set can use depends on the objective, the format and the optimisation goal.

Maximum delivery. LinkedIn bids to spend the whole budget and get the most of the optimisation goal. It is charged per thousand impressions, and you cannot set a bid or a cap on it. A new ad set on it enters a learning phase, and results swing while it learns. It suits an audience large enough that the budget will not hit the same members all month, with the optimisation goal set to the agreed conversion. It is the default in Campaign Manager. Do not leave it on for that reason. On a small list it buys frequency.

Cost cap. You set the average cost per result you will accept, and LinkedIn bids under it, cheapest results first. It is charged per thousand impressions. It works on brand awareness, website visits, engagement, video views and lead generation, and LinkedIn names it as the cost control for leads. In the connector the optimisation goal for a capped lead ad set is `CAP_COST_AND_MAXIMIZE_LEADS`. A cap set below what the market charges spends less of the budget. That is the trade.

Manual bidding. You set the bid. It can be charged per click, per thousand impressions, per video view or per send, depending on the objective and the goal. On a lead or website conversion goal LinkedIn still adjusts the bid, and labels it enhanced. Manual is the right ask on a named list where they want a ceiling, and on conversation ads, charged per send.

`cost_type` defaults to CPM when you leave it out of a create. Set it on purpose, in the preview, in words they use. If you are not sure of a goal or a strategy value, call `operation="help"`. Do not guess one.

## When to propose a cost cap

Propose one when all of this is true:

- the ad set is on maximum delivery with the leads goal
- its cost per lead has been above their target for two weeks or more
- there is volume behind it: about 15 or more leads in the last 30 days, a working line, not a LinkedIn rule
- it is spending its budget, so the auction, not the audience, is setting the price

Start the cap near what the ad set achieves now, not at the target. Then step it down by about 20% at a time, two weeks apart, and watch spend. If spend falls by more than the cost improves, the cap is too tight. Raise it back one step. A cap set straight at a target far below today's cost mostly stops delivery.

Do not propose a cap on a new ad set still learning, on a thin ad set with a few leads a month, or as a fix for a weak offer or a form that does not complete.

## What you optimise toward

The optimisation goal matches the goal. Set it with `optimization_target_type`.

A form they agreed is the goal: leads. A website event that matches the button on the page: that conversion, once the Insight Tag is recording it. Qualified leads: only when qualified lead events come back from their CRM, and only on maximum delivery. Thought leadership: reach or impressions, in its own campaign, never a lead goal.

Clicks, visits, and engagement are the wrong goal on a cold ad set whose goal is a qualified lead, a demo, or pipeline. Name the ad set and the goal in the first line when you find one. Changing it is a yes.

## The shared campaign budget

LinkedIn's Dynamic Group Budget puts the budget, the schedule and the bidding strategy on the campaign, and shares the money across its ad sets. Bid amounts for a cost cap or manual bid stay on each ad set. Every ad set in that campaign must share the objective, the bidding strategy, the optimisation goal and the schedule. It takes up to 50 ad sets, Sponsored Content formats only. AdPlug's create asks for a total budget and an end date with it.

LinkedIn does not require a shared budget for maximum delivery. AdPlug's tool help says an ad set with no bid needs its campaign on maximum delivery. If a preview or an execute says the campaign needs that setting, stop and say it plainly before anything else: "This turns on a shared budget for the whole campaign: one total, one end date, split by LinkedIn across every ad set in it." Name the ad sets it would pool. Offer the alternatives: put the ad set in its own campaign, so the pool is one ad set, or use a cost cap or a manual bid. Never pool a budget silently, and never pool thought leadership with lead gen, or a strong ad set with a weak one.

## How far you move

A bid, a cost cap, a daily budget or a total budget moves by about 20% in one step. If they ask for more, show two smaller steps and the dates you would check. A single large jump makes the next fortnight hard to read. It is still their call. Do not apply the second step in the same preview as the first.

## Budgets and pace

LinkedIn's minimum is $10 a day per ad set, or the same in the account currency. A daily budget can spend up to double on a given day. Over a week, a continuous ad set will not spend more than seven times the daily budget, and a scheduled one not more than the daily budget times its days. A single day at nearly twice the budget is normal. A lifetime budget spends unevenly by design.

Pace is a report. Month to date against the monthly budget they gave, in the account currency. Spend from the performance tool is in the account's own currency, so month to date and the budget compare directly. You can also see whether an ad set's own budget is exhausted early.

If they gave no budget, ask once. Do not invent one from last month's spend.

Pacing in the connector is `LIFETIME`, LinkedIn's normal pacing, or `ACCELERATED`. LinkedIn is still testing accelerated delivery, only for live event ads on lifetime budgets. Do not set it on lead gen.

Dayparting exists in Campaign Manager for Sponsored Content on a lifetime budget with the Audience Network off. This tool cannot set it. B2B delivery is already weekday-heavy, so it is rarely the first fix.

A frequency cap in this connector is only for a brand awareness ad set with connected TV turned on. Do not send `frequency_cap` on a lead gen ad set. You manage feed frequency with the audience size, the budget, and by pausing the tired ad.

## Enabling, and the read-back

A new ad set stays draft. Before you ask to turn a named one on, read back the budget, the bid, the objective, the optimisation goal, the end date if there is one, the exclusions, and that expansion and the Audience Network are off. Audiences has already counted the forecast. If the forecast is under 300, do not ask to enable it. The campaign has to be live for its ad set to run. Say so in the launch preview.

On an enterprise account, a campaign that is not the account's default may only accept a name or a status change. If a budget edit fails for that reason, say so. Do not keep patching fields the error refused.

## What you return

The bid in words: maximum delivery, a cost cap, or manual, with the amount and the target. Any shared campaign budget, named, with the ad sets in it. The pace, in one line, or the reason you cannot compare currencies. The one move you would preview, within about 20%, or the reason you would not move anything. Nothing applied.
