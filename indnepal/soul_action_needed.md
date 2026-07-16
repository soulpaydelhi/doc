# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/indnepal/rules/action_needed.py`](../../../../reconciliation/vendors/indnepal/rules/action_needed.py). See also [rules README](../../README.md).

| rule_order | v_status | soul_status | txn_prefix | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | PAID | SUCCESS |  | *unchanged* | No Action Required | Success Okay |
| 2 | POST | SUCCESS |  | *unchanged* | No Action Required | Success Okay |
| 3 | CANCELLED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | *unchanged* | No Action Required | Refund Okay |
| 4 | COMPLIANCE | PENDING\|SUCCESS |  | *unchanged* | No Action Required | Okay |
| 5 | HOLD | PENDING\|SUCCESS |  | *unchanged* | No Action Required | Okay |
| 6 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Not-Hit |
| 7 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | not startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Old-Txn |
| 8 | -- | PENDING | startswith DMMYY(Tran Date) | RefundPending | Mark Refund | Not-Hit |
| 9 | -- | PENDING | not startswith DMMYY(Tran Date) | RefundPending | Mark Refund | Old-Txn |
| 0 |  |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). `DMMYY` uses day without a leading zero (e.g. 7-Jun-2026 → `70626`).
