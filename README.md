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

## Skills

### `/spec-explore` — Fase 0: Exploración (divergir antes de converger)

Fase previa a definir requerimientos. Toma un problema difuso y lo explora desde **3 ópticas
fijas** con subagentes independientes en paralelo, cruza las tensiones entre ellas y converge
en 2-3 enfoques candidatos rankeados. Termina con compuerta humana — no avanza solo.

- 🎨 **UX** (rol: UX Designer/Researcher)
- 📦 **Producto** (rol: Business Analyst/PM)
- ⚙️ **Tech** (rol: Arquitecto de software)
- 🔒 Seguridad / 😈 Contrarian — transversales opcionales, solo si el problema lo amerita.

Los subagentes **no se ven entre sí** durante la divergencia: es a propósito, para evitar el
sesgo de anclaje en la primera idea.

## La metodología completa

`/spec-explore` es la **Fase 0** de un flujo spec-driven más largo. Diverge primero, converge después:

```
Fase 0: Exploración  →  Requirements → Design → Tasks → Build → Verify
   (DIVERGIR)              (CONVERGER ──────────────────────────────►)
 /spec-explore            (flujo /spec-* específico de cada proyecto)
```

Las fases de convergencia (`/spec-new`, `/spec-design`, etc.) son específicas de cada proyecto
y viven en el `.claude/skills/` de cada repo. La exploración es lo único genuinamente
transversal, y por eso vive acá.
