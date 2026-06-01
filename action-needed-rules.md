# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation_rules.py`](../../reconciliation_rules.py). See also [rules README](../README.md).

| rule_order | v_status | soul_status | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- |
| 1 | FAILED | INITIATED | RefundPending | Mark Refund | Refund Okay |
| 2 | FAILED | UNDERPROCESS | RefundPending | Mark Refund | Refund Okay |
| 3 | SUCCESS | UNDERPROCESS | Success | Mark Success | Success Okay |
| 4 | SUCCESS | INITIATED | Success | Mark Success | Success Okay |
| 5 | FAILED | HOLD | RefundPending | Mark Refund | Refund Okay |
| 6 | SUCCESS | HOLD | Success | Mark Success | Success Okay |
| 7 | SUCCESS | SUCCESS | *unchanged* | No Action Required | Success Okay |
| 8 | TIMEOUT | UNDERPROCESS | *unchanged* | No Action Required | Okay |
| 9 | -- | REFUNDED | *unchanged* | No Action Required | Old-Txn |
| 10 | -- | SUCCESS | *unchanged* | No Action Required | E-kyc |
| 11 | -- | INITIATED | RefundPending | Mark Refund | Not-Hits |
| 12 | FAILED | IN PROCESS | RefundPending | Mark Refund | Refund Okay |
| 13 | FAILED | IN-PROCESS | RefundPending | Mark Refund | Refund Okay |
| 14 | FAILED | INPROCESS | RefundPending | Mark Refund | Refund Okay |
| 15 | SUCCESS | IN PROCESS | Success | Mark Success | Success Okay |
| 16 | SUCCESS | IN-PROCESS | Success | Mark Success | Success Okay |
| 17 | SUCCESS | INPROCESS | Success | Mark Success | Success Okay |
| 18 | TIMEOUT | IN PROCESS | *unchanged* | No Action Required | Okay |
| 19 | TIMEOUT | IN-PROCESS | *unchanged* | No Action Required | Okay |
| 20 | TIMEOUT | INPROCESS | *unchanged* | No Action Required | Okay |
| 0 |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Rows after the core rules list alternate `soul_status` spellings (`IN PROCESS`, `INPROCESS`, `IN-PROCESS`) that normalize to the same canonical status before matching.
