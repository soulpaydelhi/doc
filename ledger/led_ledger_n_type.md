# Ledger N Type rules

Rules are evaluated **top to bottom**; the **first matching row wins**.
Source: [`ledger/n_type_rules.py`](../../../../ledger/n_type_rules.py). See also [rules README](../../README.md).

| Rule | Code behavior |
| --- | --- |
| Comm | `"commission:" in naration (case-insensitive)` |
| AEPS | `Only if Comm didn't match; "ap-aeps-m" in services (case-insensitive); both amounts zero` |
| MATM | `Only if Comm/AEPS didn't match; "matm-matm-cw" in services (case-insensitive); both amounts zero` |
| Refund | `Only if none above; amount_dr zero; status is "Refunded", "RefundPending", or "RefundCompleted" (case-insensitive)` |
| Cr | `Only if none above; amount_dr zero; status == "Success" (exact)` |
| Txn | `Only if none above; amount_dr not zero` |
| Reversed | `Only if none above; "fund ref#" in naration (case-insensitive); status is "ReverseComplated" or "Reversed" (exact)` |

**Unmatched:** blank `N Type` when no rule matches (see `classify_n_type`).
