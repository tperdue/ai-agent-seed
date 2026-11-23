---
name: bootstrap-project
description: Initialize a fresh Day-0 repository by interviewing the user about the project goal and tech stack, resolving Context7 library IDs, and hydrating all .agents memory and design files.
---

# Day-0 Project Bootstrap Protocol

Run this skill whenever `.agents/memories/project-arch.md` contains `[UNINITIALIZED]`.

## Step 1: Gather Project Parameters
If the user has not already specified them in their prompt, ask a concise set of questions covering:
1. **Core Goal & Deliverable:** What are we building (web app, desktop app, CLI, API, data pipeline)?
2. **Primary Tech Stack:** Language, framework, database/storage, UI library, and build/packaging tool.
3. **Key Constraints:** Local-first/offline, performance targets, auth/security boundaries, or deployment target.

## Step 2: Resolve Context7 Library IDs
For every library/framework in the chosen stack:
1. Call Context7 `resolve-library-id` to obtain the exact `/org/project` ID (e.g., `/websites/duckdb`, `/tanstack/table`).
2. Populate `.agents/memories/context7_references.md` with the verified IDs and primary query scopes, removing `[UNINITIALIZED]`.

## Step 3: Hydrate Project Memory & Design Files
Using the user's answers and verified library patterns:
1. **`project-arch.md`:** Fill in Project Overview, Directory Topology, Core Data Flows, and Non-Negotiable Technical Constraints. Remove `[UNINITIALIZED]`.
2. **`DESIGN.md`:** Fill in the UI/UX layout zones or API surface contracts. Remove `[UNINITIALIZED]`.
3. **`decisions.md`:** Replace `ADR-000` with `ADR-001` (and any additional foundational ADRs) capturing why the core stack and architecture boundaries were chosen.
4. **`handoff.md`:** Set Phase 1 scaffolding tasks as the active queue.

## Step 4: Confirm & Begin Scaffolding
Present a brief summary of the initialized architecture and ADR log to the user, then immediately proceed to scaffolding the project files.
