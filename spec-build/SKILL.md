---
name: spec-build
description: Fase 4 del flujo spec-driven — implementa specs/<feature>/tasks.md una tarea a la vez contra el plan. No cierra una tarea sin evidencia verificable (el comando de la tarea pasa). Genérico. Marca progreso en tasks.md.
---

# spec-build — Fase 4: Build (genérico)

Precondición: existe `specs/<feature>/tasks.md` aprobado. Si falta, pará y pedí /spec-tasks.

## Contexto (leer SIEMPRE antes de actuar)
Leé las convenciones del repo (`CLAUDE.md`/`AGENTS.md`, linters, docs de verdad).
- No inventes valores ni features: salen del design/docs.
- Si tocás valores/flujo/contrato documentado, la tarea de sync de docs es obligatoria (ver tasks.md).

## Loop por tarea (estricto)
Para cada tarea en orden:
1. Anunciá qué tarea vas a hacer.
2. Implementá SOLO esa tarea. No adelantes trabajo de tareas futuras.
3. Corré el criterio de verificación de ESA tarea (el comando que definió tasks.md para este stack).
4. Pegá la salida real del comando como EVIDENCIA. Si falla, arreglá antes de seguir; no avances.
5. Marcá la tarea en `tasks.md`: `- [ ]` → `- [x]` (con el comando que pasó).
6. Pasá a la siguiente.

## Reglas duras
- "Listo" no es evidencia. Solo cuenta la salida de un comando que pasó.
- No inventes tests/gates que el proyecto no tiene. Usá el gate real disponible (lint/typecheck/build
  si no hay runner de tests). No afirmes "tests pasan" donde no hay tests.
- Respetá las reglas del proyecto (las de `CLAUDE.md`/`AGENTS.md` mandan sobre cualquier default).
- Si una tarea revela que el diseño estaba mal, PARÁ y avisá — no rediseñes en silencio; volvé a /spec-design.
- No commitees ni pushees salvo que el usuario lo pida.

## Cierre
Cuando todas las tareas estén `[x]`: resumí y sugerí correr /spec-verify.
