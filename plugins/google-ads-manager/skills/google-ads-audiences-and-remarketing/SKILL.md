---
name: google-ads-audiences-and-remarketing
description: "Use when checking or creating suppression and remarketing lists, observation on Search, or a Demand Gen audience. Search observation is not a Performance Max signal."
---

# Audiences and remarketing

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Someone asks about audiences, remarketing, retargeting or suppression, a new build needs lists, or the monthly check reaches the audience section. Use the confirmed ICP so the lists match real pages. A "pricing viewers" list needs a pricing page.

## Two kinds of list

Suppression lists are people you do not want to pay for again: customers, logged-in users, people who already converted, job seekers. They are exclusions.

Remarketing lists are people who showed interest and did not finish: visitors, pricing and demo page viewers, cart and form abandoners. They are observation on Search, and targeting in a Demand Gen remarketing campaign.

Most accounts have a few remarketing lists and no suppression lists. Recommend both.

## Lists to create, and how long people stay

Membership duration is how many days someone stays on the list after their last visit. The maximum is 540. A short duration is a smaller, warmer list. Build the short one and the long one for the lists that matter, so the observation data can show which one converts. Name every list so the duration is in the name, such as "Pricing visitors 30d".

Suppression:

| List | How it is built | Duration |
|---|---|---|
| Customers | Customer Match, from the CRM | 540 days |
| Logged-in users | Visitors to the app or account URLs the ICP wrote down | 540 days |
| Converted | Visitors to the thank-you or confirmation page | 540 days for a purchase or a signup. 30 to 90 days for a demo or a lead, unless a lead who did not buy should never see the ad again |
| Recent buyers, ecommerce | Order confirmation page | The repurchase cycle, often 30 to 90 days |
| Job seekers | Careers page visitors | 90 days |

Remarketing:

| List | How it is built | Duration |
|---|---|---|
| All visitors | Every page | 30, 90 and 180 days |
| High intent | Pricing, demo or product pages | 30 and 90 days |
| Abandoners | Visited the cart, checkout or form page, and not the thank-you page | 7, 14 and 30 days |
| Engaged | Two or more key pages | 30 days |
| Researchers | Blog or guide readers who did not visit a commercial page | 90 days |

Skip a list the site cannot support. No cart, no cart abandoners. No app, no logged-in list.

## Where each list goes

- Generic Search, when the goal is new customers. Exclude customers, logged-in users and converted. Remarketing lists go on as observation.
- Brand Search. Exclude customers and logged-in users unless they want to pay for those clicks. Search build has the brand campaign rules.
- Demand Gen prospecting. Exclude customers, logged-in users, converted, job seekers and recent visitors, so prospecting is new people.
- Demand Gen remarketing. Target the high-intent and abandoner lists. Exclude converted and customers.
- Performance Max. The customer list as an audience signal, and as the list for new customer acquisition when they want that goal. Signals are hints. Say so.

## Creating a list

AdPlug can create website lists with `create_rule_based_user_list` (page URL rules, include and exclude, the match type, the membership duration, and a pre-fill from the last days of traffic), combined lists with `create_logical_user_list` (all of, any of, none of other lists, such as abandoners minus converted), and an empty Customer Match list with `create_user_list`. Call `operation="help"` before the first use, and preview each one. A list is a change. It needs a yes.

AdPlug cannot upload Customer Match members. Google moved those uploads to its Data Manager. They upload the CSV in Google Ads (Tools, Audience manager), or connect their CRM there. Say that when you create the list, and check its size the following week.

Pre-fill new website lists with the last 30 days where the tool allows it, so the list is not empty on the first day. A website list only fills when the Google tag fires on those pages. If a new list is still at zero after a few days, the tag or the consent banner is the first suspect.

Lists made in GA4 and linked to Google Ads are fine to use. Do not build a second copy in Google Ads.

## Customer Match

Customer Match only when a list is eligible. Google's policy: a compliant account can use a customer list for observation and for exclusions. Targeting, and manual bid adjustments, need 90 days of history and more than 50,000 US dollars of lifetime spend. A list needs at least 100 members added or refreshed in the last 540 days. If you cannot see eligibility, say you cannot, and do not promise a targeting campaign. The first use on a small account is usually an exclusion of existing customers, if the list is allowed at all.

## Are they usable

Query `user_list`. Membership status must be OPEN. Closed lists do not grow and should not be the thing you target.

Size: `size_for_search` and `size_for_display` are different numbers. Google's bar to serve is 100 active users in the last 30 days on Search, on the Display Network, and on YouTube. A brand-new list can take a couple of days to fill. Under 100 on the network you meant, the campaign cannot serve that list. Say so, and do not build a campaign on it.

You cannot see the tag fire in the browser. A list at zero may be a tag, a consent banner, or a new rule. Say which of those you could not check.

## Search

Observation, not targeting. In-market, affinity, and the remarketing lists that match the ICP go on Search as observation, so you can read who converts. Observation does not limit who sees the ad. A percentage on that list only changes the bid when Conversions and bidding says this campaign's strategy uses audience adjustments. Name the strategy first. Do not recommend a +20% on a strategy that ignores it. An exclusion still stops that audience when the exclusion is what blocks the traffic. You cannot get an exclusion by setting the percentage to -100%. The rule is in Conversions and bidding.

Do not set a Search campaign to Targeting by default. Targeting means only those people can see it, and it starves a keyword campaign. Keywords still have to exist. A data segment does not replace them.

Remarketing on Search is usually that observation layer, plus a bid signal. A separate Search remarketing campaign is worth it when the list is over the serving bar, the account has enough conversion volume to read it, and the offer or the ad is different from prospecting (a demo for people who already saw pricing, not the same homepage ad). It is not worth it on a small budget or a thin list. One more campaign with nothing to learn is a worse account.

If you do build it, create it paused, Search Partners off, Display Network off, AI Max off, and preview it.

## Demand Gen

Prospecting and remarketing are separate campaigns. Exclude customers, and open opportunities, from prospecting. Remarketing uses the lists above, with creative for people who already know the company.

Google's guides tell you to turn Optimized Targeting on for prospecting. Leave it off until the person asks. It spends outside the audience you chose. On a B2B account that is how a careful list becomes a wide one.

Missing creative ratios are the Placements skill and How to run the account. This skill only decides who is in the audience.

## Performance Max

Audience signals are hints. They are not targeting, and they are not the observation lists from Search. Do not say a Search observation segment is "applied" to Performance Max because you added it somewhere else. If you add a signal, say it is a signal, name it, and do not promise the campaign will stay inside it.

## Shopping

Shopping is the feed, the product status, and the negatives. It is not an audience build. A remarketing list does not fix a disapproved product. Dynamic remarketing needs the feed and the tag parameters, which you cannot see fire. Say that, and use the Shopping products skill for the catalogue.

## What you return

Suppression lists that are missing, and the campaigns still paying for those people. Remarketing lists that are missing, closed, or under 100 on the network that matters. Search campaigns set to Targeting. Observation segments you would add, tied to the ICP. Demand Gen prospecting that does not exclude customers. Whether a separate remarketing campaign is worth it, in one paragraph. The lists you would create, with the rule and the duration, as rows to preview. Nothing created unless they pick a row. New campaigns stay paused.
