# {{SPEC_NAME}}

## Overview
- **Problem & Outcome**: What user/business problem does this solve and what success looks like.
- **Target Users & Value**: Who benefits (personas/roles) and the core value proposition.
- **Workflow Type**: feature | refactor | investigation | migration | simple — explain why this type fits.

## Discovery Snapshot
- **Project Type & Maturity**: web/mobile/cli/library/api/etc. plus current state (idea/prototype/mvp/growth/mature).
- **Tech Stack**: Primary languages/frameworks and key dependencies relevant to this work.
- **Existing Behaviors**: What similar features or patterns already exist.
- **Constraints**: Time, performance, compliance, platform, or dependency limits.

## Scope
- **In Scope**: Capabilities and behaviors this work will deliver.
- **Out of Scope**: Explicit exclusions to prevent scope creep.

## Services and Architecture
- **Services Involved**: Primary and supporting services plus their roles.
- **Architecture**: High-level components, data flow, integrations, and contracts.
- **Security & Privacy**: Threats, mitigations, and access control expectations.

## Files and Patterns
- **Files to Modify**: Paths and the precise changes expected.
- **Files to Reference**: Patterns to copy or stay consistent with.
- **Patterns to Follow**: Naming, testing, error-handling, and framework conventions from referenced files.
- **Environment Details**: Run commands, ports, env vars, and entrypoints per service.

## Requirements
- **Functional Requirements**: Numbered list with acceptance notes for each.
- **Edge Cases**: Scenarios to guard against and how to handle them.

## Implementation Plan
- **Milestones/Phases**: Ordered steps or service-level phases respecting dependencies.
  - Feature flow: backend/API → worker/jobs → frontend/UI → integration.
  - Refactor/migration flow: add new → migrate consumers → remove old → cleanup.
  - Investigation flow: reproduce → investigate/root-cause → fix → harden/tests.
- **Detailed Steps**: Concrete actions per phase, aligned to files and patterns above.
- **Dependencies**: External services, migrations, feature flags, or sequencing rules.

## Environment & Operations
- **How to Run**: Dev commands and entrypoints per service (include ports/env vars if known).
- **Observability**: Logging, metrics, and alerts needed to verify health.
- **Data/Schema**: New/changed models, migrations, and backward-compatibility notes.

## Validation & QA
- **Acceptance Criteria**: Checklist tied to functional requirements.
- **Testing Strategy**: Unit, integration, E2E/manual flows with target files or commands.
- **Verification Steps**: Browser/API/CLI checks that prove the change works.

## Decision Record
- **Chosen Approach**: Summary of the selected solution.
- **Alternatives Considered**: Options rejected and why.
- **Trade-offs**: Complexity, cost, risk, and maintainability notes.

## Risks and Mitigations
- **Risks**: High-impact or uncertain areas.
- **Mitigations**: Actions to reduce likelihood or blast radius.

## Open Questions
- Outstanding questions, unknowns, or follow-ups.

## Appendices
- Links to diagrams, tickets, research, or prototypes (include roadmap/discovery/ideation insights if available).
