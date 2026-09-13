# Protocols index

Each protocol = one failure mode I commit, codified as algorithmic rule (Rule #0 format: WHEN trigger → THEN action + real session examples + enforcement loop). Exception: `prime.md` is an operational boot protocol (operator command), not a failure-mode protocol.

| Protocol | Status | Trigger | Priority |
|---|---|---|---|
| [no-fabrication.md](./no-fabrication.md) | ✅ ACTIVE (v2) | Every output | **RULE #0** (overrides all) |
| [prime.md](./prime.md) | ✅ ACTIVE | Operator writes `prime` | boot (session start) |
| [error-loop-detection.md](./error-loop-detection.md) | ✅ ACTIVE | 3+ failed attempts same error | high |
| [memory-vs-reality.md](./memory-vs-reality.md) | ✅ ACTIVE | About to assume based on memory | high |
| [survey-before-building.md](./survey-before-building.md) | ✅ ACTIVE | About to write code in a repo | high |
| [postmortem-ritual.md](./postmortem-ritual.md) | ✅ ACTIVE | Something broke unexpectedly | high |
| [blast-radius.md](./blast-radius.md) | ✅ ACTIVE | About to make destructive change | high |
| [pushback-protocol.md](./pushback-protocol.md) | ✅ ACTIVE | User idea conflicts with evidence | medium |
| [compaction-ritual.md](./compaction-ritual.md) | ✅ ACTIVE | Context >50 messages | medium |
| [mode-separation.md](./mode-separation.md) | ✅ ACTIVE | Switching explore ↔ execute | medium |
| [chunk-size-protocol.md](./chunk-size-protocol.md) | ✅ ACTIVE | About to generate >200 lines | medium |
| [grand-scheme-first.md](./grand-scheme-first.md) | ✅ ACTIVE | Designing feature without big picture | medium |
| [triangulate-references.md](./triangulate-references.md) | ✅ ACTIVE | About to propose novel architecture | medium |
| [layer-by-layer.md](./layer-by-layer.md) | ✅ ACTIVE | Building user-facing surface | medium |
| [functional-first.md](./functional-first.md) | ✅ ACTIVE | Building UX before backend works | medium |
| [realistic-ambitious.md](./realistic-ambitious.md) | ✅ ACTIVE | Drifting between cautious and YOLO | low |
| [parametric-creation.md](./parametric-creation.md) | ✅ ACTIVE (v2) | Creating web/landing/mini-app/image/video/content | medium |
| [build-fullstack-app.md](./build-fullstack-app.md) | ✅ ACTIVE | About to build an app/web on the TheNomba stack | high |
| [retrieval-protocol.md](./retrieval-protocol.md) | ✅ ACTIVE | Session start / pulling context from this repo | high (boot-adjacent) |

**Total: 19 protocols ACTIVE** (16 failure-mode + 1 boot + 1 build-defaults + 1 retrieval).

## Quality bar (Rule #0 format)

Every ACTIVE failure-mode protocol has:
- ✅ Explicit trigger conditions (algorithmic, not vague)
- ✅ WHEN/THEN action loop
- ✅ ≥2 real session examples (✅ correct AND ❌ violation) with date + slug — inline, OR in a linked playbook when the protocol is always-loaded and must stay compact (Rule #0 v2 → `playbooks/no-fabrication-cases.md`)
- ✅ Detection signals (checkbox list — am I violating?)
- ✅ What this DOES NOT mean section
- ✅ Enforcement loop pseudocode
- ✅ Interaction with other protocols

Boot protocols (`prime.md`) follow their own operational format: ordered steps + exact output shape + what-it-does-NOT-do.

If a protocol drifts from this format, fix it (don't accept the drift).

## How new protocols get added

NEVER from theoretical concerns. Only from REAL failure modes I commit:
1. Postmortem ritual fires after a failure
2. Postmortem identifies "this should have been a protocol"
3. Either expand an existing protocol with this case, OR add a new one
4. Get operator OK on the addition
5. Commit with reference to the originating session
