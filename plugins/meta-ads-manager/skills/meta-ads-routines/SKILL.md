---
name: meta-ads-routines
description: "Use when the person asks to set up the eight scheduled checks and reports, or to run one now, such as \"run the daily check\"."
---

# Meta Ads Manager routines

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## The eight routines

These are the eight routines. In Claude, create each one as a scheduled task. In Codex, create each one as a scheduled task. In Claude Code, tell the person they can run any routine by asking for it by name. Set them up one at a time, at the times below, in the person's timezone, and confirm each one once it's saved. Do not call Meta Ads tools while setting them up. Do not run them now. Each routine's prompt starts with: "Use the Meta Ads manager's skills and follow this routine."

Each routine reports only. It never previews and never executes. A routine approval expires in about 30 minutes, so the person applies changes later, in this chat, by naming the rows. You preview again at that moment and read the amounts back. A routine does not turn anything on, and never deletes.

Each routine is one ad account. Name the client and the ad account in the first line, with the currency. If they are an agency and no client was named, or more than one ad account exists and none was chosen, list the accounts and stop. Do not mix clients or currencies in one report. Do not reuse another client's offer, audience, budget or goal. An in-house team with more than one account stays on the one they named until they switch. Recommend and wait applies per account.

Each routine follows How you write in the instructions. Lead with what needs them. At most five decisions. One table at most. A section with nothing to report is one line or nothing. Do not repeat an alarm another routine raised today unless it is still open, and then in one line.

Small accounts. If the monthly budget they gave is under about 3,000 US dollars, or the same in their currency, Thursday and Friday are one line each unless something needs a decision. With no budget given, use the last 30 days' spend only to decide this, and never call it the plan.

Request limits. Every tool call counts. If `adplug_get_status` shows a limit of about 30 a month, only the Weekly report and the Monthly report should stay on. Say so once, in the first routine that runs, and list the others to pause. If fewer than about a quarter of the month's requests are left, skip the routine, say so in one line, and name which routines to pause.

Times are in the person's timezone. Performance dates follow the ad account.

## 1. Name: Daily check

Every day at 07:30, including weekends.

Follow the daily check in the skill "Daily and monthly checks". Alarms only: the account blocked or near its spend cap, spend far from the same weekday, a campaign that stopped, new disapprovals, a pixel or goal event gone quiet, month-to-date pace off the budget, an ad set knocked back into learning, and rolling seven-day frequency climbing on a live ad. On a normal day the whole reply is "Nothing on fire." Do not change anything. If there is an alarm, end with what you would do and ask which rows to preview later.

## 2. Name: Fatigue and placements

Every Monday at 08:00.

Follow "Creatives and fatigue" for the fatigue test and variety, then "Audiences and placements" for the placement breakdown. Last 7 days against the 7 days before.

Use the account you were told to use. If none was named and more than one ad account exists, list the accounts and stop.

The daily check already covered yesterday. If it raised an alarm this morning that is still open, repeat it in one line. Otherwise go straight to the ads.

Fatigue is frequency up, link click-through down and cost per result up, on the same ad, over seven days, with Meta's own fatigue flag beside it where it shows one. Link click-through is link clicks divided by impressions, not the all-clicks rate. Do not pause on frequency alone. Describe the next creative from the persona's angle and the page, with a different image or video. Recommend pausing a tired ad only when it costs more than the target per result. Do not create it and do not publish it. Name any ad set where every ad is the same idea.

Then placements. Waste is spend of about two to three times the target cost per result with none of the goal event, or leads their CRM shows do not qualify. A higher average cost alone is a test, not an exclusion. Call out Audience Network, rewarded video and the right-hand column when they spent. Recommend exclusions only where Meta may still take them, and say what is left where it will not.

Do not change anything. End with: reply with the row numbers and I will preview them.

## 3. Name: Weekly report

Every Monday at 09:00.

Follow the weekly report in the skill "Reports". The last seven full days. The report first, written so it can be forwarded. Then "For you", with the decisions and the changes from the log that are due for checking. Do not change anything.

## 4. Name: Needs you, Tuesday

Every Tuesday at 08:00.

Follow the Tuesday pass in the skill "Daily and monthly checks", and "Tracking, conversions and bidding" for the event, learning and the strategy.

Last 7 to 14 days. The event against the button or the form comes first. Then results against the target and the break-even number, ad sets in learning limited with the sum behind it, highest volume left on after they named a cost or a return, pace against the monthly budget they gave, Advantage+ audience on when the persona was meant to be a limit, a significant edit if results moved, and a missing customer exclusion when a list exists.

Meeting the goal matters. Spending more is not the goal. An ad set in learning after a significant edit does not get a pile of edits. Say so.

If no budget was given, ask once and leave pace out. Do not invent a number.

Do not move a budget, switch an event, or turn Advantage+ audience off. End with the priority list and ask which rows to preview.

## 5. Name: Lists and structure, Thursday

Every Thursday at 08:00.

Follow "Remarketing and suppression", then the overlap and Advantage+ sections of "Audiences and placements". This is the structure pass. It does not repeat Monday's fatigue table or Tuesday's pace.

In this order, only the lines that fail: prospecting that does not exclude customers or purchasers when a list exists, suppression and remarketing lists that are missing, empty or too small to deliver, a customer list not refreshed in months, two live ad sets competing for the same people, a campaign that lost its Advantage+ state by accident, too many ad sets for the budget to feed, and tests running from "Tests and changes" with their day count.

Recommend the lists with their windows, and where each goes. Do not create them, and do not attach them.

Do not change anything. End with the rows worth a preview.

## 6. Name: Ads and breakdowns, Friday

Every Friday at 08:00.

This is the ads, not a repeat of Monday's fatigue table or Tuesday's pace.

Three short sections. Skip a section that does not apply and say why, in one line.

Ads. Follow "Creatives and fatigue" for what to keep, what to retire, enhancements on that nobody chose, and the next ad to build from the persona's angle. Do not invent an offer. Do not create the ad.

Age. Follow "Audiences and placements". Use the demographic breakdown only if they set an age control. If Advantage+ audience is on, say an age maximum was only a suggestion, and do not recommend a bid change from that row. If they set no age control, one line.

Disapprovals. Enabled ads that are disapproved, with the reason Meta returns. On a large account, list them by status as well as the diagnose sweep. Skip ads still in review. If a catalogue exists, follow "Catalogue and shopping" for rejected or out-of-stock products, grouped by issue. A rejected product is a catalogue fix, not a bid change. If there is no catalogue, one line.

Do not change anything. End with the row numbers that are worth a preview.

## 7. Name: Monthly report

The 1st of every month at 09:00.

Follow the monthly report in the skill "Reports". The last calendar month. The report first, written so it can be forwarded. Then "For you". Do not change anything.

## 8. Name: Monthly check

The 2nd of every month at 08:00.

Follow the monthly check in the skill "Daily and monthly checks". The money first. Then learning and structure, creative, tracking, lists, placements, bidding, the log and tests, Meta's recommendations and the account's automated rules, competitor ads from "Competitor ads" only when competitors are on file for this account, and the next six weeks from "Seasonality and promotions". If no promotion dates are remembered for the next six weeks, ask once. Then the decisions, at most five, and the scorecard. Do not run the full audit. Do not change anything. End with the rows worth a preview.
