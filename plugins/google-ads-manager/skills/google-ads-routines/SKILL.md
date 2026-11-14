---
name: google-ads-routines
description: "Use when the person asks to set up the nine scheduled checks and reports, or to run one now, such as \"run the daily check\"."
---

# Google Ads Manager routines

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## The nine routines

These are the nine routines. In Claude, create each one as a scheduled task. In Codex, create each one as a scheduled task. In Claude Code, tell the person they can run any routine by asking for it by name. Set them up one at a time, at the times below, in the person's timezone, and confirm each one once it's saved. Do not call Google Ads tools while setting them up. Do not run them now. Each routine's prompt starts with: "Use the Google Ads manager's skills and follow this routine."

Each routine reports only. It never previews and never executes. AdPlug previews expire in about 15 minutes and a routine approval expires in about 30, so the person applies changes later, in this chat, by naming the rows.

Each routine is one account. Name the client and the customer id in the first line. If they are an agency and no client was named, or more than one customer exists and none was chosen, list the accounts and stop. Do not mix clients in one report. Do not reuse another client's negatives, budget, persona, or goal. An in-house team with more than one account stays on the one they named until they switch. Recommend and wait applies per account.

Each routine follows How you write in the instructions. Lead with what needs them. At most five decisions. One table at most. A section with nothing to report is one line or nothing. Do not repeat an alarm another routine raised today unless it is still open, and then in one line.

Small accounts. If the monthly budget they gave is under about 3,000 US dollars, or the same in their currency, Wednesday and Friday are one line each unless something needs a decision. With no budget given, use the last 30 days' spend only to decide this, and never call it the plan.

Times are in the person's timezone.

## 1. Name: Daily check

Every day at 07:30, including weekends.

Follow the daily check in the skill "Daily and monthly checks". Alarms only. On a normal day the whole reply is "Nothing on fire." Do not change anything. If there is an alarm, end with what you would do and ask which rows to preview.

## 2. Name: Search terms, Monday

Every Monday at 08:00.

Follow the skill "Search terms and negatives", and these limits.

Use the account you were told to use. If none was named and more than one customer exists, list the accounts and stop.

Follow Search build for the three locks before anything else. If any enabled Search campaign has Search Partners on, the Display Network on, or AI Max on, name those campaigns first.

The daily check already covered yesterday. If it raised an alarm this morning that is still open, repeat it in one line. Otherwise go straight to the terms. Do not mine these terms for new keywords. That is Thursday.

Then last 7 days of search terms, top rows by cost, with the count and cost of the rows you left out. Include Performance Max search categories when a Performance Max campaign is enabled, labelled as categories. Include DSA terms when a DSA campaign is enabled. On the brand campaign, include login, support and other existing-customer terms that spent, unless they said they want to pay for them.

Propose negatives in the skill's table, after the conflict check. Do not add them. End with: reply with the row numbers and I will preview them.

## 3. Name: Weekly report, Monday

Every Monday at 09:00.

Follow the weekly report in the skill "Reports". The last seven full days. The report first, written so it can be forwarded. Then "For you", with the decisions and the changes from the log that are due for checking. Do not change anything.

## 4. Name: Needs you, Tuesday

Every Tuesday at 08:00.

This is the short audit in the Account audit skill. It is a short performance pass, not the full audit, and it does not repeat Monday's search-term table or Thursday's structure table.

Last 7 to 14 days. Only what needs a decision, in the skill's priority order. Meeting the KPI matters. Spending more is not the goal.

Lead with any enabled Search campaign that has Search Partners on, the Display Network on, or AI Max on when that campaign is not a named test. Then auto-apply subscriptions that are on. Then conversions against the goal and the KPI, using the measured lag. Then Smart Bidding status: a campaign learning, limited or misconfigured. Then pace against the budget they gave, and any shared budget that puts brand and generic, or a strong campaign and a weak one, on the same pool. Name the pool and the campaigns. Then a place with real spend and no conversions. Impression share lost to budget and lost to rank is context only. Do not recommend raising a bid to buy rank. If performance moved, name a recent change from change history.

If no budget was given, ask once and leave pace out. Do not invent a number.

Lead gen and Shopping both count. On Shopping, spend ahead of plan with a weak product return is a line in the list. It is not a recommendation to scale.

Do not move a budget, raise a daily cap, pause a campaign, exclude a location, or turn a subscription off. End with the priority list and ask which rows to preview.

## 5. Name: Search terms, Wednesday

Every Wednesday at 08:00.

Follow the skill "Search terms and negatives".

This is the second pass, not a repeat of Monday. If Search Partners, the Display Network, or AI Max were still on after Monday, say so in one line. Then read Monday's report in this chat. List terms that were not in it, or terms whose cost has jumped since. If Monday's report is not in the chat, use the last 7 days, say you could not see Monday's list, and keep the table short.

Then the n-gram pass from the skill, on the last 30 days: the words and two-word phrases spending across many cheap queries with no conversions. Only the ones that are not already in Monday's table or on a negative list.

Include new Performance Max categories the same way, when that campaign type is enabled.

Propose negatives, after the conflict check. Do not add them. End with the same line: reply with the row numbers and I will preview them.

## 6. Name: Search build, Thursday

Every Thursday at 08:00.

This is the structure pass. It does not repeat Monday's search-term table. Quality Score and audiences are monthly, not here.

Follow Search build. Lead with any enabled Search campaign that has Search Partners on, the Display Network on, or AI Max on. Then cross-negatives (brand missing from generic), the brand campaign paying for login and support terms, the shared top-of-funnel list missing or not applied, duplicate keywords across ad groups, ad groups at 20 or more keywords or mixing themes, ad groups with fewer than two RSAs, ad groups with fewer than 6 sitelinks in the branch or with no sitelink of their own, other missing Search assets and the level you would create them at, and final URLs that do not match the theme. Recommend the assets. Do not create or link them.

Then the opportunities section of Search terms and negatives. Converting queries from the last 30 days and the last 90 days that are not already covered by a keyword. Not Monday's waste table. Four outcomes only: skip, add to a named ad group, a new paused ad group, or a page to write first. A close variant of an exact or phrase keyword already in the account is not a new keyword. Google's keyword and page recommendations are judged the same way. Do not apply them. Do not create a keyword, an ad group, or a page.

Do not run the full account audit. Do not change a bid strategy.

Do not change anything. End with the rows worth a preview.

## 7. Name: Placements and products, Friday

Every Friday at 08:00.

Four short sections, in this order. Skip a section that does not apply and say why, in one line.

Negatives still waiting. From Monday and Wednesday in this chat, list proposed rows that were never previewed. If there are none, say so. Do not add them.

Placements. Follow the skill "Placements". Demand Gen if any of those campaigns are enabled, otherwise Performance Max. If neither is enabled, one line.

Products. Follow the skill "Shopping products" when Shopping or Performance Max is enabled. Lead with not eligible and limited, grouped by issue. A disapproval is a Merchant Center fix, not a bid and not a budget change. Then products spending with no conversion value. If a monthly budget is known and spend is ahead of it while that return is weak, name the gap. Do not invent a margin. If there is no product campaign, one line.

Ads and sitelinks. Enabled ads that are disapproved, with the policy topic when it returns. Ads approved but limited, as a lower line. Skip ads still under review. Sitelinks with a policy problem, or a destination you could open and that did not load. Say when you could not open the URL. Do not rewrite an ad or a sitelink.

Do not change anything. End with the row numbers that are worth a preview, across all sections.

## 8. Name: Monthly report

The 1st of every month at 09:00.

Follow the monthly report in the skill "Reports". The last calendar month. The report first, written so it can be forwarded. Then "For you". Do not change anything.

## 9. Name: Monthly check

The 2nd of every month at 08:00.

Follow the monthly check in the skill "Daily and monthly checks". Quality Score always has a line. Then the decisions, at most five, and the scorecard. If no promotion dates are remembered for the next six weeks, ask once. Do not change anything. End with the rows worth a preview.
