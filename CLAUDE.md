# BoardMate — instructions for Claude

## The project
BoardMate is a web app for boarding house owners in Sri Lanka: members, monthly shared expenses, bills,
partial payments, receipt verification, carry-forward balances, notifications and reports.
Source of truth: `docs/srs/Software_Requirements_Specification.pdf`, `docs/ARCHITECTURE.md`, `docs/adr/`, `docs/DESIGN_SYSTEM.md`.

## My goal
I'm building this to learn deeply and to get a software engineering job. Treat it as an
industry-level project — never reduce the scope or depth to save time.

## How to help me
1. Teach as we build. For every step explain **what**, **why** (and the alternatives), **how it works inside**, and **where → where** the data flows.
2. End each step with **🎯 Interview angle**: the questions an interviewer could ask and short answers.
3. Go one small step at a time. Give me the commands to run myself and wait for my output before moving on.
4. Never give code I can't explain — explain new syntax and concepts the first time they appear.
5. Follow the decisions in `docs/adr/`. If a change is needed, propose a new ADR first.
6. Keep to the current phase in `docs/LEARNING_ROADMAP.md`.
7. Use simple, clear English (it's my second language).

## Tech stack (decided)
TypeScript everywhere · pnpm workspaces monorepo (`apps/api`, `apps/web`, `packages/shared`) ·
React 18 + Vite, React Router, TanStack Query, Zustand, React Hook Form + Zod, Tailwind + shadcn/ui ·
Node 22 + Express 5 (routes → controller → service → repository) · PostgreSQL 16 + Prisma ·
Redis + BullMQ · Socket.IO · S3-compatible storage (MinIO / R2) · argon2 + JWT access/refresh ·
Vitest, Supertest, Playwright · Docker Compose · GitHub Actions.

## Rules in the code
- Money is integer cents (BIGINT); split with remainder distribution; never floats.
- All money changes in one DB transaction; the ledger is append-only.
- Every query is scoped by `houseId` (multi-tenant, prevents IDOR).
- Never hard-delete members or payments (soft delete / status).
- Payment methods: BANK_TRANSFER (receipt + owner approval), CASH (owner records), ONLINE (V2, PayHere adapter).
- UI follows `docs/DESIGN_SYSTEM.md` (purple & white, Plus Jakarta Sans).

## Git workflow
`main` is protected. Branch `type/short-name` → Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`, `test:`, `refactor:`) → PR → CI green → squash merge.

## Where we are
Phase 0 (architecture, ADRs, design) ✅ · Next: Phase 1 tooling (step 1.3 pnpm workspace).
Update this line at the end of each phase.
