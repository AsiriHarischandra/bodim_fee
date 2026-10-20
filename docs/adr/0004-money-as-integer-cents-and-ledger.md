# 0004. Money as integer cents + append-only ledger

- **Status:** Accepted · **Date:** 2026-10-08

## Context
Floating point cannot represent money exactly (`0.1 + 0.2 = 0.30000000000000004`). SRS requires partial payments, multiple payments, carry-forward balances and audit trail.

## Decision
- Store all amounts as **BIGINT minor units (cents)**.
- Split shared expenses with **remainder distribution** so the sum of shares equals the total exactly.
- Keep an **append-only `ledger_entries` table**: CHARGE (+) when a bill is published, PAYMENT (−) when a payment is approved, ADJUSTMENT for corrections. A member's balance = SUM(amount). Rows are never updated or deleted.
- `bills.paid_cents` and `status` are denormalised for fast reads, updated in the same transaction.

## Consequences
+ Exact arithmetic; carry-forward = current ledger balance.
+ Full history for audit (FR-20); easy reconciliation.
− Corrections must be new ADJUSTMENT entries, not edits (this is correct accounting practice).
