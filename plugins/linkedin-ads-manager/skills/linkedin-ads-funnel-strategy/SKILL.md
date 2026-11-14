---
name: linkedin-ads-funnel-strategy
description: "Background for every LinkedIn Ads plan, build, check and report: how a B2B account is built, in layers."
---

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

# How a B2B LinkedIn account is built: the layers

## Why layers

Most of the people in a B2B audience are not buying this quarter. The LinkedIn B2B Institute's 95-5 rule, from John Dawes, says about 5% of buyers are in the market at any time. It is a rule of thumb, not a measured rate. A cold ad that asks for a demo is asking the other 95% for something they do not need yet. They scroll past, and the cost per lead looks terrible.

So a working account runs in layers. A cold layer earns attention from the ICP. That attention becomes retargeting pools. The warm pools get the ask. LinkedIn's own case studies say people who saw both brand and acquisition ads were up to six times more likely to convert, and a 2024 LinkedIn and WARC study found brand-exposed audiences clicked demand ads 58% more often. Those are LinkedIn's figures, so say so when you quote them.

Two layers is the minimum that works: cold attention and a warm ask. A third layer, consideration, sits between them once the warm pools are big enough to split.

## The three layers

| Layer | Who | Job | Objective | What runs | Judged on |
|---|---|---|---|---|---|
| Awareness | Cold: the confirmed ICP, with the exclusion block | The right people meet the point of view, and the retargeting pools fill | Brand awareness, engagement, or video views | Thought leader ads, short video, ungated document ads, event ads | Reach inside the ICP, engagement rate, cost per engagement, and how fast the pools grow. Never cost per lead |
| Consideration | Warm: engaged with the awareness layer | Proof. Why this approach, why this company | Lead generation for gated content, or website visits | Case studies, a report or a guide behind a form, a webinar, a comparison | Cost per content lead, and how many of those leads become conversations |
| Conversion | Hot: high intent | The ask | Lead generation with a demo or trial form, or website conversions | Product ads: the demo, the trial, pricing, the product itself, customer proof with numbers | Cost per qualified lead and per opportunity, from the CRM where possible |

Each layer is its own campaign with its own budget. They never share a Dynamic Group Budget, because LinkedIn would then move the money towards the cheapest result, which is always the cold engagement.

The existing skills call these jobs thought leadership, lead gen and retargeting. Awareness is the thought leadership job. Consideration and conversion are lead gen run on warm and hot audiences. Use the person's words when they have their own.

## Thought leader ads are the awareness engine

A thought leader ad sponsors a member's public post: the founder, an expert on the team, a customer, or a creator. People engage with a person far more than with a company page. Practitioner studies from 2026 put the engagement rate at several times that of a single image ad on the same objective. One study of 464 accounts found the median engagement rate was about 4.5%. Treat these as working figures, not LinkedIn's promise.

The catch is in the same study: about nine in ten thought leader ad "clicks" never reach a landing page. They are likes, comments, profile and "see more" clicks. So judge them on engagement rate and cost per landing-page click. LinkedIn's total click rate and cost per click flatter them.

What they can run under: brand awareness, engagement, or video views for a video post. No lead form. Image, video and document posts have no button, so a link goes in the post text. Event posts are the exception and get a register button. Article, newsletter and event posts can run as thought leader ads too. The author approves each sponsorship, or turns on auto-approval for the brand, in Campaign Manager. AdPlug can create the ad from the post once that approval exists. It cannot send the request.

What works: a real point of view from someone the buyer would listen to, written for the ICP's problem, not a product announcement. A few authors and a few posts at a time, refreshed as engagement falls.

## How the warm pools are built

The engagement from the awareness layer is what the later layers target. These are LinkedIn's retargeting audiences, built in Campaign Manager under Plan, Audiences, Create audience. AdPlug's connector cannot create them yet. You write the spec, they build it, then you find it and attach it after a yes. Suppression and retargeting has the sources, the lookbacks and the names.

What to know:

- Thought leader ad engagers have no audience type of their own. A thought leader ad runs inside a single image, video or document ad set, so you retarget its engagers by picking that ad set in the matching engagement audience. Every new awareness ad set has to be added to the engagement audiences, or its engagers never reach the warm layer.
- Video viewers at 50% or 75% are the strongest cold-to-warm signal. 25% is a scroll.
- Engagement audiences include past engagement within the lookback. Website audiences fill from the day they are created. So build the website pools on day one, before the awareness layer has spent.
- A pool needs 300 matched members before it can run. It takes up to 48 hours to build, and up to a day more to serve. In the EEA and Switzerland only members who consented are matched, so pools there are smaller.
- Companies Hub, in Campaign Manager, shows which target companies are engaging, from paid and organic. Since December 2025 an engaged-company segment can become a company audience in one click. On an account-based programme, that list is the conversion layer's audience.
- High-intent pools for the conversion layer: pricing, demo and case study page visitors in the last 30 days, lead form openers who did not submit, content leads from the consideration layer, and highly engaged target companies.

Open opportunities are their own ad set, with proof and the reason to decide now. Customers, employees, competitors and job seekers are excluded from every layer. Each warm and hot ad set carries the exclusion block minus the list it is built on.

## Order and timing

1. Before anything spends: the Insight Tag recording, the conversion rules, the website retargeting pools, and the exclusion block. A pool that does not exist on day one has missed the people the first weeks paid to reach.
2. Awareness first. It has to run before there is anyone to retarget.
3. The conversion layer starts when a hot pool is over 300 matched members and big enough for its budget. On a mid-sized budget that is often four to eight weeks in. Working line, not a platform rule.
4. Consideration comes in when the warm pool is too large and too cold to send straight to a demo ask.
5. After 60 to 90 days of pools growing, move budget down the funnel as the warm layers can spend it.

## Budget between the layers

There is no platform rule. These are starting points:

- The B2B Institute found the best B2B results with roughly 46% on brand and 54% on activation, across all marketing. LinkedIn rounds it to half and half.
- A new programme with no warm pools: about 50 to 60% awareness, 25 to 30% consideration, 10 to 20% conversion. As the pools grow, move towards 30 to 40% awareness, 25 to 30% consideration, 30 to 40% conversion. A LinkedIn case study ran 40, 30, 30 and cut its cost per lead by 40%.
- A small budget, under about 3,000 a month in the account currency: two layers. One awareness ad set on the ICP, and one conversion ad set on the hot pool once it passes 300. If the account already has warm pools or a named account list, the conversion ad set comes first.

The split is set from the goal and the pools, and then judged on the conversion layer's cost per qualified lead or opportunity, with the layers above it as the reason it is low. A layer whose job is attention is never cut for having no leads. It is cut when its engagement, or the warm pool it feeds, stops growing.

## Frequency by layer

Awareness can run about 6 to 10 impressions per member per month. That is the practitioner norm. LinkedIn's frequency cap exists only on brand awareness ad sets, at 3 to 30 per week, and is still rolling out. Warm and hot pools are small, so frequency climbs fast. Watch it on every retargeting ad set and refresh the ads before the same people see the same ask for a month. The working line in New campaigns, about 4 a month, is for a cold lead gen ad set, which is asking for something rather than earning attention.

## Conversion events make the layers work

Every layer needs the right event recording before it spends, or it learns nothing and reports nothing.

- Awareness: no conversion goal. The pools are the output, so the Insight Tag must be on every page.
- Consideration: the content lead form, or a website conversion on the gated page's thank-you step.
- Conversion: the demo or trial form, or the matching website conversion. Then the CRM stage: qualified lead, opportunity, closed. Sent back through the Conversions API, LinkedIn's CRM Sync, or a CSV upload, LinkedIn can optimise to qualified leads. That needs about five qualified leads every two weeks, arriving within 30 days of the lead, on the lead generation objective with maximum delivery.

Lead forms and conversions has the rules, the windows and the routes. Without the CRM loop, the conversion layer is judged on form fills, and you say that in every report.

## What a plan from you looks like

Name the layers you would run now, and the ones you would leave off. For each: the audience, the objective, the format, the budget share, the event it records, and what it is judged on. Then the pools to build first, and the date the next layer can start. Building it follows New campaigns. Nothing is created or changed without a preview and a yes.
