# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/airtel/rules/action_needed.py`](../../../../reconciliation/vendors/airtel/rules/action_needed.py). See also [rules README](../../README.md).

| rule_order | v_status | soul_status | txn_prefix | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | FAILED | HOLD\|IN PROCESS\|IN-PROCESS\|INITIATED\|INPROCESS\|PENDING\|UNDERPROCESS |  | RefundPending | Mark Refund | Refund Okay |
| 2 | SUCCESS | HOLD\|IN PROCESS\|IN-PROCESS\|INITIATED\|INPROCESS\|PENDING\|UNDERPROCESS |  | Success | Mark Success | Success Okay |
| 3 | TIMEOUT | HOLD\|IN PROCESS\|IN-PROCESS\|INITIATED\|INPROCESS\|PENDING\|UNDERPROCESS |  | *unchanged* | No Action Required | Okay |
| 4 | FAILED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | *unchanged* | No Action Required | Refund Okay |
| 5 | SUCCESS | SUCCESS |  | *unchanged* | No Action Required | Success Okay |
| 6 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Not-Hits |
| 7 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | not startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Old-Txn |
| 8 | -- | SUCCESS |  | *unchanged* | No Action Required | E-kyc |
| 9 | -- | INITIATED |  | RefundPending | Mark Refund | Not-Hits |
| 0 |  |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). `DMMYY` uses day without a leading zero (e.g. 7-Jun-2026 → `70626`).
