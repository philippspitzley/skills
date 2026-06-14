---
name: implement-feature
description: Implements a specific feature unit based on its spec file. Manages git branching from main, ensures sequential unit execution, updates the progress tracker, and adheres to scope.
---

# Feature Implementer

Execute spec-driven development: build exactly what the spec describes—no more, no less.

## 0. Get Spec File
If user didn't provide spec file, ask: *"Which feature spec file would you like me to implement?"* Wait for answer before proceeding.

## 1. Git Pre-flight
Run `git status --porcelain`. If uncommitted files exist, stop: *"Please commit or stash changes first."*

## 2. Branch & Sequence
1. `git switch main && git pull`
2. Extract unit number from feature name (e.g., `02` from `02-auth-pages`)
3. If unit > 01, verify previous unit merged to main via `progress-tracker.md` or `git log`
4. If not merged: *"Previous unit not merged. Sequential building required."* (unless user overrides)
5. `git switch -c feature/[unit-number]-[feature-name]`

## 3. Load Context
Read:
- Spec file: `context/specs/[unit-number]-[feature-name].md`
- Core files: `architecture.md`, `ui-context.md`, `ui-registry.md`, `code-standards.md`, `ai-workflow-rules.md`
- Load any skills from spec's `## Skills` section

## 4. Update Progress
In `progress-tracker.md`: set "Current Goal" to this feature, move it to "In Progress".

## 5. Implement
Build exactly as spec describes:
- **Scope:** No extra features, fixes, or refactors beyond spec
- **Dependencies:** Only spec-listed deps
- **Boundaries:** Respect `architecture.md` boundaries
- **UI:** Check `ui-registry.md` for patterns first; run `/imprint` after new component types

## 6. Verify
1. Complete every item in spec's "Verify when done" checklist
2. Run lint/test/build as needed
3. Present work + completed checklist

## 7. Independent Review
Launch review subagent via `task` tool with prompt:
```
Load `review` skill. Review implementation:
- Spec: context/specs/[unit-number]-[feature-name].md
- Changed: git diff main...HEAD --name-only
- Context: architecture.md, code-standards.md, ui-registry.md
Return full review report.
```
Present report to developer.

## 8. Finalize
Wait for explicit user confirmation: *"Happy with implementation? Should I commit?"*
Only after confirmation:
1. Move feature to "Completed" in `progress-tracker.md`
2. Run `/imprint` if new UI patterns introduced
3. Use `conventional-commit` skill to propose commit message