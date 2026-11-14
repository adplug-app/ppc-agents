---
name: meta-ads-audiences-and-placements
description: "Use when judging who sees the ads, Advantage+ audience, overlap, and placement waste. Recommends limits. Does not apply them."
---

# Audiences and placements

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Monday placement pass, the Thursday structure pass, a question about targeting, or before you create an ad set. Start from the confirmed ICP. If there is no persona yet, run ICP for Meta and wait. The lists themselves, and how long people stay on them, are Remarketing and suppression.

## Advantage+ audience

On sales, leads and app campaigns, Meta turns Advantage+ audience on. Most settings then become suggestions. Ads can be shown to other people when Meta thinks that will get more of the event.

These stay limits, in Meta's own help: location, minimum age, language, and a custom audience you exclude.

These become suggestions: a maximum age, gender, detailed targeting, lookalikes, and a custom audience you include. An included customer list does not fence the ad set. Say that in plain language when you find one. Meta removed detailed targeting exclusions in 2025, so "everyone interested in X except Y" is not a setting any more.

AdPlug's create path sets Advantage+ audience off unless the targeting turns it on. That switch sits inside the targeting, not as its own operation. Help describes it. Do not invent a second parameter name. Off is the tighter setup and this agent's default. Recommend off when the persona is a defined group. Tell them what on would widen, and the cost of off in one line: on a broad offer with a working purchase event, a fenced audience can cost volume. Wait for a yes before you turn it on, and before you turn it off on a live ad set. Turning it off is a targeting change, and Meta counts any targeting change as a significant edit.

Read the live ad set before you claim the switch is on or off: `meta_ads_list` with `entity_type` `adsets` and `fields` including targeting, or `meta_ads_get` on one ad set. Campaigns also return an Advantage+ state. If you cannot see the switch, say so. Do not infer it from a broad reach number alone.

Whatever the setting, the persona reaches the right people mainly through the creative. If the audience is wide and the ads are generic, the ads are the fix, not the targeting. ICP for Meta has the angles.

Account-level controls in Ads Manager, such as a minimum age or excluded locations for the whole ad account, apply to every campaign and keep the Advantage+ state. This connector cannot set them. Recommend them when a business can never sell to a group, such as under-18s for alcohol.

## Who should not see it

When a list of existing customers or recent purchasers exists, prospecting excludes it. Remarketing is a separate ad set with its list included as a limit. Remarketing and suppression has the lists to build, the durations, and where each one goes.

A special ad category on the campaign, such as housing, employment, credit or financial products, restricts targeting. Read it from the campaign. Do not recommend interests or limits the category will reject.

## Size

Before you create an ad set with limits, estimate its reach with `meta_ads_targeting_search`, an account id and the targeting. A pool that is far too small to buy about 50 of the events a week will sit in learning limited. Say so, and widen it or merge it before you build. Use the ids the search returns. Interests get retired, so search again rather than reusing old ids.

## Overlap

Two enabled ad sets that include the same people, with no exclusion between them, compete with each other in the same auctions. Name both ad sets and the audience they share. The usual fix is an exclusion on one of them, merging them, or pausing the weaker one. Recommend it. Do not apply it.

Do not call a large reach figure overlap. Overlap is the same people eligible for two live ad sets. Two broad prospecting ad sets in the same country are overlap by definition. That is a reason to merge them.

## Placements

Pull `report_type` `placement` for the last 7 days and the 7 days before, for campaigns that spent.

Read a breakdown with care. Meta optimises at the ad set, or at the campaign under a campaign budget, not per placement, age band or gender. A row with a higher average cost per result may still be where the next result is cheapest. So a higher average is not waste on its own.

Working line, not Meta's rule: call a placement waste only when it spent at least about two to three times the target cost per result with none of the goal event, or when their own CRM shows its leads do not qualify. Otherwise suggest a test, from Tests and changes, not an exclusion.

Call out Audience Network, rewarded video and the right-hand column when they spent. They are the usual waste on a considered offer. Feed, Reels and Stories are not waste just because the cost is higher, if they produce the event near the target. Judge them against the goal, not against the cheapest click. A placement that is cheap but brings no results is often a creative that does not fit its shape. Check that before you call it waste.

What you can still do about a placement, as of late 2026:

- Meta recommends Advantage+ placements, and keeps narrowing manual control on sales and leads.
- Since October 2025, on sales and leads, Ads Manager offers to spend up to 5% of the budget on each placement you excluded, and offers it switched on. An excluded placement may still spend. Check the ad set rather than assume zero.
- From August 2026, advertisers report that ad set placement exclusions are disappearing from Ads Manager, replaced by placement value rules that can lower a placement's bid by at most 90%. Meta has not announced a date. It may not have reached this account yet.
- Account-level placement controls in Ads Manager remain. This connector cannot set them, or value rules.

So: recommend the exclusion when the breakdown supports it, and preview it. Meta has no exclude field. AdPlug turns an exclusion into the placements that remain. Pass either the placements to keep or the ones to drop, not both. Excluding any placement turns off the campaign's Advantage+ state. Say that in the preview.

If the preview is rejected, say Meta would not take that placement limit on this objective or this account. Do not retry it with a new name. Then name what is left: the account-level control, or a value rule, both in Ads Manager, or a creative made for that placement's shape.

Do not leave a wasted placement on because Meta claims a lower cost per result for Advantage+ placements. That figure is Meta's, and it is not a reason to keep paying for a placement with no results in this account.

Age and gender breakdowns are for Friday, and only when they set that control. The same breakdown effect applies: a costly age band or gender is a test, not an exclusion, unless it meets the waste line above. If Advantage+ audience is on, a bad age row is not a clean exclusion, because the age maximum was only a suggestion. Say so instead of recommending a bid change.

## What you return

Who the live ad sets can reach, against the persona. Any Advantage+ audience that is on, and any campaign that lost its Advantage+ state by accident. Any missing customer exclusion. Overlap. The placements that meet the waste line, and what can still be done about each. Costly rows that do not meet it, as tests. Numbered rows to preview. Nothing applied.
