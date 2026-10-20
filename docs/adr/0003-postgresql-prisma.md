# 0003. PostgreSQL + Prisma for persistence

- **Status:** Accepted · **Date:** 2026-10-08

## Context
Data is relational (user → membership → bill → payment). Payment approval updates several rows that must succeed or fail together. SRS: "Payment records shall not be lost".

## Options considered
1. **MongoDB** – flexible schema, popular in MERN tutorials; multi-document transactions exist but relations/constraints are weaker.
2. **MySQL** – solid relational choice.
3. **PostgreSQL** – relational, strong constraints (CHECK, partial unique indexes), excellent JSON support, row-level locking, free managed hosting (Neon, Supabase).

ORM options: raw SQL, Knex, TypeORM, Drizzle, **Prisma**.

## Decision
PostgreSQL 16 with Prisma ORM (schema-as-code, generated types, migrations). Raw SQL allowed for complex report queries.

## Consequences
+ ACID, foreign keys, unique constraints prevent double billing.
+ Type-safe queries; migrations tracked in git.
− Must learn SQL + migrations properly (a plus for interviews).
