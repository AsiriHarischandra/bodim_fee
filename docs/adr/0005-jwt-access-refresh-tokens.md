# 0005. JWT access token + rotating refresh token cookie

- **Status:** Accepted · **Date:** 2026-10-08

## Context
SPA + future mobile apps need to call the API. Must resist XSS token theft and allow logout/revocation.

## Options considered
1. Server sessions (cookie + session store) – simple, revocable; less convenient for mobile clients.
2. Long-lived JWT in localStorage – easy, but stolen by any XSS; cannot revoke.
3. **Short-lived access JWT (15 min, in memory) + long-lived refresh token (7 days, httpOnly Secure SameSite cookie, stored hashed in DB, rotated on each use)**.

## Decision
Option 3, with refresh-token reuse detection (reuse ⇒ revoke all user sessions). Passwords hashed with **argon2id**.

## Consequences
+ Stateless request auth, revocable sessions, XSS can't read refresh token.
− More moving parts (refresh endpoint, axios interceptor, CSRF considerations for the refresh cookie → SameSite=Strict + origin check).
