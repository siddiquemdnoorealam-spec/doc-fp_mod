# Chat Handoff

This file contains the latest handoff for the next ChatGPT chat.

## Last Task

Project documentation setup.

## Last Module

Project setup / `fp_order_cancel`

## Last Status

Ready to start first project chat.

## What Was Done

- Final simplified workflow was selected.
- GitHub Issues and branches are not required.
- Documentation repo is the permanent source of truth.
- Custom module repo/branch is the working source for modules.
- Reference repo is for behavior/workflow study only.
- Cancel module flow was reduced to three main tasks:
  1. `fp_order_cancel basic module`
  2. `fp_order_cancel cancel feature`
  3. `fp_order_cancel test and final cleanup`

## Important Rules For Next Chat

- Do not write code in the first chat.
- First observe documentation and existing module repo.
- Treat existing modules as the current project state.
- Do not start from zero.
- Do not copy reference module code.
- Do not increment module version during testing/fix phase.

## Next Chat Command

Use this in the first project chat:

```text
We are starting the FP Odoo 17 POS Cancel Module project.

Document repo:
https://github.com/siddiquemdnoorealam-spec/doc-fp_mod

Custom module repo / branch:
https://github.com/siddiquemdnoorealam-spec/fp-mod-17/tree/pos_fp_17

Reference module repo:
https://github.com/siddiquemdnoorealam-spec/reference-mod-17

Current task:
Read START_HERE_FOR_CHATGPT.md, REPO_MAP.md, MODULE_MAP.md, CURRENT_STATUS.md, CHAT_HANDOFF.md, CHAT_LOG.md, and BUG_LOG.md from doc-fp_mod.
Then read the existing module structure from fp-mod-17/tree/pos_fp_17.
Prepare the current project status and tell me the next safe task for creating fp_order_cancel.

Do not write module code yet.
Do not give module ZIP yet.
Only observe and prepare status.
```
