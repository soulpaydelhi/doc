# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation_led_rules.py`](../../reconciliation_led_rules.py). See also [rules README](../README.md).

| rule_order | airtel_status | soul_status | transaction_amount | transaction_type | remark |
| --- | --- | --- | --- | --- | --- |
| 1 | -- | -- | 10.01 |  | E-kyc |
| 2 | -- | -- |  | CR | Fund |
| 3 | -- | -- |  |  | Use Case Not Defined |
| 4 | FAILED | REFUNDPENDING |  |  | Refund Okay |
| 5 | SUCCESS | SUCCESS |  |  | Success Okay |
| 6 | TIMEOUT | UNDERPROCESS |  |  | Okay |
| 0 |  |  |  |  | Use Case Not Defined |

**Default:** `rule_order` 0 applies when Airtel/Soul do not match any row and are not both `--` (`Use Case Not Defined`).
