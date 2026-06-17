# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/airtel/rules/led_remarks.py`](../../../../reconciliation/vendors/airtel/rules/led_remarks.py). See also [rules README](../../README.md).

| rule_order | partner_status | soul_status | transaction_amount | transaction_type | remark |
| --- | --- | --- | --- | --- | --- |
| 1 | -- | -- | 10.01 |  | E-kyc |
| 2 | -- | -- |  | CR | Fund |
| 3 | FAILED | REFUNDPENDING |  |  | Refund Okay |
| 4 | SUCCESS | SUCCESS |  |  | Success Okay |
| 5 | TIMEOUT | UNDERPROCESS |  |  | Okay |
| 0 |  |  |  |  | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`).
