# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/airtel/rules/action_needed.py`](../../../../reconciliation/vendors/airtel/rules/action_needed.py). See also [rules README](../../README.md).

| rule_order | v_status | soul_status | txn_prefix | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | FAILED | INITIATED |  | RefundPending | Mark Refund | Refund Okay |
| 2 | FAILED | UNDERPROCESS |  | RefundPending | Mark Refund | Refund Okay |
| 3 | SUCCESS | UNDERPROCESS |  | Success | Mark Success | Success Okay |
| 4 | SUCCESS | INITIATED |  | Success | Mark Success | Success Okay |
| 5 | FAILED | HOLD |  | RefundPending | Mark Refund | Refund Okay |
| 6 | FAILED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | *unchanged* | No Action Required | Refund Okay |
| 7 | SUCCESS | HOLD |  | Success | Mark Success | Success Okay |
| 8 | SUCCESS | SUCCESS |  | *unchanged* | No Action Required | Success Okay |
| 9 | TIMEOUT | UNDERPROCESS |  | *unchanged* | No Action Required | Okay |
| 10 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Not-Hits |
| 11 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | not startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Old-Txn |
| 12 | -- | SUCCESS |  | *unchanged* | No Action Required | E-kyc |
| 13 | -- | INITIATED |  | RefundPending | Mark Refund | Not-Hits |
| 14 | FAILED | IN PROCESS |  | RefundPending | Mark Refund | Refund Okay |
| 15 | FAILED | IN-PROCESS |  | RefundPending | Mark Refund | Refund Okay |
| 16 | FAILED | INPROCESS |  | RefundPending | Mark Refund | Refund Okay |
| 17 | SUCCESS | IN PROCESS |  | Success | Mark Success | Success Okay |
| 18 | SUCCESS | IN-PROCESS |  | Success | Mark Success | Success Okay |
| 19 | SUCCESS | INPROCESS |  | Success | Mark Success | Success Okay |
| 20 | TIMEOUT | IN PROCESS |  | *unchanged* | No Action Required | Okay |
| 21 | TIMEOUT | IN-PROCESS |  | *unchanged* | No Action Required | Okay |
| 22 | TIMEOUT | INPROCESS |  | *unchanged* | No Action Required | Okay |
| 0 |  |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Rows after the core rules list alternate `soul_status` spellings (`IN PROCESS`, `INPROCESS`, `IN-PROCESS`) that normalize to the same canonical status before matching. `DMMYY` uses day without a leading zero (e.g. 7-Jun-2026 → `70626`).
