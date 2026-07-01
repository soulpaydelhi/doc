# Va EB Remarks

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/qr/rules/va_eb_remarks.py`](../../../../reconciliation/vendors/qr/rules/va_eb_remarks.py). See also [rules README](../../README.md).

| rule_order | service_filter | status | eb | txn_prefix | remark |
| --- | --- | --- | --- | --- | --- |
| 1 | Type: QR2\|Easebuzz |  | RECEIVED |  | QR All Accepted |
| 2 | Type: QR2\|Easebuzz | ACCEPTED\|PENDING\|SUCCESS | TIMED OUT\|TIMED-OUT\|TIMEDOUT\|UNSETTLED |  | QR All Accepted |
| 3 | Type: QR2\|Easebuzz |  | -- | startswith DMMYY(Tran Date) | Trigger |
| 0 |  |  |  |  | Old-Txn |

Default remark applies when no rule matches.
