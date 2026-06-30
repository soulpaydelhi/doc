# Va Payu Remarks

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/qr/rules/va_payu_remarks.py`](../../../../reconciliation/vendors/qr/rules/va_payu_remarks.py). See also [rules README](../../README.md).

| rule_order | service_filter | payu | txn_prefix | remark |
| --- | --- | --- | --- | --- |
| 1 | Type: Payu|UPI_Collection | CAPTURED |  | QR All Accepted |
| 0 |  |  |  | Use Case Not Defined |

Default remark applies when no rule matches.
