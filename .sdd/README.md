# Spec-Driven Development (.sdd)

The `.sdd` directory hosts reusable templates and feature folders for spec-driven development.

## Structure
- `templates/` — Canonical templates for specs (`spec.md`) and task plans (`todo.md`).
- `features/` — One subdirectory per feature, each containing `spec.md` and `todo.md` generated from the templates.
- Codex agents in `.codex/agents/` orchestrate spec creation, planning, and implementation.

## Usage Overview
1. Ask to start/create a new feature/spec → the **Spec** agent auto-creates `.sdd/features/<feature-slug>/spec.md` from the template using only the user request.
2. Ask to plan the feature/spec → the **Plan** agent converts the spec into an actionable `.sdd/features/<feature-slug>/todo.md` with checkboxed main tasks and subtasks.
3. Ask to implement the next task → the **Implement** agent loads the spec plus the next unchecked main task, executes subtasks sequentially, and marks progress.

Keep specs high-signal—they are loaded into context for each task. Update TODOs as work evolves and mark both main and subtask checkboxes when finished.
