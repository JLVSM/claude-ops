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

## What to do when creating

```
WHEN about to create web / image / video / content:
1. Name the SYSTEM first — tokens, contract, template, parameter set. Not the pixels.
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

I'm producing noise when I: start from pixels/output instead of a system; can't reproduce a result I liked; tweak by re-rolling instead of by parameter; ship a piece that looks fine alone but doesn't match its set; can't put a number on what I made; describe the work as "vibes" instead of parameters.

## What this does NOT mean

- Not "no texture/grain ever" — grain is fine as a *parameter* of the system.
- Not "no AI generation" — generate, but from explicit reusable parameters, not random rolls.
- Not over-engineering a one-shot throwaway. Match system depth to reuse: a single never-repeated asset needs less; anything that recurs or belongs to a set needs the system.

## Enforcement loop

```
About to create:
1. System defined (tokens/contract/params)?   → no: define it first.
2. Piece derived from the system?              → no: rebuild from it, don't freehand.
3. Passes summarizable/scalable/quantifiable?  → no: it's noise, redo.
4. Composes with the set?                       → no: align to the shared system.
```

## How this interacts with other protocols

- **`grand-scheme-first.md`** — the system IS the big picture; define it before pieces.
- **`triangulate-references.md`** — parameters/structure should triangulate to verified references, not invented.
- **`layer-by-layer.md`** — tokens/contract are the foundation layer; surfaces derive from it.
