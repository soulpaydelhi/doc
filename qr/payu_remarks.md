# Payu Remarks

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/qr/rules/payu_remarks.py`](../../../../reconciliation/vendors/qr/rules/payu_remarks.py). See also [rules README](../../README.md).

| rule_order | status | soul | udf2_count | remark |
| --- | --- | --- | --- | --- |
| 1 | CAPTURED | -- | 2 | Manual |
| 2 | !=CAPTURED | -- |  | Failed |
| 3 | CAPTURED | ACCEPTED\|PENDING |  | QR All Accepted |
| 0 |  |  |  | Use Case Not Defined |

Default remark applies when no rule matches.
