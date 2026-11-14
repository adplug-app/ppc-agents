---
name: meta-ads-remarketing-and-suppression
description: "Use when checking or creating customer exclusions, remarketing audiences and lookalikes, with how long people stay on each list and where each list goes. Recommends the lists, then creates them after a yes."
---

# Remarketing and suppression

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Thursday routine, a new build that needs lists, someone asking about retargeting, remarketing or excluding customers, or the audit reaching the lists section. Use the confirmed ICP so the lists match real pages and real events. A "checkout abandoners" list needs a checkout event.

## Two kinds of list

Suppression lists are people you do not want to pay to find again: customers, recent buyers, people who already became a lead, job seekers. They are exclusions on prospecting. An excluded custom audience stays a hard limit even when Advantage+ audience is on, and it keeps a campaign's Advantage+ state.

Remarketing lists are people who showed interest and did not finish: visitors, product viewers, cart and checkout abandoners, people who engaged on Instagram or Facebook, video viewers, people who opened a lead form. They are the audience of a separate remarketing ad set, with Advantage+ audience off so Meta does not wander off the list.

Most accounts have a pixel and no suppression lists. Recommend both.

## Lists to create, and how long people stay

Retention is how many days someone stays on the list after the action. Website lists run 1 to 180 days. Engagement lists run 1 to 365. A customer list keeps people until it is refreshed. A short window is a smaller, warmer list. Build the short and the long one for the lists that matter, so the results can show which one pays. Put the window in the name, such as "Checkout abandoners 14d".

Suppression:

| List | How it is built | Window |
|---|---|---|
| Customers | Customer list from their shop or CRM | Refresh monthly |
| Purchasers | Website, the Purchase event | 180 days. The repurchase cycle if it is shorter, often 30 to 90 days |
| Leads | Website, the Lead or registration event. Or the lead form list below | 30 to 90 days for a lead, 180 for a signup |
| Job seekers | Website, URL contains the careers path | 90 days |

Remarketing:

| List | How it is built | Window |
|---|---|---|
| Cart and checkout abandoners | Website, AddToCart or InitiateCheckout. Exclude purchasers on the ad set | 7 and 30 days |
| Product or pricing viewers | Website, ViewContent, or URL contains the pricing or product path | 14 and 30 days |
| All visitors | Website, PageView | 30 and 180 days |
| Instagram engagers | Engagement, the Instagram account | 90 and 365 days |
| Facebook Page engagers | Engagement, the Page | 90 and 365 days |
| Video viewers | Engagement, one video they ran as an ad | 30 and 90 days |
| Lead form openers | Engagement, the lead form | 90 days |

Skip a list the account cannot support. No checkout event, no abandoners. No video ads, no video viewers. A list built on an event the pixel does not send stays empty.

## Where each list goes

- Prospecting, Advantage+ or not. Exclude customers and purchasers, and leads when the goal is new leads. The exclusion is the fence.
- New and existing customers in one sales campaign. Meta's replacement for the old existing-customer budget cap is two ad sets: one for new people with customers excluded, one with the customer list included as a limit. Each ad set has its own creative.
- Remarketing. Its own ad set, or its own campaign when it needs a separate small budget. Include the abandoner, viewer and engager lists. Exclude purchasers. Creative for people who already know the brand: reviews, the reason to buy now, the answer to the usual doubt. Never the same ad as prospecting.
- Repeat purchase, when the business has one. The customer list as a limit, with a cross-sell or refill offer from the page.
- Lookalikes. The seed is customers or the highest-value purchasers, at least 100 people in one country, from 1% to 20%. Start at 1% in the main country. With Advantage+ audience on, a lookalike is only a suggestion. Recommend one when they ask, or when the ad set is manual and the persona is wide.

A remarketing pool too small to spend is not worth its own ad set. Broad prospecting already reaches recent visitors. If the 30-day visitor list is under a few thousand people, say so and fold remarketing into the prospecting ad set's creative instead.

## Creating a list

AdPlug creates:

- website lists with `create_website_audience`: the pixel, then an event name or a URL fragment, and the window
- engagement lists with `create_engagement_audience`: the Page, the Instagram account, a video or a lead form, and the window
- a customer list with `create_custom_audience`, then its people with `add_audience_users`
- a lookalike with `create_lookalike`: the seed list, the country and the size

Call `operation="help"` before the first use, and preview each one. Meta has no dry run for audiences, so the preview is AdPlug's check and the list is created on execute. A list is a change. It needs a yes. It does not spend until an ad set that uses it is turned on. Attaching a list to a live ad set is a targeting change and a significant edit. Batch the attachments into one edit per ad set.

The ad account must have accepted Meta's Custom Audience terms. That is a human step. If the preview or execute says the terms are missing, give them the link it returns and stop.

Customer data. For a real customer file, recommend the upload in Ads Manager, under Audiences. Through this agent, the rows pass through the chat before AdPlug hashes them on its server. Use `add_audience_users` only if they ask for it, the list is small, and they confirm they may use the data for advertising. Never ask them to paste customer data unprompted, and never hash it yourself in the chat.

## Are they usable

List the account's audiences with `meta_ads_list` and `entity_type` `custom_audiences`. Size comes back as a range. Under about 100 matched people, Meta will not deliver to it. Under a few thousand, a remarketing ad set will struggle to spend its budget.

A new website list fills from the pixel, and can take a day or two. If it is still empty after a few days, the event is not firing on those pages, or the terms are not accepted. Say which you could not check.

A customer list that has not been refreshed in months still excludes people who stopped being customers, and misses new ones. Recommend a refresh in Ads Manager.

## What you return

Suppression lists that are missing, and the prospecting ad sets still paying to reach those people. Remarketing lists that are missing, too small or empty. Whether a separate remarketing ad set is worth it, in one line. The lists you would create, with the rule and the window, as rows to preview. Where each one goes. Nothing created unless they pick a row. Ad sets that use them stay paused.
