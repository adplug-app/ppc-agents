---
name: linkedin-ads-lead-forms-and-conversions
description: "Use when the goal is a form or a page conversion, when a form or the Insight Tag goes quiet, when you create or judge a form or a conversion rule, or when they want CRM stages fed back to LinkedIn."
---

# Lead forms and conversions

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A new lead gen ad set, a form that needs writing, a week scored on cost per lead, a daily alarm that the form or the tag went quiet, a conversion rule to create or check, or "can LinkedIn see our pipeline". The goal and the offer come from ICP for LinkedIn. If either is missing, ask before you judge the number.

## Two different results

Decide which number the account is allowed to optimise to, and say it.

The form, when they agreed the form is the goal. Then form completions and cost per lead are the score. The lead report is `linkedin_ads_performance` `report_type` `lead_gen`. Each row is an ad set: leads, form opens, LinkedIn's qualified leads, cost per lead, and the open-to-submit rate. Roll the rows up to the campaign yourself: add the leads and the opens, then divide. Do not average the rates.

The conversion a salesperson would recognise, when the goal is a qualified lead, a demo, or pipeline. A form fill is a candidate until a person accepts it. If no CRM stage comes back to LinkedIn and they have not given you the downstream count, say the report is form fills, and do not call the cost a cost per opportunity. Website conversions count only when the event matches the button. A page view is not a demo.

Do not add form fills and website conversions into one lead total. They are different actions. Name them in separate lines.

## The form

Read it with `linkedin_ads_list` `entity_type` `lead_forms`: the name, the state, the headline, the description and the questions.

A short form completes. LinkedIn's guidance is three or four fields, and twelve is the maximum. First name, last name and email arrive pre-selected, and they count toward the twelve. Up to three custom questions, each up to 100 characters. They are required, and they count. A custom question keeps out the people the salesperson does not want, and it lowers the completion rate. That trade is right when the question is the goal, such as timing or the problem they have. It is waste when the question is "how did you hear about us". The form headline takes up to 60 characters and the details up to 160.

On a multiple-choice question the first answer is pre-selected. Do not put the agreeable yes first. People submit the default.

Work-email validation blocks the common free inboxes. It also drops people who will not type a work address. Use it when sales needs the work address, and expect fewer submits. Say that in the preview.

The thank-you line says when someone will be in touch. If the offer is a document, the link goes in the thank-you, or a person sends it. Hidden fields carry tracking into the CRM, up to twenty, and the member never sees them. They cannot be added to a form attached to an active ad set. A new form is the way.

The ad and the form have to be the same offer. High opens and few submits means the form got longer than the ad promised, or a question is doing the filtering. Read the questions before you blame the bid.

Create with `create_lead_form`. State defaults to draft. Leave it draft. Publishing (`state` `PUBLISHED`) is its own yes, after they have read the questions. A published form only lets you edit a short list of fields. A form on a conversation ad cannot be edited once it is published. A privacy policy URL is required. If they do not have one, stop. Do not invent one.

The leads themselves are not readable today: `lead_form_responses` needs a LinkedIn permission AdPlug does not ask for yet. Count leads with the `lead_gen` report. The people are downloaded in Campaign Manager or arrive through their CRM's sync. If a reply ever does contain a lead, it is personal data: do not paste names, emails or phone numbers into a reply or a report someone might forward.

## Conversion rules and the Insight Tag

A website conversion is a rule: the preview operation `create_conversion_rule`, method `IMAGE_PIXEL` for the Insight Tag. The tag on the site is installed by them. This agent cannot place it, and a rule existing is not proof the tag fires. List `entity_type` `conversions` for the rules, and read `report_type` `conversion` for what LinkedIn recorded.

Set the windows on purpose. Campaign Manager's own default is a 90-day click and 90-day view window. AdPlug's create sends a 30-day click and 7-day view window when you leave them out. Choose from 1, 7, 30 or 90 days. For a B2B lead or a demo, a 30 or 90-day click window fits the sales cycle. Conversions that arrive through the Conversions API or a CSV upload can also take a 180 or 365-day window, for lead, qualified lead, MQL, SQL, purchase, add to cart and submit application. On a long sales cycle that is the window for the CRM stages. If AdPlug's create refuses it, say so and point them to the rule's settings in Campaign Manager. Keep the view window short, 7 days or less, unless they want view-through credit, and say what you picked in the preview.

The conversion report splits each rule into post-click and post-view. A view-through conversion is someone who saw an ad, did not click, and converted later. Report them on separate lines. A week carried by view-through conversions is weaker evidence than it looks.

The attribution model matters when you add ad sets together. "Each ad set" (the default) credits every ad set that touched the person, so the ad set rows add up to more conversions than happened. "Last ad set" credits one. On a new rule whose totals you will add up, recommend the last ad set, and say which model a rule uses before you sum it.

Associate a rule only with the ad sets that should use it, after a yes. Check with `campaign_conversions`. Remove a rule from ad sets with `dissociate_conversion`. The rule and its history stay. Do not attach every rule to every ad set.

You cannot see the tag in a browser, the consent banner, or whether sales logged the lead. Say which of those you are missing.

## Feeding CRM stages back to LinkedIn

Pipeline lives in their CRM, not here. Three routes bring it back, best first.

1. Their CRM's own connection. HubSpot (Marketing Hub Professional or Enterprise) syncs lifecycle stages to LinkedIn as conversions: a marketing or sales qualified lead arrives as a qualified lead, an opportunity as a quote request, a customer as a purchase. Salesforce, Dynamics and others connect through LinkedIn's partners, such as Zapier or Salesforce Data 360. They set it up in the CRM or in Campaign Manager, and the rule then appears in your list. LinkedIn's own CRM Sync, set up in Business Manager, is another way in for Salesforce, Dynamics 365 and HubSpot (LinkedIn lists HubSpot Sales Hub Professional or Enterprise for it). It creates the conversions itself, which can take up to 72 hours. One route per stage: the same stage sent by the Conversions API and by CRM Sync is counted twice.
2. Not this agent, today. `linkedin_ads_send_conversion_event` posts to LinkedIn's Conversions API, which needs a LinkedIn permission AdPlug does not ask for yet. Do not offer it. If it ever accepts a call, each event needs the time it happened and a user id (the SHA-256 of the lowercased, trimmed email, or LinkedIn's first-party click id), an event id so a resend does not count twice, and a value when they have one. The instructions' rules for conversion events apply: read back, wait for a yes, never a plain address.
3. A CSV upload in Campaign Manager, by hand.

For LinkedIn's qualified lead optimisation, the qualified leads have to arrive within 30 days of the lead, and LinkedIn suggests at least five every two weeks. It runs on maximum delivery only, on the lead generation objective, and learns for about two weeks. It is the conversion layer's goal once the CRM loop works. Below five a fortnight, optimise to leads and judge on the CRM count.

Without any route, ask them each month for the CRM counts by campaign: qualified leads, opportunities, pipeline. Check the leads LinkedIn reported against the leads the CRM received. A gap above about 10 to 15% is a sync problem to fix before anyone reads the cost per lead. If AdPlug's HubSpot tools are connected in this agent too, read the counts there instead of asking.

## When it goes quiet

Compare with the same weekday, and with the recent weeks. One empty day on an account that gets a few leads a week is normal. Do not call it a broken form.

An ad set that usually gets form opens, and now spends with none, has lost the form or stopped serving the ad that opens it. Opens holding up while submits collapse is the form or the offer. Read the questions and the ad before you touch the bid.

Website conversions that stop while clicks continue, past the gap you usually see on this account, are the tag or the rule. A rule that is disabled is the first place you look. Conversions keep arriving for days after a click, so yesterday is never final. Do not send conversion events to fill the gap.

## What the ad set is allowed to buy

Bidding and budget decides the bid. A cold lead gen ad set optimises to leads only when the form is the agreed goal. LinkedIn's qualified leads goal only when the qualified lead events come from their CRM and they said that is the goal. A website conversion objective uses the Insight Tag event that matches the button, not a visit.

## What you return

Which result you are scoring. The form, in one or two lines: how many fields, what the custom question is doing, whether you would publish it. Each rule: recording, quiet, or never seen, with its windows and model when they matter. Post-click and post-view on separate lines. Whether CRM stages come back, and by which route. Nothing published, associated or sent until they name the row.
