# Bug Log

This file tracks bugs/errors found during the project.

Do not delete old bugs. Add new bug entries below old ones. Update bug status when fixed.

---

## BUG-001 — Quick checkout return lineState undefined

Status:
Open / To be rechecked.

Affected/related modules:
- `fp_quick_checkout`
- `fp_order_history`
- `fp_order_return_exchange`

Error:
```text
TypeError: can't access property "lineState", this is undefined
```

Context:
Previously appeared during partial return quantity update or when unselecting a non-return product.

Next:
Recheck during `fp_order_cancel` compatibility testing if return/exchange flow is installed.

---

## BUG-002 — Quick checkout negative amount/payment confirm inactive

Status:
Open / To be rechecked.

Affected/related modules:
- `fp_quick_checkout`
- return/negative payment flow if related

Context:
Previously, with quick checkout, after selecting payment method and negative amount, confirm button stayed inactive.

Next:
Recheck during quick checkout compatibility testing.
