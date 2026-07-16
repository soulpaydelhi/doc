# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/a2z/rules/led_remarks.py`](../../../../reconciliation/vendors/a2z/rules/led_remarks.py). See also [rules README](../../README.md).

| rule_order | led_status | soul_status | description | remark |
| --- | --- | --- | --- | --- |
| 1 | SUCCESS | SUCCESS |  | Success Okay |
| 2 | REFUNDSUC | REFUNDPENDING |  | Refund Okay |
| 3 | DEBIT | NA |  | Manual Verify |
| 4 | PARTIAL REFUNDED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING |  | copy from Soul_Remarks |
| 5 | CREDIT | NA | Fund Request | Fund |
| 0 |  |  |  | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Status/Soul comparisons are case-insensitive.
