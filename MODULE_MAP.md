# Module Map

This file records module relationships and dependencies.

## Existing Related Modules

### fp_retail_base

Purpose:
Shared base/foundation module for FP retail POS features.

Relation:
- `fp_order_cancel` should depend on this module.
- Provides shared retail/POS config direction.

---

### fp_quick_checkout

Purpose:
One-screen/quick POS checkout workflow.

Relation:
- `fp_order_cancel` must not break this module.
- `fp_order_cancel` should not patch quick checkout unless a real conflict appears.
- Quick checkout must be regression tested after cancel module work.

---

### fp_order_history

Purpose:
POS order history/search/details workflow.

Relation:
- Main integration point for `fp_order_cancel`.
- `fp_order_cancel` should integrate with the order history/details screen.

---

### fp_order_return_exchange

Purpose:
Return/exchange workflow from order history.

Relation:
- Related order-management workflow.
- Must be regression tested with `fp_order_cancel`.
- No hard dependency unless later feature requires it.

---

## Target Module

### fp_order_cancel

Purpose:
Safe POS order cancel module integrated with FP order history.

Expected dependencies:
- `point_of_sale`
- `fp_retail_base`
- `fp_order_history`

Must not depend on by default:
- `fp_quick_checkout`
- `fp_order_return_exchange`

Safety rules:
- Disabled/blocked by default for unsafe states.
- Backend validation required.
- Do not blindly write `state = cancel` for paid/done/invoiced orders.
- Do not delete POS orders.
- Safe refund/reversal workflow must be approved before real confirmed-order cancellation.
