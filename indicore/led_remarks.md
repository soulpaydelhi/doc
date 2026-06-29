# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/indicore/rules/led_remarks.py`](../../../../reconciliation/vendors/indicore/rules/led_remarks.py). See also [rules README](../../README.md).

| rule_order | led_status | soul_status | remark |
| --- | --- | --- | --- |
| 1 | FAILED | REFUNDCOMPLETED\|REFUNDED\|REFUNDPENDING | Refund Okay |
| 2 | SUCCESS | SUCCESS | Success Okay |
| 0 |  |  | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Status/Soul comparisons are case-insensitive.
