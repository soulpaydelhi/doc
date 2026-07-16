# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/a2z/rules/action_needed.py`](../../../../reconciliation/vendors/a2z/rules/action_needed.py). See also [rules README](../../README.md).

| rule_order | v_status | soul_status | txn_prefix | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Remark not empty | *unchanged* | No Action Required |  |
| 2 | SUCCESS | SUCCESS |  | *unchanged* | No Action Required | Success Okay |
| 3 | REFUNDSUC | SUCCESS |  | RefundPending | Mark Refund | Refund Okay |
| 4 | -- | REFUNDED | not startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Old-Txn |
| 5 | PARTIAL REFUNDED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | Ref# from Naration startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Refund Okay |
| 6 | PARTIAL REFUNDED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | Ref# from Naration not startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Old-Txn |
| 7 | PARTIAL REFUNDED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | *unchanged* | No Action Required | Partial Refunded |
| 0 |  |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). `DMMYY` uses day without a leading zero (e.g. 7-Jun-2026 → `70626`).
