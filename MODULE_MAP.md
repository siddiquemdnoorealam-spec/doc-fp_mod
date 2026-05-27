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


## fp_order_cancel

### Purpose

POS Order Cancel extension module for FP Odoo 17 POS.

Current phase: **basic skeleton completed and tested successfully**

The module is intended to provide safe POS order cancel handling integrated with FP Order History.

### Current Status

Status: **Success**

Basic module skeleton has been installed and tested successfully.

### Dependencies

Depends on:

- `point_of_sale`
- `fp_retail_base`
- `fp_order_history`

Does not depend on:

- `fp_quick_checkout`
- `fp_order_return_exchange`

### Relation With Existing Modules

#### fp_retail_base

Uses the shared FP retail/POS base environment and follows the existing custom module pattern.

#### fp_order_history

Direct integration target.

The skeleton integrates with order history by:

- Adding cancel policy placeholder data.
- Patching the existing FP Order History screen.
- Showing a Cancel placeholder button in Order History details when enabled from POS config.

#### fp_quick_checkout

No direct dependency.

The module must not modify or break quick checkout behavior.

Current test result confirms no browser console issue and no quick checkout-breaking behavior was reported during basic module test.

#### fp_order_return_exchange

No direct dependency in the basic skeleton.

Future cancel logic must be checked against return/exchange behavior before implementation.

### Current Safety Behavior

Cancel/Delete is blocked or inactive by default.

The basic skeleton does not:

- Blindly write `state = cancel`.
- Delete POS orders.
- Cancel paid orders.
- Cancel done orders.
- Cancel invoiced orders.
- Create refund/reversal/accounting moves.
- Implement final cancel workflow.

### Next Planned Work

Next task:

`fp_order_cancel cancel feature`

The next phase should implement a safe backend-validated cancel flow while keeping paid/done/invoiced POS orders blocked unless a safe reversal/refund workflow is approved.