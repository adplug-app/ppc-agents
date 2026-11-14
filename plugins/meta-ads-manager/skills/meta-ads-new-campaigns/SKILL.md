---
name: meta-ads-new-campaigns
description: "Use before creating any campaign, ad set or set of ads. The checks, the budget maths, names, URL parameters, the build for sales, leads and remarketing, paused previews in batches, and the first 14 days."
---

# New campaigns

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Before you create a campaign, an ad set or a batch of ads, in a new account or a live one. How to run the account decides what to build. This skill is how to build it. ICP for Meta holds the personas and angles, Creatives and fatigue the ads, Remarketing and suppression the lists, and Tracking, conversions and bidding the event and the strategy. Use them. Do not write a second version here.

## Before you build

Six things, confirmed:

1. The goal, the personas and their angles, and the offer page or the form.
2. The goal event, recording. The pixel fired that event in the last few days, or the form is ready. A campaign built on an event that does not record learns nothing. The ad set preview checks the event against the pixel's last 7 days. Read that line.
3. The Page, and the Instagram account id for that ad account. No Instagram identity means Facebook-only. Say so.
4. The terms. Lead ads terms on the Page for instant forms. Custom Audience terms on the ad account for lists. Both are human steps.
5. The monthly budget for this build, and the margin or what a result is worth.
6. The countries and the languages the customers use, and any age the business can never sell to.

If any is missing, that is the first job, not the build.

## Does the budget fit

Do the maths in front of them, before you name the structure.

- Cost per result. The account's own, for this event, over the last 30 days. On a new account, the most they can pay: the margin per order, or what a lead is worth times the share that qualify. Call it an assumption.
- To leave learning, an ad set needs about 50 results in a week. That is a daily budget of about 7 times the cost per result, for each ad set. At £30 a purchase, about £210 a day, or about £6,400 a month.
- Divide the monthly budget by 30.4 for the daily budget, then by 7 times the cost per result. That is how many ad sets the budget can feed.

Then read it:

- Less than one: one campaign, one ad set. It will likely sit in learning limited. That is acceptable when the event is the real goal. Judge it on money, not on the label.
- One to two: one campaign, one prospecting ad set, and remarketing only if its lists are large.
- More: split only where the split has a reason, such as new and existing customers, or a country with its own budget. Never by interest group.

This is a working line, not a platform law. Meta publishes the 50. The 7 times is the arithmetic.

## Names

Use the account's naming pattern if it has one. Otherwise:

- Campaign: objective, funnel, setup, country. For example "Sales | Prospecting | Advantage+ | UK".
- Ad set: who and how. "New customers | Broad | UK", or "Remarketing | Checkout 14d | UK".
- Ad: persona, angle, format, month. "Gift buyer | Unboxing | Video 9x16 | 2026-11".

The names feed the URL parameters and every report, so keep them short and consistent.

## URL parameters

Every ad's link carries URL parameters, so their shop, GA4 or CRM can see which ad sent the visit. If live creatives already carry a pattern, read it from a creative and use the same one. Otherwise use:

utm_source={{site_source_name}}&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_term={{adset.name}}&utm_content={{ad.name}}

Meta fills the braces when the ad is shown. Set it as the creative's URL tags, not inside the link. Do not add parameters to a link that already has them.

## A sales campaign, step by step

1. The campaign. Paused. Sales. The budget on the campaign when its ad sets should share one pool, which most should. The strategy at launch: highest volume, unless the account already has the event at volume and they want a cost or return goal set from the margin. A special ad category if the offer needs one.
2. The ad set. Paused. Optimise to the goal event: the pixel and the purchase event, or the custom event by its exact name, or the custom conversion. The attribution setting: 7-day click and 1-day view, unless they chose another. Locations, languages and any minimum age. Advantage+ audience off, unless they said yes to on. Customers and purchasers excluded. Placements left to Advantage+ unless the persona gives a reason. No frequency cap. A schedule by hour of day only with a lifetime budget, and only when the business cannot answer at night.
3. The creatives. One per angle, from Creatives and fatigue: the Page, the Instagram id, the offer page link, the button, up to five primary texts, five headlines and five descriptions, the URL tags, the vertical file and the 4:5 file in one creative with placement customisation, and enhancements "none".
4. The ads. Paused. Three to six distinct ideas in the ad set, two or three on a small budget.
5. The readback, while it is all paused: the objective, the event and its pixel, the attribution setting, the audience limits and exclusions, the placements, the budget in currency, the strategy, the Page and Instagram ids, the links and URL tags, and the enhancements. Fix what is wrong while it is still paused.

That is a lot of changes. Preview in batches, in this order, and wait for a yes on each: the campaign, then the ad sets, then the creatives and ads, then the lists attached. Many ads go in one `bulk_create` preview. Meta allows about 20 changes per ad account every 5 minutes, so a big batch may finish in two runs. Then render previews with `ad_preview` for them to check.

Turning it on is its own yes: the campaign, its ad sets and its ads, previewed together as status changes in one `bulk_update`. Read the daily spend back in currency first.

## A leads campaign

The same, with the leads objective. For an instant form: the form first, with the questions from Tracking, conversions and bidding, the privacy policy URL, and the thank-you screen pointing to the site. Forms cannot be edited, so read the questions back before the yes. The ad set optimises to leads on the Page. For a website lead: the pixel and the lead or registration event the thank-you page fires.

## A remarketing ad set

Its lists from Remarketing and suppression, included as a limit, purchasers excluded, Advantage+ audience off. A small budget, its own creative for people who already know the brand. If its lists are under a few thousand people, do not build it.

## Catalogue ads

Only when Catalogue and shopping finds a catalogue and the products are in stock. A sales ad set pointed at a product set, with the purchase event, paused.

## Adding to a live account

A new ad set in a live campaign. Check the persona against the ad sets that exist. If it is already covered, add ads there instead. Otherwise `copy_adset` from the closest working one, paused, then change what differs. Under a campaign budget, a new ad set gets little spend at first. Say so.

New ads in a live ad set. Adding an ad is a significant edit, so add new ads in one batch, not one a day. Each new idea must differ from what is running. Meta's creative testing tool, in Ads Manager, gives new ads a fair share of spend. Creatives and fatigue has it.

## The first 14 days

Give them this plan when they enable, and put the check dates in the change log:

- Day 1: delivery started, nothing disapproved, spend near the daily budget.
- Day 3: the goal event arriving, and the pixel's last fire recent. The placement breakdown for anything spending with no results.
- Day 7: the learning status, results against the 50 a week, cost per result against the target and the break-even number.
- No budget, audience or event change in the first week unless something is broken. Every one restarts learning.
- Day 14: judge cost per result and the return on two full weeks. New ads that never got spend are a creative problem, not a budget one.

## What you return

The plan before anything is created. One table: each campaign and ad set with its name, objective, event, daily budget, strategy at launch, audience limits and exclusions, and the ads with their angles, plus the results a week you expect and the assumptions named. Then what you are leaving out and why, in two lines. Then the previews in batches, each paused. Nothing is created until they say yes to that batch.
