# Cr/Dr Status rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/a2z/rules/cr_dr_status.py`](../../../../reconciliation/vendors/a2z/rules/cr_dr_status.py). See also [rules README](../../README.md).

| rule_order | cr | dr | remarks | status |
| --- | --- | --- | --- | --- |
| 1 | -- | -- | not-hits\|old-txn | Not-Hits/Old-Txn |
| 2 | -- | -- | <any non empty text> | <copy same text> |
| 3 | -- | Dr | refund okay | Refund Cr Pending |
| 4 | -- | Dr | success okay | Success Debit |
| 5 | Cr | -- | partial refunded | Partial Refunded Cr |
| 6 | Cr | -- | old-txn\|refund okay | Refund Cr |
| 0 | * | * | * | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Remark sets are matched case-insensitively.
