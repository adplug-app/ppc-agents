---
name: meta-ads-how-to-run-the-account
description: "Use before recommending a campaign type or a structure. Covers Advantage+ sales, manual sales, leads, traffic, prospecting and remarketing, and small budgets."
---

# How to run the account

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The person asks what to launch, whether to use Advantage+ sales, how to structure the account, or you are about to create anything. If the ICP is not confirmed, run ICP for Meta first and wait. This skill decides what to build. New campaigns is how to build it.

## What you need first

What they sell, who the ad is for, the countries, the monthly budget, the goal, the button or the form, and the margin or the return they need to break even. If the goal is missing, ask before you name an objective. Remember the monthly number as the budget to pace. If they never give a budget, ask once and do not invent one.

Then look at what is already enabled. Recommend against the account you have, not against a blank diagram. The goal and the budget belong to this account. An agency does not reuse them on the next client.

You can create only the six current objectives: awareness, traffic, engagement, leads, sales, and app promotion. Older objectives remain readable on old campaigns. You cannot create them. There is no separate shopping objective. Catalogue ads are a sales campaign pointed at a product set, and only when Catalogue and shopping says they have a catalogue.

## Advantage+ sales

Advantage+ is a state a sales campaign reaches, not a type you pick. Three settings make it: the budget on the campaign, Advantage+ audience on, and no placement excluded. Meta reads the state back on the campaign, so read it with `meta_ads_list` before you call a campaign Advantage+ or manual. Moving the budget to the ad sets, fencing the audience, or excluding one placement turns it off. Since Meta's February 2026 changes, sales, leads and app campaigns start in that setup in Ads Manager. A campaign AdPlug creates starts with the audience fenced, so it will read as manual until they say yes to widening.

Recommend Advantage+ sales, and wait, when they sell online, the purchase event is real, the buyer is broad, and the volume can teach it: about 50 optimisation events a week after the last significant edit. An ad set that cannot get near that on purchases is not "fixed" by switching the event to add to cart or link clicks. Say the volume is thin, and offer one sales campaign on purchases anyway, or a hold.

When they want Advantage+ sales, still exclude existing customers from the prospecting ad set if a list exists. Inclusions are suggestions once Advantage+ audience is on. An exclusion is a limit, and it keeps the Advantage+ state. The cap on spend to existing customers is not available on new Advantage+ campaigns. Meta's own replacement is two ad sets in one campaign, one for new people and one for existing customers. Remarketing and suppression builds them.

## Manual sales

Use this when the offer is narrow, the country list is a hard limit, or prospecting and remarketing have to stay apart with their own budgets. Manual means the audience is a limit: AdPlug sends Advantage+ audience off unless they set it on. Recommend off, tell them what Meta will widen if it is on, and wait.

The cost of that default, said once: on a broad offer with a working purchase event, a fenced audience can cost volume and may cost more per purchase. Meta's own figures say so. Its figures are Meta's. If they are unsure, offer a test from Tests and changes rather than a switch.

Either way, the creative does most of the targeting. Each persona gets its own angle from ICP for Meta.

Placements follow Audiences and placements. On sales and leads Meta has been removing the placement switches. Do not promise an exclusion before the preview shows Meta will take it.

## Leads

Use the leads objective when the goal is a lead. Match the event to the button or the form.

A website lead fits when the landing page does the qualifying, and the pixel event is the thank-you page or the form submit on that site. An instant form fits when they are willing to take the lead inside Meta. Instant forms are usually cheaper. A raw lead is not a qualified lead. Say that before you recommend the form, and ask what happens to the lead after it arrives. If they cannot say, do not treat the form lead as the business result.

Do not run a website lead campaign and an instant-form campaign on the same small budget. Pick the one the page already uses. The form is immutable once created, so a thin form means a new form later, not an edit. Lead forms need the Page to have accepted Meta's lead ads terms. That is a human step. If the preview says the terms are missing, send them there and stop.

Optimising to the leads that turn into sales needs their CRM to send the stages back to Meta, and enough volume. Tracking, conversions and bidding has the requirements and the routes. You cannot see their CRM from this connector. Do not invent a qualified rate.

## Traffic, awareness, engagement, apps

Traffic is rarely the right objective. Link clicks and landing page views are not a purchase and not a lead. Recommend traffic only when they have said the goal is visits, and they will not judge the account as sales or leads. Even then, one campaign, and say what it will not tell them.

Awareness and engagement are for a goal they named as reach or attention. ThruPlays are not a sales goal. Do not add them to "feed the pixel".

App promotion only if they have an app. A website is not an app campaign.

## Prospecting and remarketing

Keep them in separate ad sets, or separate campaigns when the budgets should not share a pool. Existing customers are excluded from prospecting when a list exists. Remarketing uses its lists as a limit, with Advantage+ audience off, so Meta does not wander off the list. Remarketing and suppression has the lists and their durations.

If the remarketing pool is too small to spend, say so and leave remarketing off. A broad prospecting ad set already reaches recent visitors. A lookalike widens a seed. It is not the default for a narrow persona, and with Advantage+ audience on it is only a suggestion.

## Small budgets and narrow offers

The working line is about 3,000 US dollars a month, or the same in the account's currency. Under that, or on any budget that cannot buy about 50 of the real events a week, run one prospecting campaign and one event. The maths is in New campaigns: a daily budget of about seven times the cost per result buys about 50 a week. Say which campaign types you are leaving off, and what would have to be true before they start: a real event, enough monthly volume, and creative that differs from what is already running.

Five campaign types on a narrow offer is how the budget learns nothing. Do not propose them. Fewer ad sets with more ads in each learn faster than many thin ones.

## What you return

A short plan: what to run now, what to leave off, what has to be true before a second campaign, the money it has to make against the break-even return, and the settings you would lock. Creating or editing is a change. New campaigns builds it, paused. Wait for a yes.
