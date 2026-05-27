# Repository Map

This file explains where each type of project data should be stored.

## 1. Document Repo

Repository:
https://github.com/siddiquemdnoorealam-spec/doc-fp_mod

Purpose:
Documentation source of truth.

Contains:
- README.md
- START_HERE_FOR_CHATGPT.md
- REPO_MAP.md
- MODULE_MAP.md
- CURRENT_STATUS.md
- CHAT_HANDOFF.md
- BUG_LOG.md

Does not contain custom module source code.

## 2. Custom Module Repo

Repository:
https://github.com/siddiquemdnoorealam-spec/fp-mod-17

Purpose:
Stores our own custom Odoo 17 modules.

Recommended structure:

```text
fp-mod-17/
├── README.md
└── addons/
    ├── fp_retail_base/
    ├── fp_quick_checkout/
    ├── fp_order_history/
    ├── fp_order_return_exchange/
    ├── fp_order_cancel/
    └── other fp_ modules
```

Rule:
Before any new work, observe existing modules in this repo.

## 3. Reference Module Repo

Repository:
https://github.com/siddiquemdnoorealam-spec/reference-mod-17

Purpose:
Stores reference modules or reference archives used only for studying behavior/workflow.

Recommended structure:

```text
reference-mod-17/
├── README.md
└── archives/
    ├── ref_a01.zip
    ├── ref_a02.zip
    ├── ref_a03.zip
    └── ref_a04.zip
```

Rule:
Reference modules must not be copied directly into our custom modules.
