---
name: google-ads-reports
description: "Use for the weekly and monthly report routines, or when they ask for a report, a summary for a client or a boss, or how the account did."
---

# Reports

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Weekly report routine on Monday, the Monthly report routine on the first of the month, or "how did we do", "send me a report", "write this up for the client". The other routines are for the operator. A report is for whoever they forward it to.

## Who reads it

A boss, a client, a founder. Not a PPC specialist. They want to know whether the money worked, why, and what happens next. Write the report so it can be forwarded as it is.

- No field names, tool names, preview ids or row numbers in the report.
- The KPI first, in money, against the target they gave.
- One table. The rest is short lines.
- Explain a term the first time it appears, in a few words.
- Plain cause and effect. "CPA fell to £71 from £82 after we cut the job-seeker searches." Not "efficiency improved".

The operator's part comes after the report, under the heading "For you". That is where the decisions, the rows to preview and anything you could not see go. They can forward everything above it.

## Reading the numbers

- The KPI decides whether the week was good. Spend going up is not a result. More conversions at the same CPA is more volume, not a better account. Say which it was.
- Recent days are still filling. Use the measured lag from Conversions and bidding. Mark the days inside it as still counting, and do not call them a drop.
- Compare like with like. A week against the week before, and against the average of the four weeks before. A month against the month before, and against the same month last year when the account and its tracking were the same then. If the tracking changed in between, say so and drop the year-on-year line.
- A big move gets a reason when you can see one: a change from the change log, a search term, a budget cap, a disapproval, a holiday. If you cannot see one, say "no clear cause in the account".
- Never add figures across clients or currencies. Never project a month from one week.
- When the KPI is qualified leads and no offline stage is imported, say the report counts form fills, not qualified leads.

## The weekly report

The last seven full days, Monday to Sunday.

1. Title line. Client, customer id, the dates, the currency.
2. The week in three sentences. The KPI against the target. What moved it. Whether anything needs a decision.
3. The table. Spend, conversions, CPA or ROAS, conversion value for ecommerce, and clicks. Columns: this week, last week, the change, the four-week average, the target.
4. The month so far. Spend to date against the budget, and where the month will land at the current pace (spend so far, plus the average daily spend of the last seven days times the days left). One line.
5. Campaigns that moved. Three to five, one line each, with the reason.
6. What we did. Changes applied this week, from the change log, in plain words. Changes due for checking this week, and what happened: kept, undone, or too early to tell. If someone else changed the account, one line saying what, from change history.
7. Tests running. Name, and day so many of so many.
8. Next week. Up to three things.

Then "For you": the decisions, at most five, and the rows to preview.

## The monthly report

The last calendar month.

1. Title line. Client, customer id, the month, the currency.
2. The month in three sentences. The KPI against the target, spend against the budget, and the biggest reason for either.
3. The table. Spend against budget, conversions, CPA or ROAS against target, conversion value, clicks. Columns: this month, last month, the change, the same month last year when it is comparable.
4. Where the money went. Each campaign, or each campaign type on a big account, with its share of spend next to its share of conversions or value. Up to eight rows, inside the same table or as a second short list.
5. What moved the KPI. Three things, each with its number.
6. What we did, and whether it worked. The changes from the log that were due this month, with their result.
7. Tests finished. Each with its result in one line: promoted, ended, or not enough data.
8. Next month. The plan in up to five lines, the budget, and any promotion dates coming.

Then "For you": the decisions and the rows to preview.

## Agency mode

One report per client, with the client name and customer id in the title. Never two clients in one report. The client's own currency. The "For you" section stays out of anything they plan to send the client. If they ask for a version for the client, give the part above "For you" on its own.

## What you return

The report, then "For you". Keep the report to one screen and one table. They can ask for any campaign in full.
