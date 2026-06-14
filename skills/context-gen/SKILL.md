---
name: context-gen
description: Synthesizes a planning conversation into the Seven-File Context System plus AGENTS.md index. Use when a project architecture conversation concludes and the user wants to generate the final context documentation.
---

# Context Generator

Synthesize the architectural conversation into context files that guide coding agents. Templates are in your bundled `templates/` directory.

## Workflow

Generate files **one at a time** in order. After each file, **pause** for user approval before proceeding.

1. Create `context/` directory
2. For each file: read the template, generate content replacing `[bracketed text]`, present to user, wait for approval.

**Files (in order):**
1. [project-overview.md](./templates/context/project-overview.md) → `context/project-overview.md`
2. [architecture.md](./templates/context/architecture.md) → `context/architecture.md`
3. [ui-context.md](./templates/context/ui-context.md) → `context/ui-context.md`
4. [ui-registry.md](./templates/context/ui-registry.md) → `context/ui-registry.md`
5. [code-standards.md](./templates/context/code-standards.md) → `context/code-standards.md`
6. [ai-workflow-rules.md](./templates/context/ai-workflow-rules.md) → `context/ai-workflow-rules.md`
7. [progress-tracker.md](./templates/context/progress-tracker.md) → `context/progress-tracker.md`
8. [AGENTS.md](./templates/AGENTS.md) → `AGENTS.md` (root)

## Rules

- Preserve template headings and markdown structure exactly
- Fill `progress-tracker.md` with immediate next steps from the plan
- Never generate multiple files without explicit approval