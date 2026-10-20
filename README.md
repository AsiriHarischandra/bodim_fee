# BoardMate

**Boarding house management & payment tracking — made simple for owners and members.**

BoardMate helps boarding house owners manage members, split monthly expenses, generate bills, verify payment receipts, track outstanding balances and keep everyone informed with real-time notifications.

> Status: 🏗️ Phase 0 — architecture & project setup

## Features (V1)
- Boarding house & member management (invitations, profiles, active/inactive)
- Monthly expenses with automatic equal split
- Bill generation with carry-forward outstanding balances
- Partial & multiple payments with receipt upload (JPG/PNG/PDF)
- Owner receipt verification (approve / reject with reason)
- Payment statuses: Pending, Under Review, Partially Paid, Paid, Overdue, Rejected
- Real-time notifications, due reminders, birthday reminders, announcements
- Owner & member dashboards, collection and payment reports
- Full audit trail — nothing is permanently deleted

## Tech stack
| Area | Tech |
|---|---|
| Frontend | React 18, TypeScript, Vite, React Router, TanStack Query, Zustand, React Hook Form, Zod, Tailwind CSS, shadcn/ui |
| Backend | Node.js 22, Express 5, TypeScript, Zod, Prisma |
| Data | PostgreSQL 16, Redis 7, S3-compatible storage (MinIO / Cloudflare R2) |
| Async | BullMQ (jobs & schedules), Socket.IO (real-time) |
| Quality | Vitest, Supertest, Playwright, ESLint, Prettier, Husky, Commitlint |
| DevOps | Docker Compose, GitHub Actions |

## Repository structure
```
apps/api        Express REST API + background worker
apps/web        React single-page app
packages/shared Shared Zod schemas, types, enums, money utilities
infra/docker    Local infrastructure (Postgres, Redis, MinIO, Mailpit)
docs/           Architecture, ADRs, learning roadmap, SRS
```

## Documentation
- [Architecture](docs/ARCHITECTURE.md)
- [Architecture Decision Records](docs/adr/README.md)
- [Design system (UI)](docs/DESIGN_SYSTEM.md)
- [Build & learning roadmap](docs/LEARNING_ROADMAP.md)
- [Software Requirements Specification](docs/srs/Software_Requirements_Specification.pdf)

## Getting started
_Set up in Phase 1 (tooling)._ Prerequisites: Node.js 22 LTS, pnpm 9, Docker Desktop, Git.
