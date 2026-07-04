# Startup Creator — workflow 111x (v2)

**Status:** 🟢 ACTIVE · v2 (revisión Claude sobre el v1 del operador, 2026-07-04)
**Objetivo:** montar una startup funcional (app + landing + ads) en 1–3 días, con calidad premium y sin quemar tokens.
**Caso de validación:** MercoTax (app fiscal local) — fases 1–4 completadas antes de codificar este playbook.

---

## Principio rector

Cada fase produce UN artefacto en el repo del producto, con un gate verificable antes de pasar a la siguiente. El repo es la única fuente de verdad — no hay contexto que viva solo en un chat. Todo se crea por sistema (`protocols/parametric-creation.md`): resumible · escalable · cuantificable.

## Los roles (quién hace qué, sin pisarse)

| Actor | Hace | Nunca |
|---|---|---|
| **Operador** | Prompt inicial, decisiones de gusto/negocio, gates, edición liviana en Devin | Editar archivos que Claude tiene abiertos esa sesión |
| **Claude** | Research verificado, spec, fundación+motor con tests, infra pesada, features multi-archivo, QA navegador, MCPs (Framer/Higgsfield/Koda/Figma) | Pixel-pushing iterativo (caro), copy menor |
| **Devin/Windsurf** | Edits livianos supervisados: textos, estilos, spacing, pantallas | Motor/lógica de negocio, esquema DB, cadenas legales |

**Regla de oro:** nunca dos agentes en el mismo archivo. Reparto por carpeta (`server/` = Claude · `src/screens` textos/estilos = Devin) + commit antes de cada relevo. Git es el airlock.

## Las 8 fases (v2 — con gates y artefactos)

| # | Fase | Artefacto (en repo) | Gate para avanzar |
|---|---|---|---|
| 0 | **Spec** — prompt del operador → research real de mercado (Rule #0: fuentes verificadas) → preguntas → brief → Claude se auto-genera el prompt optimizado | `docs/BRIEF.md` | Operador aprueba brief |
| 1 | **Arquitectura + diseño como contrato** | `docs/ARCHITECTURE.md` + `docs/DESIGN.md` (tokens) + `CLAUDE.md`↔`.windsurfrules` (symlink) | Contratos escritos ANTES de píxeles |
| 2 | **Fundación** (Claude): motor puro con tests, DB, API, tokens CSS | tests verdes | `npm test` verde + typecheck |
| 3 | **Superficies** en paralelo (Workflow: 1 agente/pantalla, contrato fijo) + **inspector de elementos SIEMPRE** (⌘⇧E, data-loc file:line) | pantallas | QA navegador real (browse) + 0 errores consola |
| 4 | **Relevo Devin**: operador pule lo liviano; Claude arregla lo que el inspector reporte | commits WIP | `npm test` tras cada sesión manual |
| 5 | **Creatividades internas** (solo si la app las necesita) — Higgsfield con parámetros reutilizables (seeds/Elements/plantillas) | `docs/CREATIVE.md` (parámetros) | assets integrados |
| 6 | **Landing** — Claude → Framer MCP. La landing deriva de `DESIGN.md` (mismos tokens) | proyecto Framer publicado | operador aprueba en vivo |
| 7 | **Ads** — matriz formatos (9:16 · 16:9 · 1:1 · 4:5) × conceptos × [estático/vídeo]. Higgsfield + Koda. Un `ADS.md` con el sistema (prompts estructurados, no random) | `docs/ADS.md` + assets en batch | matriz completa entregada en una carpeta |
| 8 | **Recap** — brief de producto para cliente + postmortem al claude-ops | `docs/RECAP.md` + entrada aquí | /context-save |

Nota de orden: 6 y 7 pueden solaparse con 4 (no tocan código). Figma (si aplica: pitch/entrevista/handoff a diseñador) es una rama de la fase 6: se replica DESDE la app real, nunca antes — la app es la fuente, el mockup es un export.

## Las 4 fricciones — resueltas

**1 · Doble chat (Devin + Claude).** No se resuelve con un canal — se resuelve con que el canal no importe: el estado vive en el repo. `docs/state.md` del producto (patrón claude-ops) = qué está hecho, qué está en curso, quién tiene qué carpeta. Cada agente lo lee al entrar y lo actualiza al salir. El operador no re-explica nada: pega la ruta del repo y "lee docs/state.md". Complemento: /context-save al cerrar sesión Claude.

**2 · Contexto entre chats.** Git + markdown en el repo del producto, NO Obsidian ni notebook externo: (a) ambos agentes leen repos nativamente, Obsidian es una app-capa que los agentes no ven; (b) versionado = auditable; (c) ya existe el patrón (CLAUDE.md leído por Claude, symlink .windsurfrules leído por Windsurf/Devin — probado en MercoTax). Los transversales (este workflow, protocolos) viven en claude-ops; lo del producto, en su repo.

**3 · Tokens.** ponytail (código mínimo que funciona) + caveman (prosa comprimida) en las sesiones Claude; Devin para el pixel-pushing iterativo; Workflow/subagentes solo donde el paralelismo es real. Regla: Claude toca teclado para lo que Devin no puede hacer bien.

**4 · Desorden de contenidos.** Un archivo canónico por dominio, siempre los mismos nombres: `BRIEF.md · ARCHITECTURE.md · DESIGN.md · CREATIVE.md · ADS.md · RECAP.md · state.md`. Los assets en `assets/` con naming paramétrico: `{producto}-{concepto}-{formato}-{v}.{ext}` (ej. `mercotax-oldmoney-9x16-v2.png`). Un batch = una carpeta con manifest.

## Anti-patrones que este workflow previene

- Mockup-first (Figma antes de app): el mockup miente; la app real es más barata de mockear después.
- Generación random de creatividades: sin sistema de parámetros no hay serie coherente ni regeneración.
- Contexto en la cabeza del operador: si no está en el repo, no existe.
- Dos agentes en el mismo archivo "para ir más rápido".
