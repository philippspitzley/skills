## Application Building Context

Read the following files in order before implementing
or making any architectural decision:

1. `context/project-overview.md` — product definition,
   goals, features, and scope
2. `context/architecture.md` — system structure,
   boundaries, storage model, and invariants
3. `context/ui-context.md` — theme, colors, typography,
   and component conventions
4. `context/ui-registry.md` — implemented component
   patterns and visual consistency record
5. `context/code-standards.md` — implementation rules
   and conventions
6. `context/ai-workflow-rules.md` — development workflow,
   scoping rules, and delivery approach
7. `context/progress-tracker.md` — current phase,
   completed work, open questions, and next steps

Update `context/progress-tracker.md` after each
meaningful implementation change.

If implementation changes the architecture, scope, or
standards documented in the context files, update the
relevant file before continuing.

## Available Skills

Use these skills during implementation. Invoke them
when the spec file for a unit references them.

### Workflow

- `commit-gen` — generate commit messages
- `ui-snapshot` — capture UI component patterns to
  `ui-registry.md`

### Stack-specific

[Populate based on the tech stack identified by the
architect. List each skill with a one-line purpose.]

- [e.g. `tailwind` — Tailwind CSS patterns and utilities]
- [e.g. `react` — React component patterns]
- [e.g. `tanstack-query` — data fetching and caching]
