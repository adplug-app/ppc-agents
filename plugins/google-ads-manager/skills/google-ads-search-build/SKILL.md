---
name: google-ads-search-build
description: "Use when building or reviewing Search campaigns. Search Partners off, Display Network off, AI Max off by default, then the brand campaign, themes, negatives, ads, sitelinks, landing pages and Quality Score."
---

# Search build

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A new Search campaign, a structure review, or any look at Search settings. Monday, Wednesday and Thursday all start with the three locks below. If one of them is open, that is the first line of the reply, before search terms.

Use ICP for Google Ads before you name themes, keywords, or negatives. If the persona is not confirmed, write it first.

This skill is for Search. Performance Max, Shopping and Demand Gen do not inherit the RSA and sitelink rules. Point those at their own skills.

## The three locks

These are on every enabled Search campaign, and on every Search campaign you create. AdPlug's create already defaults the first two to off for Search. Set them anyway, and read them back.

1. Search Partners off. `campaign.network_settings.target_search_network` is false. Google includes partners by default in the UI, and partner clicks are a weaker signal. Partners stay off unless the person gives a reason for that campaign. When you review Search and any campaign has partners on, name the campaign before you talk about keywords.

2. Display Network off. `target_content_network` is false on Search. A Search campaign does not buy display inventory. Remarketing display belongs in Demand Gen, not as an expansion on Search.

3. AI Max off on the main campaigns. `campaign.ai_max_setting.enable_ai_max` stays false on brand and on generic. AI Max widens matching, can rewrite ads, and can change the landing page. If they want to test it, that is a separate campaign, created paused, with its own budget and its own search-term review. Do not turn it on inside the campaign that already has the exact and phrase keywords. On a narrow lead-gen account, do not recommend that test unless they explicitly ask for it. How to run the account is when Performance Max and AI Max are the wrong recommendation. Naming a lock that is already on is still the first line. Switching it off waits for a yes. You do not edit the live campaign to enforce the recommendation.

To change a lock on a live campaign, preview `update_campaign_network_settings` or the AI Max field through `operation="help"`. Wait for a yes.

Bid adjustments are not a fourth lock. Before you recommend a device, location, audience, or ad schedule percentage, name the strategy and follow Conversions and bidding. Do not recommend a +20% mobile adjustment on a strategy that ignores it. Excluding a device is a different recommendation, and only when that exclusion stops traffic.

## Cross-negatives

Brand and generic are separate campaigns.

Brand terms, and the obvious misspellings, are phrase or exact negatives on every generic Search campaign. Also on Performance Max when a brand Search campaign exists. Use the Search terms skill to propose them.

Themes that belong to another generic campaign are negatives on this one, so two ad groups do not buy the same query.

The brand campaign keeps brand and brand plus the product. Do not negative the product out of brand. Only propose a generic negative on the brand campaign when the search terms show the brand campaign spending on queries that already have their own generic campaign. Show those terms first.

## The brand campaign

The brand campaign is for people choosing the business, not for people who already use it.

Keywords: the brand name, its common misspellings, and brand plus a product or a buying word (pricing, demo, reviews). Exact and phrase.

Existing customers looking for the door. Login, log in, sign in, my account, password, app download, support, help, customer service, contact number, cancel, refund and invoice, each with the brand. These people are already customers. On most subscription, SaaS and ecommerce accounts the click is paid twice: once to win them, once to show them the login page they would have found on the first organic result. Propose them as phrase negatives on the brand campaign, from the words the ICP wrote down and the brand search terms that have spent. Ask once whether they want to pay for those clicks. Some do, for example when a competitor bids on their brand plus login. Remember the answer. Careers, jobs and salary with the brand go on the same list.

Existing customers as an audience. When the goal is new customers, exclude the customer and logged-in user lists from the brand campaign and from every generic Search campaign. A Customer Match list can be used as an exclusion by every account that meets Google's basic policy. A website list of logged-in users, built from the app or account URLs, works on any account with the Google tag. Audiences and remarketing builds both. An exclusion stops the ad. An observation list does not.

Bidding. Brand can use target impression share when they want to own the brand queries, with a maximum CPC limit set so a competitor cannot push the price up without anyone noticing. That is a brand decision. Do not copy it onto the generic campaign.

Brand defence, in the monthly check and the full audit. Search impression share, top and absolute top impression share, and the brand cost per click over the last three months. A brand CPC that jumps while the brand budget did not change usually means someone else started bidding on the name. Auction insights are not in this connector. Say so, and ask for a paste of that report when it matters.

Sitelinks on brand go to the pages a buyer wants (pricing, demo, product, case studies). Not to the login page.

## The shared negative list

One shared list for top-of-funnel and irrelevant queries, applied to the conversion campaigns. Build it from the ICP, not from a canned software list. Research queries (what is, how to, template, course) go on this list when the conversion campaigns are meant to sell. Jobs, careers, salary, free, and login go on it when the persona says those people are not customers.

If they run a separate research campaign on purpose, do not attach this list to that campaign.

Check the list exists and is linked. A list that is not applied does nothing. Adding to the list, and linking it, are separate previews.

## Ad groups

One theme per ad group, taken from the ICP and from a page that exists.

Fewer than 20 positive keywords in the ad group. Twenty is the ceiling that forces a look, not an order to slice synonyms. If a second offer or intent is in the group, split it, even under 20. If the keywords are one theme, say so and leave them. Do not build single-keyword ad groups.

Google's own guide tells people to merge ad groups that have fewer than about 30 conversions in 30 days. Do not merge two themes to chase that number. Mixed intent costs more than a thin ad group. If a split would leave both sides with almost no data, say that, and still keep the themes apart.

One match type per keyword text in the ad group. Do not stack the same word as exact, phrase and broad. Broad waits until Conversions and bidding says the campaign has something to learn from.

One home per keyword. The same keyword text enabled in two ad groups or two campaigns splits its data, and lets Google pick whichever ad it prefers. List each duplicate with the ad group, the match type, the spend and the conversions on each copy. Recommend keeping the copy whose ad group and page fit the theme, and pausing the other. Cross-negatives handle themes. This handles the exact same text.

Keywords that are not pulling their weight, in the monthly check and the full audit: enabled keywords with real spend and no conversions over 90 days, keywords with no impressions in 90 days, keywords Google marks as low search volume, and, on Manual CPC, keywords below the first page bid. Judge the keyword the account chose to buy here. Search terms judges the query.

## Ads and assets

At least two enabled responsive search ads in the ad group. Same theme, different angle. A third ad is optional. Do not require one. Ad strength is a hint. Do not pad headlines to chase Excellent, and do not require 15 headlines. Google's account limit is 3 enabled responsive search ads per ad group, so do not add a fourth. That cap is context. Two is this agent's minimum.

Sitelinks. At least 6 in the branch that can serve with this ad group. Account, campaign, and ad group sitelinks in that branch can show together. Google will not show sitelinks until there are 2, and its own tip for a high-volume ad group is 6 with descriptions. Two is not enough here, and 4 is not the bar. Each sitelink has link text, two description lines, and its own final URL, different from the ad's final URL.

Campaign-level sitelinks are for what is true everywhere in that campaign: the main call to action, pricing, contact, a page every ad group can use. The ad group still needs sitelinks written for that theme. Do not count a generic campaign sitelink as the ad group's whole set. If the ad group has none of its own, say so even when the campaign has six. Account level is only for a link that is true for every campaign. If a higher-level sitelink would send this theme to the wrong page, say so.

Other Search assets. Recommend one when it is missing and the page supports it. Say which level to create it at. Campaign-level assets are for what is true everywhere in that campaign. Ad-group assets are for the theme. Account-level assets are only the brand mark and anything true for every campaign. Do not create or link an asset without a yes. Call `operation="help"` before that mutation.

- Callouts. Several short ones, relevant to the theme, 25 characters or fewer. Google needs 2 before any can show, and its guide asks for at least 4. That is context, not a hard gate. Skip a claim the page does not support. Campaign level when the claim is true for the whole campaign. Ad group level when it is only this theme.
- Structured snippets. One set whose header matches the offer, such as types, services, or models, and only a header on Google's list. Google's form asks for at least 3 values, and its guide aims at 4. Skip a header that does not fit. Values are examples of the header, not a slogan. An ad group snippet stops campaign and account snippets from showing on that ad group, so use ad group level only when the theme needs a different header. Otherwise campaign level, or account level when it is true for every campaign.
- Call assets. When the conversion is a phone call. Not on a SaaS demo page that has no phone conversion. One number, at campaign level, unless ad groups use different numbers.
- Image assets. When the account has real images of the product or the work. Not stock filler. Google's guides ask for at least 3 unique images, and one asks for 4, in square and landscape. Campaign level when every ad group can use them. Ad group level when only the theme can.
- Logo and business name. Account level is enough when it is the real brand. Google may add them from the site. Do not invent a logo. They have to match the business the account verified.
- Promotion and price assets. Only when the page shows a real price or a real offer. Do not invent a discount or a price. Campaign level when the offer is the whole campaign. Ad group level when it is one theme. Do not invent how many prices the form requires. If you are not sure the asset will save, say so.
- Lead form assets. Only when the goal is a lead and the form is the conversion. Not as well as a landing page unless they asked for both. One form, at campaign level if every ad group uses it. Google limits these by country and by vertical. If you cannot see that, say so.
- Location assets. For a business people visit. Not for a remote SaaS company. The location comes from their Business Profile. Do not invent a pin. Account or campaign level.

The landing page is the page for the theme and for the query. Homepage is for brand. Pricing keywords go to pricing. If a page for the theme exists, do not use the homepage. If you only have the URL and have not read the page, say you are judging from the URL.

Ads and copy is how to judge and write the ads and the assets.

## Quality Score

Quality Score is a diagnostic, not a target, the same way optimisation score is Google's number. Read it in the full audit and the monthly check, not every week. Always show it in those two.

Read `ad_group_criterion.quality_info` for enabled keywords with real spend in the last 30 days: the score, and its three parts, expected click-through rate (`search_predicted_ctr`), ad relevance (`creative_quality_score`) and landing page experience (`post_click_quality_score`). Each part is below average, average or above average.

Show it in three lines:

1. The spend-weighted average score across Search, and the share of spend on keywords scoring 1 to 4.
2. The keywords at 1 to 4 with the most spend, grouped by the part that is below average.
3. What that part points to.

Route the fix by the weak part, because the score alone does not say what to do:

- Expected click-through rate below average. The ads. Ads and copy.
- Ad relevance below average. The ad group mixes themes, or the ads do not say the keyword's words. Split the theme or rewrite the ads.
- Landing page experience below average. The page: relevance to the query, speed on mobile, and whether it answers what the ad promised. Not the bid.

Brand keywords usually score high and new keywords show no score until they have traffic. Do not chase a 10. A keyword at 5 that converts inside the target is fine.

## When you create a Search campaign

New campaigns has the build, step by step. Create it paused. Then read back, before anyone talks about enabling it: partners off, Display Network off, AI Max off, Presence, budget, bidding strategy from Conversions and bidding, brand negatives on if it is generic, the shared list linked, ad groups under the keyword ceiling, two RSAs, at least 6 sitelinks in the branch including sitelinks that belong to the ad group, final URL per theme. Fix what is wrong while it is still paused. Do not enable it in the same step.

## What you return

The locks, campaign by campaign, bad ones first. Then missing cross-negatives, brand support terms the brand campaign is still paying for, the shared list, duplicate keywords, ad groups over the ceiling or mixing themes, ad groups with fewer than two RSAs, ad groups with fewer than 6 sitelinks in the branch or with no sitelink of their own, other missing assets and the level you would create them at, and final URLs that do not match the theme. Rows to preview. Nothing applied.
