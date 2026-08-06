# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/earthlypath/rules/action_needed.py`](../../../../reconciliation/vendors/earthlypath/rules/action_needed.py). See also [rules README](../../README.md).

| rule_order | v_status | soul_status | txn_prefix | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | FAILED | SUCCESS |  | RefundPending | Mark Refund | Refund Okay |
| 2 | FAILED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | *unchanged* | No Action | Refund Okay |
| 3 | SUCCESS | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | *unchanged* | Wrong Refund | Wrong Refund |
| 4 | SUCCESS | HOLD\|IN PROCESS\|IN-PROCESS\|INITIATED\|INPROCESS\|PENDING\|UNDERPROCESS |  | Success | Mark Success | Success Okay |
| 5 | SUCCESS | SUCCESS |  | *unchanged* | No Action | Success Okay |
| 6 | PENDING | HOLD\|IN PROCESS\|IN-PROCESS\|INITIATED\|INPROCESS\|PENDING\|UNDERPROCESS |  | *unchanged* | No Action | Okay |
| 7 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | not startswith DMMYY(Tran Date) | *unchanged* | No Action | Old-Txn |
| 8 | -- | HOLD\|IN PROCESS\|IN-PROCESS\|INITIATED\|INPROCESS\|PENDING\|REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING\|UNDERPROCESS | startswith DMMYY(Tran Date) | *unchanged* | No Action | Not-Hits |
| 0 |  |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). `DMMYY` uses day without a leading zero (e.g. 7-Jun-2026 → `70626`).
