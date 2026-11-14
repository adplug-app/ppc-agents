---
name: linkedin-ads-audiences
description: "Use when building or checking who an ad set targets, the forecasted size, a company list, or whether Audience Expansion, the Audience Network or Auto-Targeting is in play."
---

# Audiences

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A new ad set, a weekly check of size and expansion, a company or contact list, or "who are we reaching". If the ICP is not confirmed, run ICP for LinkedIn first and wait.

## Count it before you launch

Call `linkedin_ads_targeting_lookup` with `action` `audience_count` on the criteria you are about to save, including location. The number is a forecast, an estimate of members who match, not a promise of delivery.

LinkedIn will not run an ad set under 300 members. Location is required, and it can pull a matched list under 300 even when the file looked large. Under 300, say so and stop. Do not turn Audience Expansion on to clear the floor. Expansion is not in the forecast. The forecast can look acceptable while delivery wanders off the people you named.

LinkedIn's own setup guidance suggests about 50,000 members or more when you want an ad set to spend freely, and over 15,000 for message ads. A named company list under 50,000 is often the right B2B buy. Do not add a neighbouring function, a wider seniority, or extra companies to chase 50,000. Say the forecast, say whether the monthly budget will hit the same members all month, and let them choose.

A small audience with a large budget and maximum delivery is how frequency climbs. Bidding and budget treats that as a bid problem, not a reason to widen.

## Build it from the persona

Location, then the tightest cut the ICP named.

Titles, employers, skills and industries are typeahead: `action` `search`, with the facet name and no URN prefix (`titles`, `employers`, `skills`, `industries`). Seniorities, job functions and company size are closed sets. Typeahead will not find them. List `targeting_facets`, then `resolve_urns` on the values you mean to save, before they go into a preview. Company size uses `urn:li:staffCountRange:(MIN,MAX)`.

Use `resolve_urns` on every value you will put in the criteria. An unresolved URN does not go into a preview.

Exclusions are part of the audience, not a later tidy-up. Every prospecting ad set carries the account's exclusion block from Suppression and retargeting: customers, open opportunities, employees, competitors, job seekers, and the rest the ICP named.

Auto-Targeting builds an audience from a URL and from this account's past ad sets. A new account has no past. There is no flag on the ad set that says Auto-Targeting was used. If a live ad set has location and little else, say that it is not the ICP, and ask whether the width was deliberate. Do not start a new ad set that way.

Profile language and locale are the language of the ad interface. English is `en_US` in the locale. An unsupported pair is rewritten, and that rewrite is not geo targeting. The country is the location facet. Say both in the preview so a UK campaign is not silently "US English, no country".

## The two switches that widen delivery

On every live ad set with spend, read `linkedin_ads_get` `entity_type` `campaign`. The list view does not include these flags.

Audience Expansion (`audienceExpansionEnabled`) adds members with similar attributes. Exclusions still hold. Inclusions loosen. Campaign Manager turns it on where the format allows it. It is off for this agent until they name a reason on that ad set. Pass `audience_expansion_enabled` false on create. If a draft you just created comes back on, correct it: that was part of the preview they approved. If it was already on, recommend it off and wait.

The LinkedIn Audience Network (`offsiteDeliveryEnabled`) serves single image, carousel, document and video ads on third-party sites and apps, on the same bid and budget. Campaign Manager turns it on for those formats. Pass `offsite_delivery_enabled` false. Same rule as expansion: correct your own draft, wait on anything that was already live.

A reason to turn either on is a test they asked for, with its own read of the result. It is not a way to rescue an audience under 300.

## Company lists and contact lists

Create the segment with the preview operation `create_saved_audience`. Company lists use `COMPANY_LIST_UPLOAD`. Contact lists use `USER_LIST_UPLOAD`. Streaming audience types are rejected. AdPlug is not in that programme. Say so if they ask for one.

Then `add_audience_members`, after a yes. One file per segment, up to 300,000 rows. LinkedIn can take up to 48 hours to match. To change the file, create a new segment. The old one keeps the first upload.

A company row matches better with the company name and the LinkedIn company page URL. Say that before they hand you a names-only file. Do not paste the file back into the chat.

The id you target is `destinationSegmentUrn` from `entity_type` `saved_audiences`, under the segments facet. The top-level list id is not the targeting URN. Status is `READY`, `BUILDING`, `PROCESSING`, `ARCHIVED` or `FAILED`. A building segment can be attached. It will not deliver until at least 300 members match, after location. Leave the ad set in draft until the status is ready and `audience_count` clears 300. A failed segment does not get attached.

Contact emails are a hash, not the address. Do not echo addresses back. Do not upload a list from a routine.

## Changing who an ad set targets

The targeting on an ad set is replaced whole on every update. Read the live targeting with `linkedin_ads_get` `entity_type` `campaign`, change the part you mean, count the new block with `audience_count`, and preview the whole block. Show what is added and what is removed, in plain words, beside the forecast before and after. Never send a partial block. Never use `apply_targeting_audience` on an ad set with its own targeting: it swaps in the saved audience and drops the rest.

## Reach on a named list

On a company list or a small title stack, read `report_type` `reach` with the ad set ids. Audience penetration is the share of the targeted members reached in the range. On an account-based ad set it is the question: how much of the list has seen the ads. Low penetration with the budget spent means the list is bigger than the money. High penetration with frequency climbing means the list is exhausted and the ads need to change, not the bid.

Remarketing pools, suppression lists, and predictive audiences are in Suppression and retargeting.

## What you return

The forecast, with location included. Whether it is under 300, between 300 and a size the budget can sustain, or wide enough to spend. Practitioners mostly land prospecting audiences between about 30,000 and 500,000. The exclusions. Expansion and the Audience Network, each on or off, by ad set name. Any list that is still matching or has failed. Penetration on a named list. Nothing applied. A new audience is part of a draft ad set, and the draft stays draft.
