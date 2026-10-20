# @boardmate/web

React 18 + Vite + TypeScript SPA. See [docs/ARCHITECTURE.md §7](../../docs/ARCHITECTURE.md#7-frontend-architecture).

| Folder | Purpose |
|---|---|
| `src/app` | Root providers (QueryClient, Router, theme) and route config |
| `src/pages` | Route-level screens; compose features, little logic |
| `src/features/<feature>` | `api.ts`, `hooks.ts`, `components/`, `schemas.ts` for one feature |
| `src/components` | Shared presentational components (`ui/` = shadcn) |
| `src/layouts` | OwnerLayout, MemberLayout, AuthLayout |
| `src/lib` | axios instance + refresh interceptor, socket client, queryClient |
| `src/stores` | Zustand stores (auth session, UI) |
| `src/hooks`, `src/utils` | Generic hooks and formatters (`formatLKR`, dates) |
| `tests/e2e` | Playwright end-to-end tests |
