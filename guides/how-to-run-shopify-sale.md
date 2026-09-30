# How to Run a Shopify Sale

## Quick answer

Lower the selling Price, use the old price as Compare-at price, select the affected variants, and preview before applying the changes. Verify the result in Shopify Admin and on the storefront. To end a Springify sale, restore the task's saved values with **Rollback changes** after checking for later price edits.

## Sale prices and Shopify Discounts

Price is the current selling price. Compare-at price is a reference value that the theme can display beside it.

| Field | Before sale | During sale | After rollback |
| --- | --- | --- | --- |
| Price | $100 | $80 | $100 |
| Compare-at price | Empty | $100 | Empty |

The customer pays $80 during this sale; the storefront can show $100 as the old price. Themes decide whether to show crossed-out prices, badges, or percentages.

Changing Price and Compare-at price changes the product's stored pricing. This suits collection promotions, storewide sales, clearance, and temporary price cuts. Shopify Discounts instead control eligibility through rules such as codes, eligible customers, order minimums, Buy X Get Y, or discount combinations.

A sale price does not disable Shopify Discounts. Check active discount rules before launch: an eligible checkout discount may reduce the selling price further.

## Configure and apply the sale

### 1. Choose the price action

Springify's **Start sale** template prepares Price and Compare-at actions for a standard sale. Adjust them for the intended promotion.

| Action | Example | Use |
| --- | --- | --- |
| Decrease by percentage | $100 → $80 at 20% off | Same proportional reduction across selected variants |
| Decrease by fixed amount | $50 → $45 with $5 off | Same amount off each selected price |
| Set an exact price | $100 → $29.99 | One selling price for the selected group |

Split products into separate groups when they need different discounts.

### 2. Configure Compare-at price

For a standard sale, use **Decrease price** for Price and **Set to price** for Compare-at price. The latter uses the original Price as the reference value: $100 becomes a Price of $80 with Compare-at of $100.

See [Shopify Compare-at Price](shopify-compare-at-price.md) for reference-price calculations and display troubleshooting.

### 3. Select products and exclusions

Target the whole store, selected collections, specific products or variants, or products matching conditions. Exclude products, variants, or collections that should stay unchanged.

For example, a storewide 20% Black Friday promotion can exclude new arrivals and a premium collection. Check that those exclusions are reflected in the preview.

### 4. Review before applying

Choose **Prepare products for review** and inspect:

- Which variants will change and which products are excluded.
- Current and new Price values.
- Current and new Compare-at values.

If the selection or calculation looks wrong, revise the task settings before applying it. When the preview is correct, choose **Apply changes** to update the selected Shopify variants.

### 5. Verify saved values and storefront display

After completion, inspect a normal product, a multi-variant product, an excluded product, and a product with Compare-at pricing. Check both Shopify Admin and the storefront; do not assume every page shows the new values immediately.

If something looks wrong, inspect the affected variant in Admin first:

| Finding | Next check |
| --- | --- |
| Admin has incorrect Price or Compare-at values | Investigate the price update. |
| Admin is correct but the storefront differs | Check theme behavior, cache, and variant display before running another price task. |

Rerunning a pricing task to fix a display issue can change prices that were already correct.

## Restore prices when the sale ends

### Use the task's saved values

**Rollback changes** restores the original values recorded for the variants changed by the task, including the original Compare-at value. In the example above, Price returns to $100 and Compare-at returns to empty.

Reversing the percentage is not equivalent:

```text
$100 × (1 - 0.20) = $80
$80 × (1 + 0.20) = $96
```

A 25% increase would mathematically return $80 to $100. Restoring saved values avoids having to reconstruct the original price.

### Check for newer changes

Rollback can replace values written after the sale began by manual edits, imports, ERP systems, other apps, or API integrations. Review later changes before restoring an older task.

If prices were correct immediately after the sale task but changed later, investigate which other systems can write Price or Compare-at. Those later updates may explain the difference.

If Task A ran before Task B on the same variants, their saved states differ. When undoing both, work backward: roll back B, then A. Avoid overlapping temporary tasks where possible.

### Restore from Compare-at only when it is correct

An alternative is **Set to compare at price**, followed by **Remove compare at price**. This works only if Compare-at currently contains the regular price you want: Price $80 / Compare-at $100 becomes Price $100 / Compare-at empty.

If Compare-at is empty, the current sale price remains. If another update changed Compare-at, this method may restore the wrong price. Task rollback is usually safer for a Springify sale.

Deleting a completed task or uninstalling the app does not undo values already written to Shopify. Restore the prices first.

For a planned campaign, follow [How to Schedule Shopify Sale Prices](schedule-shopify-sale-prices.md) to configure start and rollback together.

## Related resources

- [Read the full guide on Springify](https://springify.io/guides/how-to-run-shopify-sale/?ref=github)
- [Bulk Price Editor by Springify on the Shopify App Store](https://apps.shopify.com/bulk-price-edit-springify?ref=github)
