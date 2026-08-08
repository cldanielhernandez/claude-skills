---
name: spec-explore
description: Fase 0 divergente antes de definir requerimientos. Explora un problema desde 3 ópticas fijas (UX, Producto, Tech) con subagentes en paralelo, cruza tensiones y converge en 2-3 enfoques candidatos rankeados. FRENA para decisión humana. Portable — no depende de ningún repo en particular.
---

# spec-explore — Fase 0: Exploración (divergir antes de converger)

Objetivo: tomar un problema difuso y explorarlo desde múltiples ángulos ANTES de comprometerse
con una solución. Acá NO se definen requerimientos, NO se diseña y NO se codea: se DIVERGE.

Esta skill es de propósito general (sirve para cualquier proyecto). No asume archivos ni docs
de ningún repo. Si el proyecto tiene docs de fuente de verdad, se leen; si no, no pasa nada.

## Principio
El error más caro no es implementar mal, es converger rápido en el problema equivocado.
Esta fase es el seguro contra eso: genera opiniones INDEPENDIENTES antes de juzgar ninguna,
para no anclarse en la primera idea.

## Las 3 ópticas (fijas) + transversales (opcionales)
Óptica = el eje que se evalúa. Rol = la persona con criterio que lo encarna.

| Óptica (siempre) | Rol por defecto | Pregunta que responde |
|---|---|---|
| 🎨 UX | UX Designer / Researcher | ¿Qué necesita el usuario de verdad? ¿Dónde hay fricción o dolor? |
| 📦 Producto | Business Analyst / PM | ¿Qué valor mueve? ¿Reglas de negocio, métricas, casos borde? |
| ⚙️ Tech | Arquitecto de software | ¿Cuál es el enfoque más simple que funciona? ¿Qué se rompe / qué deuda deja? |

Transversales — sumar SOLO si el problema lo amerita (máx 2, para no ahogar la síntesis):
- 🔒 Seguridad — datos sensibles, pagos, auth, PII, cumplimiento.
- 😈 Contrarian / Riesgo — su único trabajo es argumentar por qué NO hacer esto.

## Pasos

1. **Enmarcar.** Reformulá el problema como una PREGUNTA ("¿Cómo logramos que…?"), no como
   una solución. Mostrásela al usuario y confirmá que es el problema correcto antes de seguir.
   Compuerta corta: si el enmarcado está mal, todo lo demás está mal.
   - Si el proyecto tiene docs de contexto/negocio (ej. un PRODUCT_SUMMARY, un README, specs
     previas), leelos rápido para no explorar a ciegas. Si no hay, seguí igual.
   - Preguntá qué transversales sumar (Seguridad / Contrarian) según el riesgo del problema.

2. **Divergir (fan-out ligero).** Lanzá UN subagente por óptica EN PARALELO (una sola tanda de
   Agent tool con varios tool_use). Cada subagente:
   - Adopta su rol explícitamente ("Sos un/a <rol> senior…").
   - Recibe SOLO el problema enmarcado y el contexto mínimo — NO ve lo que opinan los otros
     (esto es lo que evita el sesgo de anclaje; es deliberado).
   - Devuelve: 3-5 insights, los principales riesgos/dolores desde su óptica, y qué enfoque
     propondría. Conciso, con criterio, sin relleno.
   - Usá subagentes ligeros (Agent tool / Explore para research). Nada de workflows pesados acá.

3. **Cruzar tensiones.** Con las 3 respuestas en mano, identificá los CHOQUES entre ópticas
   ("lo que UX quiere rompe lo que Tech puede sostener", "lo que Producto pide agrega riesgo de
   seguridad"). Las tensiones son la parte más valiosa: ahí viven las decisiones reales.

4. **Converger.** Destilá en 2-3 ENFOQUES candidatos, rankeados, cada uno con pros, contras,
   esfuerzo estimado y qué óptica prioriza. Marcá una recomendación con su porqué. Dejá las
   preguntas abiertas que el usuario necesita responder para elegir.

5. **Frenar.** Escribí el resultado (ver formato abajo) y **PARÁ**:
   "Revisá la exploración. Elegí un enfoque y con eso arrancamos la definición (ej. /spec-new
   o como definas requerimientos en este proyecto)."
   NO generes requerimientos ni diseño. La salida de esta fase ALIMENTA a la siguiente, no la
   reemplaza.

## Salida
Escribí un archivo `exploration.md`. Ubicación, en orden de preferencia:
- Si el proyecto usa la convención `specs/<feature>/` → `specs/<feature>/exploration.md`.
- Si no, preguntá dónde, o dejalo en la raíz del proyecto / carpeta de trabajo como
  `exploration-<tema>.md`.

Formato:

```markdown
# Exploración: <tema>

## Problema (enmarcado como pregunta)
> ¿Cómo logramos que…?   ← acordado en el paso 1

## Hallazgos por óptica
### 🎨 UX — rol: <rol>
- ...
### 📦 Producto — rol: <rol>
- ...
### ⚙️ Tech — rol: <rol>
- ...
### 🔒 Seguridad / 😈 Contrarian   (si se sumaron)
- ...

## Tensiones entre ópticas
- <óptica A> quiere X ↔ <óptica B> solo sostiene Y → implicancia

## Enfoques candidatos (rankeados)
| # | Enfoque | Prioriza | Pro | Contra | Esfuerzo | Reco |
|---|---------|----------|-----|--------|----------|------|

## Preguntas abiertas para decidir
- ...

## Recomendación
<cuál y por qué> → alimenta la definición de requerimientos.
```

## Reglas
- Un problema por exploración. Si aparecen dos, proponé separarlos.
- NADA de decisiones de implementación finales acá — esto abre el espacio, no lo cierra.
- Las 3 ópticas son obligatorias; las transversales son opcionales y acotadas.
- Los subagentes NO se ven entre sí durante la divergencia. Es a propósito.
- No escribas más archivos que el `exploration.md`.
- Siempre terminá con la compuerta humana. No avances de fase solo.
