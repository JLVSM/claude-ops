# Protocol: build a fullstack app (TheNomba stack)

**Status:** ✅ ACTIVE
**Trigger:** WHEN I am about to build or extend an app/web for TheNomba (CRM, dashboard, site, internal tool) on the `thenomba-stack-canonical` stack.
**Priority:** high
**Source:** distilled from ByteByteGo HIGH-relevance guides (2026-07-03 triage: 105 of 399 HIGH), filtered to Supabase + Netlify + React/Next scale. Take the principle, drop the hyperscale.

## THEN apply these defaults, per layer

### Data — Postgres via Supabase
- WHEN I design a table → THEN index the foreign keys (`customer_id`, `user_id`) and the columns dashboards filter/sort by (`created_at`, status). B-tree by default. Verify with `EXPLAIN ANALYZE` on the *real* dashboard query, not a guess.
- WHEN a dashboard aggregates → THEN denormalize ONE summary table (or a materialized view) per dashboard. Trade write cost for read speed. Never recompute heavy aggregates on every page load.
- Escalation order, measured by query logs: **index → cache → denormalize → read replica → (only then) vertical tier bump.** Sharding is overkill below ~10k concurrent.
- WHEN reads dominate → THEN Supabase read replicas + the built-in PgBouncer pooler.
- Avoid N+1: batch with joins / `in` / PostgREST embedding. Never one query per row.

### Auth — Supabase Auth
- WHEN the app needs login → THEN use Supabase Auth. I never roll my own password hashing or session store.
- Enforce access in **RLS policies** keyed to `auth.uid()` (a user reads only their own rows). RLS is the enforcement layer; client checks are convenience only.
- JWT in httpOnly cookies. Add TOTP 2FA (Supabase) for any CRM holding client data.
- Roles/permissions → model as RLS + a `roles` table, not app-side `if` branches.

### API — PostgREST / Edge / Netlify Functions
- REST via PostgREST by default. Reach for a custom Edge Function only for logic that cannot be a query + RLS.
- Version routes (`/v1`). Return correct HTTP status codes. Validate input at the boundary (frontend + Postgres `check` constraints).
- WHEN a write can be retried (payment, webhook, form submit) → THEN idempotency keys. Never assume once-only delivery.
- Pagination: cursor/keyset for large sets, not deep `OFFSET`.
- Inbound webhooks: verify the signature; retry with backoff.

### Performance — Netlify CDN
- Netlify already fronts the build with a CDN → enable image optimization (format negotiation, responsive sizes) + cache headers. Don't hand-roll.
- Client data/cache: TanStack Query. Kill request waterfalls; parallelize.
- Watch the metrics that bite: LCP, TTFB, query p95.

### Security — ties to the claudito-security threat model
- OWASP basics: input validation, no secrets in the client bundle, HTTPS everywhere (automatic on Netlify/Supabase), RLS as authorization.
- Secrets/config: Netlify env vars + Supabase vault. Never commit keys (the claudito-security patterns block this at edit time).

## Ship protocol — the "101%", right-sized (NOT Netflix)

WHEN I ship →
1. **Gate:** typecheck + lint + test on PR (GitHub Actions).
2. **Staging:** the Netlify deploy preview. Verify there before merge.
3. **Deploy:** merge → Netlify production.
4. **Monitor:** UptimeRobot on the live URL + Supabase logs.
5. **Rollback:** broke? Netlify instant rollback to the previous deploy.

❌ I do NOT reach for Jenkins, Spinnaker, canary infra, Kafka, or a service mesh. That is the cargo-cult anti-pattern (see `thenomba-stack-canonical`).

## Enforcement loop

Before writing app code, I state which layer defaults apply. After building, I confirm: index on the query? RLS on the table? idempotency on the write? preview verified before merge?
