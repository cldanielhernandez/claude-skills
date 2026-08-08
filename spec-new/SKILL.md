---
name: spec-new
description: Fase 1 del flujo spec-driven — refina un requerimiento haciendo preguntas y genera specs/<feature>/requirements.md sin ambigüedad. Genérico, sirve en cualquier proyecto. Termina resumiendo y FRENA para revisión humana.
---

# spec-new — Fase 1: Requerimiento (genérico)

Objetivo: convertir una idea vaga en un `requirements.md` sin ambigüedad. NO diseñás ni codeás acá.
Versión project-agnostic: no asume stack ni docs de un repo puntual.

## Contexto (leer SIEMPRE antes de actuar)
Buscá la fuente de verdad que EXISTA en este proyecto y leela: `CLAUDE.md`/`AGENTS.md`, README,
docs de negocio/arquitectura, ADRs, tickets (Jira/Confluence/Linear), specs previas.
- NO inventes valores ni reglas de negocio que ya viven (o deberían vivir) en esos docs: citalos.
- Si no hay docs, pedile al usuario el contexto mínimo antes de seguir.
- Si la idea contradice un doc de verdad → PARÁ y preguntá cuál gana. No resuelvas en silencio.
- Si la idea agrega/cambia algo documentado → sincronizar ese doc es una TAREA obligatoria del flujo.

## Pasos
1. Leé el contexto disponible. Ubicá el requerimiento dentro de lo que ya existe; si hay algo
   parecido, citá la sección/ticket exacto.
2. Pedí el nombre del feature en kebab-case → definís `specs/<feature>/` (respetá otra convención
   de specs si el proyecto ya la tiene).
3. Hacé preguntas hasta eliminar ambigüedad. Una tanda a la vez; no avances con huecos. Mínimo cubrí:
   - Problema y usuario/actor objetivo (¿qué gana?).
   - Alcance concreto y qué queda EXPLÍCITAMENTE fuera.
   - Criterios de aceptación observables (no "que ande bien").
   - Casos borde relevantes al dominio (errores, permisos, offline, datos vacíos, concurrencia…).
   - Impacto en config, datos, integraciones o contratos existentes (si aplica).
4. Generá `specs/<feature>/requirements.md` con esta estructura:
   `# Requerimiento: <feature>` · Problema y objetivo · Alcance · Fuera de alcance ·
   Criterios de aceptación (checklist observable) · Casos borde · Dependencias/impacto.
5. Resumí en 5-8 bullets qué quedó definido y **FRENÁ**:
   "Revisá el requirements. Cuando lo apruebes, corré /spec-design."

## Reglas
- Un requerimiento por feature. Si aparecen dos, proponé dividir.
- NADA de decisiones de implementación acá (eso es design.md).
- No escribas otros archivos que no sean el requirements.md.
