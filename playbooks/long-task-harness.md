# Long-task harness — how to run work that outlives one context window

**Status:** playbook (a pattern that works), not a protocol. A protocol here needs a real failure I committed; none is logged for this yet. If I ever close a task without observable evidence, that is the case to write up.

**Trigger:** the task spans several files, several sessions, or runs autonomously (e.g. `/goal`, an overnight run, a handoff to another session).

Sources, read 2026-10-08: [@beamnxw's 7-layer guide](https://x.com/beamnxw/status/2107522996046905797) (checked against the Claude Code docs), [@mirku21's harness framing](https://x.com/mirku21/status/2098836008468992471), [code.claude.com/docs/en/goal](https://code.claude.com/docs/en/goal), [.../advisor](https://code.claude.com/docs/en/advisor). Full table and verification notes live in the operator's private toolkit (`Security/referencias/kit-harness-tareas-largas/`).

## The loop
1. **Contract before work.** Deliverable (exact path and format) · constraints · **non-goals** · acceptance checks. Without it the model decides when it is done; with it the checks decide. If a missing detail changes the outcome, ask one question.
2. **Map, not encyclopedia.** Read `_hot.md` and the project map first; load only the passage needed for the next decision. Record source URLs and the date checked.
3. **Durable state in a file, not in the chat.** After each meaningful stage update `progress.md`: Task · Outputs (exact paths) · Completed (with observed check results) · Decisions (with evidence) · Open issues · **Next action** (one concrete step). A fresh session reads it, inspects the referenced files, and continues from the next action.
4. **Sensors before autonomy.** A command that returns an exit code or a log. "Are you sure?" is a circular check; a test run is not.
5. **`checks.md`, one row per requirement:** `requirement | verdict (pass/fail/unresolved) | evidence | correction`. Evidence = a path, a link, or real command output. Missing evidence stays visible as `unresolved`.
6. **Reviewer separate from author** (a subagent with read/search tools, or at least a distinct pass, saying which). Judgment items never get approved by the context that produced the work.
7. **Dual encoding.** A rule written in prose **plus** a mechanical gate that blocks when it breaks (deny rule, hook, `gate.py`). Prose alone is not a boundary.
8. **Never weaken a check to get a pass.** Do not repeat a failed approach without a new reason. Existing limit: 3 same-error failures → `error-loop-detection`.
9. **Close with evidence:** output paths + verification results in the conversation. If a limit or blocker stops the run, return a partial status with the exact remaining work.

## Claude Code facts verified in the docs (2026-10-08)
- `/goal <condition>`: a model checks the condition against evidence shown in the conversation between turns. A turn limit written inside the condition is model-evaluated, **not a hard limit**; hard runtime or spend limits need execution controls.
- Opus 5.5 starts at `medium`. A top-level `effortLevel` in user settings does **not** apply to Opus 5.5; saved levels are per model (`modelSettings`) or via `/effort`. In a subagent the frontmatter field is `effort:` (and `model:`).
- `deny` rules on `Read` are enforced for the file tools and recognised Bash readers (`cat`, `head`…), **not** for scripts that open files themselves; that needs the sandbox.
- **Advisor** (`/advisor`, `advisorModel`): experimental, Anthropic API only, billed at the advisor's rates against the plan, off by default. The model decides when to consult (before committing to an approach, on a recurring error, before declaring done); **there is no setting to force it**, only instructions. Opus main + Opus advisor is an accepted pairing (an independent second review). Use it opt-in for high-stakes work, and measure.
- Not real: a "subagent dispatcher pool (3x workers)". The actual cap is `CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS` (default 20).

## Measure, don't assume
Savings and quality claims belong to completed, accepted tasks: record review time, corrections needed, retries and `/usage`. One change at a time, same task and acceptance checks.

## What this does NOT mean
- Not a reason to build a harness for a one-line task.
- Not permission to stop and ask at every step: the contract is what lets the run continue unattended.
- Not a rule to enable the advisor everywhere: it costs tokens on every consultation.
