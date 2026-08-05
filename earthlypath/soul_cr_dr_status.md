# Cr/Dr Status rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/earthlypath/rules/cr_dr_status.py`](../../../../reconciliation/vendors/earthlypath/rules/cr_dr_status.py). See also [rules README](../../README.md).

| rule_order | cr | dr | remarks | status |
| --- | --- | --- | --- | --- |
| 1 | Cr | Dr | * | Refund Cr |
| 2 | -- | Dr | refund okay | Refund Cr Pending |
| 3 | -- | Dr | success okay | Success Dr |
| 4 | -- | -- | * | Not-Hits/Old-Txn |
| 0 | * | * | * | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Remark sets are matched case-insensitively.
