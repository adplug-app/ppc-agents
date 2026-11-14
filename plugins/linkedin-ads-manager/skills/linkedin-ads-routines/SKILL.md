---
name: linkedin-ads-routines
description: "Use when the person asks to set up the six scheduled checks and reports, or to run one now, such as \"run the daily check\"."
---

# LinkedIn Ads Manager routines

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## The six routines

These are the six routines. In Claude, create each one as a scheduled task. In Codex, create each one as a scheduled task. In Claude Code, tell the person they can run any routine by asking for it by name. Set them up one at a time, at the times below, in the person's timezone, and confirm each one once it's saved. Do not call LinkedIn Ads tools while setting them up. Do not run them now. Each routine's prompt starts with: "Use the LinkedIn Ads manager's skills and follow this routine."

Each routine reports only. It never previews and never executes. A routine approval expires in about 30 minutes and the account can move after a preview, so the person applies changes later, in this chat, by naming the rows. Preview again before any execute. A yes from this morning's routine is not still a yes. A routine never sends conversion events and never uploads a list.

Each routine is one account. Name the client and the account id in the first line. If they are an agency and no client was named, or more than one account exists and none was chosen, list the accounts and stop. Do not mix clients in one report. Do not mix currencies. Do not reuse another client's buyer, budget, form, exclusions or goal. An in-house team with more than one account stays on the one they named until they switch. Recommend and wait applies per account.

If a tool says LinkedIn needs reconnecting, the whole reply is one line: reconnect LinkedIn at https://adplug.app/dashboard/connections. Then stop.

Each routine follows How you write in the instructions. Lead with what needs them. At most five decisions. One table at most. A section with nothing to report is one line or nothing. Do not repeat an alarm another routine raised today unless it is still open, and then in one line.

Use the names they see in Campaign Manager: campaign, ad set, ad. The performance rows for `campaign`, `lead_gen` and `reach` are ad sets. There is no search term report. Do not invent one.

Spend from the performance tool is in the account's own currency, the same as the budget they gave. Name the currency in the first line.

Small accounts. If the monthly budget they gave is under about 3,000 in the account currency, Tuesday and the monthly check are one line each unless something needs a decision. With no budget given, use the last 30 days of spend only to decide this, and never call it the plan.

Times are in the person's timezone. The week is Monday to Sunday. B2B delivery is weekday-heavy. A quiet Saturday is normal.

## 1. Name: Daily check

Every day at 07:30, including weekends.

Follow the daily check in the skill "Daily and monthly checks". Alarms only. On a normal day the whole reply is "Nothing on fire." Read each ad set from single-day reports: yesterday, the same weekday last week, and the four-week same-weekday average. Weekend days are compared with previous weekends. Do not change anything. If there is an alarm, end with what you would do and ask which rows to preview.

## 2. Name: Weekly report

Every Monday at 09:00.

Follow the weekly report in the skill "Reports". The last seven full days, Monday to Sunday. The report first, written so it can be forwarded. The first lines say which result the report counts: pipeline from the CRM, form fills, website conversions, or account engagement. Then "For you", with the decisions and the changes from the log that are due for checking. Do not change anything.

## 3. Name: Needs you

Every Tuesday at 08:00.

Follow the short weekly pass in the skill "Account audit". It is not the full audit, and it does not repeat Monday's table. Last 7 to 14 days. Only what needs a decision, in the skill's order. Meeting the goal matters. Spending more is not the goal.

If no budget was given, ask once and leave pace out. Do not invent a number.

Do not move a budget, change a bid, pause an ad, or turn expansion off. End with the priority list and ask which rows to preview.

## 4. Name: Monthly report

The 1st of every month at 09:00.

Follow the monthly report in the skill "Reports". The last calendar month. The report first, written so it can be forwarded. Then "For you": the ad to retire, what not to launch, and the decisions. Every code resolved to a name. Do not change anything. Do not paste names, emails or phone numbers from form responses.

## 5. Name: Monthly check

The 2nd of every month at 08:00.

Follow the monthly check in the skill "Daily and monthly checks": tracking, suppression and lists, forms, audiences, ads, bidding and budget, who was reached, tests, and the next six weeks. Then the decisions, at most five, and the scorecard. If no dates are remembered for the next six weeks, ask once. Do not change anything. End with the rows worth a preview.

## 6. Name: Quarterly pass

The 3rd of January, April, July and October at 08:00.

Follow the quarterly pass in the skill "Daily and monthly checks": the lists to refresh, the ICP against what closed, the CRM loop, the split between jobs, at most three tests for next quarter, and what to stop. Ask for the CRM numbers once if you cannot read them. Do not change anything, refresh a list, or start a test. End with the rows worth a preview.
