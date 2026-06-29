# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/swift/rules/action_needed.py`](../../../../reconciliation/vendors/swift/rules/action_needed.py). See also [rules README](../../README.md).

| rule_order | v_status | soul_status | txn_prefix | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | REFUND | SUCCESS |  | RefundPending | Mark Refund | Refund Okay |
| 2 | REFUND | REFUNDPENDING |  | *unchanged* | No Action Required | Refund Okay |
| 3 | REFUND | REFUNDCOMPLETED |  | *unchanged* | No Action Required | Refund Okay |
| 4 | REFUND | REFUNDED |  | *unchanged* | No Action Required | Refund Okay |
| 5 | SUCCESS | SUCCESS |  | *unchanged* | No Action Required | Success Okay |
| 6 | -- | SUCCESS |  | *unchanged* | No Action Required | Offline |
| 7 | -- | INITIATED |  | *unchanged* | No Action Required | Offline |
| 8 | -- | UNDERPROCESS |  | RefundPending | Mark Refund | Not-Hits |
| 9 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Not-Hits |
| 10 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | not startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Old-Txn |
| 11 | -- | INITIATE |  | *unchanged* | No Action Required | Offline |
| 0 |  |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Rows after the core rules list alternate `soul_status` spellings (`IN PROCESS`, `INPROCESS`, `IN-PROCESS`) that normalize to the same canonical status before matching. `DMMYY` uses day without a leading zero (e.g. 7-Jun-2026 → `70626`).
