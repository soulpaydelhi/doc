# Cr/Dr Status rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/indicore/rules/cr_dr_status.py`](../../../../reconciliation/vendors/indicore/rules/cr_dr_status.py). See also [rules README](../../README.md).

| rule_order | cr | dr | remarks | soul_status | status |
| --- | --- | --- | --- | --- | --- |
| 1 | Credit | Debit | refund okay | REFUNDCOMPLETED\|REFUNDED | Refund Credit |
| 2 | -- | Debit | refund okay | REFUNDPENDING | Refund Cr Pending |
| 3 | -- | Debit | success okay | SUCCESS | Success Debit |
| 4 | -- | -- | not-hits\|old-txn | * | Old-Txn/Not-Hits |
| 0 | * | * | * | * | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Remark and Soul Status comparisons are case-insensitive.
