# Repository Map

This file records all repositories used by the project.

## 1. Document Repository

Repo:  
https://github.com/siddiquemdnoorealam-spec/doc-fp_mod

Purpose:

- Permanent documentation source of truth
- Current project status
- Latest handoff
- Chat/task history
- Bug/error history
- Module relationship map

Important:

- This repo should not be deleted.
- This repo stores project memory and documentation.
- No custom Odoo module source code should be placed here.

## 2. Custom Module Repository

Repo / branch:  
https://github.com/siddiquemdnoorealam-spec/fp-mod-17/tree/pos_fp_17

Purpose:

- Temporary working repo for custom Odoo 17 modules
- Existing module continuation work
- New custom modules under `fp_` namespace

Important:

- This repo/branch contains the current working module code.
- Existing modules must be observed before making new code.
- This repo may be temporary, so important summaries must be saved in `doc-fp_mod`.

## 3. Reference Module Repository

Repo:  
https://github.com/siddiquemdnoorealam-spec/reference-mod-17

Purpose:

- Store reference modules / archives
- Study workflow, behavior, and UI idea
- Do not copy-paste reference code

Important:

- Reference code is not the final implementation.
- Final custom implementation must be fresh and under `fp_` namespace.
