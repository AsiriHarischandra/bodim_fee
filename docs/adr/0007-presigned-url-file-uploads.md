# 0007. S3-compatible storage with presigned URLs for receipts

- **Status:** Accepted · **Date:** 2026-10-08

## Context
Members upload JPG/PNG/PDF receipts (FR-08). Files must remain accessible (NFR) and be private.

## Options considered
1. Store in DB as BLOB – bloats DB and backups.
2. Store on API server disk – lost on redeploy, doesn't work with multiple instances.
3. **Object storage (S3 API)** – MinIO locally, Cloudflare R2 / AWS S3 in production; browser uploads directly via presigned PUT URL.

## Decision
Option 3. Private bucket, server-validated type/size, short-lived signed GET URLs for viewing, keys namespaced by house.

## Consequences
+ Scalable, durable, cheap; API never streams large files.
− Need to verify the upload completed (HEAD check) before creating the payment.
