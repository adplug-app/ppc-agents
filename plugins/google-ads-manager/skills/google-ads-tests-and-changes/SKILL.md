---
name: google-ads-tests-and-changes
description: "Use after applying any change, when checking whether a past change worked, when undoing one, and when planning, running or reading a Google Ads experiment."
---

# Tests and changes

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Every applied change goes in the log. The weekly report reads the log. Use the test section when they want to try a bid strategy, a landing page, AI Max, broad match or another feature, or ask whether something "works".

## The change log

After every change you apply, remember for that account:

- the date
- what changed: the resource, the old value and the new value
- why, in one line
- what you expect: fewer wasted clicks, a lower CPA, more conversions
- the date to check it: two weeks for negatives and exclusions, four for structure, bidding, budgets and new ads, longer on a thin account

A batch of negatives is one entry, not forty.

## Did it work

On the check date, compare the same length of time before and after the change, on the part of the account the change touched. Read it against the KPI, after the measured lag.

Then compare with the rest of the account over the same dates. If everything moved, the season or the market moved, not your change.

Say it in one line with the numbers: "14 October, 38 negatives on Generic. Spend on those terms since: £0. Generic CPA £82 before, £71 after, on 41 and 44 conversions. Keep." When the numbers are too small, or two changes overlap, say "too early to tell" or "cannot separate the two", and set a new date.

A change that made things worse is a decision for them: undo, adjust, or give it more time. Do not undo it on your own.

## Undo

The log holds the old value. To undo, preview the reverse change, show both values, and wait for a yes. If the old value is not in the log, read `change_event` for the date and the field. If it is not there either, say you cannot see the old value. Do not guess it.

## When a test is the right tool

A test is for a change whose effect you cannot judge from the account's history: a new bid strategy, a different landing page, AI Max, broad match, or a new campaign type next to the old one.

New ad copy does not need an experiment. Two ads in the ad group already rotate, and Ads and copy reads them. A new negative does not need one either. The change log is enough.

## How to run one

1. One change, one hypothesis. "Maximise conversions with a target CPA of £70 will hold CPA and add 15% more conversions."
2. The success metric is the KPI: CPA, ROAS, qualified leads or profit. Not clicks.
3. The length: at least two to four weeks, plus the measured lag, and long enough for each side to get about 30 conversions as a working line. Say up front how long that will take at the current volume. If it is months, the account is too thin to test that change. Say so.
4. Use a Google Ads experiment where one fits, because it splits the traffic and the two sides do not bid against each other. AdPlug has `create_experiment`, `add_experiment_arms`, `schedule_experiment`, `promote_experiment` and `end_experiment`. Call `operation="help"` first, use a 50/50 split unless they want otherwise, and preview each step.
5. Before it starts: Google can apply an experiment's winner on its own. AdPlug cannot read or set that switch. Tell them to turn auto-apply off on the experiment's page in Google Ads, or to set it to 95% if they want it on. The default bar is lower than that.
6. While it runs: no other changes on those campaigns. Do not stop it early because the first week looks good or bad.
7. Remember the test: name, start date, hypothesis, metric, planned end date. The weekly report shows the day count.

An AI Max test is its own campaign either way: the trial side of an experiment, or a separate paused campaign. The experiment is the fairer read. Offer both. Do not switch AI Max on inside a live brand or generic campaign.

## Reading the result

At the planned end, compare the two sides on the KPI, with the conversions behind each number, and say whether Google's experiment report calls the difference significant. One line: "Trial CPA £64 against £71, on 41 and 38 conversions. Google marks it significant. Promote." If it is not significant, the answer is "not enough to call", not a winner.

Promote, end, or run it longer. Each is a change. Preview it, and wait for a yes. Put the result in the next monthly report.

## What you return

For a change: the log entry, and the check date. For a check: one line per change with the numbers and the verdict. For a test: the plan in seven lines, the auto-apply reminder, then the previews.
