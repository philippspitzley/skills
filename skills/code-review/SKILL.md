---
name: code-review
description: After building a feature, verify it matches what was planned, respects the system architecture and design standards, and is ready for production. Reports issues clearly so the developer decides what to fix. Run this after every feature implementation.
---

# Review

Run this after every feature, before moving on. It reports issues — it does not fix them. The developer decides what matters.

## Step 1 — Understand What Should Have Been Built

Read in this order:

1. The spec file from `context/specs/` for the feature being reviewed
2. Any relevant context files: `context/architecture.md`, `context/code-standards.md`, `context/ui-registry.md`

If no spec file exists, ask the developer to describe what the feature was supposed to do before reviewing.

## Step 2 — Discover What Changed

Run `git diff main...HEAD --name-only` to identify all files changed in this feature branch. Read each changed file.

## Step 3 — Review in Three Layers

### Layer 1 — Does it match the plan?

Compare what was built against what was planned.

- Every part of the spec — is it all there?
- The decisions made during planning — are they reflected in the code?
- The scope — did the implementation stay within bounds or add things that were not asked for?

Flag anything planned but missing. Flag anything built but not planned.

### Layer 2 — Does it respect the system?

- **Architecture boundaries** — does code in the right place own the right responsibilities? No UI logic in API routes. No DB calls in components.
- **Design system** — are the correct tokens, classes, and patterns used? Any hardcoded values that should be variables?
- **Code standards** — naming conventions, file organisation, TypeScript strictness, error handling patterns — do they match what the project established?
- **Existing patterns** — does this feature introduce a new pattern when an existing one should have been used?

### Layer 3 — Is it production ready?

- Error handling — are errors caught and handled or does the feature silently fail?
- Edge cases — empty states, loading states, missing data — are these handled?
- Console errors — any errors or warnings in the browser or terminal?
- Obvious bugs — anything that would clearly break for a real user?

## Step 4 — Report What You Found

Produce a clear report. See [references/report-template.md](references/report-template.md) for the format. Label each issue with its severity using [references/severity-guide.md](references/severity-guide.md).

## Step 5 — Let the Developer Decide

Stop after presenting the report. Do not fix or suggest fixes unless asked. Wait for the developer to:

- Ask you to fix a specific issue
- Tell you an issue is intentional and can be ignored
- Confirm everything is resolved and ready to move on
