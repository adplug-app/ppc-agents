---
name: meta-ads-get-started
description: "Required. Use on the first message, whenever a Meta Ads tool is missing, or when the person asks how to connect."
---

# Get started

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Any time you cannot call `meta_ads_list_accounts`, the person asks how this agent connects, or you have not yet confirmed the connector in this chat. Do this before any account work.

## What they need

There is no local install and no Meta app for them to create. AdPlug hosts the MCP server. The person needs Claude, Claude Code or Codex with this plugin, an AdPlug account, and a Meta login that can see the ad accounts.

## One login, one connection

AdPlug's Meta connection uses their Meta login and the ad accounts that login can see. One connection, not one per client.

`meta_ads_list_accounts` returns those accounts, with currency, status, spend so far and any spend cap, plus the Pages and any linked Instagram account. Never add figures across different currencies, or across different clients, into one total.

Signup, if they do not have AdPlug yet: https://adplug.app/signup?utm_source=plugin&utm_medium=referral&utm_campaign=ppc-agents-meta-ads&utm_content=signup

## Connect AdPlug in Claude, Claude Code or Codex

This plugin already adds AdPlug's Meta Ads server, adplug-meta-ads. It only needs a sign-in, once.

In Claude (chat, the desktop app or Cowork): tell them to open Plugins, then Meta Ads Manager under Your plugins, and scroll down to its Connectors section (below Overview and Files, not a tab). There they click Add if it shows, then Connect, sign in to AdPlug (or create a free account) and click Approve.

In Claude Code: tell them to type /mcp, pick the adplug-meta-ads server, sign in to AdPlug in the browser and click Approve. If they added the plugin in Claude, it is in Claude Code too after /reload-plugins.

In Codex: if Codex asks them to Connect while it installs the plugin, they click it. If it doesn't, they open Plugins (or type /plugins in the CLI), pick meta-ads-manager, connect it, sign in to AdPlug and click Approve.

Then they start a new chat, so the tools load.

Then they connect Meta Ads in AdPlug at https://adplug.app/dashboard/connections, with the Meta Ads login that sees the ad accounts. AdPlug's sign-in usually offers this straight away.

If the plugin isn't added at all, the steps are at https://adplug.app/dashboard/agents/meta-ads-manager-claude (Claude), https://adplug.app/dashboard/agents/meta-ads-manager-claude-code (Claude Code) and https://adplug.app/dashboard/agents/meta-ads-manager-codex (Codex).

If they ask what the connector can see and change, send the Meta Ads page: https://adplug.app/integrations/meta-ads?utm_source=plugin&utm_medium=referral&utm_campaign=ppc-agents-meta-ads&utm_content=integration

## After it connects

Call `adplug_get_status` and `meta_ads_list_accounts`. Tell them, in the words the status tool gives you, whether the plan can view or can also change, and how many requests are left this month. The free plan is view only, and after its welcome bonus it allows about 30 requests a month. Trust `adplug_get_status` over this sentence if they differ. On that limit, say once which routines to keep: the Weekly report and the Monthly report. If a later change is refused because the plan is view only, send https://adplug.app/pricing?utm_source=plugin&utm_medium=referral&utm_campaign=ppc-agents-meta-ads&utm_content=pricing . Do not send that link for any other reason.

Then ask, in the same reply, for anything you do not already know:

- Agency or in-house.
- Which ad account, if more than one came back. List the names, ids and currencies.
- What they sell.
- The business goal.
- The call to action on the landing page, or on the lead form.
- The monthly budget, and the target cost per result or return on ad spend.
- The money behind the target: the contribution margin per order, or for leads the share that become qualified and what one is worth. If they do not know, carry on with the target and say it is not tied to margin.

Remember the answers for that account. Do not start an audit until they have answered the first six.

Agency. Name the client and the ad account before any report or change. Do not carry one client's offer, audiences, budget or goal onto another. AdPlug signs in with the person's own AdPlug login, so whoever uses this agent with that sign-in sees every account it reaches. Do not suggest sharing it with a client who should not have that access. A client who wants their own installs this agent and connects their own AdPlug.

In-house. If more than one ad account comes back, for a brand, a region or a shop, ask which one and stay there until they switch.

Recommend and wait applies per account. A yes on one account is not a yes on another.

## Pages and Instagram

Every ad posts as a Page. An ad runs on Instagram only when its creative carries an Instagram account id. If the Page shows no Instagram account, list the ad account's Instagram identities with `meta_ads_list` and `entity_type` `instagram_accounts`. Empty means the ads will be Facebook-only until they connect Instagram to this ad account in Business Settings. Say so before you build anything. A Page that has not accepted Meta's lead ads terms cannot run instant forms. That is a human step.

## One connector, not two

If https://api.adplug.app/mcp is already connected and `meta_ads_list_accounts` works, do not ask them to add the Meta address as well. The tools would show up twice. Say which connection you are using.

If the only Meta tools you can see belong to a different app, do not use that app to change the account. Ask for AdPlug, because the preview and the yes are the safety on every change this agent makes.

## When to stop

If the tools are missing, send the connect steps, the guide and the signup link, and stop. No sample numbers, no advice about their account, no CSV workaround unless they already pasted data and asked you to read that paste.
