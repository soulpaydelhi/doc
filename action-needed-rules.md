# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation_rules.py`](../../reconciliation_rules.py). See also [rules README](../README.md).

| rule_order | v_status | soul_status | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- |
| 1 | FAILED | INITIATED | RefundPending | Mark Refund | Refund Okay |
| 2 | FAILED | UNDERPROCESS | RefundPending | Mark Refund | Refund Okay |
| 3 | SUCCESS | UNDERPROCESS | Success | Mark Success | Success Okay |
| 4 | SUCCESS | INITIATED | Success | Mark Success | Success Okay |
| 5 | SUCCESS | SUCCESS | *unchanged* | No Action Required | Success Okay |
| 6 | TIMEOUT | UNDERPROCESS | *unchanged* | No Action Required | Okay |
| 7 | -- | REFUNDED | *unchanged* | No Action Required | Old-Txn |
| 8 | -- | SUCCESS | *unchanged* | No Action Required | E-kyc |
| 9 | -- | INITIATED | RefundPending | Mark Refund | Not-Hits |
| 0 |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`).
