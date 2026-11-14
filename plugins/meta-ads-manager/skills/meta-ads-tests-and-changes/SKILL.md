---
name: meta-ads-tests-and-changes
description: "Use after applying any change, when checking whether a past change worked, when undoing one, and when planning, running or reading a Meta A/B test."
---

# Tests and changes

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Every applied change goes in the log. The weekly report reads the log. Use the test section when they want to try a structure, an audience setting, a bid strategy, a landing page or a new campaign type, or ask whether something "works".

## The change log

After every change you apply, remember for that account:

- the date
- what changed: the campaign, ad set or ad, the old value and the new value
- why, in one line
- what you expect: a lower cost per result, more results at the same cost, less waste
- the date to check it: two weeks for a pause, an exclusion or a tired ad, four weeks for structure, bidding, budgets and new ads, longer on a thin account

A batch of new ads, or a set of budget moves made in one go, is one entry, not twenty.

Changes someone else made are in the activity log, `meta_ads_list` with `entity_type` `activity_logs`. Read it before the weekly report, and when results move with no change of yours behind them.

## Did it work

On the check date, compare the same length of time before and after the change, on the part of the account the change touched. Read it on the goal event, after the last few days have finished counting. A change that restarted learning gets its read after the ad set leaves learning, or after two weeks.

Then compare with the rest of the account over the same dates. If everything moved, the season or the market moved, not your change.

Say it in one line with the numbers: "21 October, two tired videos paused, three new ones added in Prospecting. Cost per sale £38 before, £31 after, on 44 and 51 sales. Keep." When the numbers are too small, or two changes overlap, say "too early to tell" or "cannot separate the two", and set a new date.

A change that made things worse is a decision for them: undo, adjust, or give it more time. Do not undo it on your own.

## Undo

The log holds the old value. To undo, preview the reverse change, show both values, and wait for a yes. If the old value is not in the log, read the activity log for the date and the field. If it is not there either, say you cannot see the old value. Do not guess it.

Some changes cannot be reversed: a deleted item, a creative swap that sent an ad back through review, or an event change that restarted learning. Turning the old setting back on is a new change with its own learning period. Say so.

## When a test is the right tool

A test is for a change whose effect you cannot judge from the account's history: Advantage+ audience on against off, a campaign budget against ad set budgets, a cost goal against highest volume, a different landing page, or a new campaign type next to the old one.

New ads do not need this kind of test. Meta's creative testing in Ads Manager, or new ads side by side in the main ad set, is the method in Creatives and fatigue. A new exclusion does not need one either. The change log is enough.

## How to run one

1. One change, one hypothesis. "Advantage+ audience on will cost no more per sale and add 15% more sales."
2. The success metric is the goal: cost per sale, return against break-even, qualified leads, or profit. Not clicks.
3. The length: at least two weeks, and long enough for each side to get about 50 results a week, or 100 in total as a working line. Say up front how long that will take at the current volume. If it is months, the account is too thin to test that change. Say so.
4. Build the two sides as two campaigns, or two ad sets, identical except for the one change, each paused, with the same creatives copied across with `copy_adset` or `copy_campaign`.
5. Split the audience so the same person does not see both sides: preview `create_ab_test` with the two campaign or ad set ids. Meta divides the audience evenly. Call `operation="help"` first. Meta does not dry-run it, so the preview is AdPlug's check only. If it fails on execute, say what failed and offer the manual fallback: the two sides side by side, with each one's audience excluding the other where the settings allow, and a note that the read is less clean.
6. While it runs: no other changes on those campaigns. Do not stop it early because the first week looks good or bad.
7. Remember the test: name, start date, hypothesis, metric, planned end date. The weekly report shows the day count.

There is no conversion lift test in this connector. A lift study, which measures sales that would not have happened without the ads, needs Meta's own tools and usually a Meta rep or a large budget. Say that if they ask whether Meta "really" works.

## Reading the result

At the planned end, compare the two sides on the goal, with the results behind each number. Meta's experiment report, in Ads Manager under Experiments, gives a confidence figure. This connector cannot read it, so ask them for it. One line: "Advantage+ audience on: £29 a sale against £34, on 112 and 98 sales. Meta's report gives it 85% confidence. Keep it on." If the difference is small or the volume thin, the answer is "not enough to call", not a winner.

Keep, stop, or run it longer. Each is a change. Preview it, and wait for a yes. Pause the losing side, never delete it. Put the result in the next monthly report.

## Automated rules

Meta checks a rule every 30 minutes and acts without asking. So a rule is a standing change. First list the account's rules with `meta_ads_list` and `entity_type` `rules`, so a new one does not fight an old one.

Offer only two kinds:

- Stop-loss: pause an ad that is spending with nothing to show. Working line, not Meta's rule: pause an ad when it has spent more than twice the target cost per result and has zero results over the last 7 days.
- Notify only: a message when a number crosses a line. Nothing changes.

Do not offer a rule that raises a budget, changes a bid or turns anything back on. It would skip the 20% step and the yes in this chat.

How AdPlug builds them:

- One condition per rule. The stop-loss above needs two, spend and zero results. Build that one in Ads Manager, under Automated rules, and give them the settings in words. Through AdPlug, offer a notify-only rule on spend over the last 7 days. Meta shows rule alerts in Ads Manager notifications. Do not promise an email.
- Name the ads or ad sets it watches. Without them, it watches every one in the account.
- On a leads account, never use the cost trigger. AdPlug's cost per result trigger watches Meta's cost per purchase, so the rule would watch purchases, not leads. Use spend or results.
- Meta restricts cost and click-rate conditions on some accounts. If Meta refuses one, use spend, impressions, clicks or results instead.
- It is created disabled. Enabling it is its own yes, previewed. To stop one, disable it. Do not delete it.

Log the rule in the change log when it is created and again when it is enabled, with what it watches and the line it acts on.

## What you return

For a change: the log entry, and the check date. For a check: one line per change with the numbers and the verdict. For a test: the plan in seven lines, the length at current volume, then the previews. For a rule: what it watches, the line, the action, and where it is built, created disabled.
