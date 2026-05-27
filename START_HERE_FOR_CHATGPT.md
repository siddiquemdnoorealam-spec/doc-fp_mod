# START HERE FOR CHATGPT

This project is for continuing existing Odoo 17 POS modules that were already created earlier.

## Repositories

Document repo:  
https://github.com/siddiquemdnoorealam-spec/doc-fp_mod

Custom module repo / branch:  
https://github.com/siddiquemdnoorealam-spec/fp-mod-17/tree/pos_fp_17

Reference module repo:  
https://github.com/siddiquemdnoorealam-spec/reference-mod-17

## Project Mode

Existing module continuation.

This is not a fresh project from zero.

## Main Rules

1. Before creating any new module or fixing any bug, first observe existing modules in `fp-mod-17/tree/pos_fp_17`.
2. Do not start from zero unless the user explicitly says this is a new clean project.
3. Existing modules must be treated as the current project state.
4. Always check relation with existing modules before writing new code.
5. Especially check these modules if they exist:
   - `fp_retail_base`
   - `fp_quick_checkout`
   - `fp_order_history`
   - `fp_order_return_exchange`
   - `fp_order_cancel`
6. All new custom modules must use the `fp_` prefix.
7. Reference modules are for studying workflow, behavior, and UI flow only.
8. Do not copy-paste reference module code.
9. During testing/bug-fix phase, do not increment module version unless the user explicitly asks.
10. Keep this project context inside the ChatGPT Project only.

## Simple Chat Workflow

The user will provide only:

- Task name and module name
- Error message and Odoo/browser logs if error happens
- Success/test status if test succeeds

ChatGPT will provide:

- Code / fix / implementation plan
- Test steps
- `CHAT_HANDOFF.md` update
- `CHAT_LOG.md` entry
- `CURRENT_STATUS.md` update
- `BUG_LOG.md` update when needed
- `MODULE_MAP.md` update when module relation changes

## New Chat Start Instruction

For each new main task, first read:

- `START_HERE_FOR_CHATGPT.md`
- `REPO_MAP.md`
- `MODULE_MAP.md`
- `CURRENT_STATUS.md`
- `CHAT_HANDOFF.md`
- `CHAT_LOG.md`
- `BUG_LOG.md`

Then observe the current custom module repo branch before writing code.

## Document Update Rules

- `CHAT_HANDOFF.md` = replace with latest handoff after a main task ends or pauses.
- `CHAT_LOG.md` = append one numbered summary entry after each main task/chat ends.
- `CURRENT_STATUS.md` = update after task result, blocker, or next task change.
- `BUG_LOG.md` = append new bugs; do not delete old bugs. Update bug status when fixed.
- `MODULE_MAP.md` = update only when module/dependency/relation changes.
- `REPO_MAP.md` = one-time setup; update only if repo links or repo purpose change.
