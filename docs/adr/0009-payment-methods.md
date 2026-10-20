# 0009. Manual record-and-verify payments in V1, PayHere adapter in V2

- **Status:** Accepted · **Date:** 2026-10-14

## Context
SRS V1: payments happen outside the system; BoardMate records and verifies. In Sri Lankan boarding houses members mostly pay by bank transfer or cash. V2 wants online payments.

## Options considered
1. Gateway from day one – needs merchant account, per-transaction fees, webhooks; contradicts SRS V1.
2. Receipt upload only – forces owners to fake uploads for cash payments.
3. **Three methods with a provider abstraction** – BANK_TRANSFER, CASH, ONLINE (later).

## Decision
- `payments.method` = `BANK_TRANSFER | CASH | ONLINE`.
- BANK_TRANSFER: member uploads receipt → PENDING → owner approves/rejects.
- CASH: owner records it → APPROVED immediately, system-generated receipt for the member.
- ONLINE (V2): `PaymentProvider` interface (Adapter/Strategy pattern); first implementation `PayHereProvider`. Payment confirmed **only** by a signature-verified webhook; `providerRef` unique → idempotent.
- All methods end in the same `approvePayment()` service → same ledger and bill-status logic.

## Consequences
+ Matches real-world usage; no fees for owners in V1.
+ Adding a gateway is a new adapter + webhook route, no billing changes.
− `receiptKey` becomes nullable; validation depends on method.
