---
name: feature-spec-generator
description: Generates a highly detailed, 5-section feature implementation spec file for a specific build unit. Use this right before implementing a new feature to ensure spec-driven development.
---

# Feature Spec Generator

Your goal is to replace vague feature prompts with a complete, detailed instruction set (a Spec File) for a single build unit. The coding agent will read this spec file and implement *exactly* what is written—no more, no less.

## Prerequisites & Context Loading
Before writing the spec, you MUST understand the project constraints and available tooling. Use your `read` tool to load:
1. `context/project-overview.md`
2. `context/architecture.md`
3. `context/ui-context.md`
4. `context/ui-registry.md` (for existing component patterns — reference these in the Design section)
5. `context/specs/00-build-plan.md` (to locate the specific unit)
6. `package.json` (or equivalent build file like `Cargo.toml`, `pyproject.toml`) to inspect available scripts (e.g., test, lint, ultracite).

*(If the user hasn't specified which unit they want to build, ask them.)*

## Clarification Phase
Do NOT guess implementation details. If the specific behavior, UI layout, or technical approach for this feature is unclear from the context, **ask the user questions** to lock down the decisions *before* writing the spec.

## Generation Rules
When the feature is fully understood, generate the spec file and save it to `context/specs/[unit-number]-[feature-name-kebab-case].md` (e.g., `context/specs/01-auth-pages.md`).

You MUST strictly follow this exact 5-section template:

```markdown
# Unit NN: [Feature Name]

## Goal
[One or two sentences describing the concrete output of this unit. Be specific. E.g., "Create sign-in and sign-up pages using Clerk components with a two-panel layout on desktop and form-only on mobile."]

## Design
[Visual and structural decisions specific to this unit. Reference ui-context.md tokens where relevant. If building a component type that already exists in `context/ui-registry.md`, match its pattern exactly — reference it by name. If this introduces a new component type, note that it should be added to `context/ui-registry.md` after implementation. Describe layout behavior, component choices, and responsiveness requirements.]

## Implementation
### [Component or Sub-section Name]
[Detailed description of what to build. Enough detail that there is no ambiguity about what "done" looks like.]

### [Next sub-section]
[Description]

## Dependencies
[Any packages this unit needs that aren't already installed. List them explicitly with reasons. If none, write "None".]
- package-name (reason)

## Verify when done
[A list of specific conditions that must be true before this unit is complete. Always include the standard checks below, plus feature-specific ones. **If you found relevant scripts in `package.json` (e.g., test, lint, ultracite), add them here.**]
- [ ] [Feature specific condition one]
- [ ] [Feature specific condition two]
- [ ] No TypeScript errors
- [ ] No console errors
- [ ] Responsive at mobile and desktop
- [ ] Build passes (`npm run build` or equivalent)
- [ ] [Dynamically added check: e.g., `npm run lint` passes]
- [ ] [Dynamically added check: e.g., `npm run test` passes]
- [ ] New UI component types captured in `context/ui-registry.md` (if this unit introduced any)
```