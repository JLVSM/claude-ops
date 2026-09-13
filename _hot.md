# _hot.md — hot cache (READ FIRST · keep ≤ ~500 tokens)

> The first file I read every session, before anything else. It holds only what's
> **active right now** + the retrieval rules. If the answer isn't here, I climb the
> ladder in `protocols/retrieval-protocol.md`. On session close I refresh this;
> when it grows past ~500 tokens I demote detail down to `docs/state.md` — this
> file stays small on purpose (Karpathy LLM-Wiki hot-cache pattern).

## What this repo is
Operating playbook written for me (Claude), loaded via the operator's global
CLAUDE.md. Protocols + anti-patterns + playbooks + verified references. Reader = me.

## Read order (the retrieval ladder — token-budgeted)
1. **this file** (`_hot.md`, ~500 tok) — active state + rules.
2. **`protocols/no-fabrication.md`** (Rule #0) — overrides everything.
3. **`docs/state.md`** — fuller current state (what's complete vs stub).
4. domain file on demand (a specific `protocol`/`reference`/`playbook`).
5. `grep` across the repo by keyword.
→ **NEVER read more than 5 files per query.** Climb only as far as the question needs.

## Active now
- **19 protocols ACTIVE** (17 failure-mode + `prime` boot + `retrieval-protocol` + `build-fullstack-app` stack-defaults).
- **Creative default** for any web/landing/mini-app/image/video → `protocols/parametric-creation.md`
  **Phase 0 BEFORE any prompt or component:** ask for his references → if none, bring 3-5 from the
  shelf (refero, 60fps, collectui) and SHOW them → survey our own systems → get the anti-reference.
  Every token traces to a reference. Critique loop via `/element-inspector`. **No Figma round-trip.**
- **Stack default** for any TheNomba app/web → `references/thenomba-stack-canonical.md` (Vite/React or Next + Tailwind + Supabase + Netlify; jarvis Studio = the video-only exception).
- **Zero open build work.** Only reference-deepenings remain (not blockers):
  - Carmack PARTIAL — Keen Technologies venue still the unlock.
  - First Monday article — body fetch pending (title verified).
  - Optional quote-anchors: rauchg essay (429 ×3), one LKML quote (Linus), one iWoz quote (Wozniak).

## Non-negotiables (the reflexes)
- **Rule #0:** never fabricate quotes/metrics/attributions. Verify or omit.
- **memory-vs-reality:** a recalled fact/file is a hypothesis → verify against the repo before asserting.
- New protocols come ONLY from a real committed failure (postmortem → operator OK), never from theory.
