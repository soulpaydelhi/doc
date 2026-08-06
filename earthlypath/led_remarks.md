# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/earthlypath/rules/led_remarks.py`](../../../../reconciliation/vendors/earthlypath/rules/led_remarks.py). See also [rules README](../../README.md).

| rule_order | partner_status | soul_status | transaction_amount | transaction_type | cr_dr_type | apb_txn_id | remark |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | FAILED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  |  |  |  | Refund Okay |
| 2 | SUCCESS | SUCCESS |  |  |  |  | Success Okay |
| 3 | PENDING | HOLD\|IN PROCESS\|IN-PROCESS\|INITIATED\|INPROCESS\|PENDING\|UNDERPROCESS |  |  |  |  | Okay |
| 4 | -- | -- |  | Payment Request | CREDIT |  | Fund |
| 0 |  |  |  |  |  |  | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`).
