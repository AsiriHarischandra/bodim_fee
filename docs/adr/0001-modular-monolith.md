# 0001. Modular monolith instead of microservices

- **Status:** Accepted · **Date:** 2026-10-08

## Context
Small team (1 developer), money data that must stay consistent, SRS requires a "modular architecture". Must be deployable cheaply.

## Options considered
1. **Microservices** – independent scaling and deploys, but needs service discovery, distributed transactions (sagas), tracing, many deployments. Overkill for one team.
2. **Plain monolith (no structure)** – fast to start, becomes a "big ball of mud".
3. **Modular monolith** – one deployable, but code split into feature modules with clear boundaries.

## Decision
Modular monolith: one API process + one worker process from the same codebase. Modules communicate only through service functions.

## Consequences
+ ACID transactions across bills/payments/ledger in one DB.
+ Simple deploy, debug and local setup.
+ Modules can be extracted to services later if needed.
− Whole API scales as one unit (acceptable at our scale).
− Requires discipline to respect module boundaries (enforced by code review / lint rules).
