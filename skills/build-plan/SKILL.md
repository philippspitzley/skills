---
name: build-plan
description: Breaks down a project into a sequenced, high-level build plan for spec-driven development. Generates a structured overview in context/specs/00-build-plan.md.
---

# Build Planner

Your goal is to practice spec-driven development by breaking the user's project into specific, scoped units before any code is written. This skill generates the high-level roadmap, NOT the detailed implementation specs.

## Prerequisites
1. Use your `read` tool to load `context/project-overview.md` to understand features and scope.
2. Use your `read` tool to load `context/architecture.md` to understand the tech stack and system boundaries.
3. Use your `read` tool to load `context/ui-registry.md` to understand any existing component patterns (if it exists — it will be empty for new projects but critical when extending existing ones).
*(If these files do not exist, ask the user to provide their feature list and tech stack).*

## What is a Unit?
A unit is a single, scoped piece of work small enough to build in one focused session. 
**Bad Unit:** "Build the dashboard" (This is a phase, not a unit).
**Good Unit:** "Project sidebar with My Projects and Shared tabs, empty placeholder states, and open/close behavior. No API calls."

**Strict Rules for Units:**
- It produces ONE visible result.
- It stays within ONE system boundary (e.g., do not mix UI changes with database schema changes).
- Units that always get done together in the same session must be merged.
- Units with no standalone visible result must be merged with adjacent units.

## Rules for Ordering Units
The sequence of units is critical. You must strictly adhere to this order of operations:
- **Dependencies first:** Never build on top of something that doesn't exist yet. If B requires A, A comes first.
- **Security before functionality:** Auth and access control MUST come before the features they protect.
- **Backend before frontend wiring:** Build API routes first, then wire the UI to them. Do not combine both in one unit.
- **UI shells before real data:** Build component structures with placeholder data first, then connect them to real APIs later.
- **JIT Dependencies:** Only install a package in the unit where it first unlocks real behavior. Do not install everything upfront.

## Workflow

1. **Analyze & Propose:** Based on the features and stack, draft a numbered list of units. 
2. **Self-Validate:** Before showing the user, verify your draft:
   - Does everything this unit depends on already exist in a previous unit? (If no, reorder).
   - Are any two adjacent units always done in the same session? (If yes, merge them).
3. **Review & Refine:** Present the validated draft to the user. Ask them to review it carefully to see if the sequence makes sense or needs adjustment.
4. **Generate:** Once the user explicitly approves the sequence, create the directory `context/specs/` and write the final plan to `context/specs/00-build-plan.md`.

## Output Format (`context/specs/00-build-plan.md`)
Format the approved build plan as a concise Markdown document. This file acts as an overview. For each unit, include only:
- **Unit [Number]: [Name]**
- **Description:** [A concise 1-2 sentence summary of what this unit accomplishes]
- **Dependencies:** [Any preceding units or setup that must exist first]

Do NOT include a detailed "definition of done" or implementation details here. Those belong in separate, granular spec files.