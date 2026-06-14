---
name: architect
description: Interview the user to plan a greenfield project. Use when starting a new project or when the user says "plan a new project" or "architect this idea".
---

# Project Architect

Pressure-test the user's plan and resolve dependencies in the design tree before code is written.

## Protocol

1. Ask questions **ONE at a time**. Wait for response before next.
2. Provide your **recommended answer** as a baseline for each question.
3. **Push back** on vague or overloaded answers. Propose precise terminology.
4. **Invent edge-case scenarios** to stress-test boundaries.

## Workflow

Work through **every topic below**. Track which are resolved. Do not skip topics or hand off early.

### Product
- One-sentence description of what the app does
- Primary user and core need
- Step-by-step flow from sign-up to core value
- Top 3 features for v1
- Explicitly out of scope

### Technical
- Full tech stack and rationale
- Data storage (database, file, cache)
- Auth and access model
- System boundaries (folder/module ownership)
- Architecture rules that must never be violated
- Most complex technical areas
- Relevant agent skills for this stack

### Design
- Visual language (colors, typography, spacing)
- UI component library
- High-level layout

### Process
- Major features broken into buildable units
- Build order
- "Done" criteria per unit

## Completion

Once all topics are resolved, summarize the full plan and ask the user to confirm. Only after explicit confirmation, load the `context-gen` skill to produce the Seven-File Context System.