# Seven-File-Context Skills

A collection of agent skills for **spec-driven AI software development** — combining [JavaScript Mastery's six-file context system](https://www.youtube.com/watch?v=14RP8liACqo) and [mattpocock's grill-me-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md) into a complete pipeline.


| Skill | Phase | What it does |
|---|---|---|
| **project-architect** | Design | Relentlessly interviews you to pressure-test a new project idea before code is written. Identifies the tech stack and relevant agent skills. |
| **project-synthesizer** | Spec | Synthesizes the architectural conversation into the Seven-File Context System (`project-overview.md`, `architecture.md`, `ui-context.md`, `ui-registry.md`, `code-standards.md`, `ai-workflow-rules.md`, `progress-tracker.md` + `AGENTS.md` with available skills). |
| **build-planner** | Plan | Breaks the project into sequenced, scoped build units and writes the roadmap to `context/specs/00-build-plan.md`. |
| **feature-spec-generator** | Spec | Generates a detailed 6-section implementation spec (Goal, Design, Implementation, Dependencies, Skills, Verify) for a single unit. |
| **implement-feature** | Build | Executes spec-driven development: branches from main, implements exactly what the spec says, loads relevant skills, runs verification checks, and updates the progress tracker. |
| **conventional-commit** | Wrap | Analyzes the diff and proposes a Conventional Commits message. |
| **imprint** | Maintain | Captures UI component patterns to `ui-registry.md` for visual consistency across sessions. Supports audit mode for existing codebases. |
