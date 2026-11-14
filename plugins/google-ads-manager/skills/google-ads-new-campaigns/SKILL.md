---
name: google-ads-new-campaigns
description: "Use before creating any campaign, ad group, asset group or set of keywords. Research, the budget maths, names, and the build for Search, brand, Performance Max, Shopping, Demand Gen and DSA."
---

# New campaigns

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Before you create a campaign, an ad group, an asset group or a set of keywords, in a new account or a live one. How to run the account decides what to build. This skill is how to build it. Search build holds the Search settings, Ads and copy the ads, Audiences and remarketing the lists, and Conversions and bidding the bidding. Use them. Do not write a second version here.

## Before you build

Five things, confirmed:

1. The goal and the ICP: themes, pages, calls to action, negatives, and where existing customers go.
2. The primary conversion, recording. Its tag sent a request in the last few days. A campaign built on a conversion that does not record learns nothing.
3. Auto-tagging on.
4. The monthly budget for this build.
5. The countries and the languages the customers search in.

If any is missing, that is the first job, not the build.

## Research

Seeds come from the ICP themes and the pages. Call `google_ads_keyword_ideas` with the seeds and the page URL, for the countries and the language the campaign will target.

For each theme, note the monthly searches, the bid range, and the keywords that fit the page. Drop ideas the ICP called research or the wrong offer.

A theme with almost no searches is not an ad group. Fold its keywords into the nearest theme, or leave it out.

On a live account, the search terms that already convert are better seeds than any tool. Use the opportunities section of Search terms and negatives first.

## Does the budget fit

Do the maths in front of them, before you name the structure:

- Daily budget: the monthly number divided by 30.4.
- Clicks a day: the daily budget divided by the expected cost per click. Use the account's own CPC for the theme, or the middle of the bid range on a new account.
- Conversions a month: clicks a day, times 30.4, times the conversion rate. Use the account's own rate. On a new account ask for the site's rate, or state the rate you assumed and call it an assumption.

Then read it:

- A campaign that buys fewer than about 10 clicks a day is too thin to split. One campaign, fewer ad groups.
- If the plan needs about 30 conversions a month for a target strategy and the budget buys 8, the target is a guess.
- If the budget cannot cover every theme, keep the commercial themes and say which ones wait.

This is where a small budget gets fewer campaigns. A working line, not a platform law.

## Names

Use the account's naming pattern if it has one. Otherwise: type, brand or generic, theme, country. For example "Search | Generic | Payroll software | UK", with ad groups named by theme, such as "Payroll software pricing". Consistent names make every report readable.

## A Search campaign, step by step

1. The campaign. Paused. The daily budget from the maths. Search Partners off, Display Network off, AI Max off. Locations with Presence. The languages the customers search in. All hours, unless the conversion is a phone call and nobody answers at night.
2. The conversion goal. The campaign bids to the primary action the ICP named. If the account's default goal includes the wrong action, set the campaign's own goal (`set_campaign_conversion_goal` or `set_campaign_biddable_goals`, after `operation="help"`).
3. Bidding at launch. If the account already records the right conversion at volume, Maximise conversions with no target for the first weeks. If it does not, Maximise clicks with a maximum CPC limit near the top of the bid range, and say when it moves: once the campaign has about 15 to 30 conversions in 30 days. A target CPA or ROAS waits for about 30 conversions a month.
4. Ad groups. One per theme, from Search build: 5 to 20 keywords, exact and phrase, one match type per keyword text, and the final URL for the theme.
5. Ads. Two responsive search ads per ad group, from Ads and copy.
6. Assets. At least 6 sitelinks across the branch, with some written for each ad group's theme. Callouts and a structured snippet. Call, image, price or promotion assets only where Search build says the page supports them.
7. Negatives. Link the shared list. Brand negatives on generic. Cross-negatives between ad groups that could buy the same query: a general ad group gets "pricing" as a negative when a pricing ad group exists.
8. Audiences. Suppression lists as exclusions. Remarketing lists on observation.
9. The `AdPlug` label, if they agreed to it.
10. The readback from Search build. Fix what is wrong while it is still paused. Then the launch plan below.

That is a lot of changes. Preview in batches, in this order, and wait for a yes on each: the campaign, then ad groups and keywords, then ads and assets, then negatives and audiences.

## Adding an ad group to a live campaign

Check the theme against the ad groups that exist. If the intent is already covered, add the keywords there instead.

Otherwise the new ad group is paused, with its keywords, two RSAs, its own sitelinks and the page for the theme. Add the cross-negatives so it does not take traffic from a sibling group, or lose its own to one. Enabling it is its own yes. It starts with no history, so its first two weeks of CPA are noise.

## The brand campaign

Search build has the rules. One campaign, with one ad group for the brand and one for brand plus a product when there is volume. Exact and phrase. Support and login negatives as they agreed. Customers and logged-in users excluded when the goal is new customers. Target impression share with a maximum CPC limit, or Maximise conversions. Sitelinks to buyer pages. Brand negatived out of every generic campaign, and out of Performance Max with a brand exclusion.

## Performance Max

Only when How to run the account says it fits.

- Ecommerce with a feed: run Shopping products first. Listing groups cover the products they would pay for. Leave out the ones with no margin or no stock.
- Asset groups split by product category or theme, not one for everything. Each has its own final URL, headlines, long headlines, descriptions, images in landscape, square and portrait, a logo, and a real video if they have one. Without a video Google may make one from the images. Say so.
- Audience signals: the customer list, converters, high-intent visitors, and a custom segment built from the converting search terms. Signals are hints. Say so.
- Search themes from the converting Search terms, a handful per asset group.
- Brand exclusions when a brand campaign exists. Campaign negatives. Final URL expansion off.
- New customer acquisition only when a customer list exists and they want that goal.
- Maximise conversion value for ecommerce, Maximise conversions for leads. A target only once the history supports it.
- Its own budget. It cannot use a shared one.

The feed-only test in How to run the account is a valid first build when the creative is thin.

## Standard Shopping

Run Shopping products first. Start with one campaign, with product groups split by category or brand, then by custom label once those exist. Negatives come from its search terms. Manual CPC, or Maximise clicks with a limit, until there is conversion value to learn from, then target ROAS. Standard Shopping takes Google's own target ROAS strategy.

## Demand Gen

For proof and remarketing, as How to run the account says.

- Remarketing first when the budget only allows one campaign. Prospecting as a second campaign, never mixed into the same one.
- Remarketing targets the high-intent and abandoner lists. Prospecting uses lookalike segments from the customer list and custom segments from converting search terms. Exclusions from Audiences and remarketing.
- Choose the channels (`update_adgroup_demand_gen_channels`). For B2B, YouTube, Discover and Gmail first. Display only if they want it.
- Creative in square, landscape and vertical, and video if they have it. No stock filler.
- Optimized Targeting off. Bid to the primary conversion. Read view-through conversions separately.

## Dynamic Search Ads

Only on a large site where keywords cannot cover the pages, as its own paused campaign. Target the pages they would pay for. Exclude careers, blog, login, help and legal pages. Brand negatives and the shared list. Its search terms go through Monday's table. Not for a small site or a narrow niche.

## The first 14 days

Give them this plan when they enable, and put the check dates in the change log:

- Day 1: impressions and clicks arriving, nothing disapproved.
- Days 3 and 7: search terms. Most of a new campaign's waste shows up in the first week.
- Day 7: the tag still sending requests, the first conversions, CPC against the bid range.
- No bidding or budget change in the first two weeks unless something is broken. Smart Bidding is learning.
- Judge CPA only after two weeks plus the measured lag.

## What you return

The plan before anything is created. One table: each campaign's name, type, daily budget, bidding at launch, its ad groups or asset groups with their landing pages, and the clicks and conversions you expect, with the assumptions named. Then what you are leaving out and why, in two lines. Then the previews in batches, each paused. Nothing is created until they say yes to that batch.
