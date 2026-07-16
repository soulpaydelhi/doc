# Cr/Dr Status rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/indnepal/rules/cr_dr_status.py`](../../../../reconciliation/vendors/indnepal/rules/cr_dr_status.py). See also [rules README](../../README.md).

| rule_order | cr | dr | remarks | status |
| --- | --- | --- | --- | --- |
| 1 | -- | Dr | okay\|success okay | Success Debit |
| 2 | -- | -- | not-hit\|old-txn | Not-Hits/Old-Txn |
| 3 | Cr | -- | refund okay | Refund Credit |
| 4 | Cr | Dr | refund okay | Refund Credit |
| 5 | Cr | -- | old-txn | Old Refund Credit |
| 6 | Cr | Dr | old-txn | Old Refund Credit |
| 0 | * | * | * | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Remark sets are matched case-insensitively.
