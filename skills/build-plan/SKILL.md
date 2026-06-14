---
name: build-plan
description: Breaks down a project into a sequenced, high-level build plan for spec-driven development. Generates a structured overview in context/specs/00-build-plan.md.
---

# Build Planner

Your goal is to practice spec-driven development by breaking the user's project into specific, scoped units before any code is written. This skill generates the high-level roadmap, NOT the detailed implementation specs.

## Prerequisites
1. Load `context/project-overview.md` (features & scope)
2. Load `context/architecture.md` (tech stack & boundaries)
3. Load `context/ui-registry.md` (component patterns — exists for extensions, empty for new projects)
*If files don't exist, ask user for features and stack.*

## What is a Unit?
A unit is one visible, scoped deliverable built in a single session—NOT a phase.
- ✅ "Project sidebar with My Projects/Shared tabs, placeholder states, open/close. No API calls."
- ❌ "Build the dashboard" (too broad)

**Rules:** One visible result. One system boundary. Always-together work merges. No standalone-result work merges with adjacent units.

## Rules for Ordering Units
The sequence of units is critical. You must strictly adhere to this order of operations:
- **Dependencies first:** Never build on top of something that doesn't exist yet. If B requires A, A comes first.
- **Security before functionality:** Auth and access control MUST come before the features they protect.
- **Backend before frontend wiring:** Build API routes first, then wire the UI to them. Do not combine both in one unit.
- **UI shells before real data:** Build component structures with placeholder data first, then connect them to real APIs later.
- **JIT Dependencies:** Only install a package in the unit where it first unlocks real behavior. Do not install everything upfront.

## Workflow

1. **Draft:** Propose numbered units based on features/stack.
2. **Validate:** Ensure all dependencies exist and adjacent units are merged per rules above.
3. **Review:** Present draft to user for sequence confirmation.
4. **Generate:** On approval, write to `context/specs/00-build-plan.md`.

## Output Format (`context/specs/00-build-plan.md`)
Format the approved build plan as a concise Markdown document. This file acts as an overview. For each unit, include only:
- **Unit [Number]: [Name]**
- **Description:** [A concise 1-2 sentence summary of what this unit accomplishes]
- **Dependencies:** [Any preceding units or setup that must exist first]

Do NOT include a detailed "definition of done" or implementation details here. Those belong in separate, granular spec files.
