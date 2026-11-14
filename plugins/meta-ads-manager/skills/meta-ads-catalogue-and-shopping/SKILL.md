---
name: meta-ads-catalogue-and-shopping
description: "Use only when the account has a product catalogue, or they ask about shopping ads. A rejected product is a catalogue fix, not a bid change."
---

# Catalogue and shopping

Follow the rules in the `meta-ads-manager` skill. Read it first if you haven't in this chat.

## When to use it

Ecommerce, a question about product ads, or the Friday and monthly checks. First call `meta_ads_list` with `entity_type` `catalogs`. If the list is empty, or the account has no business portfolio and the tool says there is no catalogue to list, say that in one line and stop. Do not create a catalogue to complete a setup. Meta's own advice is one catalogue per business. Splitting products across catalogues splits the signal.

If they do not sell products, this skill does not apply. One line.

## What a catalogue campaign is

There is no shopping objective to create. A catalogue campaign is a sales campaign, or an app campaign, whose ad set points at a product set. Advantage+ catalogue ads optimise against that product set. The purchase event still has to be real. A catalogue does not replace a pixel that never fires purchases.

Recommend a catalogue campaign only when the catalogue exists, the products they would show are in stock, and the goal is purchases. Create it paused. Do not turn a live traffic campaign into a catalogue campaign.

Catalogue ads take the same creative rule as every other ad here: enhancements off unless they choose them. Meta turns some catalogue features on by default, such as showing product videos in place of the picture, and adding catalogue items to other ads. Read the creative's enhancements before you claim what the ad shows.

If they want a slice of the catalogue, a product set is the filter. Preview the product count before you create the set. An unfiltered set is every product. Say that.

## Rejected and weak products

List diagnostics with `entity_type` `catalog_diagnostics` and the catalogue id as the parent. Then products, if you need the rows. Group by the issue, not one line per SKU, unless only a few are affected.

A disapproved, rejected or out-of-stock product is a catalogue fix: the image, the price, the link, the availability, or hiding it from ads. It is not a bid change and not a budget change. `update_product` can preview a fix for one product. Prices in that write are minor units. Read the preview amount back before you ask for a yes.

Do not delete a product as a tidy-up. Hiding it is the reversible step, and only after they name it.

Spend on products with no purchase value is a listing or a margin decision. You do not know the margin. Do not invent one. If a monthly budget is known and spend is ahead of it while those products return nothing, name the gap and recommend pausing the ad set or narrowing the product set. Wait.

## What you return

Whether a catalogue exists. The issues, grouped. The product set you would use, paused, not created. Rows to preview. If there is no catalogue, one line and no further checks.
