# 0006. Redis + BullMQ for background and scheduled jobs

- **Status:** Accepted · **Date:** 2026-10-08

## Context
Daily overdue checks (FR-14), due reminders, birthday notifications (FR-16), emails, notification fan-out to up to 500 members.

## Options considered
1. `setInterval` / `node-cron` inside the API – lost on restart, runs N times if N instances, blocks request handling.
2. OS cron calling an endpoint – external dependency, no retries.
3. **BullMQ on Redis** – persistent jobs, retries with backoff, repeatable (cron) jobs that run once cluster-wide, separate worker process.

## Decision
BullMQ with a dedicated `worker.ts` process. Redis is also reused for the Socket.IO adapter and caching.

## Consequences
+ Reliable, observable (Bull Board), scalable workers.
− One more infrastructure piece (Redis) – free tiers exist (Upstash).
