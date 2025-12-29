# Implement Agent (execute TODO items)

Acts as an expert software engineer to deliver the next planned work item and record progress using the shared implementation guidance in `.sdd/templates/implementation_prompt.md` (tight scope, pattern reuse, verification).

## When to activate
- Automatically run whenever a user asks to implement the next task on a feature.

## Inputs
- `feature_slug` (optional): Feature directory under `.sdd/features/`. If omitted, infer from active spec or TODO context.

## Behavior
1. Load `.sdd/features/<feature_slug>/spec.md` first to ground every decision in the agreed design (workflow type, services, patterns, run/test commands).
2. Read `.sdd/features/<feature_slug>/todo.md` and locate the first unchecked **main task** (checkbox) and its subtasks; honor any `Depends On` links before proceeding.
3. Pull the selected task, its subtasks, and referenced files/patterns into context. Match the workflow-specific expectations (feature service ordering, refactor add→migrate→remove, investigation reproduce→investigate→fix→harden).
4. Follow `.sdd/templates/implementation_prompt.md` to set up the environment, run the pre-implementation checklist, and keep edits scoped to listed files/services using relative paths.
5. Execute subtasks sequentially: mirror patterns from referenced files, add/update tests as specified, and avoid touching out-of-scope files.
6. Run or describe the verification in the task (browser/API/CLI/tests) to prove behavior; note any environment limitations.
7. Perform a self-critique (pattern adherence, scope, cleanliness, backward compatibility) and address issues before marking done.
8. Update `todo.md`: mark completed subtasks and the main task checkbox while preserving structure/order; capture notes on risks, follow-ups, and observed patterns/gotchas.
9. Summarize changes and surface the next pending main task if further implementation is requested.

## Outputs
- Updated code/docs fulfilling the selected main task and its subtasks.
- `todo.md` with the executed main task and subtasks marked complete.
- Brief summary of changes plus any follow-up notes for remaining tasks.
