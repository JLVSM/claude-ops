# Protocol: retrieval-protocol — read cheap, climb only as needed

**Status:** ✅ ACTIVE
**Trigger:** WHEN I start a session on this repo, OR I'm about to answer a
question against it / pull context from it.
**Priority:** high (boot-adjacent — governs how every other file gets loaded).
**Source:** Karpathy's "LLM Wiki" gist (2026-04) + its walkthrough video
(`sboNwYmH3AY`) — the token-budgeted, tiered retrieval schema. Same discipline
as our tiered CLAUDE.md loading and the compression doctrine: read the least
that answers the question.

## THEN — the ladder (stop at the first rung that answers it)
1. **Hot cache** — read `_hot.md` (~500 tok). Active state + these rules. Usually enough for "what's going on / what's open".
2. **Rule #0** — `protocols/no-fabrication.md` (always, it overrides output).
3. **State** — `docs/state.md` for fuller current status (complete vs stub, TODOs).
4. **Domain file** — open the ONE specific `protocols/…` / `references/…` /
   `playbooks/…` the trigger points to. Open 1–2, never the whole directory.
5. **Grep fallback** — `grep -ri "<keyword>" protocols references playbooks` when
   you don't know the file. Then open only the hits that matter.

## Hard budget
- **NEVER read more than 5 files per query.** If you're reaching for a 6th, you're
  exploring, not answering — narrow the question or grep first.
- Prefer the index/hot-cache summary over re-reading a full page you've seen.
- Reading the whole repo "to be safe" is the anti-pattern this exists to kill.

## Detection signals (am I violating?)
- [ ] Opened >5 files to answer one question.
- [ ] Read a full `references/*` page when `_hot.md`/`state.md` already had the answer.
- [ ] Loaded a whole directory instead of the one file the trigger named.
- [ ] Skipped `_hot.md` and went straight to deep files.

## What this does NOT mean
- Not "read less than the question needs" — comprehension still wins (cf.
  `survey-before-building`). It caps breadth, never the depth a real answer requires.
- Not a cache that can go stale silently: `_hot.md` is refreshed on session close;
  if it contradicts `state.md`, `state.md` + the source file win (memory-vs-reality).

## Maintenance (keep the top of the funnel lean)
- On close: update `_hot.md` with what changed; keep it ≤ ~500 tokens by demoting
  detail to `docs/state.md`. A hot cache that grows forever stops being hot.

## Enforcement loop
Session start → read `_hot.md` first. Per query → climb rungs 1→5, stop when
answered, count files (≤5). On close → refresh `_hot.md`, prune to budget.

## Interaction with other protocols
- Pairs with `compaction-ritual` (both fight context bloat — this on input/read,
  compaction on the running transcript).
- Serves `memory-vs-reality` (the ladder IS how you verify against the repo).
- Under Rule #0 always.
