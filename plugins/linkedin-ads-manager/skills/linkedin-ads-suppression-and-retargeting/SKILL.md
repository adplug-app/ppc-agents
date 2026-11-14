---
name: linkedin-ads-suppression-and-retargeting
description: "Use when setting up or checking who a prospecting ad set must not reach, the account's exclusion block, retargeting pools and their lookback windows, open-opportunity and customer lists, or predictive audiences."
---

# Suppression and retargeting

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A new account, a new prospecting ad set, the monthly check's suppression section, "are we paying to reach our customers", or "set up retargeting". The ICP's exclusion list is the starting point. Audiences has the count, the floor and the list upload mechanics.

## Who a prospecting ad set must not reach

LinkedIn's own guidance for prospecting is to exclude customers, employees, competitors, open pipeline and past form submitters. This agent adds job seekers, and agencies and recruiters when they are not the buyer.

| Who | How you exclude them | Built by |
|---|---|---|
| Customers | Company list of customer accounts. For a large customer where other divisions are still prospects, a contact list of the customer's users instead | This agent, from a file they give |
| Open opportunities | Company list of accounts in open deals, from the CRM | This agent, from a file |
| Past converters | Lead form submitters, and site visitors to the thank-you page | Campaign Manager, by them |
| Employees | Their own company in the employers facet. Take it from `associatedEntity` on an existing ad set, or ask | This agent |
| Competitors | The competitors they name, in the employers facet, through `search` | This agent |
| Job seekers | The job seeker member trait (`memberBehaviors`) | Read from an ad set or saved audience that already uses it |
| Agencies and recruiters | Staffing and recruiting, and advertising or marketing services industries, and recruiter titles, when they are not the buyer | This agent |
| Students and juniors | Unpaid, training and entry seniority, when the offer is a sales conversation | This agent |

The job seeker trait cannot be searched through this tool. If no ad set or saved audience in the account carries it, ask them to add "Member traits: job seekers" as an exclusion on one ad set or saved audience in Campaign Manager once. Then read its value with `linkedin_ads_get` and reuse it. Confirm every value with `resolve_urns` before it goes into a preview.

Open opportunities are not only an exclusion. They are their own ad set: proof, case studies and the reason to decide now, judged on deal progress, not cost per lead. Ask before you treat them as either.

## The exclusion block

Keep one block per account, saved as a targeting audience named "Exclusions | <client>", with `create_targeting_audience`. That saved audience is the record of what every prospecting ad set must exclude. If the create refuses a block with no inclusion, add the account's main location as the inclusion and say so. It is not something you apply. `apply_targeting_audience` replaces an ad set's whole targeting with the saved one, so applying an exclusion block wipes the audience it was meant to protect.

How you use it:

1. Read the block with `linkedin_ads_get` `entity_type` `targeting_audience`.
2. On a new ad set, put the block's exclusions into the targeting you create.
3. On a live ad set, read its targeting, add the missing exclusions, count it, and preview the whole block with `update_campaign`, showing the forecast before and after.
4. When the block changes, list the live prospecting ad sets missing the new part, and ask which rows to update.

Retargeting and opportunity ad sets carry the block minus the list they are built on.

## Keeping lists fresh

A list uploaded through AdPlug takes one file, ever. To change it, create a new segment, upload, wait up to 48 hours, then swap it into the ad sets and the block, each swap a preview. Customer and open-opportunity lists go stale as deals move: refresh them monthly on an account that closes deals every month, quarterly otherwise. A failed or still-building list is not an exclusion you can trust. Keep the old one attached until the new one is ready.

## Retargeting pools

These are built in Campaign Manager under Plan, Audiences, Create audience, Matched audience. AdPlug's connector cannot create them yet: it only creates company and contact lists. LinkedIn's API can, so this may change. Until it does, you write the spec, they build it, then you find it with `saved_audiences` and `name_contains`, check it is ready and over 300 matched members, and attach it after a yes.

| Pool | Source | Lookback to build |
|---|---|---|
| High-intent visitors | Insight Tag: pricing, demo, case study or product pages | 30 and 90 days |
| All site visitors | Insight Tag: every page, minus careers and the app | 90 days, 180 on thin traffic |
| Video viewers | Viewed 50% or 75% of a video ad, including video thought leader ads | 90 days |
| Ad engagers | Engaged with a single image ad set, including the image and text thought leader ad sets | 90 and 180 days |
| Form openers who did not submit | Lead form opened, with the submitted pool excluded in the ad set | 30 days |
| Document readers | Engaged with a document ad, including document thought leader ads | 90 days |
| Conversation engagers | Opened a conversation or clicked a button | 90 days |
| Page visitors | Viewed the LinkedIn Page or clicked its button | 90 days |
| Event | Registered and did not attend, or attended | 30 to 90 days |
| Engaged companies | Companies Hub: the highly engaged or engaged-prospect segment, saved as a company audience | Refresh monthly |

LinkedIn offers 30, 60, 90, 180 or 365 days on most sources (website actions go to 180), and video at 25, 50, 75 or 97% viewed. There is no carousel engagement source.

Thought leader ads have no audience type of their own. Their engagers are retargeted by picking the thought leader ad set inside the single image, video or document engagement audience. Every new awareness ad set has to be added to those audiences, or its engagers are lost. Engagement audiences include past engagement within the lookback, as long as the ad has results. Website audiences fill only from the day they are created, so build them before the first awareness spend. A new audience takes up to 48 hours to build and up to a day more to serve.

Companies Hub, in Campaign Manager, shows which target companies engage, from paid and organic. Since December 2025 a segment there can be saved as a company audience in one click. On an account-based programme, the highly engaged companies are the conversion layer's audience. Name each pool with its source and window, such as "Site | Pricing | 30d". Build the short and the long window for the pools that matter, so the numbers can show which one converts.

Retargeting ad sets get their own ads and their own cost per lead. The warm pool, such as video viewers and ad engagers, gets proof and gated content: the consideration layer. The hot pool, such as pricing visitors, form openers and engaged companies, gets the sharper ask: a demo, a trial, the product. That is the conversion layer. Do not mix them into cold ad sets. In the EEA and Switzerland, matching only counts members who consented, so pools there are smaller.

## Predictive audiences and lookalikes

LinkedIn ended lookalike audiences on 29 February 2024. Predictive audiences replaced them. They are built in Campaign Manager from one source of at least 300 members: a lead form, a contact or company list (300 to 300,000 rows), a conversion, or a retargeting pool. Audience Expansion is off on ad sets that use them. They are a way to scale a working ad set, not a starting point. If they ask for one, write the spec, say the seed list should also be excluded if they only want new people, and test it as its own ad set against the precise version.

## What you return

The exclusion block in plain words, and which live prospecting ad sets lack part of it. Lists that are stale, building or failed. The retargeting pools to build, with source and window, as a spec they can follow in Campaign Manager. Nothing applied.
