# Eb Remarks

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/qr/rules/eb_remarks.py`](../../../../reconciliation/vendors/qr/rules/eb_remarks.py). See also [rules README](../../README.md).

| rule_order | status | soul | utr_count | remark |
| --- | --- | --- | --- | --- |
| 1 | FAILURE | -- |  | Failed |
| 2 | TIMED OUT\|TIMED-OUT\|TIMEDOUT\|UNSETTLED | -- |  | Okay |
| 3 | RECEIVED | ACCEPTED\|PENDING |  | QR All Accepted |
| 4 | TIMED OUT\|TIMED-OUT\|TIMEDOUT\|UNSETTLED | ACCEPTED\|PENDING\|SUCCESS |  | QR All Accepted |
| 5 | RECEIVED | -- | 2 | Manual |
| 6 | RECEIVED | -- |  | Trigger |
| 0 |  |  |  | Use Case Not Defined |

Default remark applies when no rule matches.
