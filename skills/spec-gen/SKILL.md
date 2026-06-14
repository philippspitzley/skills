---
name: spec-gen
description: Generates a detailed 6-section feature implementation spec file for a specific build unit. Use before implementing a new feature to ensure spec-driven development.
---

# Feature Spec Generator

Replace vague feature prompts with a complete instruction set for a single build unit. The coding agent will implement *exactly* what is written—no more, no less.

## Prerequisites
Load these files before writing the spec:
1. `context/project-overview.md`
2. `context/architecture.md`
3. `context/ui-context.md`
4. `context/ui-registry.md`
5. `context/specs/00-build-plan.md`
6. `package.json` (inspect available scripts: test, lint, etc.)
7. `AGENTS.md` (available skills for this unit)

*(If the user hasn't specified which unit to build, ask them.)*

## Clarification
Don't guess. If behavior, UI layout, or technical approach is unclear, **ask the user** to lock decisions before writing the spec.

## Generation
Save the spec to `context/specs/[unit-number]-[feature-name-kebab-case].md` (e.g., `context/specs/01-auth-pages.md`).

Follow this exact 6-section template:

```markdown
# Unit NN: [Feature Name]

## Goal
[1-2 sentences: concrete output. E.g., "Create sign-in and sign-up pages using Clerk components with a two-panel layout on desktop and form-only on mobile."]

## Design
[Layout, components, responsiveness. Reference ui-context.md tokens and ui-registry.md patterns. Note new component types to add to ui-registry.md after implementation.]

## Implementation
### [Component or Sub-section Name]
[What to build—unambiguous "done" criteria.]

### [Next sub-section]
[Description]

## Dependencies
[Packages needed that aren't installed. If none, write "None".]
- package-name (reason)

## Skills
[Relevant skills from AGENTS.md. If none, write "None".]
- skill-name (reason)

## Verify when done
[Feature-specific conditions. Always include: no TS/console errors, responsive, build passes. Add project scripts from package.json (lint, test).]
- [ ] [Feature condition 1]
- [ ] [Feature condition 2]
- [ ] New component types captured in `context/ui-registry.md` (if any)
```