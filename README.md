# `agent-seed` (Day-Zero AI Agent Workspace Template)

A reusable, stack-agnostic starter template for AI-assisted software development. Drop this folder into any new repository to give coding agents (Claude Code, Cursor, Cline, Windsurf, Gemini CLI) persistent memory, Architectural Decision Records (ADRs), session handoffs, and live Context7 documentation grounding from the very first prompt.

## Why This Exists

Without structure, AI coding agents lose architectural context across sessions, silently revert settled technical choices, and hallucinate outdated SDK syntax. This template separates **universal engineering workflow plumbing** from **project-specific state**:

* **Zero Repeated Setup:** Clone or copy once; never manually write boilerplate agent instructions per repo.

* **Self-Hydrating Day-0 Bootstrap:** On first run, the `bootstrap-project` skill detects `[UNINITIALIZED]` markers, interviews you about your stack, resolves verified Context7 library IDs, and populates your architecture, design, and decision files automatically.

* **Cross-Session Continuity:** `handoff.md` and `decisions.md` keep multi-session builds aligned without re-explaining the codebase.

## Repository Structure

```
├── README.md                              # Human guide (this file)
├── AGENTS.md                              # Root entry point directing agents into .agents/
└── .agents/
    ├── agents.md                          # Master operating manual, boot sequence & skill router
    ├── system-prompt.md                   # Execution rules, Context7 mandate & zero-TODO guardrails
    ├── DESIGN.md                          # UI/UX layout & API contract spec (hydrated on Day 0)
    ├── mcp.json                           # Context7 MCP server configuration
    ├── agents/
    │   └── code-reviewer/
    │       └── agent.md                   # Architecture, security & performance review checklist
    ├── memories/
    │   ├── project-arch.md                # System topology, data flows & technical constraints
    │   ├── decisions.md                   # Chronological Architectural Decision Records (ADRs)
    │   ├── handoff.md                     # Rolling session state, blockers & next-step queue
    │   └── context7_references.md         # Verified Context7 library IDs (/org/project)
    └── skills/
        ├── bootstrap-project/
        │   └── SKILL.md                   # Day-0 interactive hydration workflow
        └── ...                            # Reusable workflow skills (brainstorming, planning, TDD, etc.)

```

## Quick Start (New Project Workflow)

1. **Copy the Template into a New Repo:**

   ```
   cp -r /path/to/agent-seed/AGENTS.md /path/to/agent-seed/.agents /path/to/your-new-project/
   
   ```

   *(If maintaining your shared skill library in a central folder, ensure `.agents/skills/` includes `bootstrap-project`, `context7-mcp`, `writing-plans`, `executing-plans`, and `verification-before-completion`.)*

2. **Verify Context7 MCP Access:**
   Ensure your IDE or CLI agent loads `.agents/mcp.json` (or has `@upstash/context7-mcp` configured globally) so the agent can resolve and query live library documentation.

3. **Run Your First Prompt:**
   Open your AI agent in the new project directory and describe what you want to build:

   > *"We're building a local-first Python + FastAPI + DuckDB + React app to analyze historical datasets. Read `AGENTS.md` and bootstrap the project."*

4. **Automatic Hydration & Scaffolding:**
   The agent will:

   * Detect `[UNINITIALIZED]` in `.agents/memories/project-arch.md` and trigger `bootstrap-project`.

   * Ask any missing clarifying questions about stack, runtime, or constraints.

   * Look up exact Context7 library IDs and save them to `.agents/memories/context7_references.md`.

   * Populate `project-arch.md`, `DESIGN.md`, `decisions.md` (`ADR-001`), and `handoff.md`.

   * Begin scaffolding the codebase.

## Ongoing Session Hygiene

* **Starting a New Session:** Tell the agent *"Resume from `.agents/memories/handoff.md`."* It will load `project-arch.md`, `decisions.md`, and `handoff.md` before touching code.

* **Recording Major Choices:** When you settle on a library, schema, or architectural boundary mid-project, ask the agent to log an ADR in `.agents/memories/decisions.md`.

* **Ending a Session:** Ask the agent to *"Update `.agents/memories/handoff.md` with current progress and next steps"* before closing your workspace.

* **Adding Project-Specific Skills:** Place domain-specific skills (e.g., `duckdb-electron-ipc` or `dbt-modeling`) inside `.agents/skills/<skill-name>/SKILL.md` and register them in `.agents/agents.md` under **Skill Routing Protocol**.