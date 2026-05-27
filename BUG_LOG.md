# Bug Log

This file tracks bugs/errors found during the project.

Update rule:

- Add new bugs under old bugs.
- Do not delete old bugs.
- When a bug is fixed, update its status.
- Full raw logs can be kept in the ChatGPT chat or external issue/comment, but the clean summary should be kept here.

---

## BUG-001 — Quick checkout return lineState undefined

Status: Open / To be rechecked

Affected modules:

- `fp_quick_checkout`
- `fp_order_history`
- `fp_order_return_exchange` if exists

Error:

```text
TypeError: can't access property "lineState", this is undefined
```

Context:

Partial return quantity update or unselecting non-return product previously caused this error.

Expected result:

- Partial return quantity update should work safely.
- Non-return/unselected lines should not crash POS frontend.

Current action:

- Recheck after existing modules are observed.
- Must be tested again before or during `fp_order_cancel` compatibility testing.

---

## BUG-002 — Quick checkout negative amount/payment confirm inactive

Status: Open / To be rechecked

Affected modules:

- `fp_quick_checkout`
- return/negative payment flow if related

Context:

After selecting payment method and using a negative amount/return flow, confirm button previously stayed inactive.

Expected result:

- Payment method selection should allow valid confirmation when the order/payment state is valid.
- Normal checkout should not break.

Current action:

- Recheck after existing modules are observed.
- Must be tested during quick checkout compatibility testing.
