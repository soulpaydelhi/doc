# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/indnepal/rules/led_remarks.py`](../../../../reconciliation/vendors/indnepal/rules/led_remarks.py). See also [rules README](../../README.md).

| rule_order | led_status | soul_status | description | transaction_type | remark |
| --- | --- | --- | --- | --- | --- |
| 1 | PAID\|POST | SUCCESS |  |  | Success Okay |
| 2 | COMPLIANCE\|HOLD | PENDING\|SUCCESS |  |  | Okay |
| 3 |  |  |  | VOUCHER | Fund |
| 4 | CANCELLED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  |  | Refund Okay |
| 5 | (blank)\|-- | (blank)\|-- | contains(CANCELLED\|REFUNDED) |  | Old-Txn |
| 0 |  |  |  |  | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Status/Soul comparisons are case-insensitive.
