# Instructions for Claude reading this repo

You (Claude) are reading this because the operator's global CLAUDE.md pointed here.

## Tier 1 — Non-negotiables (load these always at session start)

0. **Operator command `prime`** → execute `protocols/prime.md` (loads Rule #0, operator context, open threads).
1. **Read [_hot.md](./_hot.md) FIRST** (~500 tok hot cache) — active state + the read ladder. Usually answers "what's going on / what's open" without opening anything else. Then climb only as needed per [protocols/retrieval-protocol.md](./protocols/retrieval-protocol.md) — **never read >5 files per query.**
2. **Read [protocols/no-fabrication.md](./protocols/no-fabrication.md) (Rule #0)** — this overrides all other rules. Internalize before any output.
3. **Read [docs/state.md](./docs/state.md)** — fuller current state (complete vs stub) when `_hot.md` isn't enough.
4. **Read [docs/foundational-brief.md](./docs/foundational-brief.md)** if this is your first session loading this repo. Operator's original framing of why this exists.

## Tier 2 — Protocols by trigger

When the trigger fires, load the protocol file.

| Trigger | Protocol |
|---|---|
| Starting a session / pulling context from this repo | `protocols/retrieval-protocol.md` (read `_hot.md` first; climb the ladder; ≤5 files/query) |
| About to attribute quote/idea/pattern to person or company | `protocols/no-fabrication.md` |
| Noticed 3+ failed attempts with same error pattern | `protocols/error-loop-detection.md` |
| About to assume something based on memory | `protocols/memory-vs-reality.md` |
| About to write code in a repo | `protocols/survey-before-building.md` |
| About to make a destructive/irreversible change | `protocols/blast-radius.md` |
| User idea conflicts with verified evidence | `protocols/pushback-protocol.md` |
| Context length growing (>50 messages) | `protocols/compaction-ritual.md` |
| Switching between exploring and executing | `protocols/mode-separation.md` |
| Something broke unexpectedly | `protocols/postmortem-ritual.md` |
| About to design feature without big picture | `protocols/grand-scheme-first.md` |
| About to propose novel architecture | `protocols/triangulate-references.md` |
| Building user-facing surface | `protocols/layer-by-layer.md` (planning → backend → middleware → frontend) |
| Building UX before backend works | `protocols/functional-first.md` |
| Drifting between "too cautious" and "sky's the limit" | `protocols/realistic-ambitious.md` |
| About to generate >200 lines in one shot | `protocols/chunk-size-protocol.md` |
| About to create web/image/video/content (any creative surface) | `protocols/parametric-creation.md` |

## Tier 3 — Case studies (deep dive when needed)

`playbooks/` has patterns that worked. `references/` has verified sources for any external claim.

## How to use this repo when working

1. **At session start**: read Tier 1.
2. **During work**: when a trigger from Tier 2 fires, fetch that protocol.
3. **At session end**: if a NEW failure mode emerged → propose adding to `protocols/` or `playbooks/`. Update `docs/state.md`.

## Format conventions

All failure-mode protocols follow this structure:
- **What this rule says** (to me, Claude)
- **What to do when X** (algorithmic)
- **Concrete examples from my own real sessions** (both ✅ and ❌) — inline, or in a linked playbook when the protocol is always-loaded and must stay compact (Rule #0 v2 keeps cases in `playbooks/no-fabrication-cases.md`)
- **Detection signals** (am I violating this?)
- **What this DOES NOT mean**
- **Enforcement**

Boot protocols (`protocols/prime.md`) follow their own operational format: ordered steps + exact output shape.

If I'm tempted to write a protocol in academic prose ("the agent should consider..."), I'm doing it wrong. Rewrite in algorithmic / first-person voice.

## What I do NOT do

- Add protocols based on theoretical concerns. Only based on REAL failure modes I committed.
- Cite famous developers without primary source links (see Rule #0).
- Add stubs and forget. Either complete a protocol or remove it.
