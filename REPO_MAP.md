# Repository Map

## Document Repo

URL:
https://github.com/siddiquemdnoorealam-spec/doc-fp_mod

Purpose:
Permanent source of truth for project documentation, current status, handoff, chat log, bug log, and module map.

Update:
Keep this repo permanently. Do not delete it.

---

## Custom Module Repo / Branch

URL:
https://github.com/siddiquemdnoorealam-spec/fp-mod-17/tree/pos_fp_17

Purpose:
Working repository/branch for custom Odoo 17 modules.

Expected path:
`pos_fp_17` branch should contain existing FP modules and new `fp_order_cancel`.

Update:
This repo/branch can be temporary or replaceable, but important project memory must stay in `doc-fp_mod`.

---

## Reference Module Repo

URL:
https://github.com/siddiquemdnoorealam-spec/reference-mod-17

Purpose:
Reference modules/archive for behavior/workflow/UI study only.

Rules:
- Do not copy reference code directly.
- Use reference modules only to understand feature behavior and implementation direction.
- Final implementation must be fresh `fp_` custom code.
