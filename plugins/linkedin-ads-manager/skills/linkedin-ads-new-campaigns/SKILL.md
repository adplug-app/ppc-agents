---
name: linkedin-ads-new-campaigns
description: "Use before creating any campaign, ad set, ad or form. The checks before a build, the budget maths, names, the build order in batched draft previews, and the launch."
---

# New campaigns

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Before you create a campaign, an ad set, an ad or a lead form, in a new account or a live one. How to run the account decides what to build. This skill is how to build it. Audiences, Suppression and retargeting, Lead forms and conversions, Creatives and Bidding and budget hold the detail. Use them. Do not write a second version here.

## Before you build

Six things, confirmed:

1. The goal and the ICP, with the offer in the words on the form or the button.
2. The result recording. For a form: the form written and approved, with a privacy policy URL. For a website conversion: a rule that is enabled and recorded something in the last week. A build on a conversion that does not record learns nothing.
3. The monthly budget for this build, in the account currency.
4. The countries, and the language of the ads.
5. The account's exclusion block, from Suppression and retargeting.
6. The creative: images, video or documents, or a brief they agree you can write from.

If any is missing, that is the first job, not the build.

## Does the budget fit

Do the maths in front of them, before you name the structure. Use the account's own numbers. On a new account, use these 2025 B2B figures from Metadata's study of 138 advertisers, and call them assumptions: about $63 per thousand impressions, about $9 per click, a 0.67% click rate, and a cost per lead of about $376 for the typical advertiser, under $200 for the top quarter. In another currency, say the figures are dollars.

- Daily budget: the monthly number divided by 30.4. LinkedIn's minimum is $10 a day per ad set.
- Impressions a month: the monthly budget divided by the cost per thousand, times 1,000.
- Leads a month: the monthly budget divided by the cost per lead.
- Reach pressure: impressions a month divided by the forecasted audience. Above about 4 on a cold lead gen audience, the same people will see the same ask every week. Fine for a named list. Wasteful on a cold one. An awareness ad set can run about 6 to 10 a month, because its job is attention. Both are working lines.

Then read it:

- If the budget buys fewer than about 10 leads a month, it is one campaign and one ad set. Splitting it gives two ad sets that each learn nothing.
- If the goal is qualified leads from the CRM and the budget buys a handful, say the first months are for learning what a lead costs, not for hitting a target.
- If the budget cannot cover every job, keep lead gen on the warmest audience and say which jobs wait.

A working line, not a platform law.

## Names

Use the account's naming pattern if it has one. Otherwise:

- Campaign: layer, offer, country. "Awareness | Founder posts | UK", "Consideration | CFO report | US", "Conversion | Demo | UK".
- Ad set: audience, format. "Finance leaders 200-1000 | Single image", "Retargeting | Pricing 30d | Single image".
- Ad: angle and month. "Proof | Payroll time saved | 2026-11".

Consistent names make every report, hidden field and CRM view readable.

## The build, in order

Everything is created as a draft. Preview in batches, in this order, and wait for a yes on each batch.

1. The campaign. Draft, the objective, the name. No shared budget unless they chose one in Bidding and budget.
2. The lead form, for a lead gen build. Draft, the approved questions, the privacy URL, the thank-you line, hidden fields for the campaign and ad set names.
3. The ad set. Draft, objective and format, location, the targeting with the exclusion block, counted with `audience_count` and over 300, Audience Expansion off, Audience Network off, the locale, the cost type, the bidding strategy and the optimisation goal, the daily budget, and a start date. `associated_entity` from an existing ad set on the account. If the account is empty and the create fails, say what the error asked for. Do not guess an organisation id.
4. The assets. Uploads, with the page as the owner.
5. The ads. Two or three drafts that say different things, within the limits in Creatives.
6. The conversion. For a website build, associate the rule with this ad set only.
7. The read-back. Read every new item with `linkedin_ads_get` and list it: status, budget, bid, goal, location, forecast, exclusions, both switches off, the form or the page. Fix what is wrong while it is still draft.

Then stop. Launching is a separate yes.

## Adding an ad set to a live campaign

Check the audience against the ad sets that exist. If it overlaps one heavily, the two will bid against each other for the same people: change the audience or add the ads to the existing ad set. Otherwise the new ad set is a draft with its own ads, the exclusion block, and a forecast over 300. Enabling it is its own yes. It starts with no history, so its first two weeks of cost per lead are noise.

## The launch

One preview names everything going live: the campaign, then the ad sets, then the ads, with the start date. The campaign has to be live before its ad sets can run. Their yes covers that list only.

After the launch:

- Day one: is it delivering? An ad set with no impressions after a day has a hold, a rejected ad or a bid too low. Read the serving status.
- Day three: are forms opening, or is the tag recording?
- Day seven and day fourteen: cost per lead against the target, as a first read only.

Maximum delivery ad sets learn for their first days, and results swing. Make no changes in the first one to two weeks unless something is on fire. Put the launch in the change log with a four-week check date.

## Accelerate

Campaign Manager offers Accelerate as the default campaign type in some accounts. LinkedIn's AI then picks the targeting, the creative, the bids and the placements from a URL, and the Audience Network can be included. This agent does not adopt it by default. You build Classic, from the ICP, with the switches off. If an account already runs Accelerate, judge it on the same goal as everything else, and say you cannot see or set its audience. Testing it against Classic is a test in Tests and changes, not a default.

## What you return

The budget maths, the names, and the build as numbered batches. After each batch, what was created, read back. At the end, the launch preview, waiting for a yes.
