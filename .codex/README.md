# Codex Agents for Spec-Driven Development

This directory defines Codex agents that automate the spec-driven development (SDD) workflow that lives in `.sdd/`.

## Structure
- `agents/` — Agent playbooks that orchestrate SDD actions.
  - `spec.md` — Auto-creates feature specs from user requests (no slug input required).
  - `plan.md` — Expands specs into actionable TODO plans with checkboxed tasks and subtasks.
  - `implement.md` — Executes TODO items sequentially with the spec in context, marking progress as it goes.

Each agent assumes the templates and feature folders in `.sdd/` are the source of truth and should auto-activate when users ask to start a spec, plan work, or implement the next task.
