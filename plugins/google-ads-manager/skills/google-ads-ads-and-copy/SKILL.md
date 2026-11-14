---
name: google-ads-ads-and-copy
description: "Use when reviewing or writing responsive search ads, sitelinks, callouts or snippets: which ad wins, low-rated assets, pinning, disapprovals, and new copy written paused."
---

# Ads and copy

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A new ad group, the ads section of the full audit, the monthly check, low expected click-through rate in Quality Score, or a request to write or fix ads. Search build sets how many ads and assets an ad group needs. This skill judges them and writes them.

## Reading the ads you have

Approval first. `ad_group_ad.policy_summary.approval_status`. `DISAPPROVED` leads, with the policy topic. `APPROVED_LIMITED` and `AREA_OF_INTEREST_ONLY` are serving with a restriction: a lower line, with the topic, often a trademark or a restricted category. An ad still under review is not a finding.

The two ads in an ad group. Compare conversion rate and cost per conversion over the last 30 to 90 days. Not click-through rate alone. An ad that gets more clicks and converts worse is the worse ad. Call a winner only with enough data, as a working line about 100 clicks on each ad and 10 or more conversions in the ad group. Under that, say "not enough data yet" and leave both running.

Asset labels. `ad_group_ad_asset_view.performance_label` for each headline and description: best, good, low, learning or pending. The label compares the asset with the other assets in the same ad. Replace a low asset once it has had real impressions. Keep the best ones. Labels are Google's view. Use them as a prompt, not a verdict.

Pinning. Read which assets are pinned. Pin only what has to show in one place: a legal line, or the brand in position 1 on brand. An ad with most headlines pinned can only show a few combinations, and that usually costs click-through rate.

What the ad says. At least one headline carries the ad group's keyword theme in the searcher's words. One carries the call to action from the page. Proof, a price or an offer only when the page shows it. The ad promises what the landing page delivers.

Ad strength is a hint. Do not pad an ad to raise it.

## Writing a responsive search ad

Read the page first. One ad group, one theme, one landing page. If you have not read the page, say you are writing from the URL and the ICP.

Limits. Headlines 30 characters. Descriptions 90. Two display paths of 15 each. Count every line and show the count.

Up to 15 headlines and 4 descriptions are allowed, not required. Write the good ones, usually 8 to 12 headlines and 3 or 4 descriptions. Do not pad to 15.

A mix that works for most themes:

- two or three headlines with the keyword theme, in the words people type
- two or three with the outcome the buyer wants
- one or two with proof the site supports: a number of customers, years, a rating
- one or two with the offer or the price, only if the page shows it
- one or two with the call to action, the same words as the button on the page
- one with the brand

Each description is a full thought that can stand alone. One carries the call to action.

The second ad is a different angle on the same theme, for example outcome-led against price-led. Not the same headlines in a different order.

Google's editorial rules, so the ad is not disapproved: no exclamation mark in a headline, no repeated punctuation or symbols, no words in capitals for emphasis, no unverified superlatives such as "best" or "number 1" unless the page shows the proof, no phone number in the text, and no competitor's name. Keyword insertion only when every keyword in the ad group reads well in that headline, with a sensible default text.

Do not invent a price, a discount, a review score, a customer count or a guarantee. Ask for it, or leave it out.

## Sitelinks, callouts and snippets

Sitelink text 25 characters, each of the two description lines 35, and its own final URL, different from the ad's. Callouts 25 characters each. Structured snippet values 25 characters each, under a header from Google's list. Search build says how many and at which level. Write them for the theme, from pages that exist.

## Creating and replacing

New ads and assets are created paused, beside the existing ones. Do not edit an ad that has history. An edit replaces the ad and its numbers start again. The limit is three enabled responsive search ads per ad group. When two are live, the new one goes in paused, and they decide which one to pause when it starts.

`create_rsa` and `update_rsa`, and the asset operations, after `operation="help"`. Preview every one. Nothing is created without a yes.

## Seasonal copy

When a promotion date is coming (Conversions and bidding keeps the calendar), write a dated ad or a promotion asset with its start and end dates, two weeks ahead. After the end date, check it stopped.

## What you return

Per ad group, the finding in one line, then the drafts: each headline and description with its character count, which asset it would replace, and why. A table for the drafts, not a wall of text. Then the rows to preview. Nothing created.
