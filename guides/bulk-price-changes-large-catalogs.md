# Bulk Price Changes for Large Catalogs

## Quick answer

Narrow the segment, make selection rules readable, review before launch, and plan rollback with the change. At scale, the main challenge is understanding what changes, why it is included, and how to restore it.

## Define a reviewable segment

Prefer conditions another operator can validate over scattered manual selections. Useful examples from the source guide include:

- Vendor matches the seasonal promotion.
- Collection is outlet.
- Product status is active.
- Inventory exceeds a threshold.

Review the selection before applying changes. For crossed-out reference prices, check the [Compare-at calculations and caveats](shopify-compare-at-price.md) before using one rule across many variants.

Manual exports can help validate a selection, but the source guide advises against making them the primary workflow for recurring changes across many products.

## Include restoration in the plan

Define rollback when planning launch. Manual cleanup across thousands of products can be postponed or left incomplete. The [scheduled-sale workflow](schedule-shopify-sale-prices.md) explains how Springify combines a reviewed configuration with start and rollback times.

## Related resources

- [Read the full guide on Springify](https://springify.io/guides/bulk-price-changes-large-catalogs/?ref=github)
- [Bulk Price Editor by Springify on the Shopify App Store](https://apps.shopify.com/bulk-price-edit-springify?ref=github)
