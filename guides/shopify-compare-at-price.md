# Shopify Compare-at Price

## Quick answer

Compare-at price is a reference price displayed alongside the current selling Price. For a standard sale comparison, it must be higher than Price. It does not create a Shopify discount code or automatic discount; those can apply separately, subject to their rules. Display can differ by variant, theme, market, and catalog.

## Understand the two fields

Shopify pricing is set at the variant level. Price determines the current selling price; Compare-at provides the higher reference value.

| Price | Compare-at price | Meaning |
| --- | --- | --- |
| $100 | Empty | Regular pricing |
| $80 | $100 | Selling price reduced from the reference price |
| $100 | $125 | Current price is 20% below the reference price |

The theme controls the presentation. A valid pair of values does not guarantee the same badge or crossed-out price on every storefront page.

Variants can also differ within one product: Small and Medium might each use Price $30 / Compare-at $40, while Large uses $35 / $45. Check the variants customers can actually select.

## Calculate the discount correctly

The reduction is measured against Compare-at, not against the current Price:

```text
discount fraction = (compare-at price - current price) / compare-at price
compare-at price = current price / (1 - target discount fraction)
```

Use 0.20 for a 20% target. Raising a $100 reference calculation by 20% produces Compare-at $120, but the reduction from $120 to $100 is only about 16.7%:

```text
(120 - 100) / 120 ≈ 0.1667
100 / (1 - 0.20) = 125
```

| Current Price | Target reduction | Required Compare-at |
| --- | --- | --- |
| $40 | 20% | $50 |
| $80 | 20% | $100 |
| $100 | 20% | $125 |

These calculations keep the selling Price unchanged while setting a reference value for the intended percentage. Simply multiplying Price by 1.20 does not achieve 20% off. A theme that calculates a discount percentage from the values would show the resulting ratio.

## Keep Shopify Discounts separate

Suppose Price is $80 and Compare-at is $100. If the product also qualifies for an additional 10% Shopify discount, the discount can apply to $80:

```text
$100 reference → $80 selling price → $72 after an eligible 10% discount
```

The final result depends on discount eligibility and combination rules. Review active codes, automatic discounts, and combination settings before launch so the final price matches your intention.

For the complete sale workflow, see [How to Run a Shopify Sale](how-to-run-shopify-sale.md).

## Edit a few variants or manage a bulk change

For a few products, edit Compare-at directly in Shopify Admin. For larger sets, a bulk workflow helps calculate values consistently, target collections or products, exclude variants, preview the result, schedule changes, and restore prior values afterward.

Bulk Price Editor by Springify supports these operations. When keeping selling prices and showing a 20% reduction, the calculation is `compare-at = price / 0.8`. Review representative products and variants before applying the rule across the catalog.

Use this sequence:

1. Decide whether Price, Compare-at, or both should change.
2. Define the included products and variants, plus exclusions.
3. Choose the intended price difference or discount percentage.
4. Calculate and preview the resulting values.
5. Check any Shopify Discounts that may apply as well.
6. Apply or schedule the change and plan restoration.

See [Bulk Price Changes for Large Catalogs](bulk-price-changes-large-catalogs.md) for keeping targeting rules reviewable.

## Troubleshoot a missing Compare-at price

### Price relationship and variants

Verify that Compare-at exceeds Price on the affected variant. One variant may contain $80 / $100 while another contains $80 / empty. Checking only a different variant can hide the cause.

### Theme presentation

If Admin values are correct, inspect the theme. Product pages and collection cards can use different display logic; mixed variant pricing and custom pricing code can also change the presentation.

### Markets and catalogs

Stores using Markets or catalogs may have percentage adjustments, fixed prices, or fixed Compare-at prices. Inspect the catalog assigned to the relevant market instead of relying only on the base product price.

For catalog percentage adjustments, Shopify applies the adjustment to Compare-at prices by default. The catalog's **Include compare-at price** option controls that behavior; disabling it allows Compare-at to be managed separately.

A separate visibility setting can apply in some EEA selling scenarios. Depending on the primary market and Markets configuration, Compare-at visibility may be controlled under:

```text
Markets → [Market] → More settings → Compare-at price
```

If one market shows Compare-at and another does not, check this setting. It concerns visibility; the catalog option concerns price calculation. They are not interchangeable.

## Return to normal pricing

A typical temporary sale changes Price $100 / Compare-at empty into $80 / $100. Ending it means restoring Price to $100 and Compare-at to its original empty value.

For a small set, those values can be restored manually. For larger promotions, save or note the original values before launch and decide when restoration should happen. See [How to Schedule Shopify Sale Prices](schedule-shopify-sale-prices.md) for the preview, schedule, and rollback workflow.

## Related resources

- [Read the full guide on Springify](https://springify.io/guides/compare-at-price-shopify-sales/?ref=github)
- [Bulk Price Editor by Springify on the Shopify App Store](https://apps.shopify.com/bulk-price-edit-springify?ref=github)
