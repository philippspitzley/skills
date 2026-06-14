---
name: implement-feature
description: Implements a specific feature unit based on its spec file. Manages git branching from main, ensures sequential unit execution, updates the progress tracker, and adheres to scope.
---

# Feature Implementer

Your goal is to execute spec-driven development. You will take a completed spec file provided by the user and build exactly what it describes—no more, no less.

## 0. Identify the Spec File
Check if the user explicitly provided the spec file or feature unit they want to build in their prompt.
- **If not provided:** STOP immediately. Ask the user: *"Which feature spec file would you like me to implement?"* Do NOT proceed to the next steps until the user specifies it.
- **If provided:** Proceed to step 1.

## 1. Pre-flight Git Check (CRITICAL)
Before doing anything, you MUST ensure the working directory is clean.
1. Run `git status --porcelain`.
2. **If there are uncommitted files:** STOP immediately. Tell the user: *"You have uncommitted changes. Please commit or stash them before we start a new feature."* Do NOT proceed until the user gives you the go-ahead and the working directory is clean.
3. **If clean:** Proceed to step 2.

## 2. Branch Creation & Sequence Validation
You must branch from an up-to-date `main` branch and ensure the build sequence is being followed.
1. Switch to the main branch and update it: `git switch main` followed by `git pull` (if a remote exists).
2. Identify the unit number of the requested feature (e.g., `02` from `02-auth-pages`).
3. **Sequence Check:** If this is not the first unit (i.e., greater than `01`), check `context/progress-tracker.md` or `git log` on the `main` branch to verify that the *previous* unit (e.g., `01`) has already been completed and merged.
4. **If the previous unit is NOT in `main`:** STOP. Tell the user: *"It looks like the previous unit has not been merged into main yet. Spec-driven development requires sequential building."* Do NOT proceed unless the user explicitly overrides this.
5. **If verified:** Create and switch to the new feature branch using `git switch -c feature/[unit-number]-[feature-name]`.

## 3. Context & Spec Loading
Use your `read` tool to load:
1. The requested spec file (e.g., `context/specs/[unit-number]-[feature-name].md`). This is your master instruction set for this session.
2. The core context files (if you haven't already): `context/architecture.md`, `context/ui-context.md`, `context/ui-registry.md`, `context/code-standards.md`, and `context/ai-workflow-rules.md`.
3. If the spec file contains a `## Skills` section, load those skills using the `skill` tool before implementation begins.

## 4. Update Progress Tracker
Read `context/progress-tracker.md`. Update it to reflect the current state:
- Update "Current Goal" to match this feature.
- Move this feature into the "In Progress" section.
- Save the file.

## 5. Strict Implementation
Build the feature exactly as described in the spec file. 
- **Scope Control:** Do NOT go beyond the scope of this feature. Do not "fix" unrelated things, do not refactor out-of-scope files, and do not add speculative features not explicitly requested in the spec.
- **Dependencies:** Only install the dependencies explicitly listed in the spec file.
- **Boundaries:** Respect the system boundaries defined in `architecture.md`.
- **UI Consistency:** Before building any UI component, check `context/ui-registry.md` for existing patterns. Match them exactly. After building a new UI component type, run `/imprint` to capture its pattern in `context/ui-registry.md`.

## 6. Verification
1. Go through every single item in the **"Verify when done"** checklist in the spec file.
2. Run any automated checks (lint, test, build) as required.
3. Present the finished work and the completed checklist to the user.

## 7. Independent Review
Launch an independent review subagent to verify the implementation.
1. Use the `task` tool to launch a subagent with this prompt:

```
Load the `review` skill. Then review the current feature implementation:
1. Spec file: context/specs/[unit-number]-[feature-name].md
2. Changed files: run `git diff main...HEAD --name-only`
3. Context files: context/architecture.md, context/code-standards.md, context/ui-registry.md
Return the full review report.
```

2. The subagent has no memory of the implementation — only the code, the spec, and the project rules. This ensures independence.
3. Present the review report to the developer.

## 8. Finalize
1. **Wait for the developer to decide:** The developer may fix issues from the review or accept the implementation as-is.
2. **Wait for explicit confirmation:** Ask the user: *"Are you happy with the implementation? Should I proceed to commit?"* Do NOT proceed until the user explicitly confirms.
3. **Finalize:** ONLY after the user gives explicit confirmation:
   - Update `context/progress-tracker.md` to move this feature to "Completed" and clear the "Current Goal".
   - If any new UI component patterns were introduced, run `/imprint` to update `context/ui-registry.md`.
   - Invoke the `conventional-commit` skill to analyze your changes and propose a commit message to the user.