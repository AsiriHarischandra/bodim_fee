# @boardmate/api

Express 5 + TypeScript REST API and BullMQ worker. See [docs/ARCHITECTURE.md §6](../../docs/ARCHITECTURE.md#6-backend-architecture-layers).

| Folder | Purpose |
|---|---|
| `src/config` | Load + validate environment variables (fail fast on boot) |
| `src/lib` | Infrastructure clients: Prisma, Redis, S3, mailer, logger, Socket.IO |
| `src/middlewares` | authenticate, requireHouseRole, validate, errorHandler, rateLimit, requestId |
| `src/modules/<feature>` | `*.routes.ts` → `*.controller.ts` → `*.service.ts` → `*.repository.ts` (+ `*.schemas.ts`, `*.test.ts`) |
| `src/jobs` | Queues, schedulers and job processors (run by `worker.ts`) |
| `src/shared` | AppError classes, pagination, small helpers |
| `prisma/` | `schema.prisma`, migrations, seed |
| `tests/integration` | Supertest tests against a real Postgres |

Entry points (created in Phase 2): `src/app.ts` (build app), `src/server.ts` (HTTP + sockets), `src/worker.ts` (jobs).
