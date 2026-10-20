# BoardMate — Build & Learning Roadmap

We build in **phases**. Each phase produces something that works, and teaches specific concepts.
For every step we write down: **What** we did · **Why** · **How it works** · **Where → where** the data flows · **Interview questions**.
Your personal notes go in `docs/learning/phase-XX.md` (create one per phase).

| Phase | Build | You will learn |
|---|---|---|
| **0. Foundation** ✅ (now) | SRS, architecture, ADRs, folder structure | System design, monolith vs microservices, monorepo, choosing a stack |
| **1. Tooling** | pnpm workspaces, TypeScript configs, ESLint/Prettier, Husky, Commitlint, Docker Compose (Postgres, Redis, MinIO, Mailpit) | How Node projects are wired, tsconfig, linting, git hooks, containers, env variables |
| **2. API skeleton** | Express app, config validation, logger, request-id, error handler, health check, first test | HTTP, middleware chain, request lifecycle, error handling, Supertest |
| **3. Database** | Prisma schema (all V1 tables), migrations, seed script | Relational modelling, keys, indexes, constraints, migrations, ORM vs SQL |
| **4. Auth** | Register owner, login, refresh rotation, logout, password reset, `authenticate` middleware | Hashing, JWT internals, cookies, CORS, CSRF, XSS, rate limiting |
| **5. Frontend skeleton** | Vite React app, routing, layouts, Tailwind/shadcn, axios + interceptor, auth pages | SPA, React rendering, hooks, state types, token refresh flow |
| **6. Houses & members** | Create house, invitations by email, accept invite, member profile, activate/deactivate | Multi-tenancy, RBAC, IDOR prevention, email via queue (first BullMQ job) |
| **7. Billing** | Periods, expenses, publish → bills, ledger, carry-forward | Transactions, locking, idempotency, money math, unit-testing business rules |
| **8. Payments** | Presigned uploads, submit payment, approve/reject, status derivation | Object storage, file validation, state machines, concurrency |
| **9. Notifications** | Notification table, Socket.IO, bell UI, scheduled jobs (overdue, reminders, birthdays) | WebSockets, pub/sub, cron jobs, timezones |
| **10. Dashboards & reports** | Owner/member dashboards, 3 reports, announcements | SQL aggregation, query performance, caching, charts |
| **11. Quality** | Integration + E2E tests, OpenAPI docs, audit log, security review | Testing pyramid, API docs, OWASP Top 10 |
| **12. Ship it** | GitHub Actions CI, Dockerfiles, deploy staging/prod, backups, monitoring | CI/CD, containers in prod, 12-factor, observability |

## Rules we follow while building
1. One feature branch per step → PR → merge. Commit messages use Conventional Commits.
2. Never copy code you can't explain. If something is unclear, stop and ask "why?".
3. Write the test for business rules **before** or **with** the code.
4. Update the docs/ADR when a decision changes.
