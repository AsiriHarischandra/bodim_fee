# 0002. TypeScript monorepo with pnpm workspaces

- **Status:** Accepted · **Date:** 2026-10-08

## Context
Frontend and backend must agree on request/response shapes and validation rules (e.g. allowed receipt types, payment amount > 0).

## Options considered
1. Two repos, plain JavaScript – types drift, rules duplicated.
2. Two repos, TypeScript, publish a shared npm package – versioning overhead.
3. **One repo, pnpm workspaces, `packages/shared`** – shared code imported directly.

## Decision
Monorepo: `apps/api`, `apps/web`, `packages/shared`. pnpm for fast, disk-efficient installs and strict dependency resolution.

## Consequences
+ One change to a Zod schema updates validation and types in both apps.
+ Atomic PRs across front and back; one CI pipeline.
− Slightly more tooling setup (workspace config, tsconfig references).
