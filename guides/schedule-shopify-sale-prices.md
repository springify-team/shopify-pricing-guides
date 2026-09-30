# How to Schedule Shopify Sale Prices

## Quick answer

Choose the variants, configure Price and Compare-at price, and review a preview. In Springify, copy that preview task into a new task, then configure both the scheduled start and scheduled rollback. Rollback restores saved original values rather than calculating an inverse discount.

## Define the temporary pricing

This workflow changes the product prices stored in Shopify. Shopify Discounts are a separate system for applying discounts, including codes; changing Compare-at does not replace them.

| Stage | Price | Compare-at price |
| --- | --- | --- |
| Before sale | $100 | Empty |
| During a 20% sale | $80 | $100 |
| After rollback | $100 | Original empty value |

The storefront can show the old and current prices together, depending on the theme.

## 1. Select the variants and exclusions

Target the whole store, products, variants, collections, or matching conditions. Springify supports filters such as tags, vendors, collections, status, inventory, and sale status. Combine conditions and exclude products, variants, or collections as needed.

Changes happen at the variant level. Use the preview's affected variant count to check the scope before scheduling.

## 2. Configure Price and Compare-at

Price can decrease by percentage or fixed amount, or be set to an exact amount. Decide separately whether to preserve Compare-at, take it from the current Price, or calculate it for a target discount. Both fields can change in the same task.

### Products already on sale

For Price $90 / Compare-at $100, another 5% off the current selling price gives Price $85.50. Keep Compare-at at $100 if that is still the intended reference. The extra reduction is based on $90, not $100.

### Target discount percentages

Price $100 / Compare-at $120 represents approximately 16.7% off, not 20%. For a 20% reduction from the reference:

```text
Compare-at = Price / (1 - 0.20)
$100 / 0.8 = $125
```

Springify's **Set compare-at price to show target percent off** action calculates the reference price; it adjusts accordingly if the task also changes Price. See [Shopify Compare-at Price](shopify-compare-at-price.md) for the formula and display caveats.

## 3. Preview, then copy into a scheduled task

A preview task cannot be scheduled directly. Use this sequence:

1. Create a preview task with the intended selection and pricing rules.
2. Review affected variants, exclusions, current and new Price, current and new Compare-at, and obvious price outliers.
3. Open the preview task and choose **Copy to new task**.
4. Keep the reviewed selection and pricing configuration.
5. Add the start and rollback schedule in the copied task.
6. Create the scheduled task after checking its configuration.

The preview lets you inspect variants and calculations before creating the scheduled version.

## 4. Set both start and rollback

Enable the scheduled start and choose when the promotion begins. Enable scheduled rollback and choose when it ends. For example, a Black Friday campaign could start on November 27, 2026 and roll back on November 30, 2026.

Before creating the task, recheck the selection, exclusions, pricing actions, start time, and rollback time.

## 5. Restore saved values

Springify records previous values for variants changed by the task. Manual or scheduled rollback can restore those values for that specific task.

Do not reverse a sale by applying the same percentage in the opposite direction:

```text
$100 reduced by 25% = $75
$75 increased by 25% = $93.75
Intended restoration: $75 → saved $100
```

Price Vault provides a separate pricing snapshot. Springify creates an initial snapshot on installation, and you can create another before a major campaign. A snapshot is separate from the saved values belonging to an individual task.

## Conflicts and scope limits

- **Later edits:** if Price starts at $100, the sale sets $80, and someone manually changes it to $85, rollback can still restore $100. It does not preserve the later edit.
- **Other systems:** imports, ERP integrations, sync apps, and pricing tools can change the same fields during the campaign.
- **Overlapping tasks:** Task B may save values produced by Task A. Their saved states differ, so rollback order matters. Avoid unnecessary overlap on the same variants.
- **New products:** a scheduled task affects variants selected when it runs. It does not continuously watch for products added after the sale starts.
- **Markets:** Springify changes the store's main product pricing. Verify how fixed or other market-specific prices interact with it before scheduling.
- **Cancellation and removal:** cancelling or deleting a task is different from rollback. Uninstalling the app does not restore values already written to Shopify. Restore changed prices explicitly.

## Related resources

- [Read the full guide on Springify](https://springify.io/guides/schedule-shopify-sale-prices/?ref=github)
- [Bulk Price Editor by Springify on the Shopify App Store](https://apps.shopify.com/bulk-price-edit-springify?ref=github)
