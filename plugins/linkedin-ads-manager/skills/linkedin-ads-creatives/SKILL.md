---
name: linkedin-ads-creatives
description: "Use when writing, reviewing or retiring ads, including document ads, conversation ads and thought leader ads. Has the character limits, the image sizes, rotation and the fatigue test."
---

# Creatives

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A new ad, a rejected ad, a weekly fatigue check, or a monthly "what do we retire". The offer and the job come from ICP for LinkedIn. Thought leadership and lead gen do not share an ad. If you are about to invent an offer the persona does not have, stop and ask.

## What an ad has to do

The ad repeats the offer on the form or the page. A demo ad does not offer a guide. A thought leadership ad does not pretend to be a lead.

The first line speaks to the persona's problem in their words. One clear ask per ad. Proof, a number, a customer type or a result, belongs in the ad when they have it. Do not invent one.

One ad carrying the spend is a fatigue risk. The useful version of "several ads" is two or three that say different things: the offer, the proof, the reason to act now. Four rewrites of the same sentence do not count. A small budget does not need a gallery.

New ads stay draft. `create_creative` and `create_inline_ad` default `intended_status` to `DRAFT`. Do not pass active. Enabling is a later yes.

Call `operation="help"` before a format you have not created in this chat.

## Writing within the limits

Write to the visible length, not the maximum. Count characters, including spaces, before the preview, and say the count when you are close.

| Field | Shows before cut-off | Maximum |
|---|---|---|
| Intro text, single image, video, carousel, document | 150 | 3,000 |
| Headline, single image | 70 | 200 |
| Description (only off the feed or on thumbnails) | 100 | 300 |
| Text ad headline and description | 25 and 75 | 25 and 75 |
| Conversation ad subject (optional) | 60 | 60 |
| Conversation ad message | under 500 reads best | 8,000 |
| Conversation ad button text | 25 | 25, up to five buttons including Not interested |
| Message ad subject, body, button | 60, 1,500, 20 | the same |
| Lead form headline and details | 60 and 160 | the same |

Up to ten emojis in an intro. Put any legal wording in the intro text.

## Images and video

Single image: JPG, PNG or GIF up to 5 MB. Landscape 1.91:1 at 1200 x 628, square 1:1 at 1200 x 1200, or vertical 4:5 at 720 x 900. Vertical serves on mobile only. Square works on both, and is the safe default when they send one image.

Video and documents: AdPlug's upload takes MP4 from 3 seconds to 30 minutes, 75 KB to 500 MB, and PDF, DOC or PPT for documents. Short videos with the point in the first seconds do the work in a feed.

Images and video go up with `upload_image` and `upload_video`, and the owner has to be the organisation the ad is published as. If the upload or the create says the file is not owned by the author, set the owner to the page on the account. Do not retry the same file with a guessed owner.

## Single image, video, carousel

`create_inline_ad` with `SINGLE_IMAGE` needs the image, the intro (`commentary`), the landing page or the form, the call to action, and a headline. Without a headline, Campaign Manager leaves the headline blank and will not fill the destination or the button. Pass the headline.

Video and carousel follow the same idea: the intro is the sentence, the headline is the offer, the destination matches the goal. A carousel takes 2 to 10 cards. A lead gen ad set uses `leadgen_form_id`. A website objective uses `landing_page`. Do not attach both and hope.

To change the intro, the button, or a URL the tool can edit, use `update_creative` on that ad. Read the ad first and show the old text beside the new. Do not delete it and make a new one. A new ad loses the review state and the history. Single image destinations often only accept a tracking-parameter change. Headlines and images on image, video, document and carousel ads cannot be edited in place. If the preview says a field is blocked, say so, and offer a new draft ad. Do not loop.

## Document ads

`upload_document`, then `create_inline_ad` with `DOCUMENT`. The headline is the document title, and it cannot be empty.

In a lead generation campaign the ad has to be gated: pass `leadgen_form_id`. The reader stays on LinkedIn. A landing page on that ad is ignored. On a website objective the landing page is honoured.

LinkedIn will not let you reuse a document file across gated ads. A failed create still consumes the file. Re-upload for every ad, and again after a failure.

Call to action edits on a document are rejected. Say so. Change the intro with `commentary`, or make a new draft ad with a new file.

## Conversation ads

`ad_format` `MESSAGE`, on an ad set whose `campaign_type` is `SPONSORED_INMAILS`. You need a subject (AdPlug's create asks for one), the message, a sender, the button text, and either a landing page or a form. One form per ad.

This is for a named audience and a short ask. It is charged per send, so set `cost_type` to `CPS`. The create defaults to CPM if you leave it out. LinkedIn limits how often a member receives sponsored messages, and you cannot set that limit yourself. Do not send a frequency cap here.

Sender approval may be a screen this tool cannot click. If the create fails, say what failed. Do not invent fields to get around it.

## Thought leader ads

`ad_format` `TLA`, with the URN of a public post. The author has to approve the sponsorship, per post or with auto-approval for the brand, through LinkedIn's request in Campaign Manager or Creator Marketplace. There is no tool for that request. If it is not approved, stop and tell them the screen. Polls, celebrations, multi-image posts and reposts are not eligible.

The job is reach and engagement among the titles in the ICP, under brand awareness, engagement, or video views for a video. It is the awareness layer's main format, and its engagers become the warm retargeting pools. Image, video and document posts have no button, so any link sits in the post text. Event posts get a register button. Article and newsletter posts can run too. Judge it on engagement rate and landing-page clicks: most of LinkedIn's counted clicks on these ads are likes, comments and "see more", not visits. Report who saw it from the demographic cut, when that cut has volume. Do not score it on cost per lead. If the author revokes permission, LinkedIn cancels the live ads that use the post.

## Rotation

`creative_selection` on the ad set decides how ads share delivery. Optimised lets LinkedIn favour the ad it predicts will win. Even rotation (`ROUND_ROBIN`) gives each ad a fair share, which is what a creative test needs. Read the current setting before you recommend a change, and call `operation="help"` if the value is refused.

## Rejection, fatigue, retirement

List ads with `entity_type` `creatives`. Rejected ads carry the review status and the rejection reasons. Serving problems carry the hold reasons and whether the ad is serving. An ad still in review is not a finding. A newly rejected ad is. Read the reason. Fix the claim or the file in a new draft, or edit in place when the preview says the field is editable. Do not enable a rejected ad and hope.

Read the click rate on landing-page clicks from `report_type` `creative`. LinkedIn's clicks include likes, comments and profile clicks, which flatter a tired ad.

Frequency is on the ad set, from `report_type` `reach` with the ad set ids, over 92 days or less. Fatigue is the pair: the ad set's frequency up against the previous period, and one ad taking most of the impressions while its landing-page click rate falls against its own earlier weeks. A working line from practitioners: frequency past about 4 in 30 days on a prospecting audience, and the click rate down by about a third. Name the ad. A single day is noise. An ad running more than about six to eight weeks to the same audience is due a fresh angle even before it tires.

Retire means pause: `update_creative` with `intended_status` `PAUSED`. Do not delete a served ad to retire it. Pause waits for a yes. A draft you no longer want can be deleted, still after a yes.

## Other people's ads

`linkedin_ad_library_search` is the public ad library, not this account. Use it when they ask what a category is running. The copy and the image are not in the response. Send them the ad URL. Do not treat a competitor's ad as a draft to recreate.

## What you return

The ads that need a decision: rejected, fatigued, or missing the offer. New copy within the limits, with the counts. The format you would add, as a draft, and which job it belongs to. Nothing enabled. A thought leader ad without the author's approval is a stop, not a draft.
