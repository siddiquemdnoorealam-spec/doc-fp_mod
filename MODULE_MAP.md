# Module Map

This file tracks all custom modules and their relationships.

## Current Mode

Existing module continuation mode.

Existing modules should be added here after they are uploaded to the custom module repo.

## Core Modules To Observe First

When available in `fp-mod-17`, always check these modules before creating/fixing related features:

| Module | Purpose | Status | Depends On | Related Modules |
|---|---|---|---|---|
| fp_retail_base | Foundation/common helper module | To be confirmed | point_of_sale | all POS modules |
| fp_quick_checkout | 3-column quick checkout screen | To be confirmed | fp_retail_base, point_of_sale | payment, return, order history |
| fp_order_history | Previous POS order/history flow | To be confirmed | point_of_sale | return, cancel, reprint |
| fp_order_return_exchange | Return/exchange flow | To be confirmed | fp_order_history | quick checkout, cancel |
| fp_order_cancel | POS order cancel flow | To be confirmed | fp_order_history | quick checkout, return/exchange |

## Module Update Rule

When a new module is created or uploaded, add/update:
- module name
- purpose
- dependency
- related modules
- status

## Status Values

Use simple status:
- Planned
- Uploaded
- In Progress
- Testing
- Stable
- Blocked
