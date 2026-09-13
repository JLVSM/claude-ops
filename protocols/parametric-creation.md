# Parametric Creation — vector, not noise

**Status:** ✅ ACTIVE
**Trigger:** About to create or generate any creative surface — web, image, video, content, brand asset.
**Origin:** Operator directive (2026-06). "Ya no vale solo generar ruido y grano / random de IA. Hay que trabajar por vector, parámetro, estructura y arquitectura, escalable y funcional en las partes y en el conjunto."

---

## The rule

I do not produce creative output as one-off **noise** — random AI generations, freehand pixels, "let's see what comes out" grain. I produce it by **vector, parameter, structure, architecture**: every piece is derived from a system, so it is reproducible, editable, composable, and coherent both alone and as a set.

The north star is three properties. Everything I build should be:

- **Resumible (summarizable)** — describable as a small set of parameters/decisions, not an opaque blob.
- **Escalable (scalable)** — change one parameter, regenerate the whole coherently; reuse the structure across pieces.
- **Cuantificable (quantifiable)** — measurable (tokens, dimensions, counts, scores), so quality and progress can be tracked, not vibed.

If a piece is not all three, it is noise and gets redone.

## Phase 0 — references before prompts (the intake questionnaire)

**Added 2026-09-13** (operator directive). The rule above says *derive the piece from a
system*. This phase answers the question it left open: **where does the system come from?**
Not from my imagination. From references the operator and I look at first.

Distilled from a real thread by design engineer Breeje Anadkat (X, 12-sep-2026), cross-checked
against what we already run. His step 1 — *"I start with references, not prompts"* — is the part
we did NOT have written down. His step 2 we already solve better (see below). His step 3 (round-trip
to Figma) we decline, with a reason (see below).

```
WHEN the operator asks for a web, landing, mini-app, or any visual surface:
0. BEFORE writing a prompt, a component, or a line of CSS — run the intake:
   a. "¿Qué referencias tienes?" — links, screenshots, "como X pero Y".
      If the operator has them, they win. They are the brief.
   b. If he has none → *I* bring them. Pull 3-5 from the curated shelf
      (styles.refero, 60fps.design, collectui; goatedui.dev for OG images and
      app icons) and SHOW them before building anything.
   c. "¿Qué hemos hecho ya que sirva?" — survey our own repos first
      (MercoTax/Folio tokens, Noir Design System, SUPRA, jlvsm). Reusing our own
      system beats importing a stranger's. → `survey-before-building.md`
   d. "¿Qué NO queremos?" — one anti-reference is worth three references. It
      kills a whole branch of the search space in one line.
   e. Name the constraint: brand, palette, stack, deadline, who reads it.
1. ONLY THEN derive the parameter set (tokens, type scale, motion, layout schema)
   FROM those references, and say out loud which reference each parameter came from.
2. Build. Never the reverse order.
```

**Why this is a rule and not a nicety.** A prompt without references makes me invent a
direction, and what I invent is the statistical middle of everything I have seen: the
templated look. The reference is what makes the output *his* and not *generic*. `frontend-design`
is far better fed a reference than asked to pick an aesthetic on its own.

### Step 2 — the draft is never the final design (we already solve this better)

The thread's step 2 is *"get specific about what feels wrong"*. That is the right instinct and
its bottleneck is **being specific fast**. We already have the fix the thread does not:
**`/element-inspector`** — the operator selects the element in the running app and pastes its
descriptor plus exact `file:line`. "Quita ESTO" becomes an unambiguous edit.

```
WHEN the first draft exists → THEN I do NOT ask "does it look good?"
  I make the feedback loop cheap instead:
  - The inspector goes in EARLY on any web surface we iterate on visually
    (gate it to admins, match the app's accent colour so it feels native).
  - I ask for a specific complaint per element, not a global verdict.
  - The draft is a hypothesis. Two or three critique rounds are the normal
    path, not a sign something went wrong.
```

### Step 3 — we do NOT round-trip to Figma (declined, with the reason)

His step 3 takes the built page into Figma to "make it mine". **Not for us.** On the TheNomba
stack (Vite/React or Next + Tailwind + Netlify) **the code IS the design**; a Figma file made
*after* the build is a second source of truth that goes stale the moment the repo moves. It
makes sense for him — he sells templates, so the design file is his deliverable. Our deliverable
is a deployed site.

```
WHEN the draft needs taste applied → THEN apply it ON the real thing:
  premium-web-craft (conversion + craft detailing) and /design-review on the
  rendered page, judged in the browser at real breakpoints — not on a canvas
  that nobody deploys.
  Figma stays valid BEFORE the build (moodboard, reference collage) — which is
  Phase 0 — never as a post-build refinement step.
```

## What to do when creating

```
WHEN about to create web / image / video / content:
0. Run PHASE 0 first — references in hand (his, ours, or the shelf) + anti-reference.
1. Name the SYSTEM first — tokens, contract, template, parameter set. Not the pixels.
   Each parameter traces back to a reference from Phase 0, never to my own invention.
2. Derive the piece FROM the system (a parameterization of it), never freehand.
3. Make every knob explicit and reusable: design tokens, seeds, Elements/anchors,
   prompt structure, component props, layout schema.
4. Check the piece composes with the set (shares the same system) — not just that it
   looks fine alone.
5. Texture / grain / "organic" feel is allowed ONLY as a parameter OF the system,
   never as the method of work.
```

By surface:
- **Web** → design tokens + tested component library (e.g. the MercoTax/Folio system). Never one-off CSS per screen.
- **Image / video** → explicit, reusable parameters: structured prompts, fixed seeds, Elements/character anchors, per-setting reference images, templates. Not random rolls hoping for a hit.
- **Content** → architecture first (brief, contract, template); pieces derive from the system, not the reverse.

## Acceptance test (am I shipping a system or noise?)

- Can I change ONE parameter and regenerate the whole thing coherently? (scalable)
- Can I describe the piece as a short list of parameters someone could reproduce? (summarizable)
- Can I put a number on it — size, count, score, token budget? (quantifiable)
- Does it fit the set because it shares the system, not by luck?

Any "no" → it's noise. Rebuild from the system.

## Examples from real sessions

### ✅ MercoTax (ex-Folio) design system (2026-06)
`docs/DESIGN.md` defines tokens (palette, type scale, radii, motion) + a component library. Every screen derives from it. Result: rename, re-skin (dark→Modo Pro→sky), and radius −15% were each a one-parameter change that propagated coherently. Summarizable (a token file), scalable (change token → whole app updates), quantifiable (token count, test count). That is the standard.

### ❌ The anti-pattern to avoid
Generating reels/images by firing random AI generations and picking what looks good. Each output is orphaned — not reproducible, not editable with precision, doesn't compose into a series. Fix: define the parameter set (Elements, seeds, prompt blocks, per-setting anchors) and derive every piece from it.

## Detection signals

I'm producing noise when I: start writing a prompt or a component before a single reference is on the table; invent an aesthetic direction instead of deriving it; ask "does it look good?" instead of making the critique loop cheap; start from pixels/output instead of a system; can't reproduce a result I liked; tweak by re-rolling instead of by parameter; ship a piece that looks fine alone but doesn't match its set; can't put a number on what I made; describe the work as "vibes" instead of parameters.

## What this does NOT mean

- Not "no texture/grain ever" — grain is fine as a *parameter* of the system.
- Not "no AI generation" — generate, but from explicit reusable parameters, not random rolls.
- Not over-engineering a one-shot throwaway. Match system depth to reuse: a single never-repeated asset needs less; anything that recurs or belongs to a set needs the system.

## Enforcement loop

```
About to create:
0. References on the table (Phase 0 intake done)?  → no: ask/bring them BEFORE prompting.
1. System defined (tokens/contract/params)?   → no: define it first.
2. Piece derived from the system?              → no: rebuild from it, don't freehand.
3. Passes summarizable/scalable/quantifiable?  → no: it's noise, redo.
4. Composes with the set?                       → no: align to the shared system.
```

## How this interacts with other protocols

- **`grand-scheme-first.md`** — the system IS the big picture; define it before pieces.
- **`triangulate-references.md`** — parameters/structure should triangulate to verified references, not invented.
- **`layer-by-layer.md`** — tokens/contract are the foundation layer; surfaces derive from it.
- **`survey-before-building.md`** — Phase 0 step (c) IS that survey, applied to design: check our own systems before importing anyone else's.
- **`functional-first.md`** — Phase 0 is about DIRECTION, not about building UI before the backend works. Collecting references is cheap and happens first; building the surface still waits its turn.
