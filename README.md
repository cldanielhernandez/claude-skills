# claude-skills — Skills personales de Claude Code

Skills de **usuario** (no atados a ningún repo) que uso en todas mis máquinas: laptop personal
y notebook de trabajo. Viven en `~/.claude/skills/` para que Claude Code los liste como
`/comando` en **cualquier** proyecto.

## Instalar en una máquina nueva

```bash
# ~/.claude/skills debe estar vacío o no existir
git clone <URL-de-este-repo> ~/.claude/skills
```

Para actualizar: `cd ~/.claude/skills && git pull`.

> Guardá acá **solo** skills transversales (sirven en cualquier proyecto). Los skills
> específicos de un proyecto van en el `.claude/skills/` de ese repo, no acá.

## La metodología: diverge primero, converge después

El flujo completo spec-driven, con **compuerta humana** entre cada fase (Claude resume y FRENA,
no avanza solo):

```
Fase 0: Exploración  →  Requirements → Design → Tasks → Build → Verify
   (DIVERGIR)              (CONVERGER ──────────────────────────────►)
 /spec-explore           /spec-new  /spec-design  /spec-tasks  /spec-build  /spec-verify
```

Estas son las versiones **genéricas** (project-agnostic): no asumen stack ni docs de un repo
puntual — leen la fuente de verdad que EXISTA (README, `CLAUDE.md`/`AGENTS.md`, ADRs, tickets)
y descubren los comandos de verificación del proyecto (lint/test/build) en vez de asumirlos.

## Skills

| Skill | Fase | Qué hace |
|---|---|---|
| `/spec-explore` | 0 · Explorar | Diverge un problema desde 3 ópticas (🎨 UX · 📦 Producto · ⚙️ Tech) con subagentes independientes en paralelo → tensiones → 2-3 enfoques rankeados. |
| `/spec-new` | 1 · Requerimiento | Refina la idea con preguntas → `requirements.md` sin ambigüedad. |
| `/spec-design` | 2 · Diseño | Decisiones de arquitectura + trade-offs contra el requirements → `design.md`. |
| `/spec-tasks` | 3 · Tareas | Descompone en tareas atómicas, cada una con criterio ejecutable → `tasks.md`. |
| `/spec-build` | 4 · Build | Implementa una tarea a la vez; no cierra ninguna sin evidencia (comando que pasa). |
| `/spec-verify` | 5 · Verificar | Audita el código contra el requirements original y reporta gaps (no arregla). |

Principio de la Fase 0: los subagentes **no se ven entre sí** durante la divergencia — es a
propósito, para evitar el sesgo de anclaje en la primera idea.

## Precedencia: genérico (user) vs específico (proyecto)

Un proyecto puede tener su **propia** versión afinada de estos skills en su `.claude/skills/`
(p. ej. tour-app tiene `/spec-new` que lee sus docs de negocio). Cuando coincide el nombre, la
versión **del proyecto gana** sobre la de este repo. Resultado buscado:

- **En un proyecto con `/spec-*` propios** → se usan los del proyecto (más afinados).
- **En cualquier otro proyecto** → se usan estos genéricos.

Por eso acá van **solo** skills transversales. Los específicos de un proyecto viven en su repo.
