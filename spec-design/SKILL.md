---
name: spec-design
description: Fase 2 del flujo spec-driven — lee el requirements.md APROBADO de specs/<feature>/ y propone design.md con decisiones de arquitectura y trade-offs. Genérico, sirve en cualquier proyecto. FRENA para revisión.
---

# spec-design — Fase 2: Diseño (genérico)

Precondición: existe `specs/<feature>/requirements.md` aprobado. Si falta o no está aprobado,
pará y pedí correr /spec-new primero.

## Contexto (leer SIEMPRE antes de actuar)
Leé la fuente de verdad que exista (docs de arquitectura/negocio, ADRs, convenciones del repo,
`CLAUDE.md`/`AGENTS.md`).
- Todo valor numérico o de negocio se referencia a su doc con la sección exacta. Prohibido
  hardcodear un número que ya vive (o debería vivir) en un doc de verdad.
- Si falta un valor en los docs, se agrega como tarea de doc (no se inventa en el código).
- Si el diseño contradice un doc → PARÁ y preguntá cuál gana.

## Pasos
1. Leé el `requirements.md` del feature + los docs de arquitectura/convenciones del proyecto.
2. Mapeá el cambio a la arquitectura REAL del repo: qué módulos/carpetas/archivos toca. Descubrí
   las convenciones existentes (estructura de carpetas, patrones de estado, capa de datos) y respetalas
   en vez de imponer un patrón nuevo.
3. Proponé el diseño respetando las reglas DURAS del proyecto (las que digan `CLAUDE.md`/`AGENTS.md`,
   linters, o el usuario). Principios transversales por defecto: secretos fuera del código,
   separación de capas, SSOT del estado, valores configurables fuera del código.
4. Documentá trade-offs: al menos 1 alternativa descartada y por qué.
5. Generá `specs/<feature>/design.md` con esta estructura:
   `# Diseño: <feature>` · Enfoque elegido · Archivos/módulos afectados · Decisiones clave ·
   Alternativas descartadas (con motivo) · Riesgos · Trazabilidad a cada criterio del requirements.
6. Resumí las decisiones clave y **FRENÁ**:
   "Revisá el design. Cuando lo apruebes, corré /spec-tasks."

## Reglas
- El diseño se ata 1:1 a los criterios de aceptación del requirements. Si algo no traza, marcalo.
- No escribas código de producción todavía.
