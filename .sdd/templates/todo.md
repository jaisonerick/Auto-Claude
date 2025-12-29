# TODOs for {{SPEC_NAME}}

> Generate tasks after the spec is drafted. Keep tasks granular, sequenced, and explicitly verifiable.

## Task Flow
- Ground every task in the spec’s workflow type and phase ordering:
  - **Feature**: backend/API → worker/jobs → frontend/UI → integration.
  - **Refactor/Migration**: add new → migrate consumers → remove old → cleanup.
  - **Investigation**: reproduce → investigate/root-cause → fix → harden/tests.
- Each task below should include:
  - **Task**: Concise description of the work with a main checkbox.
  - **Service/Phase**: The service or phase this task belongs to; respect dependencies between phases.
  - **Depends On**: Predecessor tasks/phases that must finish first.
  - **Files**: Paths to modify/create plus patterns to reference.
  - **Verification**: Browser/API/CLI command to prove the task works.
  - **Context**: Links or notes relevant to the task (discovery/ideation/research excerpts welcome).
  - **Prompt**: Guidance to load into the LLM context when executing.
  - **Subtasks**: Markdown checkboxes to track completion within the task. Each subtask should stay within one service and carry its own verification step when possible.

## Tasks
1. - [ ] **Task Name Here**
   - **Service/Phase**: _e.g., Backend API, Worker, Frontend, Integration_
   - **Depends On**: _Upstream tasks or phases (if any)_
   - **Files**: _Add paths to modify/create and any pattern files to mirror_
   - **Verification**: _Command/API/browser check (include expected status/output)_
   - **Context**: _Add notes, references, or links_
   - **Prompt**: _Instruction snippet to provide to Codex/LLM_
   - **Subtasks**:
     - [ ] Step 1: ... (include files/patterns)
     - [ ] Step 2: ... (include verification)
     - [ ] Step 3: ...

2. - [ ] **Next Task Name**
   - **Service/Phase**: _Name and list any dependencies on prior tasks_
   - **Depends On**: _Explicit predecessor tasks/phases_
   - **Files**: _Add paths to modify/create and any pattern files to mirror_
   - **Verification**: _Command/API/browser check (include expected status/output)_
   - **Context**: _Add notes, references, or links_
   - **Prompt**: _Instruction snippet to provide to Codex/LLM_
   - **Subtasks**:
     - [ ] Step 1: ... (single service, keep scope small)
     - [ ] Step 2: ... (call out acceptance/edge cases)
     - [ ] Step 3: ...

> Repeat tasks as needed. Mark main and subtask checkboxes as work is completed.
