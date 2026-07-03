# TheNomba stack — canonical

**Status:** 🟢 ACTIVE · the default architecture for every app/web I build for TheNomba, unless the project is the named exception.
**Verified:** 2026-07-03 from the real `package.json` across `~/Claudito` (SUPRA CRM, Pensiones dashboard, filosofos, test-factory).

## The stack (my default — do NOT re-derive per session)

| Layer | Default | Notes |
|---|---|---|
| Frontend | **Vite + React** (app/CRM) OR **Next.js** (SSR / marketing / content) + **Tailwind** | Vite for app-shell CRMs; Next for SEO/marketing/dashboards |
| Backend | **Supabase** — Postgres + Auth + Row Level Security + Storage + Realtime + Edge Functions | BaaS-first. This IS the backend. I do not stand up a server unless a primitive is genuinely missing |
| Deploy | **Netlify** | Deploy previews = my staging/UAT. Instant rollback = my safety net |
| CI | GitHub Actions (light) | typecheck + lint + test gate on PR |

Evidence: SUPRA CRM = Vite+React+Supabase+Tailwind→Netlify · Pensiones = Next+Tailwind→Netlify.

## Rule: reach for a platform primitive before custom infra

WHEN a task needs auth / file storage / realtime / a cron / a serverless endpoint / a cache →
THEN use the Supabase or Netlify primitive (Supabase Auth, Storage, Realtime, `pg_cron`, Edge/Netlify Functions), NOT a new dependency or a self-hosted service.
This is the ponytail ladder (rung 4: native platform feature) applied to the stack.

## The ONE exception

**jarvis "Studio TheNomba"** (`~/Claudito/jarvis*`) = React + **Remotion** + **Fastify** multi-service (content-engine, video-starter, studio, social-publisher). It is a video-editing PROGRAM, not the app template. Its multi-service/Fastify shape does NOT generalize — I never cite it as the pattern for a new CRM/dashboard/site.

## Anti-pattern: cargo-culting hyperscale

System-design content (ByteByteGo et al.) teaches Netflix/Uber-scale patterns. At TheNomba's scale (managed Postgres, single region, 1K–100K users) these are ANTI-patterns:
- ❌ Kafka · Cassandra · service mesh · sharding · distributed consensus · Spark/Flink
- ✅ Take the PRINCIPLE, drop the scale: indexing (not sharding), read replicas (not Cassandra), webhooks / `pg_boss` (not Kafka), denormalized view (not a data lake).

Applied defaults live in the `build-fullstack-app` protocol.
