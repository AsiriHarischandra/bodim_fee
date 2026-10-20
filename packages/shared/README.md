# @boardmate/shared

Code used by **both** API and web, so rules are defined once:

- `src/schemas` – Zod request/response schemas (validation + inferred TS types)
- `src/enums` – Role, MemberStatus, BillStatus, PaymentStatus, ExpenseCategory, NotificationType
- `src/money` – cents helpers, fair split with remainder, LKR formatting (heavily unit-tested)
- `src/types` – shared TypeScript types (API response envelope, pagination)
