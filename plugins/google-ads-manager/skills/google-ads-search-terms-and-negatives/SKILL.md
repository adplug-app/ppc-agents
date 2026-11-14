---
name: google-ads-search-terms-and-negatives
description: "Use for every search term report and every negative keyword decision, including the Monday and Wednesday routines."
---

# Search terms and negatives

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

A search term review, a request to add negatives, wasted spend, or the Monday or Wednesday routine. The opportunities section is Thursday, a full audit, or a question about what to add. Monday and Wednesday do not run it.

If no ICP is confirmed, do the short version before you propose negatives: who the customer is, and which themes are for sale. A research query is not automatically waste. Jobs, free, and login are, unless the persona says otherwise. Cross-negatives and the shared top-of-funnel list are defined in Search build. Use them. Do not invent a second system here.

On Monday and Wednesday, before the table: if any enabled Search campaign has Search Partners on, the Display Network on, or AI Max on, name that campaign first.

## Where the terms come from

Search and Shopping queries: `google_ads_search_terms`, sorted by cost. Page until `next_page_token` is null when they asked for the full report. For a routine, take the expensive rows and state how many you did not list.

Dynamic Search Ads, when a DSA campaign exists: the same tool with `dynamic_search_ads` true. Flag landing pages you would not pay for (careers, blog index, login, help centre, legal).

Performance Max does not use that tool for its own queries. Call `google_ads_reporting_view_doc` for `campaign_search_term_insight`, then query it. That report groups queries into categories. It is not the raw query list. Label it as categories. If a category is clearly the wrong intent, propose a campaign negative and say you are matching a category, not a single query. Do not invent the raw queries behind it.

Also check `google_ads_shared_set_criteria` and the campaign and ad group negatives already on the account before you propose a duplicate.

## How to read a term

Read the query. Cost with no conversions is a candidate, not a verdict. A converting query stays, including a messy one, unless its CPA is far outside the target they gave you. Then it is a decision you put in front of them, with the cost and the conversions on the row.

Competitor names are a choice. If they convert inside the target, say keep them. If they do not, propose the negative and say it is a strategy call, not hygiene.

Login, sign in, password, support and other ways an existing customer finds the door are navigational. On the brand campaign they are usually a click the business pays for twice. Search build has the brand campaign rules.

Brand queries inside a non-brand campaign are a leak when a brand campaign exists. Propose a phrase or exact negative for the brand and the obvious misspellings, at campaign level on every non-brand Search campaign, and on Performance Max when the tool allows it. A theme that belongs to another generic campaign is the same kind of leak. Brand plus the product stays in the brand campaign.

Job seekers, careers, salary, hiring, free (when free is not the offer), cracked software, and the wrong country or the wrong product go on the shared list for conversion campaigns, once the persona confirms they are never a customer. Research queries go on that same list when the conversion campaigns are meant to sell. Do not attach the list to a research campaign they chose to run.

## Where the negative goes, and which match type

Shared list or account level: waste that is never a customer, on every campaign.

Campaign level: wrong intent for that campaign only, including brand on non-brand.

Ad group level: the same word is right in one ad group and wrong in another. Use this sparingly. When the term is bad in every ad group, lift it to the campaign or the list.

Phrase for a concept. Exact when only one query is bad and the stem is a product you sell. Broad negative is wider than it looks. Name the match type and the reason in one line per row.

Exact and phrase include the same intent, and a negative does not cover a plural or a synonym. When proposing a negative, include other forms that have already spent.

Do not negative a converting query to make the list look tidy.

## Negative conflicts

Check every proposed negative before you put it in the table. A negative that blocks a keyword the account is buying is the easiest expensive mistake in this skill.

Read the enabled keywords in every campaign and ad group the negative would cover. Treat each keyword's text as if it were a query:

- A broad negative blocks it when every word of the negative is in the keyword, in any order.
- A phrase negative blocks it when the words of the negative are in the keyword, in that order.
- An exact negative blocks it when the keyword text is the negative, with no extra words.

Negatives do not match plurals, misspellings or synonyms, so a conflict is about the words as written.

Also check the negative against queries that converted in the last 90 days. If it would block an enabled keyword or a converting query, say which one and do not propose it in that form. Narrow it (exact instead of phrase, or a longer phrase), or move it to the level where it does no harm.

The full audit and the monthly check run the same test on the negatives already in the account: campaign, ad group and shared lists against enabled keywords. A conflict there is a keyword that cannot serve. Name both, and propose removing the negative or the keyword, whichever is wrong.

## N-grams

The table above reads one query at a time and stops at the expensive rows. Waste spread across a hundred cheap queries never reaches it. The Wednesday pass, the full audit and the monthly check also run n-grams.

Take every search term in the last 30 days, paging until `next_page_token` is null. Split each query into single words and two-word phrases. Add up cost, clicks and conversions for each one across every query it appears in.

List the words and phrases with real cost and no conversions, or a cost per conversion far above the target. Skip brand words and the theme's own keywords. Typical finds are free, jobs, course, template, a wrong city, a product they do not sell, and a competitor nobody chose to buy.

Each one is a candidate phrase negative, and goes through the conflict check above. A word that also appears in converting queries is not a negative. Say so, and leave it.

Show the top ten by cost: the word or phrase, how many queries contain it, cost, conversions, and the negative you would add.

## The table

Term, campaign, ad group, cost, conversions, the negative you would add, match type, level (account, shared list, campaign, or ad group), and why. Currency as the tool returned it. For a routine, cap the table at the rows that matter and give the count and cost of the rest.

Group the same text that is bad everywhere into one negative, and name the campaigns it would cover.

## Opportunities from search terms

Monday and Wednesday do not run this section. They stay on waste and proposed negatives. Thursday runs it. A full audit runs it. Run it when they ask what to add.

Use `google_ads_search_terms` with `date_range` `LAST_30_DAYS` and `LAST_90_DAYS`. For a routine, keep it to converting queries, not the whole cost list. Performance Max uses `campaign_search_term_insight`, labelled as categories, not raw queries. A converting category is a theme to look at. Do not invent the query behind it, and do not add a keyword you have not seen.

A query is uncovered only after you have checked the live keywords. The search terms tool returns the match type that triggered the row, including close variants (`NEAR_EXACT`, `NEAR_PHRASE`). Also check enabled keywords in the account before you call anything uncovered. Exact and phrase include the same intent. A close variant of an existing exact or phrase keyword is not a new keyword. Say that.

For each converting query that is uncovered, use ICP for Google Ads. Search behaviour is the intent in the query: commercial, research, navigational, brand, competitor, and the modifier. One behaviour per ad group. Software versus agency, and pricing versus alternative, are different behaviours.

Decide one of these:

- Not relevant. It converted once and still does not match the offer. Say so. Do not add it.
- Same theme as an existing ad group, and that group stays one theme and under 20 keywords. Recommend the keyword there, exact or phrase, not broad by default. Name the ad group and the match type.
- Different search behaviour from every current ad group. A different job, a different modifier, or a different buyer. Recommend a new ad group, paused, with its own two responsive search ads and sitelinks for that theme. Do not create it without a yes.
- The current landing page does not match that behaviour. Recommend a more specific page, and say what the page has to answer. Do not invent a URL that is not on the site. If no such page exists, the recommendation is to write the page first, and keep the query out of an ad group that sends people to the wrong page.

`google_ads_recommendations` is only a prompt for this same question. A keyword or a page Google suggests is judged the same way, against the persona and the page. Do not apply Google's recommendation to raise the optimisation score.

Nothing is created until they name the rows and say yes. New ad groups stay paused. No keyword, no ad group, and no page.

## Applying

You do not add them in the routine. End with: reply with the row numbers and I will preview them.

When they pick, call `google_ads_preview_add_negatives` with the right `target_type` and `target_id`. Ad group negatives use the ad group id as `target_id`. Show the preview. Execute only after a yes, with `google_ads_execute_add_negatives` and that preview id. If the preview has expired, preview again. Do not reuse an old id.

A shared list that is not applied to the campaigns does nothing. If you add to a list, check it is linked. If it is not, the link is a second change and needs its own preview.
