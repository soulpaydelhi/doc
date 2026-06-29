# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/airtel/rules/led_remarks.py`](../../../../reconciliation/vendors/airtel/rules/led_remarks.py). See also [rules README](../../README.md).

| rule_order | partner_status | soul_status | transaction_amount | transaction_type | apb_txn_id | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | -- | -- | 10.01 |  |  | E-kyc |
| 2 | -- | -- |  |  | startswith `R_` | Old-Txn |
| 3 | -- | -- |  | CR |  | Fund |
| 4 | FAILED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  |  |  | Refund Okay |
| 5 | SUCCESS | SUCCESS |  |  |  | Success Okay |
| 6 | TIMEOUT | UNDERPROCESS |  |  |  | Okay |
| 0 |  |  |  |  |  | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`).
