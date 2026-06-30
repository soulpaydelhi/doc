# Soul EB Remarks

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/qr/rules/soul_eb_remarks.py`](../../../../reconciliation/vendors/qr/rules/soul_eb_remarks.py). See also [rules README](../../README.md).

| rule_order | service_filter | eb | txn_prefix | remark |
| --- | --- | --- | --- | --- |
| 1 | Services: Easebuzz|QR2 | RECEIVED |  | QR All Accepted |
| 2 | Services: Easebuzz|QR2 | -- | startswith DMMYY(Tran Date) | Trigger |
| 0 |  |  |  | Old-Txn |

Default remark applies when no rule matches.
