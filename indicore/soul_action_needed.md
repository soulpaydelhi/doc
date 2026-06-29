# Action Needed rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/indicore/rules/action_needed.py`](../../../../reconciliation/vendors/indicore/rules/action_needed.py). See also [rules README](../../README.md).

| rule_order | v_status | soul_status | txn_prefix | status_after | action_needed | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | FAILED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | *unchanged* | No Action Required | Refund Okay |
| 2 | SUCCESS | SUCCESS |  | *unchanged* | No Action Required | Success Okay |
| 3 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Not-Hits |
| 4 | -- | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | not startswith DMMYY(Tran Date) | *unchanged* | No Action Required | Old-Txn |
| 0 |  |  |  |  | Use Case Not Defined |  |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`); Remark is left empty. `DMMYY` uses day without a leading zero (e.g. 7-Jun-2026 → `70626`).
