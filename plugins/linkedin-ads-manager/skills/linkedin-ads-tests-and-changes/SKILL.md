---
name: linkedin-ads-tests-and-changes
description: "Use after applying any change, when checking whether a past change worked, when undoing one, and when planning, running or reading a test."
---

# Tests and changes

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Every applied change goes in the log. The weekly report reads the log. Use the test section when they want to try an audience, an offer, a format, a bid strategy, Accelerate or the Audience Network, or ask whether something "works".

## The change log

After every change you apply, remember for that account:

- the date
- what changed: the resource in Campaign Manager's names, the old value you read before the preview, and the new value
- why, in one line
- what you expect: a lower cost per lead, more form completions, fewer wasted impressions
- the date to check it: two weeks for a paused ad, an exclusion or a form edit, four weeks for a new ad set, a bid, a cost cap, a budget or a new audience, longer when leads are rare

A batch of exclusions added to five ad sets is one entry, not five. Two changes on the same ad set inside a fortnight cannot be told apart later. Say that before the second one.

## Did it work

On the check date, compare the same length of time before and after the change, on the ad sets it touched. Read it against the goal, with the latest days marked as still counting.

Then compare with the rest of the account over the same dates. If everything moved, the season or the market moved, not your change.

Say it in one line with the numbers: "14 October, cost cap on Finance leaders from none to $260. Cost per lead $310 before, $255 after, on 22 and 19 leads. Spend held. Keep." When the numbers are too small, or two changes overlap, say "too early to tell" or "cannot separate the two", and set a new date.

A change that made things worse is a decision for them: undo, adjust, or give it more time. Do not undo it on your own.

## Undo

The log holds the old value. To undo, read the current value again, preview the reverse change with both values side by side, and wait for a yes. For targeting, the undo is the whole old block, not a partial edit. If the old value is not in the log, say you cannot see it. Do not guess it.

## When a test is the right tool

A test is for a change whose effect you cannot judge from the account's history: a new audience, a different offer, a format, a bid strategy, Accelerate against Classic, the Audience Network.

A new ad beside the old ones in the same ad set does not need a formal test if the ad set rotates evenly and has the volume to read. A new exclusion does not need one either. The change log is enough.

## Campaign Manager's own A/B test

LinkedIn's A/B test is the fairer read for an audience, a creative or a placement, because it splits the audience so the same member sees only one side. It is built in Campaign Manager under Measure, Test, Create test. This tool cannot create it. You write the plan, they build it, and you read the two ad sets afterwards.

LinkedIn's rules: one variable, two ad sets created by the test, at least 14 days and at most 90, and both sides pause at the end. It cannot start the day it is created. LinkedIn recommends 21 days, at least $700 lifetime or $20 a day, an audience over 300 per side, and one ad per ad set unless the ads are the variable. It reports a winner on the test metric when the difference is significant.

## The manual test

When their test does not fit Campaign Manager's, run two draft ad sets in the same campaign:

1. One change, one hypothesis. "A four-field form will lift completion from 9% to 14% at the same cost per open."
2. Everything else the same: budget, bid, schedule, ads, form, exclusions.
3. No overlap. Split the audience so a member can only be in one side: two halves of a company list, two regions, or two seniority bands that do not overlap. Two ad sets on the same people bid against each other and both look worse.
4. For an ad test inside one ad set, set even rotation with `creative_selection` and keep the other ads unchanged.
5. The metric is the goal: cost per lead, form completion, cost per qualified lead. Not clicks.
6. The length: at least two to four weeks, and about 30 results per side as a working line. Say how long that takes at the current volume. If it is months, the account is too thin to test that change. Say so.
7. While it runs, no other changes on those ad sets. Do not stop it early because the first week looks good or bad.

Each ad set and each status change is a preview and a yes, as in New campaigns.

## Remember the test

Name, start date, hypothesis, metric, the two ad sets, planned end date. The weekly report shows the day count.

## Reading the result

At the planned end, compare the two sides on the goal, with the results behind each number. One line: "Four-field form: completion 15% against 9%, on 410 and 395 opens, cost per lead $198 against $287. Keep the short form." When Campaign Manager's test ran, say whether it called a winner. If the numbers are thin, the answer is "not enough to call", not a winner.

Keep the winner, end the loser, or run it longer. Each is a change. Preview it, and wait for a yes. Put the result in the next monthly report.

## What you return

For a change: the log entry and the check date. For a check: one line per change with the numbers and the verdict. For a test: the plan in seven lines, whether it is Campaign Manager's test or the manual one, then the previews.
