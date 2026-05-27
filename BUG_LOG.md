# Bug Log

This file tracks bugs/errors in a short clean format.

The user will provide raw error message, Odoo log, browser console error, and issue/branch/module info.

ChatGPT will convert that into a clean bug summary for this file.

## BUG-001: Quick checkout return lineState undefined

Status:
Open / To be verified

Affected modules:
- fp_quick_checkout
- fp_order_history
- fp_order_return_exchange

Error:
TypeError: can't access property "lineState", this is undefined

Context:
Partial return quantity update or unselecting non-return product previously caused this frontend error.

Expected result:
Return/product line update should not crash the POS screen.

Actual result:
POS frontend crashed with `lineState` undefined.

Next action:
Verify whether this bug exists in the uploaded current modules. If still present, create a bugfix issue and branch.

Suggested branch:
bugfix/quick-checkout-line-state-error

---

## BUG-002: Quick checkout negative payment confirm button inactive

Status:
Open / To be verified

Affected modules:
- fp_quick_checkout

Context:
With quick checkout, after selecting payment method and negative amount, confirm button previously stayed inactive.

Expected result:
Valid return/negative payment flow should allow confirmation when Odoo payment rules are satisfied.

Actual result:
Confirm button stayed inactive.

Next action:
Verify against current uploaded module code and test flow.

Suggested branch:
bugfix/negative-payment-confirm-button
