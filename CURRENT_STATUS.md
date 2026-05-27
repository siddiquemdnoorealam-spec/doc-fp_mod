## Current Task
fp_order_cancel review and safe implementation planning.

## Observed Status
- Existing module continuation confirmed.
- `fp_retail_base` exists and provides shared retail POS config flags.
- `fp_quick_checkout` exists and reuses Odoo PaymentScreen validation/finalization.
- `fp_order_history` exists and provides POS previous order search/details.
- `fp_order_return_exchange` exists and patches `FPOrderHistoryScreen`.
- `fp_order_cancel` does not exist in current `fp-mod-17/pos_fp_17`.

## fp_order_cancel Planning Status
Status: Planned / Not created yet.

Recommended dependency:
- point_of_sale
- fp_retail_base
- fp_order_history

Recommended relation:
- Add cancel action by patching `FPOrderHistoryScreen`.
- Reuse order history access/domain logic.
- Do not patch quick checkout payment flow.

## Safety Decision
Do not blindly cancel paid/done/invoiced POS orders by only writing `state = cancel`.
Odoo 17 has an unused POS cancel method that only changes state, so safe implementation must validate accounting, invoice, payment, stock, and session risks.

## Next Recommended Step
Create issue branch `feature/fp-order-cancel` and implement first safe version:
- config flag
- backend validation RPC
- cancel button in order history
- reason/confirmation popup
- block unsafe confirmed states unless a proper reversal/refund workflow is approved.