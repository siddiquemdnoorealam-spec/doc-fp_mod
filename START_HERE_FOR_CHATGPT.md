# START HERE FOR CHATGPT

This is the first file ChatGPT should read before working on this project.

## Project Type

Existing Odoo 17 POS/module continuation project.

This is not a fresh project from zero. Some modules were already created earlier and will be uploaded into the custom module repo.

## Repositories

Document repo:
https://github.com/siddiquemdnoorealam-spec/doc-fp_mod

Custom module repo:
https://github.com/siddiquemdnoorealam-spec/fp-mod-17

Reference module repo:
https://github.com/siddiquemdnoorealam-spec/reference-mod-17

## Core Rule

Before creating any new module, fixing any bug, or changing existing code:

1. Observe the current custom modules in `fp-mod-17`.
2. Check module dependencies and relationships.
3. Check `MODULE_MAP.md`.
4. Check `CURRENT_STATUS.md`.
5. Check `CHAT_HANDOFF.md`.
6. Check `BUG_LOG.md`.

Do not start from scratch unless the user clearly says it is a new clean/base project.

## Naming Rule

All custom modules created for this project must use the `fp_` prefix.

Examples:
- fp_retail_base
- fp_quick_checkout
- fp_order_history
- fp_order_return_exchange
- fp_order_cancel

## Reference Rule

Reference modules are only for studying workflow, behavior, UI flow, data flow, feature relation, and implementation idea.

Do not copy-paste reference module code.

## User Input Rule

The user will usually provide only:
- issue info
- branch name
- module name
- error message and Odoo/browser log if there is an error
- success/test status if the task is completed

ChatGPT must convert that information into repo-ready updates for:
- CHAT_HANDOFF.md
- CURRENT_STATUS.md
- BUG_LOG.md
- MODULE_MAP.md when needed

## Development Rule

One task = one GitHub issue = one GitHub branch = one short ChatGPT chat.

Avoid long overloaded chats.
