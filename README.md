# PPC agents by AdPlug: Google Ads, Meta Ads and LinkedIn Ads managers for Claude, Codex and ChatGPT

Three AI ad account managers, one each for Google Ads, Meta Ads and LinkedIn Ads. Each one audits the account, runs daily, weekly and monthly checks, writes the reports, and changes only what you approve.

They're plugins for Claude (chat, the desktop app and Cowork), Claude Code and Codex. ChatGPT and OpenAI dots use the same managers as one file. Each plugin brings AdPlug's server for its platform, so there's no address to paste. You just sign in to AdPlug.

Step-by-step pages for every app, with copy buttons, are at [adplug.app/dashboard/agents](https://adplug.app/dashboard/agents) (sign in to AdPlug to open them).

Each manager has two parts. **AdPlug** safely connects your ad account to the AI app. **The manager** is a set of instructions (skills) the AI follows.

The method is Daniel Popa's. He founded AdPlug, has spent 12 years in PPC and has managed more than $100M in ad spend. It's the same method behind AdPlug's Grok Bot templates, adapted for each app. Built for PPC specialists, agencies and in-house teams.

## What the managers do

- **First chat:** checks AdPlug is connected, and gives you the steps if it isn't. Then it asks whether you're an agency or in-house, which account, what you sell, the result that counts, and the budget and target.
- **Jobs you ask for:** an account audit, wasted spend found and the fix proposed, new campaigns researched and built paused (as drafts on LinkedIn), ads written within each platform's limits, and reports written so you can forward them.
- **Routines:** a daily check at 07:30 that's alarms only (on a normal day the whole reply is "Nothing on fire."), a weekly report on Monday, a short "Needs you" list on Tuesday, a monthly report on the 1st and a month-end check on the 2nd. Each platform adds its own passes, such as search terms on Google Ads, tired ads on Meta and a quarterly pass on LinkedIn. Times are in your time zone.
- **Changes:** a preview first, then your yes to that change, in the chat. [How changes are kept safe](#how-changes-are-kept-safe) has the detail.

Where the routines run:

- **Claude:** scheduled tasks run them in the cloud, with the plugin's AdPlug connection.
- **Claude Code:** ask for one by name, like "run the daily check". For a schedule, add the same plugin in Claude.
- **Codex:** scheduled tasks in the ChatGPT desktop app run them.
- **ChatGPT:** ask it to set them up as scheduled tasks, with each routine's instructions copied into its task (a task can't always read the project's files). Read the first report to check the task reached AdPlug.
- **OpenAI dot:** it sets them up once you've answered its questions, runs them on schedule and posts each report in its chat.

Every run uses some of your AdPlug plan's monthly requests, so only keep the routines you'll read.

## What's inside

| Folder | What it is |
|---|---|
| `plugins/google-ads-manager/` | Google Ads Manager: 15 skills, the rules they follow, the nine routines, and AdPlug's Google Ads server |
| `plugins/meta-ads-manager/` | Meta Ads Manager: 15 skills, the rules they follow, the eight routines, and AdPlug's Meta Ads server |
| `plugins/linkedin-ads-manager/` | LinkedIn Ads Manager: 13 skills, the funnel strategy, the rules they follow, the six routines, and AdPlug's LinkedIn Ads server |
| `chatgpt/` | Each manager as one Markdown file, for a ChatGPT project or an OpenAI dot |
| `claude/` | Each manager as one skill (a .zip) to upload in Claude, if you'd rather not add the plugin |
| `.claude-plugin/marketplace.json` | The marketplace Claude and Claude Code read |
| `.agents/plugins/marketplace.json` | The marketplace Codex reads |

Inside each plugin, `skills/` has one folder per skill. `.mcp.json` (for Claude and Claude Code) and `mcp.json` (for Codex) hold the address of AdPlug's server for that platform: `https://api.adplug.app/mcp/google-ads`, `https://api.adplug.app/mcp/meta-ads` or `https://api.adplug.app/mcp/linkedin-ads`. `.claude-plugin/plugin.json` and `plugin.json` describe the plugin. There's no code. It's instructions, plus the address of one remote server.

<details>
<summary><strong>Google Ads Manager</strong>: 15 skills and 9 routines</summary>

| Skill | What it does |
|---|---|
| `connect-adplug-google-ads` | Checks AdPlug is connected, and gives you the steps if it isn't. One Google login covers every ad account it can see. |
| `icp-for-google-ads` | Reads your site and its buttons, then the persona, themes and negatives. |
| `google-ads-how-to-run-the-account` | Which campaign types fit: SaaS, ecommerce, lead gen, small budgets. |
| `google-ads-new-campaigns` | Research and budget maths. Everything built paused. |
| `google-ads-search-build` | Search Partners and the Display Network off, AI Max off by default, then the brand campaign, themes and sitelinks. |
| `google-ads-ads-and-copy` | Which ad wins on conversions. New copy written paused. |
| `google-ads-audiences-and-remarketing` | Suppression and remarketing lists, at several lengths. |
| `google-ads-search-terms-and-negatives` | Waste grouped, n-grams, every negative checked against your keywords. |
| `google-ads-placements` | Demand Gen first, then Performance Max. |
| `google-ads-shopping-products` | Disapprovals by issue, and products spending with no return. |
| `google-ads-account-audit` | The full pass, with a headline and a scorecard. |
| `google-ads-daily-and-monthly-checks` | Alarms every morning. The month-end pass on the 2nd. |
| `google-ads-conversions-and-bidding` | The right conversion, tag health, Smart Bidding status. |
| `google-ads-reports` | Weekly and monthly, written so you can forward them. |
| `google-ads-tests-and-changes` | A log of every change, a date to check it, and fair experiments. |
| `google-ads-manager` | The rules every skill follows, starting with a preview and your yes before any change. |
| `google-ads-routines` | Sets up the nine routines, or runs one now. |

| When | Routine | What it covers |
|---|---|---|
| Daily, 07:30 | Daily check | Spend, a stopped campaign, a quiet tag, the spending limit, new disapprovals. |
| Mon, 08:00 | Search terms | Waste grouped, negatives proposed. |
| Mon, 09:00 | Weekly report | Written to forward. |
| Tue, 08:00 | Needs you | Only what needs a decision, in priority order. Pace, Smart Bidding, auto-apply. |
| Wed, 08:00 | Search terms, second pass | What Monday missed, plus n-grams across a hundred cheap searches. |
| Thu, 08:00 | Search build | Structure and sitelinks, plus converting searches that aren't keywords yet. |
| Fri, 08:00 | Placements and products | Placements, disapprovals, negatives still waiting. |
| 1st, 09:00 | Monthly report | Last month, and whether last month's changes worked. |
| 2nd, 08:00 | Monthly check | Quality Score, targets, tracking, landing pages, audiences. |

</details>

<details>
<summary><strong>Meta Ads Manager</strong>: 15 skills and 8 routines</summary>

| Skill | What it does |
|---|---|
| `meta-ads-get-started` | Checks AdPlug is connected, and gives you the steps if it isn't. One Meta login covers every ad account it can see. |
| `meta-ads-icp-for-meta` | Reads the page or the lead form, then one angle per persona. |
| `meta-ads-how-to-run-the-account` | Which campaign fits: Advantage+ sales, leads, remarketing, small budgets. |
| `meta-ads-new-campaigns` | The checks, budget maths and names. Everything built paused. |
| `meta-ads-catalogue-and-shopping` | Only with a catalogue. A rejected product is a catalogue fix. |
| `meta-ads-remarketing-and-suppression` | Customer exclusions and remarketing lists, with their windows. |
| `meta-ads-creatives-and-fatigue` | Tired ads on rolling 7 days. New ads written paused. |
| `meta-ads-audiences-and-placements` | Advantage+ audience, overlap and placement waste. |
| `meta-ads-competitor-ads` | Their live ads in Meta's Ad Library, and the angles none of them use. |
| `meta-ads-daily-and-monthly-checks` | Alarms every morning. The month-end pass on the 2nd. |
| `meta-ads-account-audit` | The full pass, with a headline and a scorecard. |
| `meta-ads-tracking-conversions-and-bidding` | Checks the event matches the button. Pixel, Conversions API, learning. |
| `meta-ads-reports` | Weekly and monthly, written so you can forward them. |
| `meta-ads-tests-and-changes` | A log of every change, a date to check it, fair tests. |
| `meta-ads-seasonality-and-promotions` | Sales, launches and Black Friday, planned ahead. |
| `meta-ads-manager` | The rules every skill follows, starting with a preview and your yes before any change. |
| `meta-ads-routines` | Sets up the eight routines, or runs one now. |

| When | Routine | What it covers |
|---|---|---|
| Daily, 07:30 | Daily check | A stopped campaign, a quiet pixel, the spend cap, disapprovals. |
| Mon, 08:00 | Fatigue and placements | Tired ads and placement waste. |
| Mon, 09:00 | Weekly report | Written to forward. |
| Tue, 08:00 | Needs you | The event, results against target and break-even, learning, pace. |
| Thu, 08:00 | Lists and structure | Customer exclusions, remarketing windows, overlap. |
| Fri, 08:00 | Ads and breakdowns | Ads to keep and retire, disapprovals, catalogue problems. |
| 1st, 09:00 | Monthly report | Last month, written for a client or a boss. |
| 2nd, 08:00 | Monthly check | The month-end pass, the next six weeks, and competitor ads once you've named them. |

</details>

<details>
<summary><strong>LinkedIn Ads Manager</strong>: 13 skills, the funnel strategy and 6 routines</summary>

| Skill | What it does |
|---|---|
| `linkedin-ads-get-started` | Checks AdPlug is connected, and gives you the steps if it isn't. One LinkedIn login covers every ad account it can see. |
| `linkedin-ads-icp-for-linkedin` | Reads the page or the form, then who pays, who's targeted by title, and what to exclude. |
| `linkedin-ads-how-to-run-the-account` | The goal and the ICP first, then the funnel layers. |
| `linkedin-ads-new-campaigns` | The checks, budget maths and names. Everything built as a draft. |
| `linkedin-ads-audiences` | Who an ad set targets, the forecast before launch, and company lists. Expansion stays off unless you give a reason. |
| `linkedin-ads-creatives` | Writing, reviewing and retiring ads, within LinkedIn's limits. |
| `linkedin-ads-lead-forms-and-conversions` | Forms, page conversions and the Insight Tag, and when they go quiet. |
| `linkedin-ads-suppression-and-retargeting` | Customers, open deals, staff and competitors kept out of prospecting. Retargeting pools and their windows. |
| `linkedin-ads-bidding-and-budget` | Bids, cost caps, budgets and pace. A bid or a budget moves about 20% at a time. |
| `linkedin-ads-daily-and-monthly-checks` | Alarms every morning, the month-end pass, the quarterly pass. |
| `linkedin-ads-account-audit` | The full pass, and the Tuesday short pass. |
| `linkedin-ads-reports` | Weekly and monthly, written so you can forward them. |
| `linkedin-ads-tests-and-changes` | A log of every change, and whether it worked. |
| `linkedin-ads-funnel-strategy` | How a B2B account is built, in layers. The background for every plan, build, check and report. |
| `linkedin-ads-manager` | The rules every skill follows, starting with a preview and your yes before any change. |
| `linkedin-ads-routines` | Sets up the six routines, or runs one now. |

| When | Routine | What it covers |
|---|---|---|
| Daily, 07:30 | Daily check | Alarms only. On a normal day the whole reply is "Nothing on fire." |
| Mon, 09:00 | Weekly report | Written to forward. It opens by saying which result it counts. |
| Tue, 08:00 | Needs you | Only what needs a decision, five lines at most. It doesn't repeat Monday's report. |
| 1st, 09:00 | Monthly report | The goal against the target, where the money went, and which seniorities and job functions it reached. |
| 2nd, 08:00 | Monthly check | Tracking, suppression, forms, audiences, ads, bidding and tests. |
| Quarterly, 3rd | Quarterly pass | Lists due a refresh, the ICP against what closed, and up to three tests for next quarter. |

</details>

## What you need

- **An AdPlug account.** Create one free at [adplug.app](https://adplug.app), then connect your ad platform in [Connections](https://adplug.app/dashboard/connections). The free plan connects one ad platform, has a monthly request limit, and previews changes but can't apply them. Applying changes needs a paid plan ([adplug.app/pricing](https://adplug.app/pricing)).
- **One of these AI apps:** Claude, Claude Code, Codex in the ChatGPT desktop app or the Codex CLI, ChatGPT, or an OpenAI dot.

## Install

The examples use Google Ads Manager. For the others, swap `google-ads-manager` for `meta-ads-manager` or `linkedin-ads-manager`, and Google Ads for Meta Ads or LinkedIn Ads.

Every app except the OpenAI dot ends the same way: start a new chat and send this.

> Be my Google Ads Manager. Check AdPlug is connected, then ask me what you need to know.

### Claude (chat, the desktop app and Cowork)

1. In Claude, open **Plugins**, click **Add**, then **Add marketplace**, and paste `adplug-app/ppc-agents`.
2. Find **Google Ads Manager** on the Plugins page and click **Add**.
3. Open **Google Ads Manager** under **Your plugins** and scroll down to **Connectors**. Click **Add** if you see it, then **Connect**. Sign in to AdPlug, or create a free account, and click **Approve**.
4. Start a new chat and send the first message above.

Skills need **Create and edit files** switched on, under Settings, then Capabilities. On a Team or Enterprise plan, an Owner may have to turn on plugins, or add the connector, for the organisation first. You still sign in with your own AdPlug account.

To run the routines on a schedule, open **Scheduled**, then **New task**, then **Create with Claude**, and ask it to set up the routines.

**Or upload it as one skill.** Download `claude/google-ads-manager.zip`. In Claude, open **Plugins**, click **Add**, then **Upload plugin** (it takes skills too), and pick the file. Then add AdPlug as a custom connector: **Plugins**, then **Add**, then **Add custom connector**, with the name `AdPlug Google Ads` and the URL `https://api.adplug.app/mcp/google-ads`. Click **Continue**, leave the sign-in settings as they are and click **Add**, then **Connect**. Sign in to AdPlug and click **Approve**.

### Claude Code

Paste this into Claude Code, and say yes if it asks to run the commands:

> Install the google-ads-manager plugin: run claude plugin marketplace add adplug-app/ppc-agents, then claude plugin install google-ads-manager@adplug. Then tell me what to type to load it.

When it's done, type `/reload-plugins`. Then type `/mcp`, pick the server ending in `adplug-google-ads`, sign in to AdPlug in your browser and click **Approve**.

Or type these yourself in Claude Code, one line at a time, and pick **Install for you**:

```
/plugin marketplace add adplug-app/ppc-agents
/plugin install google-ads-manager@adplug
```

Added the plugin in Claude already? It's in Claude Code too when you're signed in to the same account: type `/reload-plugins`.

### Codex

Open Codex, in the ChatGPT desktop app or the Codex CLI, and paste this. If Codex asks to use the internet or run a command, say yes.

> Install the Google Ads Manager plugin from github.com/adplug-app/ppc-agents: run codex plugin marketplace add adplug-app/ppc-agents, then codex plugin add google-ads-manager@adplug. Tell me when it's installed.

If Codex asks you to **Connect** while it installs, click it. If it doesn't, open **Plugins** (type `/plugins` in the CLI), pick `google-ads-manager` and connect it there. Sign in to AdPlug and click **Approve**, then open a new chat, so the manager's tools load.

Or run the two commands yourself in a terminal:

```bash
codex plugin marketplace add adplug-app/ppc-agents
codex plugin add google-ads-manager@adplug
```

Codex's extension for code editors doesn't take plugins, so use the desktop app or the CLI.

### ChatGPT

1. Open [AdPlug in ChatGPT's plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6a57d43e98c881919c69955b71824f6b) and click **Install plugin**, then **Connect** if ChatGPT asks. Sign in to AdPlug, or create a free account, and click **Approve**. That one plugin covers all three ad platforms, plus Microsoft Ads and Reddit Ads.
2. In **Settings**, open **Plugins**, then **AdPlug**, then **Permission**, and choose **Allow read-only tools**. Reports and previews run without asking, and ChatGPT asks you before every change.
3. Download [`chatgpt/google-ads-manager.md`](chatgpt/google-ads-manager.md) (on GitHub, click **Download raw file**). In ChatGPT's sidebar, click **New project**, name it Google Ads Manager and add the file to the project's **Sources**. Then click **•••**, open **Project settings** and paste:

   > Before any work, read google-ads-manager.md in this project's sources and follow it. Use the AdPlug plugin for Google Ads.

4. Open a new chat in the project, type **@**, pick **AdPlug** and send the first message above.

### OpenAI dot

1. Do steps 1 and 2 from ChatGPT above.
2. Open your dot at [chatgpt.com/dots](https://chatgpt.com/dots). In its profile, open **Customize**, then **Plugins**, and check AdPlug is switched on.
3. Download [`chatgpt/google-ads-manager.md`](chatgpt/google-ads-manager.md), attach it in your dot's chat with **+**, and send it with this message:

   > Read this file, save it on your cloud computer as "Google Ads Manager.md" and keep it as your standing instructions. Check AdPlug is connected, then ask me what you need to know. Once I've answered, set up the routines it describes, in my time zone, with each report posted here. Confirm each one once it's saved.

There's no separate first message here. Your dot replies in the same chat.

Dots are rolling out on ChatGPT Pro outside the EEA, the UK and Switzerland, and on Business Premium and Enterprise.

Using Hermes Agent? One plugin covers Google, Meta, LinkedIn, Microsoft and Reddit Ads: [adplug-app/adplug-hermes-plugin](https://github.com/adplug-app/adplug-hermes-plugin).

## How changes are kept safe

- **A preview, then your yes.** The manager shows each change with the current value and the new one, then waits for your yes to that change in the chat. "Looks fine" isn't a yes, and neither is a yes from another agent.
- **Routines only read.** They report and stop. They never apply a change, so you apply one later, in the chat, by naming its row.
- **New work starts switched off.** New campaigns, ad groups, ad sets and ads are created paused on Google Ads and Meta, and as drafts on LinkedIn. Turning one on is its own preview and its own yes.
- **AdPlug checks Google Ads changes too.** AdPlug's server refuses a Google Ads change that wasn't previewed first: applying it needs the preview's ID, within 15 minutes. On Meta and LinkedIn, the preview is the manager's rule.
- **Big jumps come with a warning.** A budget or target moved by more than about 20% in one go gets a note in the preview and an offer to do it in two steps. It's still your call.
- **ChatGPT can ask as well.** With **Allow read-only tools**, ChatGPT asks you before any change, as a second lock.
- **Plan and team limits.** On AdPlug's free plan, changes can't be applied at all. On Max and Agency, the team owner can set each person to View only, per platform.
- **A record.** Every call is logged on the [usage page](https://adplug.app/dashboard/usage) of your AdPlug dashboard.

## Your data

- Every tool call goes to AdPlug's server for that platform: `https://api.adplug.app/mcp/google-ads`, `https://api.adplug.app/mcp/meta-ads` or `https://api.adplug.app/mcp/linkedin-ads`.
- Reports are fetched live from the ad platform and not kept.
- AdPlug logs which tool was called, for which ad account and when, for your usage page.
- A Google Ads change preview is kept so the change can be applied within 15 minutes, then deleted within two days.
- Your Google, Meta and LinkedIn sign-ins are stored encrypted on AdPlug's servers and never pass through the AI app.
- What the tools return goes to the AI app you use, under that app's own terms.
- There's no code in this repo, and no telemetry.

Privacy policy: [adplug.app/privacy](https://adplug.app/privacy) · Terms: [adplug.app/terms](https://adplug.app/terms)

## Support

Email [support@adplug.app](mailto:support@adplug.app) and Daniel Popa, AdPlug's founder, will reply.


## Licence

MIT. See [LICENSE](LICENSE). Published by MEANDATA IT SRL, trading as AdPlug.
