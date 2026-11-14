---
name: meta-ads-tracking-conversions-and-bidding
description: "Use when the event, the pixel, the Conversions API, attribution, lead quality, learning or the bid strategy is in question. The event has to match the button. Recommends. Does not switch it."
---

# Tracking, conversions and bidding

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Tuesday routine, an audit, a new campaign, a result that looks too cheap, or a question about why Meta's numbers differ from theirs. Read the goal and the button first. If you do not know them, ask, and still read the live event so the question is specific.

## The event

The primary event is the action on the button or the form. A purchase button is a purchase. A demo button is a lead or a completed registration, whichever event the page fires. A guide download is not a purchase.

More clicks, landing page views and ThruPlays are not that event. Add to cart is not a purchase. An instant-form lead is not a qualified lead. If the live ad set optimises to a cheaper action than the goal, that is the first finding. Recommend the tighter event and wait. Changing the optimisation event is a significant edit.

Read what each ad set optimises for from its promoted object, and what it got from `results` and `cost_per_result` in `meta_ads_performance`. That is Meta's Results column. After an ad set switches events, Results counts the old days as the new event, so use the named event in `conversions` for history. Custom pixel events and custom conversions come back by name. To keep a report to the events that matter, pass `conversion_events`, such as purchase, or the custom event's exact name.

When the account cannot get near 50 of the real events in a week, say so. Meta uses that figure as the usual point at which delivery settles after the last significant edit. Meta also suggests moving to a more frequent event so an ad set can leave learning. Do not follow that suggestion when the more frequent event is not the goal. Offer a simpler structure, a bigger share of budget in fewer ad sets, or a hold, and wait.

To change the event on a live ad set, preview `update_adset` with the new event. The preview shows the event now and after, checks the new one against what the pixel received in the last 7 days, and warns that learning restarts. Meta only accepts some event changes on a published ad set, such as one custom pixel event to another on the same pixel. When it refuses, the route is a new ad set with the same ads, created paused, and the old one paused after the new one is live.

## What the pixel is sending

List pixels with `meta_ads_list` and `entity_type` `pixels`. The useful field is when it last fired. One last-fired time does not tell you whether the browser pixel and the Conversions API both sent the event, or whether the purchase event is firing while page views are.

If ads are spending and the last fire is more than about a day old, that is an alarm. If the goal event had results on most days last week and none in the last two days while spend continues, that is an alarm too. One quiet morning is not a dead pixel. Say what you compared.

Then read one purchase row, or one lead row, that matches the goal. Website purchases, Meta's pooled purchases and on-site purchases overlap. Adding them inflates the result. Name the one you used, in plain language. Report an instant-form lead and a website lead as two lines when both exist.

When they give you the shop's orders for the same days, compare. If Meta's purchases on the click-only read are more than the shop's total orders, Meta is counting some purchases twice. Suspect broken deduplication or a second pixel on the site, and send them to Events Manager.

Purchase value and return on ad spend only count if a value came back. If the value columns are empty, do not recommend value bidding. Say the event is arriving without a value.

## What you cannot see, and where it lives

This connector cannot send Conversions API events, and cannot read the event match quality score or the deduplication report. Do not invent a match score.

Meta's recommendations can flag both gaps. Read `meta_ads_list` with `entity_type` `recommendations` and look for titles about the Conversions API, server events, or customer information and match keys. Put any flag in the finding, in plain words.

Then point them at Events Manager, the dataset, then Overview and Diagnostics, for:

- event match quality for the goal event. Meta grades it out of 10, for web events only, and publishes no minimum. Higher means Meta can tie more conversions to people.
- deduplication. The browser and the server must send the same event name and the same event id, within 48 hours of each other, or Meta counts the event twice.
- coverage. Meta's stated goal is server events covering about 75% of the pixel's events.
- the diagnostics Meta raises on the dataset.

If they have no server-side events, recommend them, because browser-only tracking misses conversions, and say the routes: their shop platform's Meta integration, Meta's Conversions API Gateway, or a developer or partner. You cannot set any of them up from here.

Aggregated event measurement still sits under some iOS web measurement. Meta's current help says you no longer prioritise eight events per domain, the old setup tab has been removed, and you do not pick a conversion domain to create a campaign. Do not send them back to that eight-event list. If iOS results look thin, say you cannot see modelled events from here. A device breakdown is where the impression was served. It is not the attribution report.

A custom conversion, for a thank-you URL or a named event, is something you can preview when the page has that URL and the account is optimising to a vague lead. It is a change. Wait for a yes. Do not create one from a routine.

## Attribution

Each ad set has an attribution setting that decides which conversions it learns from and reports: clicks within 1 or 7 days, views within 1 day, and for video an engaged view. Meta's default is 7-day click and 1-day view. Read it with `meta_ads_list`, `entity_type` `adsets` and `fields` including the attribution setting. AdPlug can set it when an ad set is created, not on a live one.

Reports default to the same 7-day click and 1-day view. When they compare Meta with their shop, GA4 or CRM, also pull the click-only read, `attribution_windows` `1d_click`, and show both. A large gap between the two means much of Meta's credit comes from views or late clicks. Say that in plain words. Never add Meta's conversions to their own system's numbers. Report them side by side.

Meta also offers an incremental attribution setting in Ads Manager, which credits only the conversions its models think the ad caused. This connector cannot set or read it. If they turn it on, results will look smaller. That is a change of counting, not of performance.

If they gave you total revenue for the period, revenue divided by all ad spend is the number Meta cannot inflate. Put it next to Meta's return in the monthly report.

## Lead quality

An instant form is cheap because it is easy. Two settings decide how easy:

- The form type. Meta's higher-intent type adds a review step before submit. AdPlug creates forms in Meta's default type. For the higher-intent type, they build the form in Ads Manager.
- The questions. A question a salesperson needs, such as company size or timeline, filters out people who will never buy. You can preview a new form with those questions. Forms cannot be edited, only replaced.

Ask what share of leads become qualified, and remember it. If the AdPlug HubSpot connector is also connected here, read the lead stages there and report them next to Meta's leads, never added to them.

Optimising to leads that turn into sales is Meta's conversion leads goal. Since April 2026, new campaigns can use it only with a Conversions API integration that sends CRM stages back to Meta. Existing campaigns followed from August 2026. Meta's guide for the Conversions API for CRM lists: at least about 200 leads a month, lead stages sent back at least daily with Meta's lead id, and a target stage reached within 28 days by 1% to 40% of leads. Meta's own pages disagree on which forms it covers. The help page now says website forms can use it. The developer guide still says instant forms. Tell them to check on their own campaign in Ads Manager. Setup is in Events Manager or through a CRM partner, then a learning period of a few weeks. This connector cannot send those stages. When Events Manager shows the CRM dataset ready, the quality lead goal can be previewed on a new ad set, paused.

For website leads, later CRM stages go back to Meta as server events through a partner or a developer. Again, not from here.

## Bid strategies

Read the strategy already on the campaign or the ad set before you recommend another. Call `operation="help"` before you send a strategy value. If help does not list the allowed values, do not invent the enum. Describe the strategy in plain language and stop until you can name the parameter.

AdPlug's own default, when a budget is set and no strategy is given, is highest volume. That spends the budget for as many of the chosen events as it can. It does not hold a cost or a return. If they have given you a target cost or a target return, do not leave highest volume in place. Recommend a cost-per-result goal, or a return goal when purchase value is real, and wait.

Set the target from the money, not from a wish. The return goal starts at or above break-even, 1 divided by the contribution margin. The cost-per-result goal stays under the margin per order, or under what a lead is worth times the share that qualify. Say both numbers in the preview.

Highest value spends the budget towards higher purchase value. It is not a return target. Use it only when value is on the event and they care about the value of the purchases more than a set return.

For the cost and return strategies, Meta recommends about 50 to 100 conversions a week. A thin account should not be put on a tight cost goal. Say the goal would be a guess, and wait. A goal far below what the account has been achieving will throttle delivery. Say the recent cost next to the target. Do not tighten it by more than about 20% in one step.

Placement value rules, which raise or lower a bid by placement, are not a tool here.

## Learning and edits

Read each ad set's learning status with `meta_ads_list`, `entity_type` `adsets` and `fields` including the learning status. It says learning, learning limited, or out of learning, with the events counted since the last significant edit.

Learning: leave it alone unless something is broken. Its cost per result is not the one it will settle at. Do not judge it in its first days.

Learning limited: Meta expects fewer than about 50 events in the week. Do the sum: the weekly budget divided by the cost per result. If it cannot reach 50, the fixes are fewer ad sets with more budget each, a wider audience, a budget raised in steps of about 20%, or a looser cost goal. Say which, and wait. One change at a time.

Then the activity log, `meta_ads_list` with `entity_type` `activity_logs`. If the last few days include a targeting change, a creative change, an event change, a new ad, a bid-strategy change, or a large budget change, say that this can put delivery back into learning. Do not add another edit on top. A campaign budget change can affect every ad set in that campaign. An edit on one ad set does not, by itself, reset the others.

Do not pause an ad set for a week and then turn it back on as a tidy-up. Meta treats a pause of seven days or longer as a significant edit when it is switched on again.

## Budgets

Pace is a report against the monthly number they gave you. You do not move a budget because the pace is off unless they say yes to that campaign or ad set, and even then the step is about 20% or less. Several budget moves at once go in one `bulk_update` preview, so they see every row before anything changes.

A campaign that holds the budget is one pool. Its ad sets do not also get their own budgets. If a preview says the parent already holds the budget, explain that in normal words. Meta sometimes reports that clash as a missing bid. The preview's explanation is the one you trust.

Ad set budget sharing, which lets ad sets give each other up to about 20% of their budgets, defaults off. Turning it on also defaults the strategy to highest volume. Do not turn it on without a yes that names both the sharing and the strategy.

## What you return

The event they asked for, the event the account is buying, and whether the pixel fired. The attribution setting, and the click-only read when it matters. The learning status of the ad sets that spend. The strategy in plain language, next to the target and the break-even number. What you could not see, and where it lives. Rows to preview. Nothing applied.
