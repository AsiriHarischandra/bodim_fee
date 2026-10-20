# Architecture Decision Records (ADR)

An ADR is a short file that records **one important decision**, the **context**, the **options considered**, and **why** we chose one.
Industry teams use ADRs so new developers (and interviewers!) can understand *why* the system looks the way it does.

| # | Decision | Status |
|---|---|---|
| [0001](0001-modular-monolith.md) | Modular monolith instead of microservices | Accepted |
| [0002](0002-typescript-monorepo.md) | TypeScript monorepo with pnpm workspaces | Accepted |
| [0003](0003-postgresql-prisma.md) | PostgreSQL + Prisma for persistence | Accepted |
| [0004](0004-money-as-integer-cents-and-ledger.md) | Money as integer cents + append-only ledger | Accepted |
| [0005](0005-jwt-access-refresh-tokens.md) | JWT access token + rotating refresh token cookie | Accepted |
| [0006](0006-bullmq-background-jobs.md) | Redis + BullMQ for background and scheduled jobs | Accepted |
| [0007](0007-presigned-url-file-uploads.md) | S3-compatible storage with presigned URLs for receipts | Accepted |
| [0008](0008-express-layered-architecture.md) | Express with layered, feature-based modules | Accepted |
| [0009](0009-payment-methods.md) | Manual record-and-verify payments in V1, PayHere adapter in V2 | Accepted |

**Template for new ADRs:** copy `0000-template.md`.
