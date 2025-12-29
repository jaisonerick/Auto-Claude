# Implementation Guidance

Use this prompt when executing a TODO task to stay consistent with the spec/TODO structure and verification expectations.

## Core Principles
- Work on **one main task and its subtasks at a time**; do not expand scope or switch services mid-task.
- Follow the workflow dependencies from the spec/TODO (e.g., backend → worker → frontend → integration; add → migrate → remove for refactors; reproduce → investigate → fix → harden for investigations).
- Keep changes scoped to the files and patterns named in the spec and TODO; use relative paths and confirm paths exist with `ls` before editing.
- Mirror existing conventions: naming, testing style, error handling, logging, and API shapes from referenced pattern files.
- Prefer small, verifiable increments; run checks as you go.

## Environment & Context Setup
1. Confirm the working directory and list the feature folder (e.g., `pwd && ls .sdd/features`).
2. Read the active spec and TODO:
   - `cat .sdd/features/<feature-slug>/spec.md`
   - `cat .sdd/features/<feature-slug>/todo.md`
3. Identify the workflow type and phase ordering from the spec; ensure predecessor phases/tasks are complete before proceeding.
4. Locate pattern references mentioned in the spec/TODO and skim them before editing to match imports, error handling, and structure.
5. Note any run/test commands, ports, or environment variables in the spec for the services you will touch.
6. Locate the next unchecked **main task** and its subtasks. Ensure upstream phases are complete before proceeding.

## Pre-Implementation Checklist
- Re-state the selected main task and subtask you are executing.
- List acceptance criteria and verification steps from the spec/TODO that apply to this subtask.
- Call out edge cases, risk areas, and data/compatibility concerns relevant to the files you will touch.
- Identify tests you expect to add or update and where they should live.
- Note any additional references (docs, pattern files) to review before coding.

## Executing Subtasks
- Apply edits only to the files listed for the current task/subtask; do not mix concerns across services.
- For new files, follow naming and directory conventions from the referenced patterns.
- For risky changes, prototype in a small helper or draft before touching shared paths.
- Stay within the workflow’s phase expectations:
  - **Feature**: Respect backend/worker/frontend/integration ordering.
  - **Refactor/Migration**: Add new → migrate consumers → remove old → cleanup; keep old behavior working until removal.
  - **Investigation**: Produce a findings note (e.g., INVESTIGATION.md) capturing root cause before implementing fixes.
- Keep commits coherent: finish the subtask end-to-end (code + tests/docs) before moving on.

## Verification & Quality
- Execute the verification noted in the TODO (tests, API calls, CLI, or browser steps). Capture commands and outcomes.
- Add or update tests alongside code changes; prefer the nearest existing test suite and fixtures.
- Perform a self-critique before marking complete:
  - Patterns match referenced files; naming/imports/error handling follow convention.
  - Scope adherence: only intended files changed/created; requirements and acceptance criteria met.
  - Cleanliness: no debug logs, commented-out blocks, or hidden configuration changes; backward compatibility maintained.
  - Risks/issues noted and addressed where possible.

## Progress Recording
- After completing a subtask, mark its checkbox (and the parent main task when all subtasks are done) in `.sdd/features/<feature-slug>/todo.md`.
- Summarize what changed, what was verified (with commands/results), and any follow-ups or risks to watch next.
- Capture any useful patterns or gotchas discovered so they can be reused by later tasks.
