# START HERE FOR CHATGPT

This project is for continuing existing Odoo 17 POS modules and creating the `fp_order_cancel` module.

## Important Repositories

Document repo:
https://github.com/siddiquemdnoorealam-spec/doc-fp_mod

Custom module repo / branch:
https://github.com/siddiquemdnoorealam-spec/fp-mod-17/tree/pos_fp_17

Reference module repo:
https://github.com/siddiquemdnoorealam-spec/reference-mod-17

## Core Rules

1. This is not a fresh project from zero.
2. Existing modules in `fp-mod-17/tree/pos_fp_17` are the current project state.
3. Before creating or fixing `fp_order_cancel`, observe existing modules first.
4. Especially check:
   - `fp_retail_base`
   - `fp_quick_checkout`
   - `fp_order_history`
   - `fp_order_return_exchange`
5. All custom modules must use the `fp_` prefix.
6. Reference modules are for workflow/behavior/UI study only.
7. Do not copy-paste reference module code.
8. Use Odoo 17 coding style.
9. During bug-fix/testing phase, do not increment module version unless explicitly asked.

## Cancel Module Safety Rules

1. Target module is `fp_order_cancel`.
2. `fp_order_cancel` must integrate with `fp_order_history`.
3. `fp_order_cancel` must not break `fp_quick_checkout`.
4. Do not blindly cancel paid/done/invoiced POS orders by only writing `state = cancel`.
5. Cancel/Delete must stay blocked or disabled by default unless a safe reversal/refund workflow is approved.
6. Backend validation is required. Frontend-only checks are not enough.

## Final Fixed Task Flow

Only these main tasks are used:

1. `fp_order_cancel basic module`
2. `fp_order_cancel cancel feature`
3. `fp_order_cancel test and final cleanup`

## Documentation Rules

- `CURRENT_STATUS.md` = full replacement after task success/pause/error state change
- `CHAT_HANDOFF.md` = full replacement after task success/pause
- `CHAT_LOG.md` = append one numbered entry after each completed/paused task
- `BUG_LOG.md` = append new bug entry if error happens
- `MODULE_MAP.md` = update only if module/dependency/relation changes
- `REPO_MAP.md` = update only if repo links/purpose changes
- `START_HERE_FOR_CHATGPT.md` = one-time setup file; do not rewrite in every chat

## Assistant Output Rules

When creating or fixing code:

1. Provide updated downloadable module ZIP if possible.
2. Provide file-by-file summary.
3. Provide where to paste/install/upgrade.
4. Provide exact test steps.
5. Do not provide final documentation updates before the user tests, unless user asks for pause handoff.

When user reports Success:

1. Provide full replacement content for `CURRENT_STATUS.md`.
2. Provide full replacement content for `CHAT_HANDOFF.md`.
3. Provide append entry for `CHAT_LOG.md`.
4. Provide `MODULE_MAP.md` update only if relation/dependency changed.
5. Provide next ready-to-copy chat command.

When user reports Error:

1. Provide fix plan.
2. Provide updated module ZIP if code changes are needed.
3. Provide `BUG_LOG.md` append entry.
4. Provide test steps.
5. Provide pause handoff only if task cannot continue in same chat.
