# Auto Claude Architecture Overview

## High-level layout
- **Backend** (`apps/backend/`): Python-based autonomous coding framework that runs multi-session builds via specs and orchestrates agents, QA, and project automation.
- **Frontend** (`apps/frontend/`): Electron + React desktop UI that drives the framework and provides workspace management, terminals, and feature flows.

## Backend
- Entry point: `apps/backend/run.py` exposes the CLI for running specs, merging/reviewing builds, and managing workspaces, built around multi-session autonomous coding flows and Git worktrees for isolation.【F:apps/backend/run.py†L1-L76】
- Project structure: agent execution, analysis, CLI, integrations, prompts, QA, and spec handling are organized into focused packages under `apps/backend/`.【F:apps/backend/README.md†L82-L117】
- AI client layer: `apps/backend/core/client.py` centralizes Claude SDK configuration, auth, and tool selection (built-in file operations, optional MCP tools for Linear, Graphiti memory, Context7 docs, Puppeteer/Electron automation) to enforce sandboxing and per-agent tool scopes.【F:apps/backend/core/client.py†L1-L200】
- Prompts: reusable prompt templates for planners, coders, QA reviewers/fixers, ideation, roadmap discovery, and specs live in `apps/backend/prompts/`, with additional MCP tool definitions in `apps/backend/prompts/mcp_tools/` and packaged prompts under `prompts_pkg`. These files are loaded by agent flows to seed AI calls.

## Frontend
- Desktop stack: Electron main process, preload, and React renderer organized in a feature-based architecture under `apps/frontend/src/`, covering agent management, terminals, projects, settings, roadmap/ideation, insights, changelog, GitHub, worktrees, and onboarding flows.【F:apps/frontend/README.md†L47-L91】
- Purpose: Provides the desktop UI that communicates with the backend, surfaces progress, and manages local projects/worktrees through feature modules and shared utilities.

## AI workflows & execution flow
- AI calls are funneled through the backend `create_client` helper, which injects OAuth credentials, selects Claude models, and attaches MCP tools based on agent type and project capabilities, ensuring all agent sessions share consistent security and context settings.【F:apps/backend/core/client.py†L136-L200】
- Agents use prompt templates from `apps/backend/prompts/` to run planning, coding, QA review, and follow-up steps. The CLI (`apps/backend/run.py`) triggers these sessions according to the selected spec and coordinates workspace isolation and recovery logic.【F:apps/backend/run.py†L6-L24】
- Frontend feature modules invoke backend commands and display status, terminals, and analysis results, while Electron IPC handlers in `src/main` manage process communication and secure exposure of Node capabilities to the renderer.【F:apps/frontend/README.md†L52-L91】

## Where to start
- Run the backend CLI (`python apps/backend/run.py --list` then `--spec <id>`) to exercise the autonomous pipeline.【F:apps/backend/run.py†L15-L24】
- Start the frontend (`npm run dev` in `apps/frontend`) to explore the UI and IPC-based controls that drive backend sessions.【F:apps/frontend/README.md†L25-L36】【F:apps/frontend/README.md†L93-L109】
