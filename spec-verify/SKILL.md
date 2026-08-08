---
name: spec-verify
description: Fase 5 del flujo spec-driven — verifica la implementación contra el requirements.md original de specs/<feature>/ y reporta gaps. Genérico. NO arregla nada por su cuenta, solo reporta.
---

# spec-verify — Fase 5: Verificación (genérico)

Objetivo: auditoría independiente. Leés la spec original, no las notas del build.

## Contexto (leer SIEMPRE antes de actuar)
Leé la fuente de verdad del proyecto. Una feature NO está verificada si un doc de verdad quedó
desincronizado con el código cuando el cambio lo exigía.

## Pasos
1. Leé `specs/<feature>/requirements.md` (la fuente de verdad de la spec) y `design.md`.
2. Por cada criterio de aceptación y caso borde: verificá en el código real si está cubierto.
3. Corré los gates globales del proyecto y guardá la evidencia (descubrí los comandos reales:
   lint / typecheck / test / build según el stack). Pegá la salida.
4. Chequeá que los docs de verdad quedaron en sync si el cambio lo exigía. Si no → veredicto ⚠️
   con gaps, NO ✅.
5. Generá `specs/<feature>/gap-report.md`: por cada criterio → ✅ cubierto / ⚠️ parcial / ❌ falta,
   citando qué se observó en el código.
6. Resumí el veredicto global. **NO arregles nada.**

## Reglas
- No modificás código de producción. Si hay que arreglar, el usuario decide y se vuelve a /spec-build.
- Cada gap cita el criterio del requirements + qué se observó.
