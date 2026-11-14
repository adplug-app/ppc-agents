---
name: meta-ads-creatives-and-fatigue
description: "Use for fatigue, creative variety, disapproved ads, testing new ads, and writing the next ad within Meta's limits. Recommends pauses and new ads. Does not publish them."
---

# Creatives and fatigue

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Monday routine, the Friday routine, a complaint that results got more expensive, or a request for new ads. If the ICP is not confirmed and you are about to write an ad, run ICP for Meta first. The ad can only say what the page or the form says.

## How you tell fatigue

Meta's frequency is impressions divided by reach, over the dates you ask for. One day's frequency is close to 1 on almost every ad, so it tells you nothing. Use a rolling seven days: the last 7 days against the 7 days before. Meta does not publish a number at which you pause. A frequency of 2 can be fine on broad prospecting and already high on a small remarketing pool. Remarketing runs higher than prospecting. Do not pause on frequency alone.

Fatigue is three moves on the same ad, last 7 days against the 7 days before: frequency up, link click-through down, cost per result up. Cost per result is the goal event, from `cost_per_result` or the named event in `conversions`, not link clicks, unless they told you clicks are the goal.

Link click-through is the `link_click` action divided by impressions. The tool's `ctr` is Meta's all-clicks rate. It counts likes, profile taps and opening the text too, so do not use it for fatigue.

Pull `meta_ads_performance` with `report_type` `ad` for both windows. Leave out ads with negligible spend. Sort by spend. At most ten rows, plus the count and spend of the rest.

Working lines, not Meta's rules. Judge an ad only once it has spent at least about twice the target cost per result in the window. Call it fatigue when link click-through is down 20% or more week on week, frequency is up, and cost per result is up 20% or more, or is 1.5 times or more its own 30-day level. A rising CPM on its own is not fatigue. It moves with the auction and the season.

For video, the hook rate is three-second views divided by impressions, from the video view row. A falling hook rate with steady frequency is a weak opening, not fatigue.

Then read Meta's own flags: `meta_ads_list` with `entity_type` `recommendations`. There is no type field, so match on the title: titles that mention creative fatigue or creative limited. `object_ids` names the ads or ad sets. Put the flag beside the three numbers. Meta's definitions: creative limited means the cost per result is above the ad's past level but under double. Creative fatigue means double or more. Meta shows the flag only on some ad sets, not on dynamic creative or catalogue ads, and only when the ad is eligible. A missing flag proves nothing. If only one of the three numbers moved and there is no flag, say what moved and do not call it fatigue.

Meta counts exposures per image or video, across every campaign on the Page. Copying a tired video into a new ad set does not reset it. The new ad needs a different image or video.

The first fix is a new creative, materially different, not a new headline on the same picture. Pausing the tired ad is a separate choice, made on money. Meta suggests keeping the original running while the new one ramps up. Recommend a pause only when the tired ad costs more than the target per result, and only after they say yes to that ad. Widening the audience is Meta's usual suggestion, and it is not the first fix here. A frequency cap is a change, it is only offered on some objectives, it can starve delivery, and you do not set one unless they ask.

## Variety

Meta says that when creative is too similar, its system may not recognise the ads as different. Meta also enters only one of your ads in each auction, so near-copies compete with each other rather than adding reach.

Count the distinct ideas in each live ad set. Working line, not Meta's rule: two ads are different ideas only if they differ on at least two of four things: the format, the person on screen, the setting, and the angle. Flag an ad set where one idea has more than about half the ads or half the spend. If every ad in an ad set is the same format and the same angle, that is a finding, even when nothing is tired yet.

A healthy ad set has a few ideas that differ from each other, across at least two formats, such as a short vertical video and a 4:5 picture. On a small budget, fewer ideas get more spend each. One new idea at a time, paused, is fine there.

## What the next ad is allowed to say

Take the offer, the proof and the button from the page or the form. Start from the persona's angle in ICP for Meta: the moment, the hook, the proof and the format. Write the ad as the interruption version of that page: who it is for, the problem the page already names, one proof the page already gives, and the same action as the button.

Do not invent a price, a discount, a guarantee or a result the page does not state. Do not write copy that asserts or implies a personal attribute of the viewer, such as their health, age or money troubles. Meta's standards reject it. Do not borrow a competitor's line from the Ad Library and paste it on. Competitor ads has the method for reading them.

## Text limits

Meta's recommended lengths, past which text is cut off:

- Primary text: 125 characters. Reels shows only about 40 to 44, so the first line has to work on its own.
- Headline: 40 characters. Facebook Feed shows about 27.
- Description: 25 characters, and often not shown at all.

One ad can carry up to five primary texts, five headlines and five descriptions, and Meta mixes them. Send them as lists when you create the creative. That is one ad with options, not five ads. Make the five say different things, not the same thing five ways.

## Shapes and safe zones

Feed takes 4:5, at 1440 by 1800. Stories and Reels take 9:16, at 1440 by 2560. On a 9:16 ad, keep text, logos and the product out of the top 14%, the bottom 35% and 6% on each side, because Meta's buttons and caption cover them. Burned-in captions belong in the middle of the frame, not the lower third.

When they have both shapes, put them on one ad with placement customisation: the vertical file for Stories and Reels, the 4:5 file everywhere else, with the same copy and link. If the account only has one shape, say which placements that creative cannot carry. Do not pretend a landscape image is a Reels ad.

Before they turn a new ad on, render it with `meta_ads_get` and `entity_type` `ad_preview` for the placements that matter, and give them the link. Meta expires it after 24 hours.

## Testing new ads

Meta's own creative testing, in Ads Manager, gives two to five new ads near-equal spend inside an existing campaign, with a share of the budget they choose, for up to 30 days. Meta suggests no more than 20% of the budget. It needs a daily budget and does not work with a bid cap. This connector cannot set it up. When they want a clean read on new ads, recommend it and tell them where it is: the ad, then Creative testing, then Set up test.

From here, the test is this: build the new ads paused in the main ad set, one idea each, and turn them on together after a yes. Do not judge an ad before it has spent about two to three times the target cost per result, or produced a handful of results. Judge on cost per result and the return against break-even, not on link click-through alone. A test between audiences or structures is Tests and changes.

## Winners, copies and posts

To change only the copy, the link, the button or the image of a good ad, use `copy_creative`, which keeps everything else, and swap the new creative onto the ad. A live ad whose creative changes goes back through review and takes a significant edit. Say so in the preview.

To run a winning ad in another ad set, `copy_ad` with that ad set, paused. To start a new ad set from a working one, `copy_adset`, paused. A copy keeps the original's enhancement settings once Meta processes it. Read it back and, if anything is on that they did not choose, preview turning it off. Meta does not dry-run copies, so the preview is AdPlug's check only. Say that.

An organic post that already earned comments and shares can run as the ad and keep them. List the Page's posts with `meta_ads_list`, `entity_type` `posts` and the Page as the parent. Only posts marked eligible for promotion can run. A post used as the ad keeps the post's own link, which you cannot rewrite from the ad.

## Enhancements

Every new or copied creative goes out with Advantage+ creative enhancements off, multi-advertiser ads off, and the website destination switch off, unless they name the ones they want. Meta's API default leaves multi-advertiser ads on, which can show the ad next to other brands' ads. Read a live creative's enhancements with `meta_ads_get` before you claim they are on or off. Turning them off on a live ad is a new creative on that ad, so it goes back through review.

## Disapproved ads

Use `meta_ads_diagnose` for delivery, and `meta_ads_list` with `entity_type` `ads` and `status` `DISAPPROVED` as well. The diagnose sweep checks about 75 ads by default, so on a larger account the list is the one that finds them all. Lead with the reason Meta returns. Pending review is not a finding. A paused ad is not a disapproval.

The fix is the creative or the landing page, then a corrected ad, created paused. You cannot press Meta's review button from here. Do not tell them the ad was resubmitted. A disapproval is not a reason to raise the bid or the budget.

## What you can create, and what you cannot edit

Creatives are immutable. To change a picture or the copy, create a new creative and swap it onto the ad. To change only the destination, the update-ad link does that by copying the creative.

An ad needs a Page, and an Instagram account id if it is meant to run on Instagram. If the account shows no Instagram identity, say the ads will be Facebook-only until they connect one. Do not promise Instagram delivery.

Images and videos are uploaded from a public link. AdPlug takes images and videos from a public link, so ask for a link to the file. If the file is only on their computer, ask them to put it somewhere public first. A video returns an id before Meta has finished processing it. Check it with `meta_ads_get` and `entity_type` `video` until its status is ready, then build the creative.

If you use `meta_ad_library_search`, say it is public creative, not their account. Outside the EU and the UK, commercial ads do not come back. An empty result is often that limit, or missing identity verification, which only they can complete. Do not fill the gap with made-up competitor ads. Competitor ads has the method.

## What you return

The tired ads, with the three numbers and Meta's flag where it shows one. Ad sets with no variety. The disapproved ads, with the reason. The next ad, in words, with its persona, its hook, its shape and its text options, tied to the button, marked paused and not created. Ask which rows to preview. A yes to "make new ads" is not a yes to turn them on.
