# Led Remarks rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/swift/rules/led_remarks.py`](../../../../reconciliation/vendors/swift/rules/led_remarks.py). See also [rules README](../../README.md).

| rule_order | perticular | swift | soul | transaction_type | count | remark |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | "tds" in Perticular (case-insensitive) |  |  |  |  | TDS |
| 2 | "commission" in Perticular (case-insensitive) |  |  |  |  | COMM |
| 3 |  | REFUND | REFUNDPENDING |  |  | Refund Cr Pending |
| 4 |  | REFUND | REFUNDCOMPLETED\|REFUNDED |  |  | Refund Okay |
| 5 |  | SUCCESS | SUCCESS |  |  | Success Okay |
| 6 |  | SUCCESS | -- |  |  | Offline |
| 7 |  | -- | -- | CR | > 0 | Old-Txn |
| 8 |  | -- | -- | CR | 0 or blank | Fund |
| 0 |  |  |  |  |  | Use Case Not Defined |

**Particular phase:** rules 1–2 run first (`TDS` / `COMM`). **Status phase:** rules 3–8 apply only when particular did not match. **Default:** rule 0 when no row matches (`Use Case Not Defined`). Swift/Soul comparisons are case-insensitive.
