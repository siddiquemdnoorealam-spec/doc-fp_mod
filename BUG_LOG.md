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

## BUG-003 - order button e click korle white screen eshe stuck hoye jacche. reload dile pos screen e chole asteche.
odoo log - 
odoo@2c890a5c98ac:/$ tail -n 10 -f /var/log/odoo/odoo.log
2026-05-27 20:26:23,686 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:23] "GET /pos/ui?config_id=1&debug=1 HTTP/1.1" 200 - 17 0.003 0.008
2026-05-27 20:26:23,817 1 DEBUG pos_module_create_testdb odoo.api: call barcode.nomenclature(1,).read(['name', 'rule_ids', 'upc_ean_conv', 'is_gs1_nomenclature', 'gs1_separator_fnc1'])
2026-05-27 20:26:23,819 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:23] "POST /web/dataset/call_kw/barcode.nomenclature/read HTTP/1.1" 200 - 3 0.001 0.003
2026-05-27 20:26:23,827 1 DEBUG pos_module_create_testdb odoo.api: call barcode.rule().search_read(domain=[['barcode_nomenclature_id', '=', 1]], fields=['name', 'sequence', 'type', 'encoding', 'pattern', 'alias', 'gs1_content_type', 'gs1_decimal_usage', 'associated_uom_id'])
2026-05-27 20:26:23,828 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:23] "POST /web/dataset/call_kw/barcode.rule/search_read HTTP/1.1" 200 - 2 0.000 0.002
2026-05-27 20:26:23,855 1 DEBUG pos_module_create_testdb odoo.api: call pos.session(32,).load_pos_data()
2026-05-27 20:26:23,971 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:23] "POST /web/dataset/call_kw/pos.session/load_pos_data HTTP/1.1" 200 - 147 0.029 0.089
2026-05-27 20:26:23,981 1 DEBUG pos_module_create_testdb odoo.api: call ir.model.data().check_object_reference('uom', 'product_uom_unit')
2026-05-27 20:26:23,982 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:23] "POST /web/dataset/call_kw/ir.model.data/check_object_reference HTTP/1.1" 200 - 2 0.000 0.002
2026-05-27 20:26:24,018 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:24] "GET /web/image/res.users/2/avatar_128 HTTP/1.1" 304 - 8 0.002 0.005
2026-05-27 20:26:47,093 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:47] "GET /pos/ui?config_id=1&debug=1 HTTP/1.1" 200 - 17 0.003 0.008
2026-05-27 20:26:47,160 1 DEBUG pos_module_create_testdb odoo.api: call barcode.nomenclature(1,).read(['name', 'rule_ids', 'upc_ean_conv', 'is_gs1_nomenclature', 'gs1_separator_fnc1'])
2026-05-27 20:26:47,161 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:47] "POST /web/dataset/call_kw/barcode.nomenclature/read HTTP/1.1" 200 - 3 0.000 0.002
2026-05-27 20:26:47,168 1 DEBUG pos_module_create_testdb odoo.api: call barcode.rule().search_read(domain=[['barcode_nomenclature_id', '=', 1]], fields=['name', 'sequence', 'type', 'encoding', 'pattern', 'alias', 'gs1_content_type', 'gs1_decimal_usage', 'associated_uom_id'])
2026-05-27 20:26:47,169 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:47] "POST /web/dataset/call_kw/barcode.rule/search_read HTTP/1.1" 200 - 2 0.000 0.002
2026-05-27 20:26:47,177 1 DEBUG pos_module_create_testdb odoo.api: call pos.session(32,).load_pos_data()
2026-05-27 20:26:47,288 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:47] "POST /web/dataset/call_kw/pos.session/load_pos_data HTTP/1.1" 200 - 147 0.025 0.087
2026-05-27 20:26:47,298 1 DEBUG pos_module_create_testdb odoo.api: call ir.model.data().check_object_reference('uom', 'product_uom_unit')
2026-05-27 20:26:47,299 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:47] "POST /web/dataset/call_kw/ir.model.data/check_object_reference HTTP/1.1" 200 - 2 0.000 0.002
2026-05-27 20:26:47,338 1 INFO pos_module_create_testdb werkzeug: 192.168.1.2 - - [27/May/2026 20:26:47] "GET /web/image/res.users/2/avatar_128 HTTP/1.1" 304 - 8 0.002 0.005
^A