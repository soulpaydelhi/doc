# Eb Remarks

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/qr/rules/eb_remarks.py`](../../../../reconciliation/vendors/qr/rules/eb_remarks.py). See also [rules README](../../README.md).

| rule_order | status | soul | remark |
| --- | --- | --- | --- |
| 1 | FAILURE | -- | Failed |
| 2 | RECEIVED | ACCEPTED|PENDING | QR All Accepted |
| 3 | RECEIVED | -- | Trigger |
| 0 |  |  | Use Case Not Defined |

Default remark applies when no rule matches.
