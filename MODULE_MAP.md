# Module Map

This file tracks custom modules, their purpose, and relationships.

## Project Rule

All custom modules must start with `fp_`.

## Existing / Expected Core Modules

### fp_retail_base

Purpose:

- Shared base/foundation module for FP retail POS modules
- Common POS settings/helpers/config flags

Depends:

- `point_of_sale`

Related:

- Used by other FP POS modules as a base/foundation module

Status:

- Existing module should be observed from `fp-mod-17/tree/pos_fp_17`

---

### fp_quick_checkout

Purpose:

- Quick checkout / custom POS screen flow
- Must keep payment validation/finalization compatible with Odoo POS

Depends:

- `point_of_sale`
- `fp_retail_base` if implemented that way

Related:

- Must be tested when order history, return/exchange, or order cancel changes
- Known previous risk: negative amount/payment confirm issue

Status:

- Existing module should be observed before changes

---

### fp_order_history

Purpose:

- Previous POS order search/list/details inside POS

Depends:

- `point_of_sale`
- `fp_retail_base` if implemented that way

Related:

- `fp_order_reprint`
- `fp_order_return_exchange`
- `fp_order_cancel`

Status:

- Existing module should be observed before adding cancel action

---

### fp_order_return_exchange

Purpose:

- POS return/exchange flow
- Returned quantity tracking and partial return logic

Depends:

- `point_of_sale`
- `fp_order_history` if implemented that way

Related:

- `fp_quick_checkout`
- `fp_order_cancel`

Known risk:

- Previous partial return flow had `lineState` undefined error

Status:

- Existing module should be observed before order cancel compatibility testing

---

### fp_order_reprint

Purpose:

- Reprint previous POS order receipts/reports

Depends:

- `point_of_sale`
- `fp_order_history` if implemented that way

Related:

- `fp_order_history`

Status:

- Existing module should be observed if reprint/order details flow is affected

---

### fp_bag_charges

Purpose:

- Add bag charge product/line in POS

Status:

- Existing module should be observed if present

---

### fp_default_customer

Purpose:

- Auto-set default/walk-in customer in POS

Status:

- Existing module should be observed if present

---

### fp_product_view_switch

Purpose:

- Switch POS product view layout/grid/list/card behavior

Status:

- Existing module should be observed if present

---

### fp_order_cancel

Purpose:

- POS confirmed order cancel behavior from order history/details

Recommended dependencies:

- `point_of_sale`
- `fp_retail_base`
- `fp_order_history`

Recommended relation:

- Add cancel action by extending/patching order history screen/details
- Reuse order history access/search/details logic
- Do not patch quick checkout payment flow unless absolutely required

Safety rule:

- Do not blindly cancel paid/done/invoiced POS orders by only writing `state = cancel`
- Must validate config, permission, payment/accounting/invoice/stock/session/report risk

Status:

- Planned / to be confirmed from `fp-mod-17/tree/pos_fp_17`
