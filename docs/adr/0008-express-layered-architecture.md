# 0008. Express with layered, feature-based modules

- **Status:** Accepted · **Date:** 2026-10-08

## Context
Goal includes deep understanding of how a backend works, plus industry-grade structure.

## Options considered
1. **NestJS** – opinionated, built-in DI/modules/decorators (similar to Spring). Great, but hides the mechanics.
2. **Fastify** – faster, schema-based.
3. **Express 5 + our own structure** – most widely used; we build middleware, DI and layering by hand, so every piece is understood.

## Decision
Express 5. Each feature module = routes → controller → service → repository (+ schemas, tests). Dependencies passed via factory functions (manual DI).

## Consequences
+ Transparent; transferable knowledge (NestJS/Spring become easy afterwards).
− We must enforce conventions ourselves (lint rules, reviews).
