---
name: google-ads-shopping-products
description: "Use when checking product disapprovals, limited products, or Shopping and Performance Max product waste."
---

# Shopping products

Follow the rules in the `google-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

The Friday routine, a feed question, disapprovals, or a Shopping or Performance Max ecommerce account. If no enabled campaign is `SHOPPING` or `PERFORMANCE_MAX`, say there is no product campaign to check and stop. Demand Gen only counts here when it is serving products. If you are unsure, check the channel type first.

Shopping is the feed and the negatives. An audience list does not clear a disapproval. That judgement is in Audiences and remarketing.

## Eligibility and disapprovals

Confirm fields with `google_ads_reporting_view_doc` on `shopping_product`, then query account scope (no campaign filter):

`shopping_product.item_id`, `shopping_product.title`, `shopping_product.status`, `shopping_product.availability`, `shopping_product.issues`, `shopping_product.channel`, `shopping_product.feed_label`, `shopping_product.target_countries`.

Limit the rows to `NOT_ELIGIBLE` and `ELIGIBLE_LIMITED`. If selecting `issues` fails, run again without it and say the issue text did not return.

Status and issues can lag up to 24 hours. Say that next to the table.

Group the rows by the issue, not as a dump of every SKU. For each group: how many products, one example title and item id, and what the merchant has to fix. Typical causes, which you name only when the issue text supports them: missing identifier or GTIN, image, price mismatch, availability, policy, missing tax or shipping, a feed label or language that the campaign does not include.

A disapproval is a Merchant Center fix. Do not "solve" it with a keyword negative, a bid, or a budget change. Do not tell them a Google Ads mutation will clear a feed issue.

`ELIGIBLE_LIMITED` still needs a line. Limited is serving with a restriction, and it is easy to miss because the product is not fully disapproved.

## Products that can show, and still waste money

`google_ads_campaign_performance` with `level` product, last 30 days.

Separate three lists:

- Spend and no conversions. That is a bidding or a product decision. Propose an exclusion only if they want that item out. It is not a disapproval.
- Eligible products with no impressions. That is coverage: bid, priority, the listing group, or the campaign filter. Look before you call it a feed fault.
- Out of stock, or unavailable, with spend in the period. Flag it. The feed should have stopped it. If spend continued, say so.

Profit is a fourth list, not a fifth opinion. Compare cost with conversion value on the same product rows. Spend with no conversion value is a product spending without a return. If they gave a target ROAS, say which products are under it. If they did not, ask once. Do not invent a margin, a cost of goods, or a ROAS from the title. Spend ahead of a known monthly budget, with that weak return, is a pacing deviation from Conversions and bidding. It is not a reason to raise the budget.

Friday's routine leads with the disapproval groups, then this profit list. A disapproval stays a feed fix.

## Feed improvements

The monthly check and the full audit. These are Merchant Center work. AdPlug cannot edit the feed, so you recommend and they or their feed tool make the change.

- Titles. The title does most of the matching in Shopping. Put the words people search first: product type, then brand, then model, size, colour or material. Compare the titles of products with spend and no impressions against the search terms that do convert. Show two or three rewritten examples from their own catalogue, not a template.
- Product type and Google product category filled in, and specific. They decide which queries a product can match and how the structure can be split.
- Custom labels. Margin tier, best seller, seasonal and clearance are the usual four. They let a campaign or a listing group separate the products worth pushing from the rest. Ask what they would want to split by before you name labels. Do not invent a margin.
- Identifiers and images. Missing GTINs and weak images limit a product even when it is approved. Group them by issue, like the disapprovals.

Price competitiveness is in Merchant Center, not in this API. Say so if they ask.

## What you can change, when they ask

`update_shopping_settings`, `set_inventory_filter`, `set_product_groups` and `create_product_ad` exist. Call `operation="help"` before the first use. Any of them is a preview. Listing-group and inventory-filter edits can drop a large part of the catalogue. Show which products would stop serving, not only the node you edited.

New Shopping structure stays paused until the readback in "How to run the account" is clean.

## What you return

Counts: not eligible, limited, eligible. The issue groups. The three waste lists, or "none" for each. What has to be fixed in Merchant Center, with item ids. What you would change in Google Ads, unapplied. What you could not see: billing, the full Merchant Center diagnostics screen, and issue text if the field did not return.
