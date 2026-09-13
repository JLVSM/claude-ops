# State — claude-ops

**Last updated:** 2026-09-13 by Claude session (Juan) — `parametric-creation` v2: **Phase 0 (references before prompts)** + the critique loop + Figma round-trip declined with reason. Consistency pass: this file said 17 protocols in two places while the index said 19 (build-fullstack-app and retrieval-protocol were shipped but never listed here). Fixed.
**Repo status:** OPERATIONAL AT FULL CAPACITY. Rule #0 v2 + prime boot + **19 protocols** (16 failure-mode + prime + build-fullstack-app + retrieval-protocol) + **`_hot.md` hot cache** (read first, ≤~500 tok). References: 14 devs canonical + 1 PARTIAL (Carmack), 18 companies canonical, 5 primary-sources canonical + 1 PARTIAL, + thenomba-stack-canonical. Playbook: 16 canonical patterns + no-fabrication cases. Zero open build work; only optional reference-deepenings remain.

## 🟢 Complete (in main)

- `README.md`, `CLAUDE.md`
- `docs/foundational-brief.md`, `docs/decisions.md` (3 ADRs), `docs/glossary.md`, `docs/architecture.md`, `docs/state.md`
- `protocols/README.md` (index 19/19 ACTIVE: 16 failure-mode + 1 boot + 1 build-defaults + 1 retrieval)
- **19 protocols ACTIVE** (all full content):
  - `no-fabrication.md` (Rule #0 — **v2** 2026-06-10: stakes×cost matrix, compressed always-load core, cases moved to `playbooks/no-fabrication-cases.md`)
  - `prime.md` (boot protocol — operator command `prime`: loads Rule #0, operator context, open threads)
  - `error-loop-detection.md`, `memory-vs-reality.md`, `survey-before-building.md`
  - `postmortem-ritual.md`, `blast-radius.md`
  - `pushback-protocol.md`, `compaction-ritual.md`, `mode-separation.md`
  - `chunk-size-protocol.md`, `grand-scheme-first.md`
  - `triangulate-references.md`, `layer-by-layer.md`, `functional-first.md`, `realistic-ambitious.md`
  - `parametric-creation.md` (**v2** 2026-09-13: crear por vector/parámetro/estructura, no ruido random; norte = resumible/escalable/cuantificable. **Phase 0 = referencias ANTES del prompt** — cuestionario de arranque, la shelf curada, la anti-referencia, y cada parámetro trazado a una referencia. Trigger: crear web/landing/mini-app/imagen/vídeo/contenido)
  - `build-fullstack-app.md` (2026-07-03: defaults WHEN→THEN por capa sobre el stack canónico + ship protocol right-sized. Destilado de la triage de ByteByteGo)
  - `retrieval-protocol.md` (2026-07-10: escalera de lectura con presupuesto de tokens — `_hot.md` primero, ≤5 ficheros por consulta. Patrón LLM-Wiki de Karpathy)

- `playbooks/pro-dev-references.md` — **16 canonical** (10 devs/orgs + 6 operator-specified Mag7: Microsoft, Apple, NVIDIA, Meta, Alphabet, AWS)
- `playbooks/no-fabrication-cases.md` — Rule #0 v2 case studies (extracted from v1)
- `references/README.md` — active template
- `references/developers-canonical.md` — **14 canonical + 1 PARTIAL** (Carmack — no true primary venue reachable; .plan mirror verified + flagged)
- `references/companies-canonical.md` — **18 canonical** (Mag7 batch added 2026-06-10: Apple, NVIDIA, Meta, Alphabet-GCloud/YouTube, AWS — all from operator-supplied sources, 24 URLs verified; third-party sources tiered B inside entries, never canonical)
- `references/primary-sources.md` — **5 canonical + 1 PARTIAL** (added: Coimbra "Overview of Facebook scalable architecture" metadata via Crossref; First Monday article PARTIAL — title only)
- `references/coding-wikis-troubleshooting.md` — Section D added (MIT/Broad CommLab tier A + DataCamp tier B, operator-supplied)
- `references/claude-code-canonical.md` — distilled from verified code.claude.com/docs/en/best-practices (2026-05-27)
- `references/coding-wikis-troubleshooting.md` — Section A (12 verified llms.txt) + Section B (5 docs URLs) + Section C (MDN + React ref + Tailwind community wiki). Every URL HTTP-verified 200.
- `docs/decisions/ADR-gstack-integration.md` — gstack as proactive layer; claude-ops as reactive layer. Verified against gstack repo + ETHOS.md (2026-05-27). Pruned earlier draft's fabricated "8 commands" claim per Rule #0.

## 🟡 Active TODO list (work to do via WebFetch verification, NOT permanently empty)

Per Rule #0 active framing: these are work-items, not "Rule #0 forbids it" excuses.

- **Mag7 list: ✅ CLOSED** by operator 2026-06-10 at 6 companies (Microsoft, Apple, NVIDIA, Meta, Alphabet, AWS — all processed; Tesla/xAI dropped)
- **First Monday article PARTIAL:** title verified, body fetch pending (authors/year/quote)
- **Coimbra ACM paper:** metadata canonical via Crossref; PDF unread — only needed if its claims get cited
- **Carmack PARTIAL:** unchanged — Keen Technologies venue still the unlock
- **Carmack PARTIAL:** no true primary venue reachable (X auth-walled; .plan archive is a verified-but-flagged mirror). Next: check if Keen Technologies publishes a blog/research page
- **Deepening (optional, not blockers):** rauchg.com essay anchor (429 ×3 — retry later) · one LKML thread quote for Linus · one iWoz chapter quote for Wozniak · one specific cookbook guide URL for OpenAI

Each session aims to deepen existing canonical entries (quote-anchored fetches) OR convert PARTIAL → Canonical.

## ✅ Shipped (full chronology)

- 2026-05-26 (1) — Bootstrap commit: README + CLAUDE.md + foundational-brief + docs + Rule #0 first version
- 2026-05-26 (2) — 14 protocol stubs + 1 playbook stub + 3 reference stubs
- 2026-05-26 (3) — Chunk A: 5 high-priority protocols full content
- 2026-05-26 (4) — Chunk B: 5 medium-priority protocols full content
- 2026-05-26 (5) — Chunk C: 4 remaining protocols full content (15/15 ACTIVE)
- 2026-05-26 (6) — Final: index + state + reference templates
- 2026-05-26 (7) — **REFACTOR Rule #0**: gatekeeper-not-excuse framing (operator feedback)
- 2026-05-26 (8) — **First batch verifications**: 4 devs + 1 company + 2 primary-sources via WebFetch
- 2026-05-27 (refs-batch) — Big batch verification: 22 candidates fetched in parallel, 19 promoted to Canonical, 3 to PARTIAL with explicit failure-mode docs
- 2026-05-27 (9) — Housekeeping + playbook canonical entries for the 4 verified devs
- 2026-06-10 (10) — **Rule #0 v2 + prime protocol** (PR #4): stakes×cost matrix, compressed core, cases → playbook; CLAUDE.md Tier 1 item 0 = `prime` command
- 2026-06-10 (11) — PR #1 conflict resolved + merged (kept both 2026-05-27 sessions' facts); indexes + format conventions synced to v2 reality
- 2026-06-10 (12) — **TODO list cleared**: 2 primary-sources entries (foundational-brief + RSP with verified quote) · Rauch + OpenAI promoted to Canonical via gh API + cookbook web fetch · Carmack mirror verified + flagged · 6 new playbook entries · 4 existing playbook entries quote-anchored. Remaining: operator names list + Carmack true-primary venue
- 2026-06-10 (13) — **First operator Mag7 name: Microsoft.** Both supplied sources verified (Dev Center via WebFetch; YouTube channel consent-walled to WebFetch → verified via yt-dlp: 684k subs, agent-centric recent titles). Reference + playbook entry (pattern: pre-configured sandbox onboarding). Remaining names still pending
- 2026-06-29 (15) — **New protocol `parametric-creation.md`** (operator directive): crear web/imagen/vídeo/contenido por vector·parámetro·estructura·arquitectura, NO ruido/grano/random de IA. Norte = resumible·escalable·cuantificable. Tier 2 trigger added; índice 16→17. Ejemplo ✅ = MercoTax design system.
- 2026-06-10 (14) — **Mag7 batch: Apple, NVIDIA, Meta, Alphabet, AWS.** 24 operator-supplied URLs verified in 5 WebFetch waves + gh API + Crossref. 5 company entries + 5 playbook patterns (Apple = design governance via artifacts, NVIDIA = APOD loop quote-anchored, Meta = shift errors to compile-time quote-anchored, Alphabet = pillar-walk reviews with AWS cross-triangulation, AWS = reference-architecture-first). Tiering enforced: codekarle/geeksforgeeks/greenware/Wikipedia/DataCamp flagged tier-B/tertiary inside entries, NOT canonical; Coimbra ACM paper resolved via Crossref (external academic study, ~2014, flagged as such); flux noted ARCHIVED. Mag7 6/7 — Tesla + xAI never supplied

## 🔄 Pre-flight (every session using this repo)

```
0. Operator writes `prime` → execute protocols/prime.md (covers steps 1-2 + context)
1. cat protocols/no-fabrication.md     # Rule #0 v2 (active gatekeeper)
2. cat docs/state.md                   # this file
3. cat docs/foundational-brief.md      # first time loading
4. When a Tier 2 trigger fires, load that protocol.
```

## 🚨 Risks / debt

- **Operator confirmed pasting claude-ops pointer in ~/.claude/CLAUDE.md global (2026-05-26).** Without this, repo doesn't change behavior.
- **TODO entries are real work, not "fine to leave empty."** Per Rule #0 active framing, each session aims to convert 2-3 TODO → Canonical.

## 📝 Session log

- **2026-05-26 (1-8)** — see "Recently shipped" above. Major reframe at (7) corrected Rule #0 from passive avoidance to active verification stance. First proof-of-active-stance at (8): 7 canonical entries via WebFetch.
- **2026-05-27 (refs-batch)** — 22 references batch verification. 19 promoted to Canonical (9 devs + 10 companies on top of 5 existing). 3 marked PARTIAL with explicit failure-mode documentation: Rauch (HTTP 429 rate-limit), Carmack (no public personal site — primary venue is X auth-walled), OpenAI (HTTP 403 to platform + root; cookbook verified via gh CLI instead). All WebFetches batched in 2 parallel waves of 11. Each PARTIAL entry includes exact failure mode + next retry path per Rule #0.
- **2026-05-27 (9)** — Housekeeping: bumped layer-by-layer stub count to reality (15). Promoted Vitalik / Julia / Simon / Mitchell from playbook-TODO to playbook-Canonical with verified-source-backed WHEN/THEN patterns. Per operator: "como aceite a un coche" — entries kept lean, one actionable pattern each. (Ran parallel to refs-batch; merged 2026-06-10 with conflict resolution keeping both sessions' facts.)
- **2026-06-10 (10-11)** — Rule #0 v2 shipped (PR #4): stakes×cost matrix, compressed core, case studies extracted to `playbooks/no-fabrication-cases.md`; `prime.md` boot protocol added (CLAUDE.md Tier 1 item 0). Then PR #1 unblocked: state.md conflict resolved keeping both parallel 2026-05-27 sessions, playbook TODO table synced to post-refs-batch reality (6 candidates have verified references — next step is derive-pattern, not re-fetch). Consistency pass: protocol/playbook indexes + CLAUDE.md format conventions updated to match v2 structure.
- **2026-06-10 (12)** — TODO-list completion run. Verification wins: RSP announcement fetched (direct quote secured) · Rauch identity verified via `gh api users/rauchg` (rauchg.com still 429 ×3 — promoted with scoped caveat) · OpenAI cookbook verified live at developers.openai.com/cookbook + org/repo via gh API (root 403 persists — promoted with scoped caveat) · Carmack .plan archive verified as community MIRROR of floodyberry.com (stays PARTIAL; mirror flagged, never cited as primary). Playbook: 6 new entries derived from verified references (Linus = canonical-venue discipline, Wozniak = route-to-substance, Anthropic = capability-gated safeguards, OpenAI = executable docs, SRE = ops-as-software, Carmack = daily .plan → state.md session log) + 4 existing entries quote-anchored (Vitalik fv.html, Julia wizardzines, Simon TIL count+self-description, Mitchell building-block-economy). primary-sources at 4/4 canonical. Only operator-blocked item remains: Mag7/Tesla/xAI names.
- **2026-09-13 (16)** — **`parametric-creation` v2 + consistency pass.** Operator drop: a 3-step thread by design engineer Breeje Anadkat (X, 12-sep-2026) on making better-looking apps with AI. Distilled instead of adopted wholesale: **step 1 (*"references, not prompts"*) was the real gap** — it is now **Phase 0**, an intake questionnaire (his references → ours → the curated shelf → the anti-reference → the constraint) that must run before any prompt or component, with every parameter traced back to a named reference. **Step 2** (get specific about what's wrong) we already solve better via `/element-inspector` (element → `file:line`), so it is written as the cheap-critique loop, not as a new idea. **Step 3 (round-trip to Figma) declined with the reason on record:** on our stack the code IS the design, so a post-build Figma file is a second source of truth that goes stale; taste gets applied on the rendered page (`premium-web-craft`, `/design-review`). Figma stays valid BEFORE the build, which is Phase 0. No new protocol — the gap belonged inside an existing one (rung 2: reuse before adding). **Consistency pass on this file:** it claimed 17 ACTIVE protocols in two places while `protocols/README.md` said 19; `build-fullstack-app.md` (2026-07-03) and `retrieval-protocol.md` (2026-07-10) had shipped without ever being listed in 🟢 Complete. Both added, counts reconciled, the "last 24h" heading dropped (it spanned four months).
