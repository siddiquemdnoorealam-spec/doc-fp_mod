## CHAT-002 — fp_order_cancel Review

Date:
2026-05-27

Task:
fp_order_cancel review

Module:
fp_order_cancel

Request:
Review existing Odoo 17 POS custom modules before creating `fp_order_cancel`, then provide a safe implementation plan for POS confirmed order cancel.

Existing Modules Checked:
- `fp_retail_base`
- `fp_quick_checkout`
- `fp_order_history`
- `fp_order_return_exchange`
- `fp_order_cancel`

Reference Modules Requested:
- `sh_pos_all_in_one_retail`
- `pos_retail`

Findings:
- `fp_retail_base` exists and should be treated as the shared foundation module.
- `fp_quick_checkout` exists and must not be broken by cancel/reversal flow.
- `fp_order_history` exists and is the correct integration point for order cancel UI/action.
- `fp_order_return_exchange` exists and already represents a safer refund/return direction for confirmed orders.
- `fp_order_cancel` does not exist yet in the active custom module branch.
- Requested reference modules were not confirmed available in the checked reference repository state.

Technical Decision:
- Do not write final code yet.
- Do not increment module version.
- Do not directly cancel paid/done/invoiced POS orders by only writing `state = "cancel"`.
- Confirmed order cancel must remain blocked by default until a safe reversal/refund workflow is approved.
- Backend validation is mandatory; frontend-only checks are not enough.

Recommended Implementation Direction:
- Create `fp_order_cancel` as a conservative module.
- Depend on `point_of_sale`, `fp_retail_base`, and `fp_order_history`.
- Add POS config fields disabled by default.
- Integrate cancel action into `FPOrderHistoryScreen`.
- Add backend RPC methods for eligibility and cancel request.
- Allow only safe draft/unpaid cancellation initially if backend validation passes.
- Block paid/done/invoiced/invoiced orders by default.
- Preserve compatibility with `fp_quick_checkout` and `fp_order_return_exchange`.

Missing Parts Identified:
- Module skeleton.
- Manifest.
- Backend model extensions.
- POS config fields.
- POS loader fields.
- Frontend order history button/action.
- Backend cancel eligibility validation.
- Backend cancel request validation.
- Optional audit/reason tracking.
- Test coverage/manual test checklist.

Risk Points:
- Direct state cancellation can break payment/accounting/stock consistency.
- Delete/cancel must not be allowed only by frontend flags.
- Invoiced POS orders require special protection.
- Paid/done orders require refund/reversal workflow, not raw cancellation.
- Quick checkout and return/exchange flows must remain compatible.

Result:
Review completed successfully.
No code written.
No version increment.
No bug log entry required.
No `MODULE_MAP.md` update required yet because no implemented module relation/dependency changed.



## 3. Append this to `CHAT_LOG.md`:

```md
---

## CHAT-004 — fp_order_cancel Skeleton Install Success

Date: 2026-05-27

Module:

- `fp_order_cancel`

Task:

- Confirm `fp_order_cancel` skeleton installation and update documentation after successful test.

Status:

- Success.

User test result:

- Module installed successfully.
- Module shows in Apps.
- POS config opens successfully.
- Server log is clean.
- Browser console is clean.
- User settings/config option for order cancel shows correctly.
- Option can be selected/enabled.
- POS order history shows the Cancel button.

Summary:

- `fp_order_cancel` skeleton is now present and installed.
- Initial install/UI/config test passed.
- POS config integration works.
- POS frontend asset loading works.
- Order history Cancel button appears after enabling the setting.
- No server log error was reported.
- No browser console error was reported.

Safety status:

- This is still a skeleton only.
- Real cancellation is not implemented.
- Paid/done/invoiced orders must remain blocked.
- The module must not blindly write `state = cancel`.
- The module must not delete POS orders.
- A safe refund/reversal workflow must be designed and approved before real cancel execution is added.

Result:

- `fp_order_cancel` skeleton task completed successfully.

Next:

- Design safe confirmed POS order cancel workflow.
- Define behavior for draft, paid, done, and invoiced POS orders.
- Keep backend validation mandatory.
- Preserve compatibility with:
  - `fp_order_history`
  - `fp_order_return_exchange`
  - `fp_quick_checkout`