# Cr/Dr Status rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`reconciliation/vendors/airtel/rules/cr_dr_status.py`](../../../../reconciliation/vendors/airtel/rules/cr_dr_status.py). See also [rules README](../../README.md).

| rule_order | cr | dr | remarks | status |
| --- | --- | --- | --- | --- |
| 1 | -- | Dr | okay|success okay | Success Dr |
| 2 | -- | -- | e-kyc | E-kyc |
| 3 | -- | -- | not-hits|old-txn | Old-Txn/Not-Hits |
| 4 | Cr | Dr | * | Refund Cr |
| 0 | * | * | * | Use Case Not Defined |

**Default:** `rule_order` 0 applies when no rule matches (`Use Case Not Defined`). Remark sets are matched case-insensitively.
