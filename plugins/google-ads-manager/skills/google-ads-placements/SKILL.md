---
name: google-ads-placements
description: "Use when checking or excluding placements. Demand Gen first if those campaigns exist, otherwise Performance Max. Skip Search-only accounts."
---

# Placements

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Friday routine, or any ask about placements, apps, YouTube channels, or sites the ads should not be on.

## See which campaigns are running

Query enabled campaigns and `campaign.advertising_channel_type`. Then follow this order.

If any campaign is `DEMAND_GEN`, review those placements. Demand Gen is where YouTube, Discover, Gmail and Display sit for most accounts now.

If there is no Demand Gen, and a campaign is `PERFORMANCE_MAX`, review Performance Max placements.

If neither type is enabled, say so in one line and stop. Do not build a placement report for Search.

## Demand Gen

Confirm the fields with `google_ads_reporting_view_doc` on `group_placement_view`, then query the last 30 days, filtered to `DEMAND_GEN`, ordered by cost. You want display name, placement type, target URL, impressions, clicks, cost, conversions.

Use `detail_placement_view` only when a channel or a domain needs the specific video or page underneath it.

Read it the way you read search terms. Cost with no conversions is a candidate. A placement that converts inside the target stays, even if the name looks odd.

Flag, and propose an exclusion for, mobile apps on a B2B or lead gen account, kids' content, parked domains, and sites or channels that are obviously not the buyer's context. Confirm the app exclusion once per account and remember it. Do not auto-exclude the whole of YouTube on a Demand Gen campaign that was built to run there.

Also note, without changing them: whether prospecting and remarketing are split, whether customers are excluded, and whether the assets cover square, landscape and vertical. Missing ratios mean missing placements. That observation goes in the same reply. The fix is creative, and you do not upload creative unless they ask.

## Performance Max

Confirm the fields with the view doc for `performance_max_placement_view`. This view is an impression report. Do not pretend it has cost if the query will not return cost. Say "impressions" in the table header.

Sort by impressions. Same judgement: apps, kids, parked and irrelevant sites, and YouTube videos that have nothing to do with the offer. Brand queries are not a placement. Those belong to the search term skill.

If a separate brand campaign exists, check whether PMax brand exclusions are on before you talk about placements. A brand leak is usually the more expensive finding. Use `add_pmax_brand_exclusion` only after `operation="help"` and a preview.

## How an exclusion is applied

Websites and domains: `add_placement_exclusion`. That operation does not accept YouTube URLs.

YouTube channels: `add_youtube_channel_exclusion`. Specific videos: `add_youtube_video_exclusion`. Apps: `add_mobile_app_exclusion`. Kids and other inventory labels: `add_content_label_exclusion`, campaign or account scope.

Call `operation="help"` and use the parameter names it returns. Preview with `google_ads_preview_mutation`. Show the placement, the type, and the scope. Execute only after a yes.

A routine never executes. It ends with the table and the row numbers to reply with.

## What you return

Which campaign type you checked and why the other was skipped. The table. The exclusions you would preview. Anything you could not see, including a placement view that rejected the query after two attempts.

Who the campaign is aimed at is Audiences and remarketing. This skill does not decide prospecting versus remarketing.
