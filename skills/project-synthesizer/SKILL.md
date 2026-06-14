---
name: project-synthesizer
description: Synthesizes a planning conversation into the Seven-File Context System plus AGENTS.md index. Use when a project architecture conversation concludes and the user wants to generate the final context documentation.
---

# Project Synthesizer

Your job is to synthesize the preceding architectural conversation into a "Seven-File Context System" (plus an AGENTS.md index) that will guide coding agents through the build phase. You have a set of exact templates provided in your bundled `templates/` directory.

## Workflow

This is a sequential process. You must generate the files ONE AT A TIME, in the exact order below. After generating a file, STOP and wait for the user to review, request changes, or approve it before you move on to the next file.

1. **Create the directory:** Create a `context/` directory in the user's current working project folder.
2. **Generate and Review (Sequential):** For each file below:
   - Read its corresponding template from your `templates/` directory (links provided below).
   - Generate the file in the project's `context/` directory (or root for AGENTS.md), replacing `[bracketed text]` with specific decisions.
   - Present the contents or a summary to the user.
   - **PAUSE** and ask the user for approval or edits. Do NOT generate the next file until the user approves.

**The Order:**
1. [Project Overview Template](./templates/context/project-overview.md) -> `context/project-overview.md`
2. [Architecture Template](./templates/context/architecture.md) -> `context/architecture.md`
3. [UI Context Template](./templates/context/ui-context.md) -> `context/ui-context.md`
4. [UI Registry Template](./templates/context/ui-registry.md) -> `context/ui-registry.md`
5. [Code Standards Template](./templates/context/code-standards.md) -> `context/code-standards.md`
6. [AI Workflow Rules Template](./templates/context/ai-workflow-rules.md) -> `context/ai-workflow-rules.md`
7. [Progress Tracker Template](./templates/context/progress-tracker.md) -> `context/progress-tracker.md`
8. [AGENTS.md Template](./templates/AGENTS.md) -> `AGENTS.md` (in the root directory)

## Rules
- Do NOT alter the headings or markdown structure of the templates. Only replace the placeholder text.
- `progress-tracker.md` should be filled out with the immediate next steps based on the plan.
- **CRITICAL:** Do NOT generate all files in one go. You must wait for explicit user approval after each file.