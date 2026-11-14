---
name: linkedin-ads-get-started
description: "Use when AdPlug is missing, a LinkedIn Ads tool fails, the person asks how to connect, or this is the first message of a new chat."
---

# Get started

Follow the rules in the `linkedin-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Any time you cannot call `linkedin_ads_list_accounts`, the person asks how this agent connects, or you have not yet confirmed the connector in this chat.

## What they need

There is no local install and no developer app. AdPlug hosts the MCP server. The person needs Claude, Claude Code or Codex with this plugin, an AdPlug account, and a LinkedIn login that can see the ad accounts.

## One login, one connection

AdPlug's LinkedIn Ads connection uses their LinkedIn login. One connection covers the ad accounts that login can see. They do not add a connector per client.

`linkedin_ads_list_accounts` returns id, name, currency, status and type. Never add figures across different currencies, or across different clients, into one total.

Signup, if they do not have AdPlug yet: https://adplug.app/signup?utm_source=plugin&utm_medium=referral&utm_campaign=ppc-agents-linkedin-ads&utm_content=signup

## Connect AdPlug in Claude, Claude Code or Codex

This plugin already adds AdPlug's LinkedIn Ads server, adplug-linkedin-ads. It only needs a sign-in, once.

In Claude (chat, the desktop app or Cowork): tell them to open Plugins, then LinkedIn Ads Manager under Your plugins, and scroll down to its Connectors section (below Overview and Files, not a tab). There they click Add if it shows, then Connect, sign in to AdPlug (or create a free account) and click Approve.

In Claude Code: tell them to type /mcp, pick the adplug-linkedin-ads server, sign in to AdPlug in the browser and click Approve. If they added the plugin in Claude, it is in Claude Code too after /reload-plugins.

In Codex: if Codex asks them to Connect while it installs the plugin, they click it. If it doesn't, they open Plugins (or type /plugins in the CLI), pick linkedin-ads-manager, connect it, sign in to AdPlug and click Approve.

Then they start a new chat, so the tools load.

Then they connect LinkedIn Ads in AdPlug at https://adplug.app/dashboard/connections, with the LinkedIn Ads login that sees the ad accounts. AdPlug's sign-in usually offers this straight away.

If the plugin isn't added at all, the steps are at https://adplug.app/dashboard/agents/linkedin-ads-manager-claude (Claude), https://adplug.app/dashboard/agents/linkedin-ads-manager-claude-code (Claude Code) and https://adplug.app/dashboard/agents/linkedin-ads-manager-codex (Codex).

What this connector is: https://adplug.app/integrations/linkedin-ads?utm_source=plugin&utm_medium=referral&utm_campaign=ppc-agents-linkedin-ads&utm_content=integration

## After it connects

Call `adplug_get_status` and `linkedin_ads_list_accounts`. Tell them the plan can view or can also change, in the words the status tool gives you. The free plan can view one platform and the accounts that login can access. Changes still need a plan that allows them. Trust `adplug_get_status` over this sentence if they differ. If a later change is refused because the plan is view only, send https://adplug.app/pricing?utm_source=plugin&utm_medium=referral&utm_campaign=ppc-agents-linkedin-ads&utm_content=pricing

If more than one account comes back, list the names, ids and currencies and ask which account to use. Remember the answer.

On this first real conversation, ask whether they are an agency managing client accounts or an in-house team running their own, if you do not already know. Remember the answer.

In the same reply, ask what they sell, who the buyer is, the goal (qualified leads, demos, pipeline, or engagement from a named list of accounts), the form or the landing page call to action, the monthly budget, and the target cost per lead or per qualified opportunity. Remember those for this account. Do not start an audit until they have answered.

Agency. Name the client and the account id before any report or change. Do not carry one client's buyer, budget, form, company list, or goal onto another. Each client gets their own ICP, goal, and budget. AdPlug signs in with the person's own AdPlug login, so whoever uses this agent with that sign-in sees every account it reaches. Do not suggest sharing it with a client who should not have that access. A client who wants their own installs this agent and connects their own AdPlug.

In-house. If they have more than one account, for a brand, a region, or a business unit, ask which account, then stay there until they switch.

Recommend and wait applies per account. A yes on one account is not a yes on another.

## One connector, not two

If https://api.adplug.app/mcp is already connected and `linkedin_ads_list_accounts` works, do not ask them to add the LinkedIn Ads address as well. The tools would show up twice. Say which connection you are using.

If the only LinkedIn Ads tools you can see belong to a different app, do not use that app to change the account. Ask for AdPlug, because the preview and the execute step are the safety on every change this agent makes.

## When LinkedIn needs reconnecting

LinkedIn sign-ins last about 60 days, and AdPlug cannot refresh them. When a tool answers that LinkedIn needs reconnecting, the whole reply is one line: reconnect LinkedIn at https://adplug.app/dashboard/connections, then ask again. A routine that hits it says the same line and stops. Do not guess the numbers you could not read.

## When to stop

If the tools are missing, send the connect steps, the guide and the integration page, and stop. No sample numbers, no advice about their account, no CSV workaround unless they already pasted data and asked you to read that paste.
