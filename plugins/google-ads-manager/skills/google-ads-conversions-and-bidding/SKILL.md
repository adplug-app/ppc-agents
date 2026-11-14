---
name: google-ads-conversions-and-bidding
description: "Use when checking what the account bids toward, whether conversions are recording, tracking hygiene, conversion lag, Smart Bidding status and targets, seasonality and data exclusions, or which bid strategy a campaign should use. Change nothing without a preview."
---

# Conversions and bidding

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

An audit, a new campaign, a CPA or ROAS question, or a week that spent with no conversions. The daily check's tag alarm and Tuesday's conversion line use the short version. The full check is this skill, not a weekly essay.

The confirmed ICP names the goal and the call to action on the page. If either is missing, ask before you judge the primary action. More clicks is not a goal.

## The right conversion

Read `conversion_action`. Primary for goal (`primary_for_goal` true) is what bidding uses. Secondary is for observation.

The call to action on the landing page is what the campaign is allowed to optimise toward. Read the button if you can open the page. "Book a demo" means the primary action should be a demo or a qualified lead. "Buy" means a purchase. If the primary conversion does not match the button on the page the ads send to, say so in the first line.

Lead gen, including B2B, is the careful case. Do not optimise that campaign to a page view, a scroll, or an easy form fill when the page is asking for a sales conversation. Shopping is the other case. The goal is profitable sales, not lead quality. Use the Shopping products skill for product-level cost against conversion value. Do not invent a margin the feed does not have. If you need a target ROAS or a margin to judge a product, ask for it.

Leads are counted once (`ONE_PER_CLICK`). Purchases are counted every time (`MANY_PER_CLICK`). A lead counted many times teaches the bids to love repeat form fills.

If the business wanted a qualified lead or a sale, and the primary action is a page view, a scroll, or an easy form fill, say that in the first line. That action will buy the cheapest version of itself. Do not "fix" a bad week by loosening keywords while this is true.

`campaign_conversion_goal` says what a campaign is allowed to bid to, by category and origin, through `biddable`. A campaign sitting on the account default is a problem when that default is the wrong action. A custom conversion goal can still bid to an action marked secondary. If you see one, say so. Do not assume the primary flag is the whole story. If the query fails, use the view doc and try once more, then say what you could not see.

## Are conversions recording

`google_ads_conversion_performance` and the campaign comparison. Google attributes conversions to the click date. A recent CPA can look worse until conversions land. Do not call a quiet recent week a broken tag until the account's usual delay has passed. A campaign that has never converted is still a tracking or an offer problem. A campaign that used to convert, and is still at zero after that delay, is a tracking problem until something else is proved. Say that before you recommend a bid change or a negative.

Measure the usual delay. Do not guess it. Query conversions by `segments.conversion_lag_bucket` over the last 90 days, or compare `metrics.conversions` with `metrics.conversions_by_conversion_date` by day. Find the number of days within which about 90% of conversions arrive. Remember it per account, say it in days, and use it everywhere this agent talks about lag. Refresh it in the monthly check.

Tag health. Read `metrics.conversion_last_received_request_date_time` and `metrics.conversion_last_conversion_date` on each primary `conversion_action`. A tag that last sent a request four days ago, on an account that converts every day, has stopped, whatever the lag. A tag that pings but records nothing is a different problem: the event fires, and the conversion settings or the page are wrong.

You cannot see the tag fire in a browser, or the consent banner. You can see when Google last heard from the tag, the actions configured, and the conversions recorded. Say which one you are looking at.

## Tracking hygiene

The monthly check and the full audit.

- Auto-tagging. `customer.auto_tagging_enabled`. If it is off, the click id is not added to the URL. GA4 cannot attribute the click, imported GA4 conversions break, and offline uploads have nothing to match. Recommend it on. The connector can switch it with `update_customer`, after `operation="help"` and a preview.
- URL tracking. `tracking_url_template` and `final_url_suffix` at account, campaign and ad group level. Two levels that set different UTMs, or a suffix that strips the click id, break the source data in GA4 and the CRM. Name the level and the value.
- Counted twice. Two primary actions for the same event, usually the Google Ads tag and a GA4 import of the same purchase or lead. Bidding sees double. One of them goes to secondary. Ask which one they trust before you recommend which.
- Window and attribution. `click_through_lookback_window_days` and the attribution model on each primary action. A 7-day window on a sales cycle of six weeks under-counts and teaches the bids the wrong lesson. Data-driven is Google's default. Last click on a primary action is worth a line.
- Offline uploads. When the account imports CRM stages, read `offline_conversion_upload_client_summary` and the per-action summary: the last successful upload, the success rate and any alerts. An upload that stopped is the same alarm as a tag that stopped.
- Lead quality. When the KPI is qualified leads and no offline stage is imported, the account can only count form fills. Say so in reports, because a lower CPA on unqualified leads is not an improvement anyone can see from here.

Enhanced conversions for leads: read `customer.conversion_tracking_setting.enhanced_conversions_for_leads_enabled`. For B2B, also look for offline or CRM conversion actions (imported stages, not another website page view). If the field is false or the action is absent, say it is not set up. Do not infer it from a healthy lead count.

Consent mode, for an account that targets the EEA or the UK: ask whether it is in place. You cannot verify the banner from this API.

## Bidding

The strategy matches the goal and the volume.

Under about 30 conversions in a month on the campaign, a tCPA or a tROAS is a guess. Say so. Keep match types tight. Do not raise the target to make a thin campaign "more efficient".

Maximise conversions or maximise conversion value wants a real primary conversion. Manual CPC, or Maximise clicks, only when there is nothing for smart bidding to learn from, and you say why in the same paragraph. They are not a permanent home once qualified conversions are coming in.

Brand Search can use target impression share when they want to own the brand queries. That is a brand decision. Do not copy it onto the generic campaign.

Do not change a bid strategy, a target, or a campaign goal without a preview and a yes. Read the strategy back before a new campaign is enabled. The campaign is still paused when you do that readback.

Name the bidding strategy on the campaign before you recommend a device, location, audience, or ad schedule change.

## Smart Bidding status and targets

Read `campaign.bidding_strategy_system_status`. A campaign that is learning after a change is not judged on CPA until the learning ends and the measured lag has passed. Say "learning since" and the date of the change. Limited by budget, limited by data, or misconfigured is a finding: name the campaign and the reason.

Portfolio strategies are one strategy across several campaigns, like a shared budget is one pool. Name the portfolio and every campaign on it before you talk about its target.

Target against actual, in the monthly check and the full audit. Compare each campaign's target CPA or target ROAS with what it achieved over the last 30 days, read with the lag. A target CPA well below the actual CPA usually chokes volume: the campaign cannot win the auctions it needs. A target well above the actual lets spend drift up. Either is a finding with both numbers. Moving a target is a change, with the 20% step rule from the instructions.

## Seasonality and data exclusions

Two Smart Bidding controls that most accounts never use.

A data exclusion tells Smart Bidding to ignore the conversion data from a date range: a tag that broke, a site that was down, a checkout that failed. When the daily check or Monday finds a tracking break and it is fixed, recommend a data exclusion for those exact dates, so the bids do not learn that the account stopped converting.

A seasonality adjustment tells Smart Bidding that conversion rate will change for a short event: a sale, a launch, a flash promotion. It is for one to seven days. A whole season or a normal busy month does not need one. Smart Bidding sees those.

You can read both (`bidding_data_exclusion` and `bidding_seasonality_adjustment`). AdPlug cannot create them yet. Tell them to add it in Google Ads, under the advanced controls for bid strategies in the tools menu, with the dates, the campaigns and, for seasonality, the expected change in conversion rate. Check it is there the next time you look.

Promotion dates. In the monthly check, ask once whether there is a sale, a launch or a closure in the next six weeks, and remember the dates. Two weeks before one: a seasonality adjustment if it is short, a promotion asset with the dates, the budget pace against the extra spend, and ads that mention the offer. The day after it ends, check the adjustment, the asset and the ads have stopped.

## Bid adjustments

A percentage is not an exclusion. Name the strategy in the same sentence as the advice.

Manual CPC. Device, location, ad schedule, and audience percentages change the bid. A -100% device adjustment stops that device. Location percentages only go down to -90%, so they do not stop a place. Exclude the location for that.

Enhanced CPC. Google's help says it is no longer available for Search and Display as of the week of 31 March 2025, and campaigns that were not moved now behave as Manual CPC. If the campaign still shows Enhanced CPC, treat percentages as Manual CPC and say the label may be stale. Do not recommend turning it on. If that help page has changed, say so.

Maximise clicks. Percentages apply, on top of a max CPC limit if one is set. Google's page says a mobile adjustment is incorporated. Recommend one only when the numbers support it. It is not the default.

Target impression share. A device percentage is ignored except -100%, which excludes that device. Location, ad schedule, and audience percentages are not supported. Do not recommend a +20% mobile adjustment.

Target CPA. A device percentage does not change the bid. It changes the CPA target on that device. Say the target in money. A +20% on mobile is a higher CPA target on mobile, not a higher bid. Do not recommend it unless they want that different target. A -100% device adjustment stops ads on that device. Location, ad schedule, and audience percentages are ignored on Search and Display.

Target ROAS, Maximise conversions, and Maximise conversion value. Percentage adjustments are ignored. That includes +20% mobile, a location percentage, an audience percentage, and a percentage on an hour. Do not recommend them. A -100% device adjustment still excludes that device.

Performance Max does not support these bid adjustments. Do not recommend one. If the campaign is not Search, do not copy this chart onto it. Say the campaign type.

What still stops traffic:

- Device. -100% on that device stops it, including on the strategies that ignore every other percentage.
- Ad schedule. The days and hours in the schedule are when ads can run. Smart Bidding follows those hours and ignores a percentage on them, such as +20% on Saturday. Target impression share does not support that percentage either. On Manual CPC and Maximise clicks, the percentage does change the bid. To stop a day, leave it out of the schedule.
- Audience. An exclusion stops that audience. An observation list does not limit who sees the ad, and a percentage on it does nothing on a strategy that ignores audience adjustments. You cannot exclude an audience by setting the percentage to -100%. The floor is -90%. Use an exclusion. Search stays on observation unless Audiences and remarketing says otherwise.
- Location. A percentage does not stop a place. On a strategy that ignores it, do not recommend one. To stop a place, exclude it, and wait for a yes.

Do not change an adjustment without a preview and a yes. Search build and Audiences and remarketing point here. They do not keep a second copy of this rule.

## Auto-applied recommendations

Most auto-apply subscriptions should be off. Recommend turning them off. Do not turn one off without a yes. A routine never does.

Read `recommendation_subscription` with `google_ads_query`: type and status. ENABLED is on. Also read `google_ads_recommendations`, and label those rows as Google's suggestions, not as subscriptions.

Name every type that is on. Recommend switching off anything that changes keywords, match types, negatives, networks, bidding, or budgets. That includes adding keywords, adding broad match, removing keywords, removing conflicting negatives, Search Partners, Display expansion, and any bid strategy or target. Google's help says auto-apply will not increase the budget, and budget raising is not in the current set. If a budget subscription is ever on, recommend it off. Do not say auto-apply raised the budget unless change history shows that. Search Partners and Display expansion can still be turned on by auto-apply, which puts those networks back on.

From 26 January 2026, Google's help says "Add responsive search ads" no longer suggests or applies new responsive search ads, and it is removed from the Auto-apply page. If that subscription is still enabled, name it. "Improve your responsive search ads" can still add headlines and descriptions from existing content. That is not a sitelink. Recommend it off.

Also recommend off, because the default is off: dynamic search ads, optimised ad rotation, added audiences, and targeting expansion. Upgrade conversion tracking changes what the account counts. Name it, and do not leave it running unattended.

Sitelink and callout suggestions are a review item. Google's current auto-apply page does not list them as subscriptions. Do not apply them to raise optimisation score. If an asset subscription for them is on, do not leave it running unattended. Recommend pausing it, and wait for a yes.

If you are not sure this help page is still current, say so. Do not invent a date.

AdPlug's operation is `set_recommendation_auto_apply`. Call `operation="help"` before you preview it. Do not invent parameters. The connector takes `recommendation_types` (a list, or all) and `status` (ENABLED to opt in, OPTED_OUT or PAUSED to turn off). `disable_all_auto_apply` pauses every type that connector supports. Those types are KEYWORD, USE_BROAD_MATCH_KEYWORD, KEYWORD_MATCH_TYPE, SEARCH_PARTNERS_OPT_IN, DISPLAY_EXPANSION_OPT_IN, TARGET_CPA_OPT_IN, TARGET_ROAS_OPT_IN, MAXIMIZE_CONVERSIONS_OPT_IN, MAXIMIZE_CLICKS_OPT_IN, ENHANCED_CPC_OPT_IN, OPTIMIZE_AD_ROTATION, RESPONSIVE_SEARCH_AD, and RESPONSIVE_SEARCH_AD_IMPROVE_AD_STRENGTH. A type Google shows that the tool cannot set is still a finding. Say so. They turn that one off in Google Ads. You recommend. You do not apply.

## Budget pace

If they have given a budget, look after it. Account total, a campaign's daily or monthly amount, or a monthly number they told you. Remember which one.

Where the month should be: their monthly number times the day of the month, divided by the number of days in the month. Compare that with spend so far from `google_ads_account_performance` and `google_ads_campaign_performance`, and with the previous period when the tool can compare. Use `google_ads_daily_trends` when the month is ahead or behind and you need to see whether it was one day or a slope.

Impression share lost to budget and impression share lost to rank are context for that pace, not a target. Lost to budget is not an order to raise the budget. Lost to rank is not an order to raise a bid. A winner that is capped while a weak campaign still has room is a finding you put in front of them. Meeting the KPI matters. Spending more is not the goal. If the campaign tool does not return the lost-share fields, query them and call the view doc if a field fails. Do not invent a percentage.

A shared budget is one pool. Read `campaign_budget.explicitly_shared` and the budget's name, and name every enabled campaign on it. Brand and generic on the same pool, or a strong campaign and a weak one, is a finding. Do not split the pool, and do not create a shared budget, without a yes. Google's shared-budget help limits them to Search, Shopping, Display, and Video. Performance Max cannot use one, and nor can App campaigns, Hotel campaigns on Commission, Smart Shopping, a campaign in an experiment, or a campaign that uses a total budget. Performance Max keeps its own budget. Google's help does not state a cap on how many campaigns can share one pool, and the API limits page says there is no such cap. Do not invent one. If those pages have changed, say so.

Surface a deviation with the campaign name, the number, and the gap. Overspending against the month. A campaign that will exhaust its budget before the month ends. A campaign that is barely spending. The winner capped while a weak campaign still has room.

Lead gen and Shopping both count. On Shopping, spend ahead of the plan with a weak product return is a deviation. It is not a reason to scale. Do not invent margin or a target ROAS. Ask if you need one.

If no budget was given, ask once, then skip the pace lines until they answer. Do not invent a monthly number from last month's spend and call it the plan.

Do not move a budget, raise a daily cap, or pause a campaign because of pace unless they say yes. The Tuesday short audit includes this section whenever a budget is known.

## What you return

The primary actions, whether they match the call to action on the page, and whether they match the business goal. Campaigns bidding to the wrong goal. Any campaign with spend and zero conversions, read with conversion lag. The measured lag in days. When each primary tag last sent a request. Enhanced conversions for leads and offline stages: on, off, or not visible. Auto-tagging, URL tracking, double counting and windows, only where one is wrong. Smart Bidding status where it is learning, limited or misconfigured, and targets far from actual. The bid strategy against the month's conversion count, using their target CPA or ROAS when they have given you one. Auto-apply subscriptions that are on, by name. Any percentage you would not recommend because the strategy ignores it, with the strategy named. Shared budgets that mix the wrong campaigns, by pool name. What you would change, unapplied. You have not changed anything.
