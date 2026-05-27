## Last Task
Reviewed planned `fp_order_cancel` module for POS confirmed order cancel.

## What Was Observed
- `fp_order_cancel` is not present in `fp-mod-17/pos_fp_17`.
- `fp_retail_base`, `fp_quick_checkout`, `fp_order_history`, and `fp_order_return_exchange` exist.
- `fp_order_history` should be the base dependency for cancel UI.
- `fp_order_return_exchange` already patches `FPOrderHistoryScreen`, so `fp_order_cancel` should follow the same safe extension pattern.
- Odoo 17 POS cancel state/method exists but is marked unused and only writes state, so it is unsafe for direct confirmed paid/posted/invoiced cancellation.

## Decision
Do not write final code yet.
Plan `fp_order_cancel` as a new `fp_` module depending on `fp_order_history`.
First safe version should block unsafe confirmed states and avoid accounting/stock damage.

## Suggested Branch
feature/fp-order-cancel

## Pending Implementation Plan
- Add `fp_order_cancel` module skeleton.
- Add POS config fields.
- Add backend RPC with strict validation.
- Patch `FPOrderHistoryScreen` to show Cancel action.
- Add confirm/reason popup.
- Refresh order history after successful cancel.
- Runtime test with quick checkout and return/exchange modules installed.

## Important Rule
No existing module version increment during this planning/bug-fix phase unless explicitly requested.