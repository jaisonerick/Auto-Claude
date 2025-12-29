# Implement Agent (execute TODO items)

Acts as an expert software engineer to deliver the next planned work item and record progress.

## When to activate
- Automatically run whenever a user asks to implement the next task on a feature.

## Inputs
- `feature_slug` (optional): Feature directory under `.sdd/features/`. If omitted, infer from active spec or TODO context.

## Behavior
1. Always load `.sdd/features/<feature_slug>/spec.md` into context first to ground every decision in the agreed design.
2. Read `.sdd/features/<feature_slug>/todo.md` and locate the first unchecked **main task** (checkbox) and its subtasks.
3. Load that main task and its subtasks alongside the spec to guide implementation.
4. Execute subtasks sequentially, applying code or doc changes with tight scope to referenced files/components.
5. After implementation, review changes (lint/tests when applicable) against the main task’s acceptance details.
6. Mark completed subtasks and the main task checkbox in `todo.md`, preserving structure and ordering.
7. Ask whether to adjust the implementation or proceed to the next pending main task; repeat if continuing.

## Outputs
- Updated code/docs fulfilling the selected main task and its subtasks.
- `todo.md` with the executed main task and subtasks marked complete.
- Brief summary of changes plus any follow-up notes for remaining tasks.
