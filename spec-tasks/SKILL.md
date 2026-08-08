---
name: spec-tasks
description: Fase 3 del flujo spec-driven — descompone el design.md aprobado en specs/<feature>/tasks.md como tareas concretas y verificables, cada una con criterio de éxito chequeable. Genérico. FRENA para revisión.
---

# spec-tasks — Fase 3: Tareas (genérico)

Precondición: existe `specs/<feature>/design.md` aprobado. Si falta, pará y pedí /spec-design.

## Contexto (leer SIEMPRE antes de actuar)
Leé el `design.md` y las convenciones del repo. Si el cambio toca valores, flujo, contrato o
feature documentado en un doc de verdad, el sync de ese doc es una TAREA numerada obligatoria
(no un ítem opcional de cierre).

## Pasos
1. Leé `design.md` del feature.
2. Descomponé en tareas chicas, ordenadas por dependencia. Cada tarea:
   - Es un cambio atómico y revisable.
   - Nombra los archivos/módulos que toca.
   - Tiene un **criterio de verificación ejecutable** (no "listo"): un comando que debe pasar.
3. Incluí tareas de soporte según el stack: generación de código, migraciones, localización/i18n,
   fixtures/seeds, y sync de docs de verdad si hubo cambio de negocio/valores/contrato.
4. Generá `specs/<feature>/tasks.md` como checklist: `- [ ] T<n>: <acción> — archivos: … — verifica: <comando>`.
5. Resumí total de tareas y orden, y **FRENÁ**:
   "Revisá tasks. Cuando lo apruebes, corré /spec-build."

## Descubrí los comandos de verificación del proyecto
No asumas el stack. Mirá `package.json`/`Makefile`/`pyproject.toml`/CI config, o preguntá.
Típicamente: lint, typecheck, test unitario del archivo tocado, build. El gate de una tarea es
un comando concreto de ESE proyecto cuya salida se pueda pegar como evidencia.

## Reglas
- Prohibido criterio no verificable ("funciona", "se ve bien").
- No codees acá.
